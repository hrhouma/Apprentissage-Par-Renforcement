# Introduction au TD-Learning

- Le **TD-Learning** est une méthode d'apprentissage par renforcement qui combine des aspects des méthodes de Monte Carlo et de la programmation dynamique. Il permet à un agent d'apprendre en mettant à jour les estimations de la valeur des états ou des paires état-action à chaque étape, sans attendre la fin d'un épisode.

- Le **TD-Learning** (Temporal Difference Learning) est une technique d'apprentissage par renforcement qui aide un agent à prendre de meilleures décisions en apprenant progressivement de ses expériences.

## Simplification

1. *Valeur de l'État* **$$V(S_t)$$** : C'est une estimation de la qualité d'un état donné. Plus la valeur est élevée, plus l'état est considéré comme bon.
2. *Récompense Immédiate* **($R_{t+1}$)** : C'est le retour immédiat reçu après une action. Cela peut être positif (récompense) ou négatif (punition).
3. *Taux d'Apprentissage* **($\alpha$)** : Un nombre entre 0 et 1 qui détermine à quelle vitesse l'agent apprend. Un taux élevé signifie que l'agent s'adapte rapidement aux nouvelles informations.
4. *Facteur de Discount* **($\gamma$)** : Un nombre entre 0 et 1 qui réduit l'importance des récompenses futures. Plus il est proche de 1, plus l'agent valorise les récompenses futures.

## Fonctionnement

- **Mise à Jour Progressive** : Contrairement aux méthodes qui attendent la fin d'un épisode pour apprendre, le TD-Learning met à jour les valeurs après chaque étape.
- **Combinaison d'Approches** : Il utilise des idées des méthodes Monte Carlo (qui apprennent à partir d'expériences complètes) et de la programmation dynamique (qui utilise des estimations actuelles pour améliorer les décisions futures).
  
## Pourquoi Utiliser TD-Learning ?

- **Efficacité** : L'apprentissage se fait en temps réel, ce qui est utile dans des environnements où les épisodes sont longs ou continus.
- **Flexibilité** : Il s'adapte bien aux environnements changeants, permettant à l'agent d'améliorer ses décisions au fur et à mesure qu'il acquiert de nouvelles informations.

En résumé, le TD-Learning est une méthode efficace pour enseigner à un agent comment naviguer dans un environnement complexe en apprenant progressivement de ses propres actions et résultats.





# 2 - Concepts Clés

### 1. Équation de Mise à Jour TD(0)

L'algorithme TD(0) met à jour la valeur d'un état en utilisant l'équation suivante :

$$
V(S_t) \leftarrow V(S_t) + \alpha [R_{t+1} + \gamma V(S_{t+1}) - V(S_t)]
$$

**Termes :**
- **$$V(S_t)$$** : Valeur de l'état actuel.
- **$$R_{t+1}$$** : Récompense immédiate après l'action.
- **$$\alpha$$** : Taux d'apprentissage.
- **$$\gamma$$** : Facteur de discount.

### 2. Q-Learning

Le **Q-Learning** est une extension du TD-Learning qui apprend les valeurs des paires état-action :

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha [R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t)]
$$

## Comparaison avec Monte Carlo

- **Monte Carlo** : Nécessite la fin d'un épisode pour mettre à jour les valeurs.
- **TD-Learning** : Met à jour après chaque étape, permettant un apprentissage plus rapide dans des environnements longs ou infinis.

## Applications et Exemples

### Exemple Pratique : Lancer de Dé

Pour estimer la valeur attendue d'un lancer de dé :

$$
E(X) = \frac{1 + 2 + 3 + 4 + 5 + 6}{6} = 3.5
$$

### Code Python pour Estimation Empirique

```python
import numpy as np
import matplotlib.pyplot as plt

def estimate_expected_value(num_throws):
    sum_of_dice_values = 0
    running_average = []
    
    for i in range(num_throws):
        dice_value = np.random.randint(1, 7)
        sum_of_dice_values += dice_value
        running_average.append(sum_of_dice_values / (i + 1.0))
    
    average = sum_of_dice_values / num_throws
    print(f"Valeur moyenne après {num_throws} lancers: {average}")
    
    plt.plot(running_average, label="Moyenne empirique")
    plt.axhline(y=3.5, color='k', linestyle='-', label="Valeur attendue théorique (3.5)")
    plt.legend()
    plt.show()

estimate_expected_value(10000)
```

