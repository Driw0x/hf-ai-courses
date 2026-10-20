# Résumé
> Source : [Hugging Face LLM Course - Summary](https://huggingface.co/learn/llm-course/en/chapter1/10)

## Concepts clés abordés

### Traitement automatique du langage naturel et LLM

On a exploré ce qu'est le traitement automatique du langage naturel (*NLP*) et comment les grands modèles de langage ont transformé ce domaine. On a vu que :

- Le NLP englobe une grande variété de tâches, allant de la classification à la génération.
- Les LLM sont des modèles puissants entraînés sur d'énormes quantités de données textuelles.
- Ces modèles peuvent accomplir plusieurs tâches au sein d'une même architecture.
- Malgré leurs capacités, les LLM ont des limites, notamment les hallucinations et les biais.

### Capacités des Transformers

On a vu comment la fonction `pipeline()` de 🤗 Transformers facilite l'utilisation de modèles pré-entraînés pour différentes tâches :

- Classification de texte, classification de tokens et réponse aux questions.
- Génération de texte et résumé.
- Traduction et autres tâches de séquence à séquence.
- Reconnaissance vocale et classification d'images.

### Architecture Transformer

Fonctionnement général des modèles Transformer:

- L'importance du mécanisme d'attention.
- La manière dont l'apprentissage par transfert permet aux modèles de s'adapter à des tâches spécifiques.
- Les trois grandes variantes architecturales : encodeur seul, décodeur seul et encodeur-décodeur.

### Architectures de modèles et leurs applications

Quelle architecture utiliser pour différentes tâches :

| Modèle | Exemples | Tâches |
|---|---|---|
| Encodeur seul | BERT, DistilBERT, ModernBERT | Classification de phrases, reconnaissance d'entités nommées, réponse extractive aux questions |
| Décodeur seul | GPT, LLaMA, Gemma, SmolLM | Génération de texte, IA conversationnelle, écriture créative |
| Encodeur-décodeur | BART, T5, Marian, mBART | Résumé, traduction, réponse générative aux questions |

### Développements récents des LLM

Les évolutions récentes du domaine :

- La manière dont les LLM ont gagné en taille et en capacités au fil du temps.
- Le concept des lois de mise à l'échelle (*scaling laws*) et la manière dont elles orientent le développement des modèles.
- Les mécanismes d'attention spécialisés qui aident les modèles à traiter des séquences plus longues.
- L'approche d'entraînement en deux phases, avec le pré-entraînement et l'ajustement aux instructions (*instruction tuning*).

### Applications pratiques

Comment ces modèles peuvent être appliqués à des problèmes du monde réel :

- Utiliser le Hugging Face Hub pour trouver et utiliser des modèles pré-entraînés.
- Exploiter l'API d'inférence (*Inference API*) pour tester des modèles directement dans votre navigateur.
- Comprendre quels modèles conviennent le mieux à des tâches spécifiques.
