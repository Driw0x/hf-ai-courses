# Observer : intégrer le retour d’information pour réfléchir et s’adapter

> Source : [Hugging Face Agents Course — Observe: Integrating Feedback to Reflect and Adapt](https://huggingface.co/learn/agents-course/fr/unit1/observations)

Perception des conséquences d'une action.

Les observations permettent de guider les prochains cycles de réflexion.

Dans la phase d'observation, l'agent :

* Collecte des retours : reçoit des données ou l'état résultant de l'action (succès/échec).
* Ajoute les résultats : intègre les nouvelles informations au contexte existant et MAJ mémoire.
* Adapte sa stratégie : planifie les réflexions et les actions futures, ou produit une réponse finale si l’objectif est atteint.

L'intégration itérative des résultats des observations permet à l'agent de rester dynamiquement aligné avec ses objectifs.

| Type d’observation        | Exemple                                                                                    |
| ------------------------- | ------------------------------------------------------------------------------------------ |
| Retour système            | Messages d’erreur, notifications de succès, codes de statut                                |
| Modifications de données  | Mises à jour de bases de données, modifications du système de fichiers, changements d’état |
| Données environnementales | Relevés de capteurs, métriques système, utilisation des ressources                         |
| Analyse des réponses      | Réponses d’API, résultats de requêtes, sorties de calcul                                   |
| Événements temporels      | Dates limites atteintes, tâches programmées terminées                                      |

## Comment les résultats sont-ils ajoutés ?

Après avoir effectué une action, le *framework* suit les étapes suivantes :

1. Analyse l'action afin d'identifier la ou les fonctions à appeler ainsi que les arguments nécessaires.
2. Exécute l'action.
3. Ajoute le résultat en tant qu'observation.
