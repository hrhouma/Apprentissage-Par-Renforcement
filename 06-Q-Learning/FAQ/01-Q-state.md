# Q-state ?

En **reinforcement learning (RL)**, un **Q-state** fait référence à une paire **(état, action)**, où l'on associe un état particulier d'un environnement et une action possible à partir de cet état. Cela fait partie de l'approche **Q-learning**, qui vise à apprendre une **fonction de valeur d'action**, appelée fonction **Q**.

### Concept de base :
Dans un environnement de RL, un agent interagit avec l'environnement en choisissant des actions dans des états spécifiques. Après chaque action, l'agent reçoit une récompense et l'environnement évolue vers un nouvel état.

La fonction **Q(s, a)** représente la valeur attendue (ou la somme des récompenses futures) lorsque l'agent est dans un état **s** et choisit une action **a**, puis suit la meilleure stratégie par la suite (ce qui est appelé la "politique optimale").

### Détails :

- **État (s)** : Représente une configuration spécifique de l'environnement, ce qui peut inclure des informations comme la position de l'agent, l'heure actuelle, les ressources disponibles, etc.
- **Action (a)** : L'action que l'agent peut prendre dans cet état. L'ensemble des actions dépend de l'état et de l'environnement (par exemple : se déplacer vers la gauche ou vers la droite, sauter, attendre, etc.).

### Le rôle du Q-state :
- La fonction Q évalue la **qualité d'une action** dans un état donné. Plus précisément, elle donne une estimation de la récompense totale que l'agent peut espérer obtenir en prenant cette action dans cet état et en suivant la meilleure politique ensuite.
  
L'objectif du Q-learning est de **mettre à jour** les valeurs de la fonction **Q(s, a)** pour chaque paire d'état et d'action en fonction des nouvelles informations acquises après chaque interaction avec l'environnement.

### Formule de mise à jour de Q-learning :
L'algorithme de Q-learning met à jour la valeur de **Q(s, a)** à chaque pas de temps en utilisant la formule suivante :

$$Q(s, a) \leftarrow Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right]$$

- **α** : Taux d'apprentissage (learning rate) qui contrôle dans quelle mesure les nouvelles informations écrasent les anciennes.
- **r** : Récompense immédiate obtenue après avoir pris l'action **a** dans l'état **s**.
- **γ** : Facteur d'actualisation (discount factor), qui détermine l'importance des récompenses futures.
- **max_{a'} Q(s', a')** : La valeur maximale estimée pour l'état suivant **s'** en prenant la meilleure action possible à partir de **s'**.

### Exemple :
Imagine un robot qui essaie d'apprendre à naviguer dans un labyrinthe. L'état **s** pourrait être la position actuelle du robot dans le labyrinthe, et l'action **a** pourrait être "avancer", "tourner à gauche", ou "tourner à droite". La fonction **Q(s, a)** indique la qualité de l'action dans cet état, c'est-à-dire combien de récompense le robot peut s'attendre à obtenir en choisissant cette action.

Ainsi, un **Q-state** est la paire **(état, action)** qui est associée à une valeur de qualité **Q**, que l'algorithme de Q-learning essaie d'estimer et d'améliorer au fil du temps.

-----------------------------------
# Exercice à réaliser en groupe
-----------------------------------

**"Faites une recherche sur l'évolution de l'estimation de la fonction Q dans le Q-learning. Comment l'agent met-il à jour ses valeurs Q au fil du temps ? En parallèle, explorez comment l'agent fait des choix entre l'exploration de nouvelles actions et l'exploitation des actions apprises. Quels sont les mécanismes utilisés pour équilibrer ces deux stratégies ?"**

Cela les invite à explorer les deux concepts en profondeur.

------------------
# Annexe 1 (correction) : Parlons alors de deux aspects essentiels dans le **Q-learning** : 
------------------

1. **L'évolution de l'estimation des valeurs de Q** (mise à jour de la fonction Q).
2. **L'équilibre entre exploration et exploitation**.

### 1. L'évolution de l'estimation des valeurs de Q

Dans le **Q-learning**, l'algorithme essaie d'améliorer l'estimation de la fonction **Q(s, a)** au fur et à mesure que l'agent interagit avec l'environnement. Cette mise à jour repose sur une idée fondamentale : à chaque fois que l'agent prend une action, il reçoit une récompense et observe le nouvel état, ce qui permet d'améliorer son estimation de la valeur future.

La fonction **Q(s, a)** est mise à jour selon la formule suivante, que nous avons déjà vue :

$$Q(s, a) \leftarrow Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right]$$

