# Comment les *transformers* résolvent les tâches ?
> Source : [Hugging Face LLM Course — How Transformers solve tasks](https://huggingface.co/learn/llm-course/en/chapter1/5)

Dans [Que peuvent faire les *transformers* ?](./02-que-peuvent-faire-les-transformers.md), on a découvert le NLP et les tâches qu'ils peuvent résoudre telles que des tâches de vision par ordinateur, de reconnaissance vocale et audio et leurs applications.

Il existe plusieurs manières de résoudre ces problèmes, la résolution peut être différente selon le modèle et la stratégie adoptée, mais pour les modèles *transformers*, l'idée générale ne change pas.

Grâce à leur architecture flexible, la plupart des modèles sont des variantes des structures encodeur, décodeur ou encodeur-décodeur.

> Avant de voir les différentes variantes d'architecture, il est important de comprendre que la résolution de problèmes se fait généralement de la même manière : les données en entrée sont traitées par un modèle et la sortie est interprétée par rapport au problème. Les différences dépendent de comment les données sont préparées, quelle variante de modèle est utilisée et de comment la sortie est interprétée.

## Modèles *transformer* pour le langage

Les modèles de langage sont au cœur du NLP moderne. Ils permettent de comprendre et de générer du langage humain à partir de l'apprentissage des motifs statistiques et des relations entre mots ou tokens du texte.

Le Transformer a été initialement conçu pour la traduction machine mais depuis il est devenu l'architecture par défaut pour résoudre toutes les tâches d'IA. Certaines tâches dépendent de la structure encodeur, d'autres de la structure décodeur et d’autres de la structure encodeur-décodeur.

## Comment les modèles de langage fonctionnent

Les modèles de langage fonctionnent grâce à leur entraînement sur la prédiction de la probabilité d'un mot donné par rapport aux mots qui l'entourent. Ce qui leur permet d'obtenir une compréhension de base du langage qui pourra être généralisée aux autres tâches.

Deux approches d'entraînement :
* Modélisation par langage masqué (Masked language modeling (MLM)) : utilisée par des encodeurs comme BERT, cette approche cache aléatoirement des tokens de l'entrée et entraîne le modèle à prédire le token d'origine en s'appuyant sur les mots qui l'entourent. Ce qui permet au modèle d'apprendre le contexte bidirectionnel (regarde les mots avant et après le mot masqué).
* Modélisation causale du langage (Causal language modeling (CLM)) : utilisée par des décodeurs comme GPT, cette approche prédit le prochain token par rapport aux tokens passés de la séquence. Le modèle ne peut qu'utiliser le contexte de gauche (tokens d'avant) pour prédire le prochain token.

## Types de modèles de langage

Dans la bibliothèque Transformers, la plupart des modèles suivent trois types d'architecture :
1. Modèle à encodeur uniquement (Encoder-only models (like BERT)) : Ces modèles analysent le contexte avec une approche bidirectionnelle. Ils sont adaptés aux tâches qui nécessitent une compréhension approfondie du texte, comme la classification, la reconnaissance d'entités nommées et la réponse aux questions.
2. Modèle à décodeur uniquement (Decoder-only models (like GPT, Llama)) : Ces modèles traitent le texte de gauche à droite et sont bons pour les tâches de génération de texte. Ils complètent des phrases, écrivent des essais et génèrent même du code à partir d'un prompt.
3. Modèle à encodeur-décodeur (like T5, BART) : Ces modèles utilisent les deux approches, utilisant l'encodeur pour comprendre l'entrée et le décodeur pour générer la sortie. Ils sont excellents pour la traduction, les résumés et la réponse aux questions.

![Architecture du transformer](../../images/transformers_architecture.png)

Les modèles de langage sont généralement entraînés de manière auto-supervisée sur un jeu massif de données non annotées, puis fine-tunés sur une tâche spécifique. Cette approche, appelée apprentissage par transfert, permet aux modèles de s'adapter à différentes tâches NLP avec relativement peu de données spécifiques à la tâche.

## Génération de texte

La génération de texte consiste à créer un texte cohérent et pertinent à partir du prompt d'entrée.

GPT-2 est un modèle à décodeur uniquement capable de générer du texte convaincant (pouvant être faux) à partir d'un prompt et d'accomplir d'autres tâches de NLP, comme répondre à des questions, même s'il n'a pas été spécifiquement entraîné pour celles-ci.

![Architecture de GPT-2](../../images/gpt2_architecture.png)

