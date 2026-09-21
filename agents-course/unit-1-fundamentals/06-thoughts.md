# Réflexions : raisonnement interne et l’approche ReAct
> Source : [Hugging Face Agents Course — Thought: Internal Reasoning and the ReAct Approach](https://huggingface.co/learn/agents-course/fr/unit1/thoughts)

Les réflexions représentent la capacité du LLM de l’agent à tirer les points importants du prompt utilisateur.

Ce processus lui permet de décomposer le problème en étapes plus petites et plus faciles à gérer, tout en considérant les expériences passées et les informations futures.

## Chaîne de réflexion (Chain-of-Thought, généralement abrégée en CoT)

Technique de prompting consistant à décomposer le problème en étapes avant de produire la réponse finale.

Cette approche aide le modèle à raisonner en interne.

## ReAct : Raisonnement + Action

Méthode qui combine le « raisonnement » (*Reasoning*) et l’« action » (*Acting*).

Elle permet au modèle de réfléchir étape par étape et d’intercaler des actions, comme l’utilisation d’outils, entre les étapes de raisonnement.

L’agent résout alors les tâches complexes en plusieurs étapes en alternant entre :

* **Réflexion** : raisonnement interne.
* **Action** : utilisation d’outils.
* **Observation** : réception des résultats de l’outil.

## Comparaison : ReAct vs CoT

| Caractéristique         | Chain-of-Thought (CoT)                  | ReAct                                                           |
| ----------------------- | --------------------------------------- | --------------------------------------------------------------- |
| Logique étape par étape | ✅ Oui                                   | ✅ Oui                                                           |
| Outils externes         | ❌ Non                                   | ✅ Oui (actions + observations)                                  |
| Convient le mieux à     | Logique, mathématiques, tâches internes | Recherche d’informations, tâches dynamiques en plusieurs étapes |
