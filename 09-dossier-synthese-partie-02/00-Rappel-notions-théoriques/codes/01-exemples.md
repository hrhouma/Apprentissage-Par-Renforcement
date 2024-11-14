# TD(0), TD(1), TD(2), TD(n), SARSA, Q-Learning.

### 1. Implémentation de TD(0)

TD(0) met à jour la valeur d'un état \( V(s) \) en utilisant uniquement la récompense immédiate et la valeur de l'état suivant.

```python
import numpy as np

# Définir les états et la politique
states = [0, 1, 2, 3, 4]
policy = {s: np.random.choice(['a', 'b']) for s in states}

# Règle de mise à jour TD(0)
def td_0(policy, episodes=100, alpha=0.1, gamma=0.9):
    V = np.zeros(len(states))
    for _ in range(episodes):
        state = np.random.choice(states)
        while state != 4:  # état terminal
            next_state = np.random.choice(states)
            reward = np.random.randn()  # récompense aléatoire
            V[state] = (1 - alpha) * V[state] + alpha * (reward + gamma * V[next_state])
            state = next_state
    return V

# Exécution de TD(0)
value_function_td0 = td_0(policy)
print("Valeurs estimées avec TD(0) :", value_function_td0)
```

### 2. Implémentation de TD(1)

TD(1) prend en compte deux étapes : la récompense immédiate, la récompense suivante et la valeur de l'état atteint après deux transitions.

```python
def td_1(policy, episodes=100, alpha=0.1, gamma=0.9):
    V = np.zeros(len(states))
    for _ in range(episodes):
        state = np.random.choice(states)
        while state != 4:  # état terminal
            next_state = np.random.choice(states)
            reward1 = np.random.randn()  # première récompense aléatoire
            reward2 = np.random.randn()  # deuxième récompense aléatoire
            V[state] = (1 - alpha) * V[state] + alpha * (reward1 + gamma * reward2 + gamma**2 * V[next_state])
            state = next_state
    return V

# Exécution de TD(1)
value_function_td1 = td_1(policy)
print("Valeurs estimées avec TD(1) :", value_function_td1)
```

### 3. Implémentation de TD(2)

TD(2) utilise trois étapes : il prend en compte trois récompenses et la valeur de l'état après trois transitions.

```python
def td_2(policy, episodes=100, alpha=0.1, gamma=0.9):
    V = np.zeros(len(states))
    for _ in range(episodes):
        state = np.random.choice(states)
        while state != 4:  # état terminal
            next_state = np.random.choice(states)
            reward1 = np.random.randn()
            reward2 = np.random.randn()
            reward3 = np.random.randn()
            V[state] = (1 - alpha) * V[state] + alpha * (reward1 + gamma * reward2 + gamma**2 * reward3 + gamma**3 * V[next_state])
            state = next_state
    return V

# Exécution de TD(2)
value_function_td2 = td_2(policy)
print("Valeurs estimées avec TD(2) :", value_function_td2)
```

### 4. Implémentation Générique de TD(n)

Voici une version générique pour TD(n), où \( n \) est un paramètre. Cette fonction permet de tester TD avec n'importe quel nombre de pas \( n \).

```python
def td_n(policy, episodes=100, alpha=0.1, gamma=0.9, n=1):
    V = np.zeros(len(states))
    for _ in range(episodes):
        state = np.random.choice(states)
        while state != 4:  # état terminal
            rewards = []
            next_state = state
            for i in range(n):
                next_state = np.random.choice(states)
                reward = np.random.randn()  # récompense aléatoire
                rewards.append(reward)
            total_return = sum(gamma**k * rewards[k] for k in range(n)) + gamma**n * V[next_state]
            V[state] = (1 - alpha) * V[state] + alpha * total_return
            state = next_state
    return V

# Exécution de TD(n) pour n=3
value_function_td3 = td_n(policy, n=3)
print("Valeurs estimées avec TD(3) :", value_function_td3)
```

### 5. Implémentation de SARSA (Sur-Politique)

SARSA met à jour la valeur \( Q(s, a) \) en fonction de la politique actuelle, en utilisant la prochaine action \( A_{t+1} \) choisie par la politique.

```python
from collections import defaultdict

def sarsa(episodes=100, alpha=0.1, gamma=0.9, epsilon=0.1):
    Q = defaultdict(lambda: np.zeros(len(actions)))
    
    def epsilon_greedy_policy(Q, state, epsilon):
        if np.random.rand() < epsilon:
            return np.random.choice(actions)
        else:
            return actions[np.argmax(Q[state])]
    
    for _ in range(episodes):
        state = np.random.choice(states)
        action = epsilon_greedy_policy(Q, state, epsilon)
        while state != 4:  # état terminal
            next_state = np.random.choice(states)
            reward = np.random.randn()
            next_action = epsilon_greedy_policy(Q, next_state, epsilon)
            Q[state][actions.index(action)] = (1 - alpha) * Q[state][actions.index(action)] + \
                                              alpha * (reward + gamma * Q[next_state][actions.index(next_action)])
            state, action = next_state, next_action
    return Q

# Exécution de SARSA
Q_sarsa = sarsa()
print("Valeurs Q estimées avec SARSA :", Q_sarsa)
```

### 6. Implémentation de Q-Learning (Hors-Politique)

Q-Learning est une méthode hors-politique qui met à jour \( Q(s, a) \) en utilisant la meilleure action possible dans l'état suivant, indépendamment de l'action réellement prise.

```python
def q_learning(episodes=100, alpha=0.1, gamma=0.9, epsilon=0.1):
    Q = defaultdict(lambda: np.zeros(len(actions)))
    
    def epsilon_greedy_policy(Q, state, epsilon):
        if np.random.rand() < epsilon:
            return np.random.choice(actions)
        else:
            return actions[np.argmax(Q[state])]
    
    for _ in range(episodes):
        state = np.random.choice(states)
        while state != 4:  # état terminal
            action = epsilon_greedy_policy(Q, state, epsilon)
            next_state = np.random.choice(states)
            reward = np.random.randn()
            best_next_action = np.argmax(Q[next_state])
            Q[state][actions.index(action)] = (1 - alpha) * Q[state][actions.index(action)] + \
                                              alpha * (reward + gamma * Q[next_state][best_next_action])
            state = next_state
    return Q

# Exécution de Q-Learning
Q_q_learning = q_learning()
print("Valeurs Q estimées avec Q-Learning :", Q_q_learning)
```

### Explications des Méthodes

- **TD(0)**, **TD(1)**, **TD(2)** : Chacune de ces méthodes prend en compte un nombre croissant de transitions futures (respectivement 1, 2 et 3 étapes) pour mettre à jour la valeur d'un état.
- **TD(n)** : Méthode généralisée permettant de définir n'importe quel nombre d'étapes \( n \), se rapprochant de Monte Carlo lorsque \( n \to \infty \).
- **SARSA** : Méthode sur-politique qui utilise l'action réelle suivant la politique actuelle pour la mise à jour.
- **Q-Learning** : Méthode hors-politique qui utilise la meilleure action possible dans l'état suivant pour la mise à jour, indépendamment de la politique actuelle.

Ces exemples de code sont structurés pour être facilement compréhensibles et exécutables dans des environnements Python. Assurez-vous que les variables `states` et `actions` sont définies dans votre environnement avant d'exécuter le code pour SARSA et Q-Learning.
