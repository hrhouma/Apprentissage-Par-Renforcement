-------------------------------------------------------
# 1 - *propriété de Markov*
-------------------------------------------------------

- Dans un processus de décision markovien (MDP), la **propriété de Markov** est essentielle.
- Elle stipule que la probabilité de transition vers un nouvel état dépend uniquement de l'état actuel et de l'action entreprise, et non des états précédents. Cela simplifie l'analyse et la modélisation des systèmes dynamiques.
- Pour vilgariser, on peut dire que la propriété de Markov stipule que le futur état dépend uniquement de l'état actuel et de l'action choisie, et non des états ou actions précédents. Cela simplifie le processus de modélisation en ne nécessitant que l'état courant pour prendre des décisions.

-------------------------------------------------------
# 2 - **Équation de probabilité des états**
-------------------------------------------------------

![image](https://github.com/user-attachments/assets/b62ec8f2-fe25-48bb-9db1-1e76074d5b7f)


L'équation de probabilité pour la transition entre les états dans un MDP est généralement formulée comme suit :

$$
P(s' | s, a)
$$

où :
- $$s$$ est l'état actuel.
- $$a$$ est l'action entreprise.
- $$s'$$ est le nouvel état après la transition.
- $$P(s' | s, a)$$ est la probabilité de passer à l'état $$s'$$ en prenant l'action $$a$$ depuis l'état $$s$$.

Cette équation illustre comment les transitions d'états sont déterminées dans un environnement stochastique, en se basant uniquement sur l'état actuel et l'action choisie, conformément à la propriété de Markov.
