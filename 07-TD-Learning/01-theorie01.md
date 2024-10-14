## Introduction au TD-Learning

Le **TD-Learning** est une méthode d'apprentissage par renforcement qui combine des aspects des méthodes de Monte Carlo et de la programmation dynamique. Il permet à un agent d'apprendre en mettant à jour les estimations de la valeur des états ou des paires état-action à chaque étape, sans attendre la fin d'un épisode.

## Concepts Clés

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

Citations:
[1] https://pplx-res.cloudinary.com/image/upload/v1728874976/user_uploads/szareivvb/image.jpg

[2] https://fr.wikipedia.org/wiki/Temporal_difference_learning

[3] https://www.td.com/ca/fr/investir/placement-en-direct/education

[4] https://www.lancaster.ac.uk/stor-i-student-sites/jordan-j-hood/2021/04/12/reinforcement-learning-temporal-difference-td-learning/

[5] https://towardsdatascience.com/temporal-difference-learning-and-the-importance-of-exploration-an-illustrated-guide-5f9c3371413a?gi=de80dad61959

[6] https://www.csd.uwo.ca/~xling/cs346a/extra/tdgammon.pdf
