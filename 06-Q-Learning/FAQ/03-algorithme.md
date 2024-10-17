### 1. Bellman Equation

```latex
Q(S_1, right)_observed = R(S_2) + γ max_a Q(S_2, a)
```

### 2. TD Error

```latex
TD Error = Q(S_1, right)_observed - Q(S_1, right)_expected
```

### 3. Update Rule

$$
Q(S_1, \text{right}) = Q(S_1, \text{right}) + \alpha \times \text{TD Error}
$$

-------------------------------
# Annexe - explications
-------------------------------


### 1. Équation de Bellman

L'équation de Bellman est utilisée dans le cadre des algorithmes de contrôle et de décision, notamment dans le **Q-Learning**. Elle exprime la relation entre la valeur actuelle de la fonction Q et la récompense attendue en fonction de l'état futur S_2, pondérée par un facteur d'actualisation γ.

```latex
Q(S_1, right)_observed = R(S_2) + γ max_a Q(S_2, a)
```

- S_1 : état initial.
- S_2 : état suivant après avoir pris l'action "right".
- R(S_2) : récompense associée à l'état S_2.
- γ : facteur d'actualisation (discount factor).
- max_a Q(S_2, a) : meilleure valeur Q possible pour l'état S_2 en prenant la meilleure action a.

### 2. Erreur de différence temporelle (TD Error)

L'erreur de différence temporelle (TD Error) est utilisée pour mesurer la différence entre la valeur Q observée après une mise à jour et la valeur Q attendue avant l'observation.

```latex
TD Error = Q(S_1, right)_observed - Q(S_1, right)_expected
```



### 3. Règle de mise à jour (Update Rule)

La règle de mise à jour spécifie comment la valeur Q d'un état-action est ajustée en fonction de l'erreur de différence temporelle (TD Error). Le terme α représente le taux d'apprentissage (learning rate), qui contrôle à quel point la nouvelle information affecte la mise à jour de la valeur Q.

$$
Q(S_1, \text{right}) = Q(S_1, \text{right}) + \alpha \cdot \text{TD Error}
$$

- α : taux d'apprentissage (learning rate), qui détermine dans quelle mesure la nouvelle information affecte l'ajustement de la valeur Q.

Cette explication unifie vos demandes en intégrant chaque équation et sa description, formatée pour un fichier README.md.
