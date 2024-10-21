# Exercice : Mise à jour de la Q-table

### Contexte
Dans cet exercice, vous allez utiliser les concepts de **Q-learning** pour mettre à jour une Q-table en fonction des décisions prises par un agent évoluant dans un environnement de grille (Grid World). L'agent devra apprendre une **politique cible** en explorant cet environnement.

### Objectifs
1. Analyser une **Q-table**.
2. Comprendre l'environnement **Grid World** et les déplacements possibles.
3. Mettre à jour une valeur de la Q-table.

---

### #1 Q-table initiale

Voici la **Q-table** initiale, qui contient les valeurs des actions possibles dans différents états. Chaque ligne représente un état, et chaque colonne représente une action (gauche, droite, haut, bas).

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

---

### #2 Environnement Grid World

L'environnement dans lequel l'agent évolue est une grille (Grid World). Chaque cellule de la grille contient une récompense. Les états terminaux ont des récompenses spéciales, comme indiqué ci-dessous :

```
+----+----+----+
| -1 | -1 | -1 |
+----+----+----+
| -1 | -1 | -1 |
+----+----+----+
| -1 | -10| +10|
+----+----+----+
```

- **Récompenses** : Toutes les actions entraînent une récompense de **-1**, sauf lorsqu'un état terminal est atteint. Les récompenses dans les états terminaux sont **-10** et **+10** respectivement.

---

### #3 Déplacement de l'agent

L'agent, représenté par un robot **(🤖)**, commence dans l'état **S1**, en haut à gauche de la grille :

```
+------+----+----+
| 🤖 S1 | -1 | -1 |
+------+----+----+
| -1   | -1 | -1 |
+------+----+----+
| -1   | -10| +10|
+------+----+----+
```

---

### #4 Prise de décision

L'agent prend une décision basée sur une **politique de comportement**. Depuis l'état **S1**, l'agent peut se déplacer **vers la droite** ou **vers le bas** :

```
+---------+----+----+----+
| 🤖 S1 → | -1 | -1 | -1 |
+---↓-----+----+----+----+
|   -1    | -1 | -1 | -1 |
+---------+----+----+----+
|   -1    | -10| +10| -1 |
+---------+----+----+----+
```

---

### #5 Action choisie

L'agent choisit de se déplacer **vers la droite**, atteignant ainsi l'état **S2** :

```
+------+----+----+
| 🤖 S1|→ -1 (S2) | -1 | 
+------+----+----+
| -1   | -1 | -1 | 
+------+----+----+
| -1   | -10| +10| 
+------+----+----+
```

---

### #6 Mise à jour de la Q-table

**Question :** En utilisant vos connaissances du Q-learning (référez-vous à vos notes de cours), mettez à jour la valeur de **Q(S1, droite)**, initialement à **1**, dans la Q-table ci-dessous.

- **Alpha** (taux d'apprentissage) : 0.1
- **Récompenses** : Toutes les récompenses sont de **-1**, sauf pour les états terminaux où les récompenses sont **-10** et **+10**.
- **Bruit** : Aucun bruit.

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

---

**Instructions :**
- Calculez la nouvelle valeur de **Q(S1, droite)** en appliquant la mise à jour de la Q-table.
- Indiquez les étapes de votre raisonnement, et montrez comment vous avez utilisé les récompenses et le taux d'apprentissage pour ajuster cette valeur.

