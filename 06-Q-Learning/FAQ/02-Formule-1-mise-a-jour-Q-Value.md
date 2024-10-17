# Les deux formes de l'algorithme de mise à jour **$$Q(s, a)$$**

Dans le cadre du Q-learning, la mise à jour de la fonction **Q(s, a)** se fait selon deux formules couramment utilisées, en fonction de la manière dont on pondère l'apprentissage entre la nouvelle information et l'estimation précédente.

# 1. Forme classique avec **α** (taux d'apprentissage) :
Cette forme pondère la différence entre l'ancienne estimation et la nouvelle valeur calculée à partir de la récompense immédiate et de la meilleure action possible dans l'état suivant.

$$Q(s, a) \leftarrow Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right]$$

Ici, **α** (alpha) est le taux d'apprentissage qui contrôle à quel point les nouvelles informations influencent la mise à jour. Si **α** est proche de 1, l'agent se fie principalement à la nouvelle information ; s'il est proche de 0, il se fie davantage à l'estimation précédente.

# 2. Forme équivalente avec **(1 - α)** :
Une forme équivalente de la mise à jour consiste à réécrire la formule en pondérant directement la nouvelle estimation avec **α** et l'ancienne estimation avec **(1 - α)** :

$$Q(s, a) \leftarrow (1 - \alpha) Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') \right]$$

Dans cette version, on voit explicitement comment **(1 - α)** contrôle l'influence de l'ancienne valeur de **Q(s, a)**, et **α** contrôle l'intégration de la nouvelle information obtenue après la prise de l'action **a** dans l'état **s**.

Les deux formes sont équivalentes, mais elles montrent de manière différente la combinaison de la nouvelle information et de l'estimation passée.
