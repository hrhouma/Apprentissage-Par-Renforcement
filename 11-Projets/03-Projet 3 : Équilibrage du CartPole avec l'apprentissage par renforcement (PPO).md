# **Projet 3 : Équilibrage du CartPole avec l'apprentissage par renforcement (PPO)**

#### **Objectif :**

L'objectif de ce projet est de créer, entraîner et évaluer un agent basé sur l'algorithme **Proximal Policy Optimization (PPO)** pour résoudre le problème classique du **CartPole**. L'agent doit apprendre à équilibrer un bâton sur un chariot en choisissant les meilleures actions pour éviter que le bâton ne tombe.

---

#### **Description générale :**

Le problème du **CartPole** est un benchmark classique en apprentissage par renforcement. Le but est d'appliquer des forces à un chariot en mouvement pour maintenir un bâton en équilibre. C'est un excellent exemple pour comprendre les bases de l'apprentissage par renforcement, notamment la relation entre **états**, **actions**, **récompenses**, et **transitions**.

---

#### **Caractéristiques du projet :**

1. **Problème étudié :**
   - Le système est composé d'un chariot, d'un bâton, et d'une surface plane.
   - À chaque étape, l'agent peut pousser le chariot vers la gauche ou la droite.

2. **Objectif d'optimisation :**
   - **Maximiser le score** : Le score correspond au nombre d'étapes pendant lesquelles le bâton reste en équilibre.

3. **Composants de l'agent :**
   - **États** : Position et vitesse du chariot, angle et vitesse angulaire du bâton.
   - **Actions** : Appliquer une force à gauche ou à droite.
   - **Récompenses** : Une unité de récompense est attribuée pour chaque étape où le bâton reste en équilibre.

4. **Algorithme utilisé :**
   - **Proximal Policy Optimization (PPO)** : Un algorithme de gradient de politique qui ajuste les actions pour maximiser les récompenses accumulées tout en gardant des changements graduels pour éviter les sur-ajustements.

---

#### **Étapes du projet :**

1. **Exploration de l'environnement :**
   - Utilisez un agent aléatoire pour observer l'interaction entre les actions et les états.
   - Affichez les frames (images) du jeu pour mieux comprendre la dynamique.

2. **Construction et entraînement de l'agent PPO :**
   - Configurez l'environnement avec Gym et DummyVecEnv pour la compatibilité avec **Stable-Baselines3**.
   - Développez un modèle PPO avec une politique basée sur un réseau neuronal (Multilayer Perceptron).
   - Entraînez l'agent sur 20 000 étapes pour qu'il apprenne à maintenir le bâton en équilibre.

3. **Évaluation et visualisation des performances :**
   - Rechargez l'environnement et laissez l'agent entraîné jouer.
   - Affichez le jeu et évaluez le score obtenu.

4. **Analyse et optimisation :**
   - Étudiez les performances de l'agent avant et après entraînement.
   - Expérimentez avec des hyperparamètres comme le nombre d'étapes d'entraînement ou la structure du réseau.

---

#### **Livrables attendus :**

1. **Code fonctionnel :**
   - Implémentation complète de l'agent PPO, de l'entraînement, et de l'évaluation.
   - Fonction pour afficher les frames du jeu de manière fluide.

2. **Rapport d'analyse :**
   - Description des concepts appris (états, actions, récompenses).
   - Comparaison des performances de l'agent aléatoire et de l'agent entraîné.
   - Suggestions pour améliorer encore l'agent (ajustement des hyperparamètres, autres algorithmes).

3. **Démonstration :**
   - Vidéo ou présentation montrant l'agent jouant au jeu avant et après l'entraînement.

---

#### **Compétences développées :**

- Compréhension des **fondamentaux de l'apprentissage par renforcement**.
- Familiarité avec les environnements Gym et l'algorithme PPO.
- Implémentation pratique de modèles d'IA pour résoudre des problèmes de contrôle dynamique.
- Analyse et visualisation des performances avec Matplotlib et Jupyter Notebook.

---

#### **Ressources utiles :**

1. **Apprentissage par renforcement :**
   - Sutton & Barto : ["Reinforcement Learning: An Introduction"](http://incompleteideas.net/book/the-book.html).
   - Tutoriels et documentation Gym : [https://www.gymlibrary.dev](https://www.gymlibrary.dev).

2. **Bibliothèques utilisées :**
   - Documentation Stable-Baselines3 : [https://stable-baselines3.readthedocs.io](https://stable-baselines3.readthedocs.io).
   - Tutoriels PyTorch pour les bases du Deep Learning.

3. **Exemples de projets similaires :**
   - Études de cas sur des environnements comme LunarLander et MountainCar.

---

#### **Pourquoi ce projet est important :**

Ce projet est une introduction pratique et accessible à l'apprentissage par renforcement. Il combine théorie et application pour démontrer comment l'IA peut résoudre des problèmes de contrôle complexes en apprenant de ses erreurs. C'est une base solide pour des projets plus avancés comme les véhicules autonomes ou la robotique.

Prenez ce projet comme une opportunité d'explorer un domaine fascinant et d'acquérir des compétences précieuses pour l'avenir ! 🎯
