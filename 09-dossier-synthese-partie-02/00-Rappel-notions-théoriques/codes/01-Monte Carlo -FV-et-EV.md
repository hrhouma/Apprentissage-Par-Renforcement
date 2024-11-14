# Lecture 01 - Monte Carlo *"première visite"* VS *"toutes les visites"*

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

------------

# Lecture 02 - **fréquentation d'un nouveau café**.

### Scénario : Mesurer l'intérêt pour un nouveau café en ville

Imaginons qu’un nouveau café vient d'ouvrir, et l'on souhaite mesurer l’intérêt qu’il suscite auprès des clients.

### 1. Première Visite (first-visit)
**Quand l’utiliser** : Cette méthode est utile pour savoir combien de clients ont été intéressés **dès leur première visite**.

**Exemple d’interprétation** :
   - On observe les clients la première fois qu’ils visitent le café. Est-ce qu’ils aiment l’endroit, est-ce qu’ils reviennent une autre fois ?
   - Ici, seule **la première expérience** est comptée : on se concentre sur l’effet initial que le café produit sur les nouveaux clients.
   - Si un grand nombre de clients apprécient leur première visite, cela peut indiquer que l’endroit est attrayant et répond bien aux attentes initiales.

**Utilité** : Cette méthode est utile si l’on cherche à évaluer le **pouvoir d’attraction initial du café**. C'est pertinent pour les gestionnaires qui veulent savoir si les premières impressions des clients sont positives.

### 2. Toutes les Visites (every-visit)
**Quand l’utiliser** : Cette méthode est utile pour mesurer **la fidélité des clients** en comptant chaque visite au café, pas seulement la première.

**Exemple d’interprétation** :
   - Ici, on compte toutes les visites d'un client, même s’il revient régulièrement. On mesure ainsi la **fréquence des visites** et l’intérêt continu pour le café au fil du temps.
   - Si certains clients reviennent tous les jours ou chaque semaine, cette méthode capture cette **fidélité et satisfaction régulière**, indiquant que l’expérience proposée plaît suffisamment pour les faire revenir.

**Utilité** : Cette approche est utile si l'on souhaite mesurer **la fidélité et l’intérêt à long terme** des clients. Elle aide à voir si le café continue à plaire après la première visite, ce qui est essentiel pour bâtir une clientèle régulière.

### En résumé
- **Première visite** : Mesure l'impact de la **première expérience** au café, utile pour évaluer l'attrait initial.
- **Toutes les visites** : Mesure la **régularité et la fidélité** des clients, utile pour évaluer si le café réussit à conserver une clientèle.

Ces deux mesures permettent au gérant du café de savoir si le lieu attire d’abord par son ambiance ou son offre (première visite) et, à plus long terme, s’il fidélise réellement les clients (toutes les visites).


------------
# Lecture 03 - **Est-ce du Monte Carlo ?**.

J'ai utilisé l'exemple du café pour illustrer les concepts de **première visite** et **toutes les visites**, mais il manquait l'essence même de **Monte Carlo**, qui repose sur l’**aléatoire** et la **simulation**.

La méthode de Monte Carlo est généralement utilisée dans des situations où les résultats sont incertains et dépendent de multiples facteurs aléatoires. Voici comment cela se traduit dans un exemple plus proche du vrai **Monte Carlo** appliqué.

### Exemple adapté : Prévisions de fréquentation d’un café grâce à la méthode Monte Carlo

Imaginons que le propriétaire d'un café veut estimer combien de clients le café pourrait attirer au cours du mois prochain. Il sait que la fréquentation est influencée par plusieurs facteurs **aléatoires** comme la météo, les jours de semaine, les événements locaux, et les promotions.

Pour effectuer cette prévision, on peut utiliser une **simulation de Monte Carlo** en modélisant les visites des clients comme des événements probabilistes :

