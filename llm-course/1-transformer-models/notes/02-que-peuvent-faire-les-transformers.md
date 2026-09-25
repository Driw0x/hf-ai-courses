# Que peuvent faire les *transformers*
> Source : [Hugging Face LLM Course — Transformers, what can they do?](https://huggingface.co/learn/llm-course/fr/chapter1/3)

## Travailler avec les pipelines

La fonction `pipeline()` relie un modèle avec ses étapes de pré-traitement et de post-traitementafin de simplifier son utilisation pour une tâche donnée.

Lorsque le modèle à utiliser n'est pas spécifié, `pipeline` sélectionne un modèle par défaut par rapport à la tâche fournie qui est téléchargé lors de l'appel de `pipeline()`.

Il y a trois étapes principales lorsque nous passons du texte à un pipeline:
1. Prétraitement du texte pour être compréhensible pour le modèle
2. Envoie des données prétraitées au modèle
3. Post-traitement des prédictions du modèle pour qu'on puisse les comprendre

Liste non-exhaustive des [pipelines disponibles](https://huggingface.co/docs/transformers/main_classes/pipelines):
* feature-extraction (pour obtenir la représentation vectorielle d’un texte)
* fill-mask
* ner (named entity recognition ou reconnaissance d’entités nommées)
* question-answering
* sentiment-analysis
* summarization (ancien pipeline, supprimé dans Transformers récent)
* text-generation
* translation (ancien pipeline, supprimé dans Transformers récent)
* zero-shot-classification

## *Zero-shot classification*

`zero-shot-classification` permet de classer des textes qui n'ont pas nécessairement été vus explicitement pendant l'entraînement du modèle.

On n'a pas besoin d'entraîner spécifiquement le modèle sur nos propres labels pour l'utiliser. Il retourne des scores de probabilité pour n'importe quel ensemble de labels.

## Génération de texte

Le modèle génère la suite d'un extrait de texte que l'on lui a fourni.

Pour contrôler le nombre de séquences générées : `num_return_sequences` 
Pour contrôler la longueur totale du texte généré : `max_new_tokens`

## Utiliser n'importe quel modèle du *Hub* dans un pipeline

Les tâches utilisent un modèle qui est défini par défaut si aucune indication est donnée. Cependant on a la possibilité de choisir le modèle utilisé en l'indicant en argument dans `pipeline`.

On peut trouver une large base de modèles pour toutes tâches [ici](https://huggingface.co/models)

## Remplacement des mots masqués

`fill-mask` permet de remplir les mots manqués d'un texte donné

Il dispose d'un argument `top_k`qui permet de contrôler le nombre de possibilités pour le mot masqué

## Reconnaissance d’entités nommées

La reconnaissance d’entités nommées ou NER (*Named Entity Recognition*) consiste à demander au modèle de reconnaitre les entités du input tel que des personnes, des lieux ou des organisations.

Le prétraitement de l'entrée peut séparer des mots en plusieurs sous-tokens.
Par exemple : `Sylvain` → `S`, `##yl`, `##va`, `##in`.

On peut utiliser `aggregation_strategy="simple"` pour regrouper les sous-tokens appartenant à une même entité.
D'autres stratégies existent comme `first`, `average` et `max`.

## Réponse à des questions

`question-answering` répond à des questions en utilisant les informations qu'on a dans le contexte

## Résumé et traduction

Dans les versions récentes de Transformers, les pipelines `summarization` et `translation` n'existent plus.

Pour obtenir un comportement équivalent, on peut utiliser `text-generation` avec un modèle *Instruct* et lui donner explicitement une instruction de résumé ou de traduction.

Lorsqu'un modèle possède un `chat_template`, on peut utiliser des messages `system` et `user` afin de structurer les instructions. Si le modèle ne possède pas de `chat_template`, on peut lui fournir directement un prompt sous forme de texte brut.

Pour ne récupérer que la génération et pas le prompt complet, on peut utiliser `return_full_text=False`.