# Apprentissage Hors-Politique (Off-Policy) et Q-Learning

L'apprentissage par renforcement (RL - **Reinforcement Learning**) peut être classé en deux grandes catégories en fonction de la manière dont l'agent apprend à partir de ses interactions avec l'environnement : **on-policy** et **off-policy**. Le **Q-Learning** est un exemple classique d'**apprentissage hors-politique (off-policy)**.

#### 1. **On-Policy vs Off-Policy**

Avant d'expliquer pourquoi le **Q-Learning** est un algorithme hors-politique, il est important de comprendre la distinction entre **on-policy** et **off-policy** :

- **On-Policy** : 
  - L'agent **apprend** et **exécute** des actions en suivant la **même politique**.
  - La politique utilisée pour explorer l'environnement (behavior policy) est **la même** que la politique cible (target policy), que l'agent essaie d'optimiser.
  - Exemple : L'agent évalue ou améliore la politique qu'il suit pendant l'apprentissage.

- **Off-Policy** :
  - L'agent **apprend** à partir d'une politique, mais **exécute** des actions en suivant une **autre politique**.
  - Cela signifie que la politique utilisée pour explorer l'environnement (behavior policy) peut être **différente** de la politique cible (target policy), que l'agent apprend à optimiser.
  - Exemple : L'agent peut apprendre une politique optimale tout en suivant une politique différente, comme une politique ε-greedy qui favorise l'exploration.

#### 2. **Pourquoi le Q-Learning est Off-Policy ?**

Le **Q-Learning** est un algorithme d'apprentissage hors-politique parce que l'agent peut apprendre une **politique cible optimale** sans nécessairement suivre cette politique pendant l'apprentissage. Autrement dit, l'agent n'a pas besoin de suivre la politique qu'il est en train d'apprendre (la target policy) pour mettre à jour ses estimations.

##### Algorithme du Q-Learning :

La mise à jour de la fonction Q(s, a) dans le Q-Learning se fait avec la règle suivante :

$$Q(s, a) \leftarrow Q(s, a) + \alpha \left( r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right)$$

- α : Taux d'apprentissage (learning rate)
- γ : Facteur d'actualisation (discount factor)
- r : Récompense immédiate obtenue après avoir exécuté l'action a depuis l'état s
- max_{a'} Q(s', a') : Estimation de la valeur d'action optimale dans l'état futur s' (la meilleure action que l'agent pourrait choisir dans s')

##### Pourquoi est-ce hors-politique ?

- Le Q-Learning **apprend une politique optimale** en cherchant à maximiser Q(s, a) pour chaque état-action, mais **l'agent n'a pas besoin de suivre cette politique pendant qu'il explore l'environnement**.
- Pendant l'exploration, l'agent peut suivre une **politique d'exploration** différente, comme une politique ε-greedy qui choisit parfois des actions aléatoires pour découvrir de nouvelles récompenses dans l'environnement.
- La mise à jour de Q(s, a) repose sur l'hypothèse que l'agent choisira l'action a' qui maximise Q(s', a'), **indépendamment de l'action réellement prise** dans l'état s. Cette capacité à mettre à jour les valeurs optimales sans suivre la politique cible fait du Q-Learning un algorithme **off-policy**.

En résumé :
- **Behavior policy** (exploration) : L'agent peut choisir une action aléatoire pour explorer (par exemple, avec ε-greedy).
- **Target policy** (exploitation) : L'agent cherche à maximiser Q(s, a) et apprend la meilleure action à prendre à chaque état, sans la suivre nécessairement pendant l'exploration.

#### 3. **Avantages de l'apprentissage Off-Policy** (comme dans le Q-Learning)

- **Exploration plus large** : L'agent peut utiliser une politique d'exploration agressive (comme ε-greedy), tout en apprenant une politique optimale. Cela permet de mieux explorer l'environnement pour découvrir toutes les possibilités.
- **Utilisation d'anciens échantillons** : L'agent peut apprendre à partir de données ou d'échantillons stockés (c'est ce qu'on appelle parfois **expérience rejouée**), car les données n'ont pas besoin de provenir de la politique optimale actuelle.
- **Convergence vers une politique optimale** : Le Q-Learning est prouvé pour converger vers une politique optimale, même si une politique non optimale est suivie pendant l'apprentissage.

#### 4. **Différence entre Q-Learning et SARSA (on-policy)**

Pour mieux comprendre l'aspect **off-policy** du Q-Learning, il est intéressant de le comparer avec un algorithme **on-policy** tel que **SARSA**.

Dans **SARSA** (State-Action-Reward-State-Action), l'agent met à jour la fonction Q(s, a) en utilisant **l'action réellement choisie** dans l'état suivant s'. La règle de mise à jour dans SARSA est la suivante :

$$Q(s, a) \leftarrow Q(s, a) + \alpha \left( r + \gamma Q(s', a') - Q(s, a) \right)$$

Dans SARSA :
- a' est l'**action réellement prise** dans l'état s', donc l'agent apprend une politique en fonction des actions qu'il exécute.
- SARSA est **on-policy**, car il met à jour la fonction Q en suivant la **même politique** qu'il exécute pendant l'apprentissage.

### Conclusion

Le **Q-Learning** est un algorithme hors-politique (**off-policy**) parce qu'il apprend une **politique optimale** indépendamment de la politique effectivement suivie pendant l'exploration. Cela permet à l'agent d'explorer l'environnement librement tout en apprenant à long terme quelle est la meilleure action à prendre dans chaque état. Ce contraste avec des algorithmes on-policy comme **SARSA** montre la flexibilité du Q-Learning, surtout dans des environnements complexes où l'exploration extensive est nécessaire.
