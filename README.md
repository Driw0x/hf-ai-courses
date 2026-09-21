# Hugging Face AI Courses

Dépôt personnel regroupant mes notes, exercices, notebooks et expérimentations réalisés dans le cadre des cours proposés par [Hugging Face](https://huggingface.co/learn).

L'objectif est de construire progressivement des compétences autour des **Large Language Models**, des **agents IA**, du **context engineering**, du **fine-tuning** et du **reinforcement learning**.

---

## Parcours d'apprentissage

Le parcours alterne entre pratique et approfondissement théorique.

L'idée est de commencer par comprendre concrètement le fonctionnement d'un agent, puis d'étudier plus en détail le LLM qui constitue son moteur avant de revenir vers des architectures agentiques plus avancées.

```text
Agents — fondamentaux
        ↓
LLM — fondamentaux
        ↓
Agents — approfondissement
        ↓
Context Engineering
        ↓
Fine-tuning
        ↓
Reinforcement Learning
```

### Ordre prévu

1. **Agents Course — Units 0 et 1**
2. **LLM Course — fondamentaux**
3. **Agents Course — Units 2, 3 et Final Project**
4. **Context Course**
5. **a smol course**
6. **Deep RL Course**
7. **Open-Source AI Cookbook — ressource complémentaire**

---

## 1. Agents Course — fondamentaux

> ✅ Terminé

Première introduction aux agents basés sur les LLM.

Cette étape permet de comprendre comment un LLM peut interagir avec son environnement à travers des outils et effectuer des tâches en plusieurs étapes.

### Sujets

- fonctionnement général d'un agent ;
- rôle du LLM ;
- messages et conversations ;
- tools ;
- function calling ;
- cycle `Thought → Action → Observation` ;
- construction d'un premier agent ;
- utilisation de `smolagents`.

### Progression

- [x] Unit 0 — Introduction
- [x] Unit 1 — Agent Fundamentals

Une fois les fondamentaux du Agents Course terminés, le parcours continue avec les bases des LLM et des Transformers.

---

## 2. LLM Course — fondamentaux

> 🚧 En cours

Cette étape vise à mieux comprendre le moteur utilisé par les agents : les **Large Language Models** et l'architecture **Transformer**.

L'objectif n'est pas nécessairement de terminer immédiatement l'intégralité du cours, mais d'acquérir suffisamment de bases pour comprendre plus précisément le fonctionnement des systèmes agentiques.

### Sujets principaux

- architecture Transformer ;
- fonctionnement général des LLM ;
- bibliothèque `transformers` ;
- modèles pré-entraînés ;
- tokenisation ;
- génération de texte ;
- inference ;
- gestion du contexte ;
- utilisation du Hugging Face Hub ;
- bases du fine-tuning.

### Objectif

Comprendre plus précisément ce qui se passe derrière :

```python
model.generate(...)
```

et derrière les appels effectués par les frameworks d'agents.

Après cette étape, retour au Agents Course pour étudier des systèmes plus avancés.

---

## 3. Agents Course — approfondissement

> ⏳ À venir

Après l'étude des fondamentaux des LLM, reprise du Agents Course avec une meilleure compréhension du fonctionnement interne des modèles utilisés.

### Unit 2 — Frameworks

Découverte de plusieurs frameworks permettant de construire des agents.

Principaux sujets :

- `smolagents` ;
- LlamaIndex ;
- LangGraph ;
- orchestration d'agents ;
- outils ;
- workflows agentiques.

### Unit 3 — Agentic RAG

Étude de systèmes combinant agents et récupération d'information.

Principaux concepts :

- Retrieval-Augmented Generation ;
- recherche documentaire ;
- récupération de contexte ;
- agents utilisant des bases de connaissances ;
- orchestration entre récupération et raisonnement.

### Final Project

Mise en pratique des différentes notions vues pendant le cours à travers un projet final.

Objectifs :

- construire un agent complet ;
- utiliser des outils ;
- gérer plusieurs étapes ;
- évaluer le comportement de l'agent ;
- appliquer les concepts étudiés dans les unités précédentes.

---

## 4. Context Course

> ⏳ À venir

Cours consacré au **context engineering**, particulièrement important pour les agents modernes et les agents de développement.

L'objectif est d'apprendre à construire et organiser efficacement le contexte fourni à un modèle.

### Sujets

- context engineering ;
- agents de code ;
- gestion du contexte ;
- instructions ;
- Skills ;
- MCP ;
- plugins ;
- sous-agents ;
- hooks ;
- outils externes ;
- boucles agentiques.

Cette étape complète naturellement le Agents Course en étudiant plus précisément la manière dont l'information est fournie aux agents.

---

## 5. a smol course

> ⏳ À venir

Cours consacré à l'adaptation et au fine-tuning des modèles.

Après avoir appris à utiliser des LLM dans des systèmes agentiques, cette étape permet de comprendre comment modifier leur comportement par entraînement.

### Sujets

- instruction tuning ;
- Supervised Fine-Tuning (`SFT`) ;
- préparation des datasets ;
- preference alignment ;
- évaluation ;
- fine-tuning de LLM ;
- modèles multimodaux ;
- techniques modernes d'entraînement.

L'objectif est de passer de :

```text
Utiliser un modèle existant
        ↓
Adapter un modèle à une tâche spécifique
```

---

## 6. Deep Reinforcement Learning Course

> ⏳ À venir

Introduction puis approfondissement du **Reinforcement Learning** et du **Deep Reinforcement Learning**.

Cette partie permet d'étudier des agents qui apprennent à prendre des décisions par interaction avec un environnement.

### Sujets

- agents et environnements ;
- états ;
- actions ;
- récompenses ;
- Markov Decision Processes ;
- Q-Learning ;
- Deep Q-Learning ;
- Policy Gradients ;
- Actor-Critic ;
- PPO ;
- Stable-Baselines3 ;
- CleanRL.

Cette étape permet d'étudier une autre famille d'agents, différente des agents principalement pilotés par des LLM.

---

## 7. Open-Source AI Cookbook

Le **Open-Source AI Cookbook** sera utilisé comme ressource complémentaire plutôt que comme un cours linéaire.

Les notebooks seront consultés selon les besoins rencontrés dans les projets et les autres cours.

### Sujets utiles

- RAG ;
- fine-tuning ;
- inference ;
- évaluation des LLM ;
- LLM-as-a-Judge ;
- GRPO ;
- optimisation ;
- embeddings ;
- workflows avec des modèles open source.

---

## Structure du dépôt

La structure évoluera progressivement avec l'avancement dans les différents cours.

```text
hf-ai-courses/
│
├── requirements.txt
├── README.md
├── .gitignore
│
├── agents-course/
│   ├── README.md
│   ├── docs/
│   ├── unit-1-fundamentals/
│   ├── unit-2-frameworks/
│   ├── unit-3-agentic-rag/
│   └── final-project/
│
├── llm-course/
│   └── ...
│
├── context-course/
│   └── ...
│
├── smol-course/
│   └── ...
│
└── deep-rl-course/
    └── ...
```

Chaque cours possède son propre dossier afin de séparer les notes, notebooks, exercices et éventuels projets associés.

---

## Organisation

Pour chaque cours, les fichiers peuvent notamment contenir :

```text
notes/
notebooks/
exercises/
projects/
```

La structure exacte est adaptée au contenu proposé par chaque cours afin d'éviter d'ajouter des dossiers inutiles.

---

## Objectifs

Ce dépôt a plusieurs objectifs :

- conserver une trace structurée de ma progression ;
- documenter les concepts étudiés ;
- reproduire les exemples importants ;
- expérimenter avec les bibliothèques de l'écosystème Hugging Face ;
- approfondir les notions au-delà des notebooks du cours ;
- relier les concepts étudiés à des projets personnels.

---

## Compétences étudiées

Au fil du parcours, ce dépôt couvre progressivement plusieurs domaines :

- Transformers
- Large Language Models
- Tokenization
- Inference
- Fine-tuning
- AI Agents
- Tool Calling
- Agentic RAG
- Context Engineering
- MCP
- LLM Evaluation
- Reinforcement Learning
- Deep Reinforcement Learning

---

## Ressources

- [Hugging Face Learn](https://huggingface.co/learn)
- [Hugging Face Documentation](https://huggingface.co/docs)
- [Hugging Face Hub](https://huggingface.co/)

---

## Certifications

- ✅ Unit 1 — Fundamentals of Agents  
  [Voir le certificat](agents-course/unit-1-fundamentals/certificate.webp)