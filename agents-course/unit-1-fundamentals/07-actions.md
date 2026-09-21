# Actions : permettre à l’agent d’interagir avec son environnement

> Source : [Hugging Face Agents Course — Actions: Enabling the Agent to Engage with Its Environment](https://huggingface.co/learn/agents-course/fr/unit1/actions)

Étape où l'agent interagit avec son environnement.

## Types d'actions

Il existe plusieurs types d'agents qui réalisent des actions de différentes manières :

| Type d’Agent              | Description                                                                                                         |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Agent à JSON              | L’action à entreprendre est spécifiée au format JSON.                                                               |
| Agent à code              | L’agent génère un bloc de code qui est interprété de manière externe.                                               |
| Agent à appel de fonction | Il s’agit d’une sous-catégorie de l’agent JSON qui a été affiné pour générer un nouveau message pour chaque action. |

Les actions peuvent aussi avoir des objectifs différents :

| Type d’Action                    | Description                                                                                      |
| -------------------------------- | ------------------------------------------------------------------------------------------------ |
| Collecte d’informations          | Effectuer des recherches sur le web, interroger des bases de données ou récupérer des documents. |
| Utilisation d’outils             | Effectuer des appels API, réaliser des calculs et exécuter du code.                              |
| Interaction avec l’environnement | Manipuler des interfaces numériques ou contrôler des dispositifs physiques.                      |
| Communication                    | Interagir avec les utilisateurs via le chat ou collaborer avec d’autres agents.                  |

Le LLM ne gérant que du texte et générant les paramètres nécessaires aux outils, il doit savoir s'arrêter de générer de nouveaux *tokens* lorsque l'action est terminée, afin de rendre la main à l'agent.

## L'approche Stop and Parse

Permet de garantir une sortie structurée et prévisible :

1. Génération dans un format structuré :
   L'agent produit l'action dans un format prédéfini, comme du JSON ou du code.

2. Arrêt de la génération :
   Le LLM arrête de générer des *tokens* lorsque l'action est complète afin d'éviter d'ajouter du texte inutile ou invalide.

3. Analyse de la sortie :
   Un parseur externe identifie l'outil à appeler et extrait les paramètres nécessaires.

## Agents à code

Alternative : agents [générateurs de] code.

On produit alors des blocs de code exécutables dans un langage de haut niveau comme Python au lieu d'un simple objet JSON.

Cette approche offre plusieurs avantages :
* Expressivité : Le code peut naturellement représenter une logique complexe, incluant des boucles, des conditionnels et des fonctions imbriquées, offrant ainsi une flexibilité supérieure au JSON.
* Modularité et réutilisabilité : Le code généré peut inclure des fonctions et des modules réutilisables.
* Débogage amélioré : Les erreurs de code sont plus faciles à détecter et à corriger.
* Intégration directe : Les agents à code peuvent s’intégrer directement à des bibliothèques et des API externes, permettant ainsi des opérations plus complexes comme le traitement de données ou la prise de décision en temps réel.
