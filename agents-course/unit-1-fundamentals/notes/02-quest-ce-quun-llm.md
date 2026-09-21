# Qu'est-ce qu'un LLM ?
> Source : [Hugging Face Agents Course — What are LLMs?](https://huggingface.co/learn/agents-course/fr/unit1/what-are-llms)

Un LLM comprend et génère du langage humain, basés sur l'architecture *Transformer* pour la plupart.

3 types de *transformers*:
* Encodeurs: 
    * input: texte (ou autre données)
    * output: représentation dense (embedding) du texte
    * Exemple: BERT Google
    * Cas d'utilisation: Classification de texte, recherche sémantique, reconnaissance d'entités nommées
    * Taille: Des millions de paramètres
* Décodeurs:
    * ouput: un *tokens* à la fois
    * Exemple: Llama de Meta
    * Cas d'utilisation: Génération de texte, chatbots, génération de code
    * Taille: Des milliards de paramètre
* Seq2Seq: Encodeur + Décodeur
    * Exemple: T5, BART
    * Cas d'utilisation: Traduction, résumé, paraphrase
    * Taille: Des millions de paramètre

LLM généralement basés sur des décodeurs avec des milliard de paramètres.

LLM: prédire le token suivant, étant donnée une  séquance de tokens précédents.

En anglais, environ 600 000 mots peuvent être représentés par un vocabulaire d'environ 32 000 tokens grâce à une combinaison d'unités sous-mots.

Exemple: token "intéress" et "ant", on obtient "intéressant", et avec "é", on obtient "intéressé"

Chaque LLM possède des tokens spéciaux.

Exemple: token de fin de séquence (**EOS**)

## Prédiction du token suivant

LLM sont autoregressifs : la sortie d'une passe devient l'entrée de la suivante.

Fin lorsque le token prédit est le token EOS

Boucle de décodage unique: 
* Input tokenisé, calcule d'une représentaion de la séquence qui parture des inforamtions sur la signification et la position de chaque token.
* Traitement pour savoir quel token de son vocabulaire a la plus haute proba d'apparaitre à la suite de séquence. Plusieurs stratégies de score:
    * Choix du score max
    * Beam search: choix du score max sur des séquences entières (potentiellement des tokens avec un score plus faible individuellement séléctionnés)

# Attention

Dans l'architecture Transformers, l'Attention permet de d'identifier les mots important de l'input

La **context length** correspond au nombre maximal de tokens que le LLM peut traiter.

Un prompt bien conçu permet d'augmenter les chances d'obtenir un output satisfaisant du LLM.

## Entraînement

Les LLM sont entraînés sur de grandes bases de données textuelles grâce à un objectif d'apprentissage autosupervisé ou de modélisation du langage masqué.

**Apprentissage autosupervisé :** les données d'entraînement servent elles-mêmes à créer les réponses attendues. Par exemple, à partir d'une séquence de tokens, le modèle apprend à prédire le token suivant.

**Modélisation du langage masqué :** certains tokens d'une séquence sont cachés et le modèle doit les prédire à partir du contexte. C'est notamment le principe utilisé par BERT.

Les modèles peuvent ensuite être spécialisés via un apprentissage supervisé pour des tâches comme la conversation, l'utilisation d'outils, la classification ou la génération de code.

## LLM et agents

Les agents utilisent les LLM pour comprendre et produire du langage humain.

Ils interviennent notamment dans :
* la compréhension des instructions
* le maintien du contexte
* la planification
* le choix des outils

Le LLM est le **cerveau de l'agent**.
