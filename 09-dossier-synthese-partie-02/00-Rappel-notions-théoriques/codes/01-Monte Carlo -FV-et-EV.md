# Monte Carlo *"première visite"* VS *"toutes les visites"*

La différence entre **Monte Carlo "première visite"** (first-visit) et **Monte Carlo "toutes les visites"** (every-visit) se trouve dans la manière dont on comptabilise les résultats obtenus au cours des simulations.

Imaginons que vous êtes dans un parc et que vous voulez savoir la **fréquence des oiseaux bleus** que vous croisez au cours de vos promenades. Parfois, vous repassez plusieurs fois par le même endroit où vous voyez un oiseau bleu, et d'autres fois, vous le voyez pour la première fois.

### Monte Carlo "Première Visite" (first-visit)
Dans cette approche, **on ne compte que la première fois** qu'on croise un oiseau bleu lors de chaque promenade. Si vous passez plusieurs fois par le même point et voyez l'oiseau bleu plusieurs fois, **seule la première rencontre est comptée**. C’est utile pour obtenir une mesure plus "unique" par promenade, en se concentrant uniquement sur le premier aperçu.

### Monte Carlo "Toutes les Visites" (every-visit)
Ici, **chaque fois que vous voyez l'oiseau bleu au cours de la promenade, vous le comptez**, même si vous le revoyez en repassant au même endroit. Cela donne une mesure plus détaillée de la fréquence des observations sur toute la promenade, en comptant chaque fois que l'événement se produit.

### En résumé :
- **Première visite** : On ne tient compte que du premier passage par chaque endroit lors d'une promenade (mesure plus unique).
- **Toutes les visites** : On compte chaque observation de l'événement, même si c’est au même endroit (mesure plus détaillée).

Les deux approches sont utiles selon qu’on veut une estimation basée uniquement sur les premières apparitions ou sur toutes les occurrences.

# Implémentation en Python

### 5.1 Prédiction Monte Carlo (First-Visit)

```python
import numpy as np
from collections import defaultdict

# Définition de la politique et de l'environnement
states = [0, 1, 2, 3, 4]
actions = ['a', 'b']
policy = {s: np.random.choice(actions) for s in states}

# Générer un épisode aléatoire basé sur la politique
def generate_episode(policy):
    episode = []
    state = np.random.choice(states)
    while state != 4:  # État terminal
        action = policy[state]
        next_state = np.random.choice(states)
        reward = np.random.randn()  # Récompense aléatoire
        episode.append((state, action, reward))
        state = next_state
    return episode

# Prédiction Monte Carlo (First-Visit)
def monte_carlo_prediction_first_visit(policy, episodes, gamma=0.9):
    V = defaultdict(float)
    returns = defaultdict(list)
    for _ in range(episodes):
        episode = generate_episode(policy)
        G = 0
        visited = set()
        for t in reversed(range(len(episode))):
            state, _, reward = episode[t]
            G = gamma * G + reward
            if state not in visited:
                visited.add(state)
                returns[state].append(G)
                V[state] = np.mean(returns[state])
    return V

# Exécution
value_function = monte_carlo_prediction_first_visit(policy, episodes=1000)
print("Fonction de Valeur Estimée :")
for state, value in value_function.items():
    print(f"V({state}) = {value:.2f}")
```

### 5.2 Contrôle Monte Carlo (Sur-Politique, Every-Visit)

Cet exemple montre comment estimer \( Q(s, a) \) et obtenir une politique optimale via une approche epsilon-greedy.

```python
def monte_carlo_control_on_policy(episodes, gamma=0.9, epsilon=0.1):
    Q = defaultdict(lambda: np.zeros(len(actions)))
    policy = {s: np.random.choice(actions) for s in states}

    def epsilon_greedy_policy(state):
        if np.random.rand() < epsilon:
            return np.random.choice(actions)
        else:
            return actions[np.argmax(Q[state])]

    for _ in range(episodes):
        episode = []
        state = np.random.choice(states)
        while state != 4:  # État terminal
            action = epsilon_greedy_policy(state)
            next_state = np.random.choice(states)
            reward = np.random.randn()  # Récompense aléatoire
            episode.append((state, action, reward))
            state = next_state

        G = 0
        for t in reversed(range(len(episode))):
            state, action, reward = episode[t]
            G = gamma * G + reward
            if (state, action) not in [(x[0], x[1]) for x in episode[:t]]:
                Q[state][actions.index(action)] += (G - Q[state][actions.index(action)]) / len(episode)
                policy[state] = actions[np.argmax(Q[state])]

    return policy, Q

# Exécution
optimal_policy, action_value_function = monte_carlo_control_on_policy(episodes=1000)
print("Politique Optimale :")
for state, action in optimal_policy.items():
    print(f"État {state}: {action}")

print("Fonction de Valeur Action Estimée :")
for state, values in action_value_function.items():
    for action, value in zip(actions, values):
        print(f"Q({state}, {action}) = {value:.2f}")
```


## Conclusion

Les méthodes de Monte Carlo sont des techniques puissantes pour l’apprentissage par renforcement, en particulier *lorsque l’on ne dispose pas d’un modèle de l’environnement.*
- Les algorithmes de Monte Carlo permettent d’apprendre des politiques optimales sur la base de retours observés dans des épisodes complets, offrant ainsi une alternative intéressante aux méthodes basées sur les différences temporelles.



