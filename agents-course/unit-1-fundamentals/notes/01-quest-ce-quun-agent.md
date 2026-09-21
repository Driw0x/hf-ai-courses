# Qu'est-ce qu'un agent ?
> Source : [Hugging Face Agents Course — What are Agents?](https://huggingface.co/learn/agents-course/fr/unit1/what-are-agents)

Un agent est une entité qui **comprend le langage naturel**, puis raisonne et planifie pour accomplir une demande.

Il établit un plan et l'exécute en utilisant **des outils qu'il connaît**.

Un agent est un **système capable de raisonner, de planifier et d'interagir avec son environnement**.

Il est composé :

* du modèle d'IA lui permettant de réfléchir et de planifier (LLM en général, mais Vision Language Model - VLM possible)
* des capacités et des outils qu'il peut utiliser

La qualité de l'agent sera grandement impactée par la conception des outils fournis à l'agent.

## Définition

Un Agent est un système qui utilise un modèle d’IA pour interagir avec son environnement afin d’atteindre un objectif défini par l’utilisateur. Il combine le raisonnement, la planification et l’exécution d’actions (souvent via des outils externes) pour accomplir des tâches.

On peut donc voir un agent comme :

* un **cerveau** : le modèle d'IA qui raisonne, planifie et décide des actions
* un **corps** : les capacités et outils permettant d'agir

## Spectre de capacité

| Niveau de capacité | Description | Comment ça s'appelle | Exemple de modèle |
|---|---|---|---|
| ☆☆☆ | La sortie de l’agent n’a aucun impact sur le flux du programme | Processeur simple | `process_llm_output(llm_response)` |
| ★☆☆ | La sortie de l’agent détermine le flux de contrôle de base | Routeur | `if llm_decision(): path_a() else: path_b()` |
| ★★☆ | La sortie de l’agent détermine l’exécution de la fonction | Appeleur d’outils | `run_function(llm_chosen_tool, llm_chosen_args)` |
| ★★★ | La sortie de l’agent contrôle l’itération et la continuation du programme | Agent multi-étapes | `while llm_should_continue(): execute_next_step()` |
| ★★★ | Un flux de travail agentique peut en démarrer un autre | Multi-Agent | `if llm_trigger(): execute_agent()` |

## Outils et actions

Un LLM seul ne peut produire que du texte. Les **outils** permettent à l'agent d'interagir avec son environnement et d'effectuer des actions.

Une **action n'est pas forcément un outil** : une action peut nécessiter l'utilisation de plusieurs outils.

## Résumé

Agent = système muni d'un modèle d'IA (LLM, VLM...) capable de :

* Comprendre le langage naturel
* Raisonner et planifier
* Interagir avec son environnement
* Utiliser des outils pour effectuer des actions
