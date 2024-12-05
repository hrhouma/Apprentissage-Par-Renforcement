### **Classe `DQNAgent`**
Cette classe implémente un agent qui utilise un algorithme DQN (Deep Q-Network) pour apprendre à interagir de manière optimale avec un environnement donné. L'agent prend des décisions, apprend à partir d'expériences passées et améliore progressivement sa stratégie pour maximiser les récompenses.

---

#### **Diagramme ASCII de la classe `DQNAgent`**
```
+------------------------------------------------------+
|                   DQNAgent                           |
+------------------------------------------------------+
| Attributes:                                         |
| - gamma: float (facteur de discount)               |
| - epsilon: float (taux d'exploration)              |
| - lr: float (taux d'apprentissage)                 |
| - n_actions: int (nombre total d'actions possibles)|
| - input_dims: tuple (dimensions de l'état)         |
| - batch_size: int (taille du batch pour l'apprentissage)|
| - eps_min: float (valeur minimale de epsilon)      |
| - eps_dec: float (diminution progressive de epsilon)|
| - replace_target_cnt: int (fréquence de mise à jour du réseau cible)|
| - algo: str (nom de l'algorithme, ex: 'DQN')       |
| - env_name: str (nom de l'environnement)           |
| - chkpt_dir: str (répertoire des checkpoints)      |
| - memory: ReplayBuffer (mémoire des expériences)   |
| - q_eval: DeepQNetwork (réseau principal)          |
| - q_next: DeepQNetwork (réseau cible)              |
| - learn_step_counter: int (compteur d'étapes d'apprentissage)|
| - action_space: list (liste des actions possibles) |
+------------------------------------------------------+
| Methods:                                           |
| - __init__: Initialise l'agent                     |
| - choose_action: Choisit une action               |
| - store_transition: Stocke une transition         |
| - sample_memory: Récupère un batch de la mémoire  |
| - replace_target_network: Met à jour le réseau cible |
| - decrement_epsilon: Réduit epsilon               |
| - save_models: Sauvegarde les réseaux             |
| - load_models: Charge les réseaux                 |
| - learn: Met à jour le réseau principal (apprentissage)|
+------------------------------------------------------+
```

---

#### **Attributs**

