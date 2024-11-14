
### **Comparaison Pratique des Méthodes de Mise à Jour : TD(0), TD(1), TD(2), TD(n), SARSA et Q-Learning en Python**




1. **TD(0), TD(1), TD(2), TD(n)** : J'ai ajouté des commentaires pour indiquer la logique de mise à jour pour chaque méthode.
2. **SARSA et Q-Learning** : Ajout de la définition de `actions` pour éviter les erreurs lors de l'exécution.

*Ces exemples montrent bien les différences entre chaque méthode et sont exécutables en Python. Assurez-vous que `states` et `actions` sont bien définis avant d’exécuter chaque fonction.*

-----------
# 1. TD(0) - Mise à jour avec une seule étape

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
            # Mise à jour en utilisant une seule étape
            V[state] = (1 - alpha) * V[state] + alpha * (reward + gamma * V[next_state])
            state = next_state
    return V

# Exécution de TD(0)
value_function_td0 = td_0(policy)
print("Valeurs estimées avec TD(0) :", value_function_td0)
```

-----------
# 2. TD(1) - Mise à jour avec deux étapes

```python
def td_1(policy, episodes=100, alpha=0.1, gamma=0.9):
    V = np.zeros(len(states))
    for _ in range(episodes):
        state = np.random.choice(states)
        while state != 4:  # état terminal
            next_state = np.random.choice(states)
            reward1 = np.random.randn()  # première récompense
            reward2 = np.random.randn()  # deuxième récompense
            # Mise à jour en utilisant deux étapes
            V[state] = (1 - alpha) * V[state] + alpha * (reward1 + gamma * reward2 + gamma**2 * V[next_state])
            state = next_state
    return V

# Exécution de TD(1)
value_function_td1 = td_1(policy)
print("Valeurs estimées avec TD(1) :", value_function_td1)
```

-----------
# 3. TD(2) - Mise à jour avec trois étapes

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
            # Mise à jour en utilisant trois étapes
            V[state] = (1 - alpha) * V[state] + alpha * (reward1 + gamma * reward2 + gamma**2 * reward3 + gamma**3 * V[next_state])
            state = next_state
    return V

# Exécution de TD(2)
value_function_td2 = td_2(policy)
print("Valeurs estimées avec TD(2) :", value_function_td2)
```

-----------
# 4. TD(n) - Mise à jour avec \( n \) étapes (paramétrable)

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
            # Calcul du retour total avec n étapes
            total_return = sum(gamma**k * rewards[k] for k in range(n)) + gamma**n * V[next_state]
            V[state] = (1 - alpha) * V[state] + alpha * total_return
            state = next_state
    return V

# Exécution de TD(n) pour n=3
value_function_td3 = td_n(policy, n=3)
print("Valeurs estimées avec TD(3) :", value_function_td3)
```

-----------
# 5. SARSA - Mise à jour en fonction de l'action réelle suivant la politique

Définition de `actions` pour exécuter correctement SARSA et Q-Learning.

```python
from collections import defaultdict

# Actions possibles
actions = ['a', 'b']

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
            # Mise à jour SARSA
            Q[state][actions.index(action)] = (1 - alpha) * Q[state][actions.index(action)] + \
                                              alpha * (reward + gamma * Q[next_state][actions.index(next_action)])
            state, action = next_state, next_action
    return Q

# Exécution de SARSA
Q_sarsa = sarsa()
print("Valeurs Q estimées avec SARSA :", Q_sarsa)
```


-----------
# 6. Q-Learning - Mise à jour en utilisant la meilleure action possible (hors-politique)

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
            # Mise à jour Q-Learning
            Q[state][actions.index(action)] = (1 - alpha) * Q[state][actions.index(action)] + \
                                              alpha * (reward + gamma * Q[next_state][best_next_action])
            state = next_state
    return Q

# Exécution de Q-Learning
Q_q_learning = q_learning()
print("Valeurs Q estimées avec Q-Learning :", Q_q_learning)
```

-----------
# Explications supplémentaires des Méthodes

- **TD(0), TD(1), TD(2)** : Ces méthodes prennent en compte respectivement 1, 2, et 3 étapes de récompense futures pour la mise à jour de la valeur d'un état.
- **TD(n)** : Permet de définir un nombre arbitraire de transitions (n étapes) pour se rapprocher de Monte Carlo lorsque \( n \to \infty \).
- **SARSA** : Met à jour la valeur \( Q(s, a) \) en fonction de l'action réellement choisie par la politique, ce qui en fait une méthode sur-politique.
- **Q-Learning** : Utilise la meilleure action possible dans l'état suivant, indépendamment de la politique actuelle, ce qui en fait une méthode hors-politique.