1. **Modéliser les visites des clients** : Chaque jour, le nombre de visites dépendra de probabilités (ex. : 30 % de chance de pluie, 50 % de chance d’une promotion, etc.).
2. **Première visite Monte Carlo** : On pourrait vouloir estimer combien de clients viendront **pour la première fois** au cours du mois. En simulant chaque jour avec les facteurs aléatoires, on compterait **uniquement** les nouvelles visites dans chaque simulation.
3. **Toutes les visites Monte Carlo** : On peut aussi simuler **chaque visite quotidienne** pour voir le nombre total de passages (y compris les clients réguliers). Cela permet de voir comment les visites totales varient dans des conditions changeantes.

En répétant cette simulation des milliers de fois, on obtiendrait une estimation de la fréquentation moyenne du café, prenant en compte la **variabilité** et les différents scénarios possibles. 

### Pourquoi c'est du Monte Carlo ?

Parce que cette approche :
- Utilise des **simulations aléatoires** (par ex., chaque jour avec différents facteurs aléatoires) pour prédire le nombre de visites.
- Fournit des estimations statistiques (moyennes, écarts-types) en répétant les simulations pour obtenir une **approximation**.

Ainsi, en appliquant Monte Carlo à ce contexte, on peut prédire de manière probabiliste le succès d’un café selon les différents aléas de chaque jour, et mesurer l’effet global (toutes les visites) ou initial (première visite) dans un cadre réaliste.


------------
# Lecture 04 - **Comparaison simplifiée**

Je vous présente une table comparative simplifiée pour mieux comprendre **quand utiliser "première visite"** (first-visit) et **"toutes les visites"** (every-visit) en méthode Monte Carlo, avec des exemples de situations réelles comme le marketing et l'engagement des clients.

| **Critère**              | **Première Visite (first-visit)**                                                      | **Toutes les Visites (every-visit)**                                                     |
|--------------------------|----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| **Quand l’utiliser**     | Pour évaluer l'impact **initial** d'un événement ou d'une première interaction.         | Pour mesurer l'**engagement global** ou la **fidélité** au fil du temps.                |
| **Objectif principal**   | Capturer l’effet de la **première impression** sur un client ou utilisateur.            | Évaluer la **fréquence et la persistance** de l'intérêt ou de l’interaction.            |
| **Exemples de situations** | - L’effet d’une première campagne publicitaire ou promotion. <br> - Première impression d’un produit ou d’un service. <br> - Visite initiale sur un site web ou en magasin. | - Suivre l’attrait d’un produit via toutes les interactions de clients réguliers. <br> - Mesurer le nombre total de visites en magasin ou sur un site web pour fidéliser. <br> - Évaluer l'impact d'une campagne publicitaire répétée. |
| **Utilité en marketing** | Comprendre si la **première interaction** attire les clients et donne envie d’essayer.  | Analyser **la fidélisation** et l'impact cumulatif de plusieurs campagnes de marketing.  |
| **Quand préférer cette méthode** | Lorsque l'**effet de nouveauté** ou l'impact initial est crucial pour le succès (par ex., lancement d’un produit). | Lorsqu’on cherche à savoir si le produit ou service **garde l’intérêt** des utilisateurs ou génère des clients réguliers. |
| **Limite**               | Ne tient pas compte des interactions répétées, donc moins utile pour la fidélité à long terme. | Peut être trompeur si les premières impressions sont mauvaises, même si les visites augmentent ensuite. |

### Résumé rapide :
- **Première Visite (first-visit)** : Idéale pour évaluer **la première impression** ou le succès initial d’une campagne, un produit ou une interaction.
- **Toutes les Visites (every-visit)** : Préférable pour mesurer **l'engagement à long terme** et la fidélité, en comptant chaque interaction. 

Ces deux méthodes offrent des insights complémentaires en marketing, permettant d’optimiser à la fois **l’attraction initiale** et la **loyauté à long terme** des clients.

------------

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



