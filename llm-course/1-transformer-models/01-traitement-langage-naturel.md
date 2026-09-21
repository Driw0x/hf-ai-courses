# Traitement du langage naturel (NLP pour *Natural Language Processing*)

> Source : [Hugging Face LLM Course — Natural Language Processing and Large Language Models](https://huggingface.co/learn/llm-course/fr/chapter1/2)

## Le NLP, qu'est-ce que c'est ?

C'est un domaine de la linguistique et de l'apprentissage automatique se concentrant sur la compréhension de tout ce qui est lié à la langue humaine. L'objectif n'est pas seulement de comprendre un mot, mais aussi de comprendre le contexte associé à son utilisation.

Les tâches NLP les plus courantes :

* **Classification de phrases entières** :
  * analyser le sentiment d'un avis ;
  * détecter un spam ;
  * déterminer si une phrase est grammaticalement correcte ;
  * déterminer si deux phrases sont logiquement reliées ou non ;
  * etc.

* **Classification de chaque mot d'une phrase** :
  * identifier les composants grammaticaux d’une phrase (nom, verbe, adjectif) ;
  * identifier les entités nommées (personne, lieu, organisation) ;
  * etc.

* **Génération de texte** :
  * compléter le début d’un texte avec du texte généré automatiquement ;
  * remplacer les mots manquants ou masqués dans un texte.

* **Extraction d'une réponse à partir d'un texte** :
  * étant donné une question et un contexte, extraire la réponse à la question en fonction des informations fournies par le contexte.

* **Génération de nouvelles phrases à partir d'un texte** :
  * traduire un texte ;
  * résumer un texte.

Le NLP peut aussi être utilisé pour la reconnaissance vocale et la vision par ordinateur, par exemple pour la retranscription d'un enregistrement audio ou la description d'une image.

## Pourquoi est-ce difficile ?

Les ordinateurs ne traitent pas les informations de la même manière que les humains. Le texte doit donc être traité et représenté d'une manière permettant au modèle d'apprendre.

La difficulté vient de la complexité du langage et de son contexte. Il existe ainsi différentes méthodes permettant de représenter le texte afin qu'il puisse être traité par un modèle.