## Conclusion

Le TD-Learning est une méthode puissante pour l'apprentissage en temps réel dans des environnements dynamiques. Le Q-Learning, une version avancée, permet d'apprendre directement les actions optimales.

Pour plus de détails sur les algorithmes et leurs applications, vous pouvez consulter des ressources comme "Reinforcement Learning: An Introduction" par Sutton et Barto.



-------------
# Annexe 1 - Pourquoi l'appelle-t-on TD(0) ?
-------------


Le **TD(0)** est appelé ainsi parce qu'il utilise une estimation à un seul pas pour mettre à jour la valeur d'un état. Le "0" indique qu'il ne regarde qu'un seul pas dans le futur (c'est-à-dire, la prochaine récompense et l'état suivant immédiat).

### Différence avec le Q-Learning

- **TD(0)** : Met à jour uniquement la valeur des états.
- **Q-Learning** : Met à jour la valeur des paires état-action, ce qui permet de déterminer directement quelle action est optimale dans chaque état.

-------------
# Annexe 2 - Différence avec l'Équation de Bellman
-------------

- **Équation de Bellman** : Utilisée dans la programmation dynamique, elle calcule les valeurs optimales en utilisant des connaissances complètes de l'environnement (modèle).
- **TD(0)** et **Q-Learning** : N'ont pas besoin de modèle complet. Ils apprennent à partir d'expériences directes et ajustent les valeurs au fur et à mesure.

En résumé, TD(0) et Q-Learning sont des méthodes d'apprentissage par renforcement qui permettent d'apprendre sans connaître entièrement l'environnement, contrairement à l'équation de Bellman utilisée dans des contextes où le modèle est connu.

-------------
# Annexe 3 - Différence des méthodes TD(0), TD(1), TD(2), et Q-Learning :
-------------


```
| Méthode      | Type       | Mise à jour de la valeur                   | Équation                                                                 | Avantages                                           | Inconvénients                         |
|--------------|------------|--------------------------------------------|--------------------------------------------------------------------------|-----------------------------------------------------|---------------------------------------|
| TD(0)        | On-policy  | État uniquement                            | V(S_t) ← V(S_t) + α [R_{t+1} + γ V(S_{t+1}) - V(S_t)]                    | Simple, rapide                                      | Ne considère qu’un seul pas           |
| TD(1)        | N-step     | État et prochaines récompenses             | V(S_t) ← V(S_t) + α [Σ R_{t+i} + γ^i V(S_{t+i})]                         | Mieux pour de courtes époques                      | Complexité plus élevée                |
| TD(2)        | N-step     | État et plusieurs récompenses              | V(S_t) ← V(S_t) + α [Σ R_{t+i} + γ^i V(S_{t+i})]                         | Équilibre entre exploration et exploitation         | Peut être lent                        |
| Q-Learning   | Off-policy | Paire état-action                          | Q(S_t, A_t) ← Q(S_t, A_t) + α [R_{t+1} + γ max Q(S_{t+1}, a) - Q(S_t, A_t)] | Efficace pour trouver une politique optimale       | Nécessite un plus grand espace de stockage |
```



## Anenxe 4 - Résumé **TD(0)**  vs **TD(1)** vs **TD(2)** 

- **TD(0)** : Met à jour la valeur d'un état immédiatement après chaque action, en utilisant la récompense immédiate et la valeur de l'état suivant.

- **TD(1)** et **TD(2)** : Utilisent plusieurs étapes futures pour mettre à jour les valeurs, ce qui peut améliorer la précision mais augmente la complexité.

- **Q-Learning** : Apprend les valeurs des paires état-action, permettant de déterminer directement l'action optimale à partir de n'importe quel état. C'est une méthode off-policy, ce qui signifie qu'elle apprend indépendamment de la politique suivie par l'agent.

Chaque méthode a ses propres avantages et inconvénients en fonction du contexte d'application et des besoins spécifiques de l'environnement d'apprentissage.




# Équations pour **TD(0)**, **TD(1)**, **TD(2)**, et ainsi de suite, ainsi que pour **Q-Learning**.