1. **Hyperparamètres :**
   - **`gamma`** : Facteur de discount pour évaluer l'importance des récompenses futures.
   - **`epsilon`** : Taux d'exploration initial. Contrôle la probabilité d'effectuer une action aléatoire.
   - **`eps_min`** : Valeur minimale pour epsilon (fin de l'exploration).
   - **`eps_dec`** : Taux de diminution d'epsilon à chaque apprentissage.
   - **`lr`** : Taux d'apprentissage utilisé par l'optimiseur des réseaux.

2. **Réseaux de neurones :**
   - **`q_eval`** : Réseau principal utilisé pour sélectionner les actions.
   - **`q_next`** : Réseau cible utilisé pour calculer les valeurs Q cibles lors de l'apprentissage.

3. **Gestion de la mémoire :**
   - **`memory`** : Une instance de `ReplayBuffer` qui stocke les transitions (états, actions, récompenses, etc.).
   - Permet d'échantillonner des mini-lots pour briser la corrélation temporelle.

4. **Autres :**
   - **`learn_step_counter`** : Compte le nombre total d'étapes d'apprentissage.
   - **`replace_target_cnt`** : Détermine la fréquence de mise à jour du réseau cible (`q_next`).

---

#### **Méthodes**

##### **1. `__init__` : Constructeur**
```python
def __init__(self, gamma, epsilon, lr, n_actions, input_dims,
             mem_size, batch_size, eps_min=0.01, eps_dec=5e-7,
             replace=1000, algo=None, env_name=None, chkpt_dir='tmp/dqn'):
```
- Initialise les attributs, les réseaux et la mémoire de l'agent.
- **Paramètres :**
  - `gamma` : Importance des récompenses futures.
  - `epsilon` : Niveau d'exploration initial.
  - `n_actions` : Nombre d'actions possibles dans l'environnement.
  - `input_dims` : Dimensions de l'état observé.
  - `batch_size` : Taille des mini-lots pour l'apprentissage.
  - `replace` : Fréquence de mise à jour du réseau cible.
  - `algo` et `env_name` : Identifiants pour sauvegarder et charger les checkpoints.

---

##### **2. `choose_action` : Choisir une action**
```python
def choose_action(self, observation):
```
- **Fonctionnement :**
  1. Génère un nombre aléatoire.
  2. Si le nombre est supérieur à `epsilon`, l'agent **exploite** le réseau principal (`q_eval`) pour choisir l'action ayant la plus grande valeur Q.
  3. Sinon, l'agent **explore** en choisissant une action aléatoire.
- **Entrée :**
  - `observation` : État actuel de l'environnement.
- **Sortie :**
  - Une action (index entier dans `action_space`).

---

##### **3. `store_transition` : Stocker une transition**
```python
def store_transition(self, state, action, reward, state_, done):
```
- Stocke une transition dans la mémoire replay.
- **Paramètres :**
  - `state` : État courant.
  - `action` : Action effectuée.
  - `reward` : Récompense obtenue.
  - `state_` : Nouvel état.
  - `done` : Booléen indiquant si l'épisode est terminé.

---

##### **4. `sample_memory` : Échantillonner la mémoire**
```python
def sample_memory(self):
```
- Récupère un mini-lot de transitions depuis la mémoire replay.
- **Sortie :**
  - Un tuple contenant les états, actions, récompenses, nouveaux états et indicateurs de fin d'épisode (`done`).

---

##### **5. `replace_target_network` : Mise à jour du réseau cible**
```python
def replace_target_network(self):
```
- Met à jour les paramètres du réseau cible (`q_next`) avec ceux du réseau principal (`q_eval`).
- La mise à jour se fait périodiquement, selon `replace_target_cnt`.

---

##### **6. `decrement_epsilon` : Réduire epsilon**
```python
def decrement_epsilon(self):
```
- Réduit progressivement `epsilon` pour encourager l'exploitation des connaissances acquises.
- La valeur minimale est limitée à `eps_min`.

---

##### **7. `save_models` et `load_models` : Gestion des modèles**
```python
def save_models(self):
    self.q_eval.save_checkpoint()
    self.q_next.save_checkpoint()

def load_models(self):
    self.q_eval.load_checkpoint()
    self.q_next.load_checkpoint()
```
- Sauvegarde ou charge les modèles `q_eval` et `q_next` à partir des fichiers checkpoints.

---

##### **8. `learn` : Apprentissage**
```python
def learn(self):
```
- Fonction principale qui entraîne le réseau principal (`q_eval`).
- **Étapes :**
  1. Vérifie que suffisamment d'expériences sont stockées dans la mémoire.
  2. Échantillonne un mini-lot depuis la mémoire.
  3. Calcule les valeurs Q prédites et les cibles Q :
     - **Cibles Q** : Basées sur les récompenses immédiates et les valeurs Q du réseau cible (`q_next`).
  4. Minimise la fonction de perte (MSE) entre les valeurs Q prédites et les cibles Q.
  5. Met à jour les poids du réseau principal (`q_eval`) avec `optimizer.step()`.
  6. Met à jour `epsilon` pour réduire l'exploration.

---

#### **Résumé des responsabilités des composants :**

| Composant          | Rôle                                                                                     |
|---------------------|------------------------------------------------------------------------------------------|
| **`q_eval`**       | Réseau principal qui prédit les valeurs Q pour sélectionner les actions.                 |
| **`q_next`**       | Réseau cible utilisé pour calculer les valeurs Q cibles.                                 |
| **Mémoire Replay** | Stocke les transitions pour un apprentissage par mini-lots aléatoires.                   |
| **Epsilon-Greedy** | Permet un équilibre entre exploration et exploitation lors de la sélection des actions.   |
| **Gamma**          | Pondère les récompenses futures dans le calcul des cibles Q.                             |

---

### **Pourquoi utiliser cette architecture ?**

1. **Réseaux séparés (q_eval et q_next)** :
   - Stabilise l'apprentissage en décorrélant les valeurs Q estimées et les cibles Q.

2. **Mémoire replay** :
   - Réduit la corrélation temporelle entre les expériences.
   - Permet un apprentissage plus efficace et stable.

3. **Epsilon-Greedy** :
   - Encourage l'exploration au début de l'entraînement et passe progressivement à l'exploitation.

4. **Approche modulaire** :
   - Chaque composant a un rôle spécifique (prise de décision, apprentissage, gestion des modèles

, etc.).

---

### **Visualisation ASCII du processus global**
```
+--------------------+       +--------------------+
|   Environnement    | <---> |      DQNAgent      |
+--------------------+       +--------------------+
            ^                           |
            |                           v
     Observation                   Action choisie
            |                           |
+--------------------+       +--------------------+
|    Mémoire Replay  | <---  |   Réseau Principal |
+--------------------+       +--------------------+
            ^                           ^
            |                           |
+--------------------+       +--------------------+
|    Réseau Cible    | <-----|   Apprentissage    |
+--------------------+       +--------------------+
```

Ce processus itératif permet à l'agent d'améliorer sa performance dans l'environnement au fil des épisodes.
