

On considère la Q-table suivante :

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



On considère l'environnement suivant **Grid World** :
```
+----+----+----+
| -1 | -1 | -1 |
+----+----+----+
| -1 | -1 | -1 |
+----+----+----+
| -1 | -10| +10|
+----+----+----+
```


Nous voulons que l'agent apprenne la politique cible.


```
+------+----+----+----+
| 🤖    | -1 | -1 | -1 |
+------+----+----+----+
| -1   | -1 | -1 | -1 |
+------+----+----+----+
| -1   | -10| +10| -1 |
+------+----+----+----+
```

- Le robot est représenté par le symbole 🤖 en haut à gauche. 
- Chaque cellule de la grille correspond à une récompense ou une pénalité, avec -10 et +10 comme objectifs importants.
