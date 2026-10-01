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