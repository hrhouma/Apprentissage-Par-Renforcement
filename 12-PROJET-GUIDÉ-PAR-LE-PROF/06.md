### **Tutoriel détaillé : Comprendre le fonctionnement de DQN dans Pong**

Dans ce tutoriel, nous allons expliquer étape par étape comment fonctionne l'agent **DQN (Deep Q-Network)** lorsqu'il apprend à jouer au jeu **Pong**. Nous discuterons des joueurs, du rôle de l'agent, du mécanisme d'apprentissage et de l'importance des récompenses.

---

### **Introduction**

Pong est un jeu classique où deux raquettes (gauche et droite) se déplacent verticalement pour frapper une balle. Le but est de marquer des points en faisant passer la balle derrière l'adversaire.

Dans ce projet, nous utilisons un agent basé sur **l'apprentissage par renforcement (Reinforcement Learning)** et un réseau de neurones profond (**DQN**) pour qu'il apprenne à jouer au jeu de manière optimale.

---

### **Les Joueurs**

#### **1. L'Agent DQN**
- **Rôle** : Contrôle la **raquette verte à droite**.
- **Objectif** : Gagner contre l'adversaire en frappant la balle stratégiquement.
- **Caractéristiques** :
  - Utilise un réseau de neurones pour analyser l'état du jeu.
  - Choisit des actions optimales (monter ou descendre la raquette).
  - Apprend en recevant des **récompenses** basées sur ses performances.

#### **2. L'Adversaire**
- **Rôle** : Contrôle la **raquette marron à gauche**.
- **Caractéristiques** :
  - Intelligence simple intégrée dans l'environnement Pong d'Atari.
  - Ses mouvements ne changent pas ou ne s'adaptent pas à l'agent DQN.

---

### **Fonctionnement de l'Agent DQN**

L'agent suit un processus d'apprentissage itératif pour s'améliorer. Voici les étapes principales :

#### **1. Observation**
- L'agent **observe l'état actuel du jeu** : 
  - La position de la balle.
  - La position de sa raquette (verte).
  - La position de la raquette adverse (marron).
- L'état du jeu est représenté sous la forme d'une **image prétraitée** (par exemple, une image en niveaux de gris de 84x84 pixels).

#### **2. Action**
- Sur la base de l'observation, l'agent choisit une **action** :
  - Monter la raquette.
  - Descendre la raquette.
  - Rester immobile (dans certains cas).
- L'action est choisie en utilisant une stratégie **epsilon-greedy** :
  - **Exploration** : Essayer des actions aléatoires pour découvrir de nouvelles stratégies.
  - **Exploitation** : Utiliser les actions qui semblent les meilleures d'après les connaissances actuelles.

#### **3. Récompense**
- Après chaque action, l'agent reçoit une **récompense** de l'environnement :
  - **+1** : Si l'agent marque un point.
  - **-1** : Si l'adversaire marque un point.
  - **0** : Dans tous les autres cas.
- La récompense motive l'agent à apprendre les bonnes actions pour maximiser ses points.

#### **4. Apprentissage**
- L'agent stocke ses expériences dans une **mémoire replay** :
  - Chaque expérience comprend : 
    \( (état, action, récompense, nouvel état, terminé?) \).
- À chaque étape, l'agent **entraîne son réseau de neurones** en :
  - Échantillonnant des expériences aléatoires de la mémoire replay.
  - Calculant les valeurs Q cibles pour apprendre quelle action est la meilleure dans un état donné.
  - Mettant à jour son réseau pour améliorer les prédictions futures.

---

### **Défis lors de l'Apprentissage**

#### **1. Scores Négatifs**
- Lorsque l'entraînement commence, l'agent joue mal car il ne connaît pas encore les règles ou les stratégies gagnantes.
- Les scores **-20 ou -21** sont normaux au début, car l'agent perd presque tous les points contre l'adversaire.
- Avec le temps et l'expérience, l'agent commence à s'améliorer et les scores deviennent moins négatifs.

#### **2. Exploration et Exploitation**
- Au début, l'agent fait beaucoup d'**exploration** (choix aléatoires).
- Peu à peu, il passe à l'**exploitation**, en choisissant des actions basées sur ce qu'il a appris.
- Le paramètre **epsilon** diminue progressivement au cours des épisodes pour encourager cette transition.

#### **3. Stabilité**
- L'entraînement peut être instable, car les valeurs cibles changent constamment.
- Pour stabiliser l'entraînement, le DQN utilise :
  - **Mémoire Replay** : Réduit les corrélations entre les expériences.
  - **Réseau cible** : Un second réseau de neurones mis à jour moins fréquemment.

---

### **Pourquoi le DQN Perd-il au Début ?**

1. **Manque d'expérience** :
   - L'agent commence sans aucune connaissance du jeu.
   - Les premières actions sont aléatoires, ce qui entraîne des défaites fréquentes.

2. **Exploration initiale** :
   - Pendant les premiers épisodes, l'agent explore en prenant des actions aléatoires, même si elles ne sont pas optimales.

3. **Complexité de l'environnement** :
   - Pong est un jeu à haute dynamique (balle rapide, mouvements précis requis).
   - L'agent doit apprendre à coordonner ses mouvements avec ceux de la balle et de l'adversaire.

---

### **Illustration des Scores**

| **Épisode** | **Score** | **Average Score** | **Best Score** | **Epsilon** | **Steps** |
|-------------|-----------|-------------------|----------------|-------------|-----------|
| 1           | -20.0     | -20.0            | -20.0          | 0.98        | 1923      |
| 2           | -21.0     | -20.3            | -20.0          | 0.97        | 2687      |
| 3           | -21.0     | -20.5            | -20.0          | 0.96        | 3629      |

- **Score** : Le score de chaque épisode.
- **Average Score** : Moyenne mobile des scores des 100 derniers épisodes.
- **Best Score** : Meilleur score atteint jusqu'à présent.
- **Epsilon** : Le taux d'exploration (diminue à chaque épisode).
- **Steps** : Le nombre total d'actions prises depuis le début de l'entraînement.

---

### **Conclusion**

Le DQN est un agent puissant, mais son apprentissage nécessite du temps et de nombreuses itérations :

1. **Scores Négatifs Normaux** :
   - Les scores négatifs sont courants au début car l'agent explore et apprend.
2. **Progression** :
   - Avec plus d'expérience, l'agent commence à prendre de meilleures décisions et à marquer des points.
3. **Récompenses et Stratégies** :
   - L'agent apprend à maximiser les récompenses en développant une stratégie pour contrôler la raquette efficacement.

Avec suffisamment de données et d'épisodes, le DQN peut surpasser un adversaire intégré et jouer de manière optimale.
