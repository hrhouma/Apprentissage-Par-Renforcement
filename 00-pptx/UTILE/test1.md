# Examen : Mise à jour de la Q-table

## Contexte
Dans cet exercice, vous allez utiliser les concepts de **Q-learning** pour mettre à jour une Q-table en fonction des décisions prises par un agent évoluant dans un environnement de grille (Grid World). L'agent devra apprendre une **politique cible** en explorant cet environnement.

## Objectifs
1. Analyser une **Q-table**.
2. Comprendre l'environnement **Grid World** et les déplacements possibles.
3. Mettre à jour une valeur de la Q-table.

---

# Partie 1 : Mise à jour de la Q-table après un déplacement initial

### Étape 1 : Q-table initiale

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

### Étape 2 : Environnement Grid World

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

### Étape 3 : Déplacement de l'agent

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

### Étape 4 : Prise de décision

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

### Étape 5 : Action choisie

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

### Étape 6 : Mise à jour de la Q-table

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

### Instructions :
- Calculez la nouvelle valeur de **Q(S1, droite)** en appliquant la mise à jour de la Q-table.
- Indiquez les étapes de votre raisonnement, et montrez comment vous avez utilisé les récompenses et le taux d'apprentissage pour ajuster cette valeur.

---

# Partie 2 : Déplacement supplémentaire et mise à jour de la Q-table

### Étape 1 : Déplacement supplémentaire de l'agent

Après avoir mis à jour la valeur de **Q(S1, droite)**, l'agent continue à se déplacer. Cette fois-ci, depuis l'état **S2**, l'agent choisit de se déplacer **vers la droite**, atteignant ainsi l'état **S3**.

```
+----+----+----+----+
| -1 | 🤖 S2 → | S3 -1 |
+----+----+----+----+
| -1 | -1 | -1 | -1 |
+----+----+----+----+
| -1 | -10 | +10| -1 |
+----+----+----+----+
```

### Étape 2 : Mise à jour de la Q-table pour S2

**Question :** Mettez à jour la valeur de **Q(S2, droite)** en appliquant à nouveau vos connaissances du Q-learning. Référez-vous à vos notes de cours pour effectuer cette mise à jour.

- **Alpha** (taux d'apprentissage) : 0.1
- **Récompenses** : Toutes les récompenses sont de **-1**, sauf pour les états terminaux où les récompenses sont **-10** et **+10**.
- **Bruit** : Aucun bruit.

Voici la Q-table à compléter :

```
+----+--------+--------+------+-------+
| Q  | gauche | droite |  haut | bas  |
+----+--------+--------+------+-------+
| S1 |  -0.5  |   ?    |  2.1 |  1.3  |
+----+--------+--------+------+-------+
| S2 |   0.5  |   ?    | -0.5 |  1.5  |
+----+--------+--------+------+-------+
| S6 |  -1.2  |   1.2  |  0.7 |  1.7  |
+----+--------+--------+------+-------+
```

---

### Instructions :
- Calculez la nouvelle valeur de **Q(S2, droite)** en appliquant la mise à jour de la Q-table.
- Expliquez les étapes de votre raisonnement et montrez comment vous avez utilisé les récompenses et le taux d'apprentissage pour ajuster cette valeur.

---

# Partie 3 : Réévaluer dans un environnement stochastique

Dans cette partie, vous allez réévaluer les résultats des **Parties 1 et 2**, mais cette fois-ci dans un **environnement stochastique**.

### Question

Comment ce problème changerait-il si l'environnement était **stochastique**, avec une probabilité de **0.2** que l'agent glisse et se déplace dans une direction aléatoire différente de celle choisie ?

---

### Instructions :
- Reprenez les **Parties 1 et 2** en tenant compte du fait que l'agent peut glisser dans une direction aléatoire avec une probabilité de 0.2.
- Calculez à nouveau les mises à jour des valeurs de **Q(S1, droite)** et **Q(S2, droite)** en prenant en compte cet environnement stochastique.
- Expliquez comment cela affecte votre raisonnement et les valeurs mises à jour dans la Q-table.