Voici comment cela fonctionne en pratique :

- **Initialisation** : Au début, les valeurs **Q(s, a)** sont souvent initialisées à zéro (ou une petite valeur aléatoire).
  
- **Prise de décision et mise à jour** :
  1. L'agent choisit une action **a** dans un état **s**.
  2. Il exécute cette action, reçoit une récompense **r** et atteint un nouvel état **s'**.
  3. Il met à jour **Q(s, a)** en utilisant la récompense **r**, mais aussi en tenant compte de la valeur de la meilleure action possible à partir du nouvel état **s'** (le terme **max_{a'} Q(s', a')**).

Avec le temps, ces valeurs **Q(s, a)** se raffinent et deviennent de meilleures approximations des récompenses futures attendues. L'algorithme de Q-learning converge vers une politique optimale, où l'agent prend les meilleures actions dans chaque état pour maximiser ses récompenses.

Cependant, pour que cela fonctionne bien, l'agent doit explorer suffisamment l'environnement. Cela nous amène au deuxième point clé : **exploration vs exploitation**.

### 2. L'équilibre entre exploration et exploitation

Lors de la prise de décision, un agent dans un environnement de **reinforcement learning** doit choisir entre :

- **Exploitation** : Choisir l'action qui a la plus grande valeur estimée actuellement (selon la fonction **Q(s, a)**).
- **Exploration** : Essayer de nouvelles actions pour découvrir de meilleures solutions à long terme.

Ce dilemme est crucial dans l'apprentissage. Si l'agent exploite toujours ce qu'il connaît déjà, il risque de passer à côté d'actions plus profitables à long terme. En revanche, s'il explore trop souvent, il n'exploitera pas assez les bonnes actions qu'il a déjà apprises.

### Stratégie d'exploration : **ε-greedy**

L'approche la plus courante pour gérer cet équilibre est la stratégie **ε-greedy**. Voici comment elle fonctionne :

- Avec une probabilité **ε**, l'agent **explore** en choisissant une action au hasard, indépendamment de la fonction **Q(s, a)**.
- Avec une probabilité **1 - ε**, l'agent **exploite** en choisissant l'action avec la plus grande valeur actuelle de **Q(s, a)** (c'est-à-dire celle qui est jugée la meilleure selon ses estimations actuelles).

Au fil du temps, **ε** peut être réduit progressivement, de sorte que l'agent commence par explorer beaucoup, puis se concentre de plus en plus sur l'exploitation à mesure qu'il acquiert de l'expérience.

### Exemple pratique :
Prenons l'exemple du robot dans un labyrinthe :

- Au début, les valeurs **Q(s, a)** sont initialisées à zéro. Le robot n'a aucune idée des bonnes actions à prendre dans les différents états (positions dans le labyrinthe).
- Il commence à explorer le labyrinthe en prenant des actions aléatoires (forte probabilité d'exploration avec un **ε** élevé).
- Chaque fois qu'il trouve une sortie (récompense), il met à jour sa fonction **Q(s, a)** pour indiquer que certaines actions à partir de certaines positions sont plus rentables.
- Avec le temps, il diminue **ε**, exploitant de plus en plus les actions qu'il a apprises, jusqu'à ce qu'il connaisse le chemin optimal vers la sortie.

### Conclusion :
L'agent doit équilibrer exploration et exploitation pour apprendre efficacement. Il doit explorer pour découvrir de nouvelles stratégies potentielles tout en exploitant les stratégies déjà optimales qu'il a découvertes. Le paramètre **ε** dans la stratégie **ε-greedy** aide à contrôler cet équilibre, et il peut être ajusté dynamiquement pour s'adapter à différentes phases d'apprentissage.


------------------
# Annexe 2 : Exercice à réaliser en groupe
------------------

**"Comment peut-on ajuster la valeur de ε dans la stratégie ε-greedy pour équilibrer efficacement exploration et exploitation au fil du temps ? Explorez également d'autres stratégies d'exploration, telles que Softmax et Upper Confidence Bound (UCB), et comparez leurs avantages et inconvénients."**


