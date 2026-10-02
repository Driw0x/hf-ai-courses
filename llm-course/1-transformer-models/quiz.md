# Quiz Chapitre 1

> Source : [Hugging Face LLM Course — Chapter 1](https://huggingface.co/learn/llm-course/chapter1/)

Ce fichier contient uniquement les erreurs, hésitations et points importants rencontrés dans les quiz de l’unité.

---

## Ungraded Quiz

### Erreur — What possible source can the bias observed in a model have?

**Erreur :**  
Oubli de **The metric the model was optimizing for is biased.**

**Correction :**  
Le biais observé dans un modèle ne provient pas uniquement des données d'entraînement. Il peut également provenir de l'objectif ou de la métrique utilisée pour optimiser le modèle. Si cette métrique favorise certains comportements ou certains groupes, le modèle peut apprendre et reproduire ce biais.

**À retenir :**
- Les biais d'un modèle peuvent avoir plusieurs sources, notamment les données et le processus d'optimisation.
- Une métrique ou un objectif d'entraînement biaisé peut orienter ce que le modèle apprend.
- Il faut donc analyser l'ensemble du pipeline d'apprentissage, et pas seulement les données, lorsqu'on cherche l'origine d'un biais.

**Note liée :**  
[Traitement du langage naturel](./notes/01-traitement-langage-naturel.md)

---