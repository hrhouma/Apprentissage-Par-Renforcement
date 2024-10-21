
# 1 
- On considère la Q-table suivante :

```
+----+--------+--------+------+-------+
| Q  | gauche | droite |  haut | bas  |
+----+--------+--------+------+-------+
| S1 |  -0.5  |   1    |  2.1 |  1.3  |
+----+--------+--------+------+-------+
| S2 |   0.5  |  0.75  | -0.5 |  1.5  |
+----+--------+--------+------+-------+
| S6 |  -1.2  |   1.2  |  0.7 |  1.7  |
+----+--------+--------+------+-------+
```

# 2

- On considère l'environnement suivant **Grid World** :
```
+----+----+----+
| -1 | -1 | -1 |
+----+----+----+
| -1 | -1 | -1 |
+----+----+----+
| -1 | -10| +10|
+----+----+----+
```

# 3
- Nous voulons que l'agent apprenne la politique cible.
- Dans chaque image, le robot (🤖) représente l'agent, les flèches indiquent les mouvements possibles ou choisis, 


```
+------+----+----+----+
| 🤖  | -1 | -1 | -1 |
+------+----+----+----+
| -1   | -1 | -1 | -1 |
+------+----+----+----+
| -1   | -10| +10| -1 |
+------+----+----+----+
```

- Le robot est représenté par le symbole 🤖 en haut à gauche. 
- Chaque cellule de la grille correspond à une récompense ou une pénalité, avec -10 et +10 comme objectifs importants.




# 4

### Le rebot est initialement dans l'état S1

```
+------+----+----+----+
| 🤖 S1 | -1 | -1 | -1 |
+------+----+----+----+
| -1   | -1 | -1 | -1 |
+------+----+----+----+
| -1   | -10| +10| -1 |
+------+----+----+----+

L'agent prend une décision basée sur une politique de comportement.
```

# 5
###  L'agent peut se déplacer vers la droite ou vers le bas

```
+---------+----+----+----+
| 🤖 S1 → | -1 | -1 | -1 |
+---↓-----+----+----+----+
|   -1    | -1 | -1 | -1 |
+---------+----+----+----+
|   -1    | -10| +10| -1 |
+---------+----+----+----+
```


# 6

### L'agent prend la décision de se déplacer vers la droite.

```
+------+----+----+----+
|🤖 S1|→ -1 (S2) | -1 | -1 |
+------+----+----+----+
| -1   | -1 | -1 | -1 |
+------+----+----+----+
| -1   | -10| +10| -1 |
+------+----+----+----+


```


#7 Question

EN  utilisant les équations de bellman comme vu en classe , mettre à jour la Q-table pour le Q(s1, right) qui est initalement à 1

```
+----+--------+--------+------+-------+
| Q  | gauche | droite |  haut | bas  |
+----+--------+--------+------+-------+
| S1 |  -0.5  |   ?    |  2.1 |  1.3  |
+----+--------+--------+------+-------+
| S2 |   0.5  |  0.75  | -0.5 |  1.5  |
+----+--------+--------+------+-------+
| S6 |  -1.2  |   1.2  |  0.7 |  1.7  |
+----+--------+--------+------+-------+
```







-----------


## Partie 3 : Problème pratique (30 points)

11. Considérez le MDP suivant représentant un petit labyrinthe :

```
   +---+---+---+
   | S | 0 | 0 |
   +---+---+---+
   |-1 |-1 | 0 |
   +---+---+---+
   |-1 |-1 | G |
   +---+---+---+
```

S est l'état initial, G est l'état but (récompense +10), les cases marquées -1 sont des pièges (récompense -1), et les 0 sont des cases neutres. L'agent peut se déplacer dans les 4 directions (haut, bas, gauche, droite) et reste sur place s'il tente de sortir de la grille. Le facteur de discount γ est de 0.9. Les transitions sont déterministes.

a) Écrivez la fonction de récompense r(s,a,s') pour ce MDP. Précisez clairement les récompenses pour chaque type de transition, y compris lorsque l'agent reste dans la grille ou tente d'en sortir. (5 points)

b) Calculez la valeur optimale V*(s) pour l'état initial S en utilisant l'équation de Bellman. Montrez vos calculs en détail, en considérant uniquement les déplacements vers la droite et vers le bas à partir de S. Utilisez les valeurs des états voisins immédiats pour votre calcul. (10 points)

c) Quelle est la stratégie optimale pour ce MDP ? Justifiez votre réponse en expliquant votre raisonnement et en calculant V*(s) pour les autres états pertinents du chemin optimal. (10 points)

d) Comment ce problème changerait-il si l'environnement devenait stochastique, avec une probabilité de 0.8 que l'agent se déplace dans la direction choisie, et une probabilité de 0.2 qu'il "glisse" et se déplace dans l'une des trois autres directions aléatoirement (chacune avec une probabilité de 0.2/3) ? Discutez des implications sur la stratégie optimale et la difficulté du problème. (5 points)