### TD(0) — Mise à jour immédiate après chaque étape

L'algorithme **TD(0)** met à jour la valeur de l'état après chaque transition, en tenant compte de la récompense immédiate et de la valeur estimée de l'état suivant :

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right]
$$

### TD(1) — Utilisation d'une récompense complète après un épisode

Dans **TD(1)**, on attend une étape supplémentaire, en tenant compte non seulement de la récompense immédiate mais aussi de la récompense après deux étapes :

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 V(S_{t+2}) - V(S_t) \right]
$$

### TD(2) — Deux étapes de transition

Pour **TD(2)**, la mise à jour prend en compte deux étapes supplémentaires, ce qui donne :

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 V(S_{t+3}) - V(S_t) \right]
$$

### TD(n) — Généralisation pour \(n\) étapes

De manière générale, pour **TD(n)**, où nous utilisons \(n\) étapes futures pour la mise à jour, l'équation devient :

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ \sum_{k=1}^{n} \gamma^{k-1} R_{t+k} + \gamma^n V(S_{t+n}) - V(S_t) \right]
$$

Ici, \( \sum_{k=1}^{n} \gamma^{k-1} R_{t+k} \) représente la somme pondérée des récompenses jusqu'à \(n\) étapes.

### Q-Learning — Apprentissage des paires état-action

Le **Q-Learning** est une extension du TD-Learning qui apprend des paires état-action \( (S, A) \) au lieu de simplement les valeurs d'états. L'équation de mise à jour pour **Q-Learning** est :

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right]
$$

- **$$Q(S_t, A_t)$$** : la valeur de la paire état-action **$$(S_t, A_t)$$**.
- **$$\max_{a} Q(S_{t+1}, a)$$** : la meilleure valeur de l'action possible à partir de l'état suivant **$$S_{t+1}$$**.

### Résumé

- **TD(0)** se met à jour immédiatement après une étape.
- **TD(1)** se met à jour en prenant en compte une étape supplémentaire.
- **TD(2)** prend en compte deux étapes.
- **TD(n)** généralise à \(n\) étapes avant de faire une mise à jour.
- **Q-Learning** optimise l'apprentissage pour des paires état-action, cherchant à maximiser la récompense en choisissant l'action optimale à chaque étape.






### TD(0) — Mise à jour immédiate après chaque étape

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right]
$$

### TD(1) — Utilisation d'une récompense après une étape supplémentaire

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 V(S_{t+2}) - V(S_t) \right]
$$

### TD(2) — Utilisation de deux étapes supplémentaires

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 V(S_{t+3}) - V(S_t) \right]
$$

### TD(n) — Généralisation pour \(n\) étapes

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ \sum_{k=1}^{n} \gamma^{k-1} R_{t+k} + \gamma^n V(S_{t+n}) - V(S_t) \right]
$$

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








------------------------------
# Annexe 5 - Résumé
------------------------------


### TD(0) — Mise à jour immédiate après chaque étape

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right]
$$

### TD(1) — Utilisation d'une récompense complète après un épisode

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 V(S_{t+2}) - V(S_t) \right]
$$

### TD(2) — Deux étapes de transition

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 V(S_{t+3}) - V(S_t) \right]
$$

### TD(n) — Généralisation pour $$n$$ étapes

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ \sum_{k=1}^{n} \gamma^{k-1} R_{t+k} + \gamma^n V(S_{t+n}) - V(S_t) \right]
$$

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


------------------------









# Citations:

[1] https://mpatacchiola.github.io/blog/2017/01/29/dissecting-reinforcement-learning-3.html

[2] https://fr.wikipedia.org/wiki/Temporal_difference_learning

[3] https://www.td.com/ca/fr/investir/placement-en-direct/education

[4] https://www.lancaster.ac.uk/stor-i-student-sites/jordan-j-hood/2021/04/12/reinforcement-learning-temporal-difference-td-learning/

[5] https://towardsdatascience.com/temporal-difference-learning-and-the-importance-of-exploration-an-illustrated-guide-5f9c3371413a?gi=de80dad61959

[6] https://www.csd.uwo.ca/~xling/cs346a/extra/tdgammon.pdf
