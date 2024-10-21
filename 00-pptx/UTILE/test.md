
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
