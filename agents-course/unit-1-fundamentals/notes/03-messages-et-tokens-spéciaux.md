# Messages et tokens spéciaux
> Source : [Hugging Face Agents Course — Messages and Special Tokens](https://huggingface.co/learn/agents-course/fr/unit1/messages-and-special-tokens)

## Patron de chat (gabarit de chat)

Structuration de la communication entre l'utilisateur et l'agent.

On utilise les *tokens* spéciaux pour délimiter le début et la fin des tours de l'utilisateur et de l'assistant.

Selon le LLM, les règles de formatage et les délimiteurs sont différents.

## Messages : Le système sous-jacent des LLM

### Message Système (*prompt* système)

Indique au modèle comment il doit se comporter. Ce sont des instructions persistantes.

Fournit les informations sur les outils disponibles, sur comment formater les actions à prendre et sur comment le processus de pensée doit être segmenté.

### Conversations : Messages Utilisateur et Assistant

Dans une conversation alternant entre utilisateur et assistant (LLM), les gabarits de chat maintiennent le contexte en préservant l'historique de conversation.

Tous les messages de la conversation (de l'utilisateur comme de l'assistant) seront concaténés en un prompt donné au LLM ensuite.

Le LLM ne mémorise donc pas directement la conversation : l'historique lui est fourni à nouveau dans le prompt à chaque appel.

## Gabarits de Chat

Les gabarits de chat font le pont entre les messages d'une conversation et le format attendu par le modèle.

### Modèles de Base vs. Modèles d'Instructions

Modèle de Base : entraîné sur des données textuelles brutes pour prédire le prochain *token*.

Modèle instruit : spécialisé (*fine-tuné*) pour suivre des instructions et s'engager dans des conversations.

Pour qu'un modèle de base se comporte comme un modèle instruit, il faut formater les *prompts* de manière cohérente et compréhensible pour le modèle. C'est là qu'interviennent les gabarits de chat.

Un modèle de base peut être *fine-tuné* avec différents patrons de chat, donc il est important de choisir le bon patron.

### Comprendre les gabarits de Chat

Le gabarit de chat est capable de s'adapter au modèle lorsqu'il formate le *prompt* qu'il fournit au modèle.

### Convertir des messages en un prompt

Les messages structurés par rôle, par exemple `system`, `user` et `assistant`, sont convertis par le gabarit de chat en une séquence de texte et de tokens spéciaux comprise par le modèle.