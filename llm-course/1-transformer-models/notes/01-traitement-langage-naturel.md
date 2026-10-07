# Traitement du langage naturel (NLP pour *Natural Language Processing*)
> Source : [Hugging Face LLM Course — Natural Language Processing and Large Language Models](https://huggingface.co/learn/llm-course/fr/chapter1/2)
> - [Version anglaise](https://huggingface.co/learn/llm-course/en/chapter1/2)
>
> Les passages signalés **« Complément EN »** proviennent de la version anglaise actuelle du cours et sont absents de la traduction française.

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
  * identifier les composants grammaticaux d'une phrase (nom, verbe, adjectif) ;
  * identifier les entités nommées (personne, lieu, organisation) ;
  * etc.

* **Génération de texte** :
  * compléter le début d'un texte avec du texte généré automatiquement ;
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

> **Complément EN :** Malgré les progrès des LLM, la compréhension de l'ambiguïté, du contexte culturel, du sarcasme et de l'humour reste difficile. Cependant, l'entraînement sur de très grands jeux de données diversifiés leur permet de mieux gérer ces cas. Leurs performances restent tout de même inférieures à celles des humains.

## L'essor des grands modèles de langage (LLM) — Complément EN

> Cette section est uniquement présente dans la version anglaise actuelle du cours.
> [!NOTE]
> **Complément EN :**  
> Le domaine du NLP a été révolutionné par les LLM.
>
> Ils sont caractérisés par leur **échelle**, avec un nombre de paramètres pouvant s'exprimer en millions, milliards, voire centaines de milliards, leur **capacité générale** à traiter différentes tâches sans être entraînés spécifiquement pour chacune d'elles, l'**apprentissage en contexte** qui leur permet d'apprendre à partir d'exemples donnés dans le prompt, et enfin des **capacités émergentes** qui leur permettent d'effectuer des tâches qui n'avaient pas été anticipées lors de leur conception.
>
> Mais les LLM ont aussi leurs limites : **hallucinations** (ils peuvent inventer des informations incorrectes tout en restant confiants), **biais** dus aux jeux de données d'entraînement, **fenêtre de contexte** limitée malgré les améliorations apportées, et enfin **ressources de calcul importantes** nécessaires à leur entraînement et à leur utilisation.