1. GPT-2 utilise l’[encodage par paires d’octets](https://huggingface.co/docs/transformers/tokenizer_summary#bytepair-encoding-bpe) ([BPE](https://huggingface.co/docs/transformers/tokenizer_summary#bytepair-encoding-bpe)) pour tokeniser les mots et générer un embedding pour chaque token. Des encodages positionnels sont ajoutés aux embeddings des tokens afin d’indiquer la position de chaque token dans la séquence. Les embeddings d’entrée passent ensuite à travers plusieurs blocs de décodeur pour produire un état caché final. Dans chaque bloc de décodeur, GPT-2 utilise une couche d'auto-attention (self-attention) masquée qui le restreint à ne pouvoir prendre en compte que les tokens passés. Cela est différent du token [mask] de BERT : ici, le masque d'attention fixe à 0 le score des tokens futurs. Ces tokens sont présents dans la séquence, mais GPT-2 ne peut pas y prêter attention.

2. La sortie du décodeur passe par une tête de modélisation du langage, qui transforme les états cachés en logits représentant les scores des différents tokens possibles. Lors de l'entraînement, les prédictions sont décalées par rapport aux tokens cibles afin que le modèle apprenne à prédire le token suivant. Une perte d'entropie croisée est ensuite calculée entre les logits et les tokens attendus.

L'objectif du préentraînement de GPT-2 était basé sur la modélisation causale du langage : prédire le prochain token dans une séquence. Ce qui le rendait adapté aux tâches incluant de la génération de texte.

[Exemple de modèle causal de langage](../notebooks/language_modeling.ipynb)

## Classification de texte

La classification de texte consiste à assigner des labels prédéfinis à des textes pour l'analyse de sentiment, la classification thématique ou la détection de spam.

[BERT](https://huggingface.co/docs/transformers/model_doc/bert) est un modèle à encodeur uniquement et le premier modèle à avoir efficacement utilisé un apprentissage bidirectionnel pour mieux représenter le texte en prenant en compte les mots situés avant et après chaque mot.

1. BERT utilise la tokenisation [WordPiece](https://huggingface.co/docs/transformers/tokenizer_summary#wordpiece) pour transformer le texte en embeddings de tokens. Un token spécial [CLS] est ajouté au début de la séquence et sa représentation finale est utilisée pour les tâches de classification. Le token [SEP] permet notamment de séparer deux phrases et des embeddings de segment indiquent à quelle phrase appartient chaque token.
2. BERT a deux objectifs de préentraînement:
    * Modélisation du langage masqué (*masked language modeling* MLM): une partie des tokens d'entrée est masquée aléatoirement et le modèle doit retrouver les tokens d'origine. Il procède à un apprentissage bidirectionnel sans directement voir le token qu'il doit prédire (peut pas tricher). Les états cachés finaux correspondant aux tokens masqués passent ensuite dans un réseau *feedforward*, suivi d'un *softmax* sur le vocabulaire afin de prédire les tokens masqués
    * Prédiction de la phrase suivante (*next-sentence prediction* NSP): Le modèle doit déterminer si une phrase B suit une phrase A. Dans la moitié des cas, B est la phrase suivante et dans l'autre moitié B est une phrase choisie aléatoirement. La prédiction passe ensuite dans un réseau *feedforward* avec un *softmax* sur deux classes : `IsNext` et `NotNext`.
3. Les embeddings d'entrée passent à travers plusieurs couches d'encodeur afin de produire les états cachés finaux.

Pour utiliser BERT pour une tâche de classification de texte, on lui ajoute une tête de classification de séquence. Elle transforme l'état caché final associé au token [CLS] en scores associés aux différents labels. Une perte d'entropie croisée est ensuite calculée entre ces scores et le label attendu afin d'entraîner le modèle à prédire le label le plus probable.

état caché = représentation numérique de l'information
→ couche linéaire / feedforward = transforme la représentation
→ logits = scores numériques bruts pour les sorties possibles
→ softmax = transforme les logits en probabilités

[Exemple de classification de texte](../notebooks/sequence_classification.ipynb)

## Classification de tokens

Elle consiste à assigner un label à chaque token d'une séquence pour la reconnaissance d'entités nommées (NER) ou l'étiquetage grammatical (*part-of-speech tagging*).

Pour utiliser BERT pour ce type de tâche, on lui ajoute une tête de classification de tokens. Elle transforme l’état caché final de chaque token en scores associés aux différents labels. Une perte d’entropie croisée est ensuite calculée entre les scores et le label attendu de chaque token afin d’apprendre à prédire le label le plus probable.