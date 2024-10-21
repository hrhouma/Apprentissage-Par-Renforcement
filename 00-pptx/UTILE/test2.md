-----------
# Partie 1 : Questions à choix multiples (5 points chacune)
-----------

### 1. Qu'est-ce qu'un Processus de Décision Markovien (MDP) ?
   
   a) Un algorithme d'apprentissage supervisé
   
   b) Un modèle mathématique pour la prise de décision séquentielle
   
   c) Une technique de clustering
   
   d) Un type de réseau neuronal

### 2. La propriété de Markov stipule que :
   
   a) L'état futur dépend uniquement de l'état présent
   
   b) L'état futur dépend de tous les états passés
   
   c) L'état futur est complètement aléatoire
   
   d) L'état futur dépend uniquement de l'action présente
   

### 3. Quelle est la différence entre l'exploration et l'exploitation en apprentissage par renforcement ?
   
   a) L'exploration cherche de nouvelles actions, l'exploitation utilise les meilleures actions connues
   
   b) L'exploration est utilisée en apprentissage supervisé, l'exploitation en apprentissage non supervisé
   
   c) L'exploration est déterministe, l'exploitation est stochastique
   
   d) Il n'y a pas de différence, ce sont des synonymes
   

### 4. Qu'est-ce que le "discounting" en apprentissage par renforcement ?
   
   a) Une technique pour réduire la taille du modèle
   
   b) Un moyen de donner moins d'importance aux récompenses futures
   
   c) Une méthode pour accélérer l'apprentissage
   
   d) Un type de fonction d'activation

### 5. Quelle est la différence entre la valeur d'état et la valeur Q-state ?
    
   a) La valeur d'état considère toutes les actions possibles, la valeur Q-state une action spécifique
   
   b) La valeur d'état est toujours plus grande que la valeur Q-state
   
   c) La valeur d'état est utilisée pour les environnements déterministes, la valeur Q-state pour les stochastiques
   
   d) Il n'y a pas de différence, ce sont des synonymes


-----------
# Partie 2 : Questions à réponse courte (10 points chacune)
-----------

### 6. Expliquez la différence entre un environnement dynamique et un environnement statique en apprentissage par renforcement.
   

### 7. Décrivez l'approche ε-greedy en apprentissage par renforcement. Pourquoi est-elle utilisée ?
   

### 8. Qu'est-ce qu'un état absorbant dans un MDP ? Donnez un exemple.
    

### 9. Expliquez la différence entre une stratégie (policy) et une stratégie optimale en apprentissage par renforcement.
    

### 10. Décrivez brièvement l'algorithme d'itération de valeur (value iteration). Quel est son objectif principal ?
    

-----------
# Partie 3 : Problème pratique 
-----------

###  11. Considérez le MDP suivant représentant un petit labyrinthe :

```
   +---+---+---+
   | S | 0 | 0 |
   +---+---+---+
   |-1 |-1 | 0 |
   +---+---+---+
   |-1 |-1 | G |
   +---+---+---+
```

S est l'état initial, G est l'état but (récompense +10), les cases marquées -1 sont des pièges (récompense -1), et les 0 sont des cases neutres. L'agent peut se déplacer dans les 4 directions (haut, bas, gauche, droite) et reste sur place s'il tente de sortir de la grille. Le facteur de discount γ est de 0.9.

###   a) Écrivez la fonction de récompense r(s,a,s') pour ce MDP. 

###   b) Calculez la valeur optimale V*(s) pour l'état initial S en utilisant l'équation de Bellman. Montrez vos calculs. 

###   c) Quelle est la stratégie optimale pour ce MDP ? Justifiez votre réponse. 

###   d) Comment ce problème changerait-il si l'environnement était stochastique, avec une probabilité de 0.2 que l'agent glisse et se déplace dans une direction aléatoire différente de celle choisie ? 












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


