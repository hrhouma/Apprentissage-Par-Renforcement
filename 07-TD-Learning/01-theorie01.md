# Introduction à TD-Learning (Temporal Difference Learning)

## 1. Qu'est-ce que TD-Learning ?

Le **TD-Learning** (ou Apprentissage par Différence Temporelle) est une méthode d'**apprentissage par renforcement**. L'idée principale est que l'agent apprend en se basant sur les **récompenses reçues immédiatement** après une action, mais aussi en prenant en compte la **valeur estimée des états futurs**.

### Pourquoi est-ce utile ?
TD-Learning est utile lorsque vous n'avez pas besoin d'attendre la fin d'un épisode (comme une partie de jeu) pour apprendre. Vous apprenez au fur et à mesure.

## 2. L'équation principale de TD(0)

L'algorithme TD(0) est l'une des versions les plus simples de TD-Learning. Il met à jour la valeur d'un état après chaque action.

Voici l'équation de mise à jour de TD(0) :

$$
V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right]
$$

### Explication des termes :
- $$ V(S_t) $$ : la **valeur** de l'état actuel $$ S_t $$
- $$ R_{t+1} $$ : la **récompense immédiate** reçue après l'action
- $$ \alpha $$ : le **taux d'apprentissage**, un nombre compris entre 0 et 1 qui contrôle à quelle vitesse l'agent apprend
- $$ \gamma $$ : le **facteur de discount** (ou de dépréciation), un nombre compris entre 0 et 1, qui réduit l'importance des récompenses futures. Plus $$ \gamma $$ est proche de 1, plus l'agent valorise les récompenses futures

**En termes simples**, cela signifie que l'agent met à jour sa compréhension de l'état actuel en tenant compte de la récompense qu'il vient de recevoir et de la valeur de l'état suivant.

## 3. Comparaison entre TD-Learning et Monte Carlo

Dans les méthodes de **Monte Carlo**, l'agent doit attendre **la fin de l'épisode** (par exemple, la fin d'une partie) pour ajuster la valeur de ses états.

Avec **TD-Learning**, l'agent ajuste immédiatement après chaque étape, ce qui est beaucoup plus rapide dans des environnements où les épisodes sont longs ou infinis.

## 4. Exemple avec des dés : Estimation d'une Valeur Attendue

Pour mieux comprendre, imaginons que nous essayons d'estimer la **valeur attendue** lorsque nous lançons un dé.

La **valeur attendue théorique** pour un dé à 6 faces est :

$$
E(X) = \frac{1 + 2 + 3 + 4 + 5 + 6}{6} = 3.5
$$

Cela signifie que si vous lancez un dé de manière infinie, la moyenne des valeurs sera **3.5**.

## 5. Estimation empirique avec du code Python

Voici un code Python qui **simule** le lancer d'un dé et estime la valeur attendue après un certain nombre de lancers. Nous afficherons la **moyenne empirique** après chaque lancer.

```python
import numpy as np
import matplotlib.pyplot as plot

def estimate_expected_value(num_throws):
    sum_of_dice_values = 0
    running_average = []
    
    for i in range(num_throws):
        dice_value = np.random.randint(1, 7)
        sum_of_dice_values += dice_value
        running_average.append(sum_of_dice_values / (i + 1.0))
    
    average = sum_of_dice_values / num_throws
    print(f"Valeur moyenne après {num_throws} lancers: {average}")
    
    # Graphique
    x = [i for i in range(num_throws)]
    y = [3.5 for i in range(num_throws)]
    
    plot.plot(running_average, label="Moyenne empirique")
    plot.plot(x, y, 'k-', label="Valeur attendue théorique (3.5)")
    plot.legend()
    plot.show()

# Exécuter avec différents nombres de lancers
estimate_expected_value(10)
estimate_expected_value(100)
estimate_expected_value(1000)
estimate_expected_value(10000)
```

### Explication :
- **num_throws** : représente le nombre de lancers de dés simulés.
- **running_average** : garde une trace de la moyenne des résultats après chaque lancer.
- Le graphe montre la convergence vers la valeur théorique de **3.5** au fur et à mesure que le nombre de lancers augmente.

## 6. Q-Learning : Une Extension de TD-Learning

Le **Q-Learning** est une version plus avancée du TD-Learning où l'on apprend non seulement la valeur des états, mais aussi la valeur des **paires état-action** $$ (S, A) $$. Cela permet de choisir les actions optimales dans chaque état.

L'équation de mise à jour du **Q-Learning** est :

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left[ R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right]
$$

Cela signifie que l'agent apprend quelle est la meilleure action à prendre dans un état donné, en tenant compte de la récompense immédiate et des actions futures.

## 7. Conclusion

Le **TD-Learning** est une méthode puissante pour l'apprentissage en temps réel dans des environnements dynamiques. Contrairement à d'autres méthodes, il permet d'ajuster les valeurs au fur et à mesure, sans avoir besoin d'attendre la fin de l'épisode. **Q-Learning** en est une version améliorée qui permet d'apprendre directement des actions optimales.
