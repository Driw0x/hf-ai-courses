# Comprendre les agents à travers le cycle Réflexion-Action-Observation
> Source : [Hugging Face Agents Course — Understanding AI Agents through the Thought-Action-Observation Cycle](https://huggingface.co/learn/agents-course/fr/unit1/agent-steps-and-structure)

Cette section explore le **workflow** de l'agent, le cycle Réflexion-Action-Observation (Thought-Action-Observation).

## Les composants de base

Fonctionnement d'un agent :

réfléchir (Réflexion) -> agir (Action) -> observer (Observation)
thinking (Thought) -> acting (Act) -> observing (Observe)

Réflexion : partie LLM de l'agent qui décide de la prochaine étape.
Action : appel de l'outil avec les arguments associés.
Observation : retour obtenu après l'action.

## Le cycle Réflexion-Action-Observation

L'agent boucle sur ces trois composants jusqu'à atteindre son objectif (`while`).

L'observation est ajoutée au contexte de l'agent et lui permet d'adapter sa prochaine réflexion.

Si l'action échoue ou si les informations sont insuffisantes, l'agent peut recommencer un nouveau cycle.

Une fois l'objectif atteint, l'agent génère une réponse finale.

Dans de nombreux *frameworks* d'agents, les règles et directives sont intégrées directement dans le *prompt* système dans lequel on définit :
* le *comportement* de l'agent
* les *outils* accessibles
* le cycle *Réflexion-Action-Observation*
