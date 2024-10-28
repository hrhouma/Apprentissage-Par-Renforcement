---
# Exemple détaillé pour l'algorithme **ε-greedy** avec deux valeurs différentes de **ε** (grand et petit), pour illustrer la balance entre exploration et exploitation.
---

# Exemple : Algorithme ε-greedy avec ε Grand et Petit

**Contexte :**
Imaginons que nous avons trois machines à sous (A, B et C), et chaque machine rapporte une récompense moyenne différente :
- Machine **A** : récompense moyenne de 5
- Machine **B** : récompense moyenne de 3
- Machine **C** : récompense moyenne de 8

L'objectif est de trouver la machine qui offre la meilleure récompense moyenne en équilibrant exploration (essayer les différentes machines) et exploitation (jouer sur la machine qui semble la meilleure).

**Définition de l'Algorithme ε-greedy** : 
- Avec une probabilité **ε**, l’agent choisit une machine aléatoirement (exploration).
- Avec une probabilité \(1 - ε\), l’agent choisit la machine avec la plus haute récompense moyenne observée (exploitation).

---

#### 1. Exemple avec **ε élevé (ε = 0.8)**

Ici, **80% du temps, l'agent explore** en choisissant une machine aléatoirement, et **20% du temps, il exploite** la machine avec la meilleure récompense moyenne observée.

- **Étape 1** : L'agent commence avec aucune information sur les machines.
- **Étape 2** : Il explore la majorité du temps (80%) et essaye régulièrement toutes les machines pour recueillir des informations.
- **Étape 3** : Après plusieurs tours, même si l'agent découvre que la machine C offre la meilleure récompense, il continue à explorer très souvent. Donc, même si la machine C semble être la meilleure, il n'exploitera ce choix qu'environ 20% du temps.

**Résultat avec ε = 0.8** :
- L'agent passera beaucoup de temps à essayer les différentes machines, ce qui peut l'amener à passer à côté de la meilleure option pendant un certain temps. Cette stratégie est utile si l’on pense que la machine optimale pourrait changer ou si l'on a peu d'informations initiales et que l'on veut éviter de s'engager trop vite dans l'exploitation.

---

#### 2. Exemple avec **ε faible (ε = 0.1)**

Ici, **10% du temps, l'agent explore** en choisissant une machine aléatoirement, et **90% du temps, il exploite** la machine avec la plus haute récompense moyenne observée.

- **Étape 1** : L'agent commence par essayer toutes les machines quelques fois.
- **Étape 2** : Après avoir identifié que la machine C donne la meilleure récompense moyenne, il continue de choisir la machine C la majorité du temps (90%).
- **Étape 3** : L'agent n'explore que 10% du temps, donc il revient occasionnellement sur les machines A et B pour vérifier si leur rendement a changé, mais il privilégie fortement la machine C.

**Résultat avec ε = 0.1** :
- L'agent exploite la machine C presque tout le temps, maximisant sa récompense en fonction des informations connues. Cela est efficace si l'on a déjà une idée précise de la meilleure machine et que l'on souhaite minimiser les pertes dues à l'exploration.

---

### Conclusion : Différences entre ε Grand et Petit

| **Valeur de ε** | **Exploration**                         | **Exploitation**                   | **Avantages**                                         | **Inconvénients**                                      |
|------------------|----------------------------------------|------------------------------------|-------------------------------------------------------|--------------------------------------------------------|
| **ε = 0.8**     | L’agent explore fréquemment            | Exploite rarement la meilleure option| Utile pour explorer toutes les options et éviter les biais initiaux.| Peut mener à des gains moyens si une machine est clairement meilleure.|
| **ε = 0.1**     | L’agent explore occasionnellement      | Exploite souvent la meilleure option | Efficace pour maximiser les gains si l’on connaît la meilleure option.| Risque de négliger des options qui pourraient s’améliorer.|

Cet exemple montre comment ajuster **ε** influence la stratégie et les gains dans le temps. Un **ε élevé** permet d'explorer davantage mais peut sacrifier les gains immédiats, tandis qu'un **ε faible** permet d'exploiter la meilleure option dès qu'elle est identifiée, au risque de rater des changements dans les autres options.
