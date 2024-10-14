

*******************************************************************
### Q-Learning — Apprentissage des paires état-action

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right]
$$




### Explication des termes :

- **$$ V(S_t) $$** : la *valeur* de l'état actuel $$ S_t $$
- **$$ R_{t+1} $$** : la *récompense immédiate* reçue après l'action
- **$$ \alpha $$** : le *taux d'apprentissage*, un nombre compris entre 0 et 1 qui contrôle à quelle vitesse l'agent apprend
- **$$ \gamma $$** : le *facteur de discount* (ou de dépréciation), un nombre compris entre 0 et 1, qui réduit l'importance des récompenses futures. Plus $$ \gamma $$ est proche de 1, plus l'agent valorise les récompenses futures

### Décomposition pour les politiques optimales

Dans le cas des **politiques optimales** (optimisation de l'agent), l'équation de Bellman devient :

$$
V^*(S) = \max_a \mathbb{E} \left[ R_{t+1} + \gamma V^*(S_{t+1}) \right]
$$

Pour une notation plus précise avec conditions :

$$
V^*(s) = \max_a \mathbb{E} \left[ R_{t+1} + \gamma V^*(s_{t+1}) \mid s_t = s, a_t = a \right]
$$

### Ajustements effectués :

- Utilisation de la minuscule $$ s $$ pour les états, selon la convention.
- Ajout des conditions pour indiquer que l'espérance est calculée conditionnellement.

Cela exprime que la valeur optimale de l'état $$ S $$ est la meilleure valeur que l'agent peut obtenir en choisissant l'action optimale. Assurez-vous que votre plateforme supporte le rendu LaTeX pour un affichage correct.


### Q-Learning — Apprentissage des paires état-action

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right]
$$





-------------------------
### Équation de Bellman 
-------------------------

- L'équation de Bellman est fondamentale dans l'apprentissage par renforcement, car elle décrit la relation récursive entre la valeur d'un état et les valeurs des états futurs. Elle est utilisée pour calculer les valeurs optimales d'une politique ou d'une fonction de valeur dans un processus de décision markovien (MDP).
- Les équations de Bellman sont les bases théoriques derrière de nombreux algorithmes d'apprentissage par renforcement, y compris le TD-Learning et le Q-Learning.


### Équation de Bellman pour la Valeur d'État (Bellman Equation for State Value)

L'équation de Bellman pour la valeur d'un état **$$V(S)$$** est :

$$
V(S) = \mathbb{E} \left[ R_{t+1} + \gamma V(S_{t+1}) \right]
$$

Cela signifie que la valeur d'un état **$$S$$** est égale à l'espérance de la récompense immédiate **$$R_{t+1}$$** plus la valeur de l'état suivant **$$S_{t+1}$$**, actualisée par le facteur **$$gamma$$**.

### Équation de Bellman pour la Valeur d'État-Action (Bellman Equation for Action Value)

Pour une fonction de valeur d'action **$$Q(S, A)$$**, l'équation de Bellman est :

$$
Q(S, A) = \mathbb{E} \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) \right]
$$

Cela signifie que la valeur de la paire état-action **$$(S, A)$$** est égale à l'espérance de la récompense immédiate **$$R_{t+1}$$** plus la meilleure valeur de l'action future à partir de l'état suivant **$$S_{t+1}$$**, actualisée par **$$gamma$$**.


-------------------------


### Décomposition pour les politiques optimales

Dans les cas de **politiques optimales** (optimisation de l'agent), l'équation de Bellman devient :

$$
V^*(S) = \max_a \mathbb{E} \left[ R_{t+1} + \gamma V^*(S_{t+1}) \right]
$$

$$
V^*(s) = \max_a \mathbb{E} \left[ R_{t+1} + \gamma V^*(s_{t+1}) \mid s_t = s, a_t = a \right]
$$

Cela signifie que la valeur optimale de l'état **$$s$$** est la meilleure valeur que l'agent peut obtenir en choisissant l'action optimale \(a\) dans cet état. L'espérance \(\mathbb{E}\) est calculée conditionnellement à partir de l'état **$$s_t = s$$** et de l'action **$$a_t = a$$**.

### Équation de Bellman pour Q-Learning

L'équation de Bellman est directement liée à l'algorithme de **Q-Learning**, qui met à jour la fonction de valeur d'état-action **$$Q(S, A)$$** avec l'équation suivante :

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right]
$$


***************
