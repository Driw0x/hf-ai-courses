# Que sont les outils ?
> Source : [Hugging Face Agents Course — What are Tools?](https://huggingface.co/learn/agents-course/fr/unit1/tools)

Les outils permettent aux agents de pouvoir effectuer des actions.

Un set d'outils complet et bien documenté permet à l'agent d'augmenter considérablement ses compétences.

## Que sont les outils d'IA ?

Un outil est une fonction fournie au LLM qui remplit un objectif clair.

Les outils permettent aussi de maj les données qui ne sont plus à jour par rapport à leur base d'entraînement.

Un outil doit contenir:
* Une description textuelle de ce que fait la fonction 
* Un appeleur (quelque chose pour effectuer une action)
* Des arguments avec typage
* (Optionnel) Des sorties avec typage

## Comment fonctionnent les outils ?

Les LLM ne peuvent pas appeler directement les outils. Ils génèrent une invocation textuelle lorsqu'un outil est nécessaire.

L'agent détecte cette invocation, exécute l'outil, récupère son résultat et l'ajoute à un nouveau message transmis au LLM avant de générer la réponse à l'utilisateur.

## Comment fournir des outils à un LLM ?

Les outils sont principalement fournis au LLM par le biais du *prompt* système.

Il faut être précis sur ce que fait l'outil et les entrées exactes attendues. C'est pourquoi leur description est souvent fournie dans des structures expressives telles que des langages informatiques ou du JSON. Ce n'est néanmoins pas une obligation tant qu'on reste précis.

## Sections d'auto-formatage des outils

Un outil pourrait être écrit en Python pour être expressif, concis et précis.

Grâce à l'introspection Python, on peut récupérer automatiquement le nom de la fonction, sa docstring, ses arguments et leurs types ainsi que son type de retour.

Un décorateur `@tool` peut alors transformer automatiquement une fonction en outil et générer sa description pour le LLM.

On peut le fournir tel quel directement à notre LLM.

## Implémentation générique d'un outil

On peut créer une classe Tool en Python qui inclut:
* name (str): nom de l’outil.
* description (str): description de l’outil.
* function (callable): la fonction que l’outil exécute.
* arguments (list): les paramètres d’entrée attendus.
* outputs (str ou list): les sorties attendues de l’outil.
* __call__() : appelle la fonction lorsque l’outil est invoquée.
* to_string() : convertit les attributs de l’outil en une représentation textuelle.

## Model Context Protocol (MCP) : une interface d’outils unifiée

Protocole ouvert qui standardise la manière dont les applications fournissent des outils aux LLM:

* Une liste croissante d’intégrations pré-construites que votre LLM peut directement utiliser
* La flexibilité de changer entre fournisseurs et vendeurs de LLM
* Les meilleures pratiques pour sécuriser vos données dans votre infrastructure

Un framework compatible MCP peut ainsi utiliser les outils définis avec ce protocole sans devoir réimplémenter une interface d'outils spécifique.