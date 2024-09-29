# ε-greedy en Apprentissage par Renforcement

L'approche **ε-greedy** est une stratégie utilisée en apprentissage par renforcement pour gérer le compromis entre **exploration** et **exploitation**.

## Principe

L'agent choisit entre :

- **Exploration** : Action aléatoire avec probabilité ε
- **Exploitation** : Action maximisant la récompense attendue avec probabilité 1-ε

L'idée est d'introduire une composante de hasard contrôlée dans la prise de décision. Au début, l'agent explore davantage (ε grand), puis ε diminue pour favoriser l'exploitation des actions efficaces.

## Équation

$$
\text{Action choisie} =
\begin{cases} 
\text{action aléatoire} & \text{avec probabilité } \epsilon \\
\arg \max_{a \in A} Q(s,a) & \text{avec probabilité } 1 - \epsilon
\end{cases}
$$

Où :
- $$a \in A$$ : Ensemble des actions possibles
- $$Q(s, a)$$ : Fonction de valeur d'action, estimant la récompense pour l'action $$a$$ dans l'état $$s$$
- $$\arg \max_{a \in A} Q(s,a)$$ : Action maximisant $$Q(s,a)$$

## Stratégie adaptative de ε

ε peut être fixe ou décroissant. Une stratégie adaptative courante est :

$$\epsilon_t = \frac{\epsilon_0}{1 + kt}$$

- $$\epsilon_0$$ : Valeur initiale de ε
- $$k$$ : Facteur de déclin
- $$t$$ : Étape de temps

## Avantages

- Simple à implémenter
- Bon équilibre exploration/exploitation
- Applicable à de nombreux problèmes

## Inconvénients

- Exploration aléatoire
- Risque de décisions sous-optimales même en fin d'apprentissage

## Conclusion

ε-greedy offre une approche probabiliste efficace pour gérer le dilemme exploration/exploitation en apprentissage par renforcement.
