
----------------
# Partie 1
----------------

Le Q-learning est une méthode d'apprentissage par renforcement très populaire, qui se concentre sur l'optimisation d'une politique pour maximiser une récompense. Tout au long de cette méthode, nous avons abordé les trois paradigmes principaux de l'apprentissage automatique : l'apprentissage supervisé, l'apprentissage non supervisé et l'apprentissage par renforcement.

L'apprentissage supervisé implique un modèle initialement non performant, des données et une étiquette, et il s'agit de reconnaître les motifs entre ces deux éléments. L'apprentissage non supervisé, quant à lui, cherche à identifier des motifs dans les données sans étiquettes, et est couramment utilisé pour des tâches telles que le regroupement ou la réduction de dimensions.

L'apprentissage par renforcement, qui nous intéresse ici, vise à apprendre des actions optimales à partir d'une situation pour maximiser une récompense. Il existe deux types de méthodes dans ce domaine : celles basées sur la valeur et celles basées sur la politique. Les méthodes basées sur la valeur se concentrent sur l'élaboration d'une fonction de valeur, tandis que les méthodes basées sur la politique tentent de déterminer directement la politique optimale, celle qui maximise la récompense totale.

Le Q-learning est une méthode basée sur la valeur, qui cherche à apprendre une fonction de valeur d'état-action, également connue sous le nom de valeur Q. Cette fonction mesure à quel point il est avantageux d'être dans un état donné et d'y entreprendre une action particulière. L'objectif est d'optimiser ces valeurs Q pour maximiser la récompense totale.

Pour illustrer le fonctionnement du Q-learning, imaginez un environnement en grille où un agent se déplace et reçoit des récompenses en fonction de sa position. Il existe un état de départ, des actions possibles et des états résultants avec des récompenses associées. L'agent doit apprendre à naviguer dans cet environnement pour atteindre une récompense maximale en s'appuyant sur une table de valeurs Q. Ces valeurs évoluent au fil du temps grâce à une série d'épisodes, pendant lesquels l'agent explore l'environnement de manière aléatoire, puis affine ses choix d'actions en fonction des meilleures valeurs Q apprises.

La formule clé dans ce processus est l'équation de Bellman, qui décrit comment les valeurs Q sont mises à jour en fonction des récompenses actuelles et des valeurs futures possibles. Un facteur de réduction, appelé gamma, est utilisé pour pondérer l'importance des récompenses futures par rapport à celles immédiates. À chaque étape, l'agent met à jour la table de valeurs Q à l'aide d'une règle d'apprentissage, qui ajuste les valeurs en fonction de l'erreur de différence temporelle (temporal difference), c'est-à-dire la différence entre les valeurs Q attendues et observées.

L'algorithme répète ces mises à jour sur plusieurs épisodes, jusqu'à ce que les valeurs Q se stabilisent et que l'agent ait appris une politique optimale. Cette politique, une fois apprise, permet à l'agent de prendre des décisions qui maximisent la récompense. Une distinction importante à faire est que la politique d'exploration initiale, souvent aléatoire, est utilisée pour apprendre, tandis que la politique optimale, appelée politique cible, est celle qui guide l'agent une fois que les valeurs Q sont stables.

Le Q-learning est un algorithme hors-politiques (off-policy), ce qui signifie que la politique d'exploration peut être distincte de la politique cible. Cela permet à l'agent de collecter des informations tout en apprenant à optimiser sa politique.

Avec une compréhension de base du Q-learning, vous pouvez maintenant explorer davantage comment il fonctionne et comment il est appliqué dans des environnements variés pour résoudre des problèmes complexes d'apprentissage par renforcement.






----------------
# Partie 2
----------------


Pour approfondir le fonctionnement du Q-learning, imaginons un environnement de grille simple composé de neuf cases, où certaines cases offrent des récompenses spécifiques. Par exemple, une case offre une récompense de +10, une autre contient un poison avec une pénalité de -10, et les autres cases attribuent une petite pénalité de -1 pour chaque déplacement. L'objectif de l'agent est d'atteindre la case offrant la récompense maximale de +10 tout en évitant le poison et les autres cases moins intéressantes.

Pour apprendre à naviguer efficacement dans cet environnement, l'agent utilise un tableau de valeurs Q, où chaque état de la grille (une case) est associé à des actions possibles (comme se déplacer vers le haut, vers le bas, à gauche ou à droite). Ce tableau commence avec des valeurs Q arbitraires, car au départ, l'agent ne connaît pas les récompenses associées à ses actions.

Lorsque l'agent commence à explorer l'environnement, il prend des actions basées sur une politique d'exploration, qui est souvent aléatoire au début. Par exemple, si l'agent se trouve dans la première case (état S1), il peut décider de se déplacer à droite ou vers le bas. Disons que l'agent choisit de se déplacer à droite et se retrouve dans un nouvel état (état S2). À ce moment-là, il reçoit une récompense associée à cet état, dans ce cas, une pénalité de -1.

À ce stade, l'agent utilise l'équation de Bellman pour mettre à jour la valeur Q associée à l'état S1 et à l'action de se déplacer à droite. Cette équation prend en compte la récompense immédiate (ici, -1) et la meilleure valeur Q future possible à partir de l'état S2. Un facteur de réduction (gamma) est également appliqué pour ajuster l'importance des récompenses futures.

Si, par exemple, la meilleure valeur future à partir de l'état S2 est de 1,5 (obtenue en se déplaçant vers le bas), l'agent calcule la nouvelle valeur Q pour l'état S1 et l'action de se déplacer à droite en utilisant la formule :

$$Q(S1, \text{droite}) = \text{récompense de S2} + \gamma \times \text{meilleure valeur future de S2}$$

Avec une récompense de -1 et un gamma de 0,1, cela donnerait :

$$Q(S1, \text{droite}) = -1 + 0,1 \times 1,5 = -0,85$$

Si la valeur initiale de Q pour cette action était de 1, l'agent constate une différence entre la valeur attendue (1) et la valeur observée (-0,85). Cette différence est appelée erreur de différence temporelle (temporal difference error). L'agent ajuste alors la valeur Q à l'aide d'un taux d'apprentissage (alpha) pour réduire cet écart. Si alpha est fixé à 0,1, la nouvelle valeur Q serait mise à jour selon la formule suivante :

$$Q_{\text{nouveau}} = Q_{\text{ancien}} + \alpha \times (\text{erreur})$$

En substituant les valeurs :

$$Q(S1, \text{droite}) = 1 + 0,1 \times (-1,85) = 0,815$$

Le processus se répète à chaque action et pour chaque état que l'agent explore. Petit à petit, les valeurs Q dans le tableau sont mises à jour, et l'agent apprend les actions qui mènent aux plus grandes récompenses. Au fur et à mesure que l'agent complète des épisodes, c'est-à-dire qu'il navigue de l'état initial jusqu'à un état final (soit la case de récompense +10 ou la case de poison -10), les valeurs Q deviennent plus stables.

Une fois que les valeurs Q ont convergé vers des valeurs optimales, l'agent peut utiliser ce tableau pour prendre des décisions éclairées. Par exemple, dans un état donné, l'agent sélectionnera l'action avec la valeur Q la plus élevée, ce qui lui permettra de maximiser ses chances de recevoir une récompense élevée.

Il est important de noter que la politique d'exploration initiale, souvent basée sur des actions aléatoires, est différente de la politique cible que l'agent adopte une fois qu'il a appris les valeurs Q optimales. Cette politique cible guide l'agent vers les meilleures décisions basées sur les valeurs Q apprises.

Le Q-learning est donc un algorithme efficace pour apprendre à résoudre des problèmes complexes où l'agent doit maximiser ses récompenses en explorant et en apprenant à partir de son environnement. De plus, le fait qu'il soit un algorithme hors-politiques (off-policy) permet à l'agent d'explorer avec une politique d'exploration tout en apprenant une politique cible distincte pour optimiser ses actions.

Ainsi, avec ces étapes répétées sur plusieurs épisodes, l'agent devient de plus en plus performant dans la prise de décisions optimales, et le tableau de valeurs Q finit par représenter un modèle fiable de l'environnement, guidant l'agent vers la maximisation de la récompense totale.



----------------
# Partie 3
----------------



En continuant avec l'exemple du Q-learning, il est important de comprendre le rôle fondamental que jouent les épisodes et les interactions de l'agent avec l'environnement. Chaque fois que l'agent traverse une séquence d'états, effectue des actions, et reçoit des récompenses, nous parlons d'un **épisode**. Un épisode se termine lorsque l'agent atteint un objectif final, que ce soit une récompense positive, comme la case +10, ou une situation défavorable, comme la case de poison à -10.

### Les différents éléments du Q-learning :
1. **Les états (S)** : Ce sont des représentations du moment présent dans l'environnement. Dans notre exemple, chaque case de la grille représente un état spécifique dans lequel l'agent peut se trouver.
  
2. **Les actions (A)** : Ce sont les choix que l'agent peut faire à partir d'un état donné. Par exemple, à partir d'une case, l'agent peut choisir de se déplacer à gauche, à droite, en haut ou en bas.

3. **La récompense (R)** : Après chaque action, l'agent reçoit une récompense basée sur l'état dans lequel il se retrouve. Cette récompense peut être positive, négative ou neutre. Dans notre cas, les récompenses varient de +10 (récompense finale) à -10 (poison) et -1 pour chaque case ordinaire.

4. **La fonction de valeur d'état-action (Q)** : Cette fonction est ce que l'agent tente d'apprendre au fil du temps. Elle associe une paire état-action à une valeur qui représente l'importance de choisir cette action dans cet état pour maximiser la récompense totale. L'agent modifie et met à jour cette fonction au fur et à mesure de ses expériences.

5. **Le facteur de réduction (γ - gamma)** : Ce paramètre détermine l’importance que l’agent accorde aux récompenses futures par rapport aux récompenses immédiates. Un gamma proche de 0 signifie que l'agent privilégie les récompenses immédiates, tandis qu'un gamma proche de 1 incite l'agent à tenir compte des récompenses à long terme.

6. **Le taux d'apprentissage (α - alpha)** : C’est le taux auquel l'agent ajuste les valeurs Q au fil du temps. Un taux d'apprentissage élevé permettra à l'agent d'apporter des modifications importantes aux valeurs Q rapidement, mais cela peut aussi entraîner des oscillations et une instabilité. Un taux plus faible permet un apprentissage plus lent et plus stable.

### L'exploration vs. l'exploitation

Un concept clé dans le Q-learning est celui de l'**exploration** et de l'**exploitation**. Lorsqu'un agent explore, il choisit des actions de manière aléatoire, sans nécessairement se baser sur les valeurs Q actuelles, dans le but de découvrir de nouvelles possibilités. L'exploration est essentielle car elle permet à l'agent de trouver de nouvelles stratégies qui pourraient être plus avantageuses à long terme. Cependant, si l'agent explore tout le temps, il risque de négliger les actions qui ont déjà montré qu'elles offraient une bonne récompense.

En revanche, lorsque l'agent exploite, il choisit systématiquement les actions qui lui offrent les meilleures valeurs Q actuelles. Cela peut conduire à une politique optimisée basée sur ce qu'il a déjà appris, mais si l'agent exploite trop tôt ou trop souvent, il risque de ne pas découvrir d'autres actions potentiellement meilleures à long terme.

L'équilibre entre l'exploration et l'exploitation est souvent géré par une stratégie dite **epsilon-greedy**. Dans cette stratégie, l'agent choisit une action aléatoire avec une certaine probabilité (epsilon), et avec une probabilité complémentaire, il choisit l'action qui a la meilleure valeur Q actuelle. L'epsilon peut être réduit au fil du temps, de sorte que l'agent explore davantage au début, puis exploite de plus en plus à mesure que les valeurs Q se stabilisent.

### Exemple d’un épisode complet

Prenons un exemple simple pour illustrer un épisode complet dans un environnement de grille :

1. **Début de l'épisode** : L'agent commence dans la case S1 (premier état). Il peut choisir d'aller à droite ou en bas. Disons que, dans le cadre de l'exploration, il choisit d'aller à droite.

2. **Nouvel état (S2)** : Après avoir bougé à droite, il atteint l'état S2 et reçoit une récompense de -1. Il met à jour la valeur Q associée à l'état S1 et à l'action "aller à droite" en fonction de cette nouvelle information.

3. **Prochaine action** : À l'état S2, il peut encore choisir d'aller à droite, à gauche ou vers le bas. Disons qu'il décide d'aller vers le bas (en fonction de sa politique d'exploration aléatoire).

4. **Nouvel état (S3)** : Il arrive dans un nouvel état, reçoit une autre récompense, et met à jour la valeur Q de l'état S2. Ce processus continue jusqu'à ce que l'agent atteigne la case de récompense +10 ou la case de poison -10.

À chaque étape, la table de valeurs Q est ajustée, et l'agent affine progressivement sa politique en apprenant les meilleures actions à prendre pour maximiser sa récompense. Après avoir répété ces épisodes de nombreuses fois, la table de valeurs Q reflète une bonne approximation des meilleures actions à entreprendre dans chaque état.

### Le Q-learning hors-politiques (off-policy)

Un des aspects uniques du Q-learning est qu'il s'agit d'un algorithme **hors-politiques** (off-policy). Cela signifie que l'agent peut utiliser une politique différente pour explorer l'environnement tout en apprenant une politique optimale distincte. En d'autres termes, l'agent peut explorer l'environnement avec une politique aléatoire (ou une politique epsilon-greedy) mais, en arrière-plan, il apprend et met à jour la politique cible optimale.

Cela offre une grande flexibilité au Q-learning, car il permet à l'agent de séparer l'apprentissage de la politique optimale des actions d'exploration, ce qui améliore son efficacité d'apprentissage.

### Conclusion

Le Q-learning est une méthode puissante et largement utilisée pour résoudre des problèmes complexes d'apprentissage par renforcement, notamment dans des environnements où l'agent doit apprendre à naviguer en fonction des récompenses reçues. Grâce à sa capacité à mettre à jour les valeurs Q de manière itérative, à équilibrer exploration et exploitation, et à apprendre de manière hors-politiques, le Q-learning est devenu un outil de choix pour des applications telles que les jeux, la robotique et d'autres domaines nécessitant une prise de décision optimisée dans des environnements dynamiques.

L'agent améliore progressivement ses performances en apprenant à partir de ses interactions avec l'environnement, ce qui illustre la puissance de l'apprentissage par renforcement dans des contextes variés et complexes.

-------------------
# Anenxe 1 - Étapes clés du processus de mise à jour des valeurs Q dans l'algorithme de Q-learning
------------------

Cet annexe présente les équations fondamentales et les étapes essentielles du processus de mise à jour des valeurs Q dans l'algorithme de Q-learning.

## Équations principales

1. Calcul de la nouvelle valeur Q :
   $$Q(S1, \text{droite}) = \text{récompense de S2} + \gamma \times \text{meilleure valeur future de S2}$$

2. Exemple de calcul avec des valeurs spécifiques :
   $$Q(S1, \text{droite}) = -1 + 0,1 \times 1,5 = -0,85$$

3. Formule générale de mise à jour de la valeur Q :
   $$Q_{\text{nouveau}} = Q_{\text{ancien}} + \alpha \times (\text{erreur})$$

4. Exemple de mise à jour avec des valeurs spécifiques :
   $$Q(S1, \text{droite}) = 1 + 0,1 \times (-1,85) = 0,815$$

## Processus de mise à jour

1. L'agent effectue une action dans un état donné.
2. Il observe la récompense immédiate et le nouvel état.
3. Il calcule la nouvelle valeur Q en utilisant l'équation de Bellman (équation 1).
4. Il compare cette nouvelle valeur à l'ancienne valeur Q.
5. Il met à jour la valeur Q en utilisant la formule de mise à jour (équation 3).
6. Ce processus est répété pour chaque action dans chaque état.

## Paramètres importants

- γ (gamma) : facteur de réduction pour les récompenses futures
- α (alpha) : taux d'apprentissage

## Objectif

L'objectif de ce processus est d'affiner progressivement les valeurs Q pour que l'agent apprenne la politique optimale, maximisant ainsi les récompenses à long terme dans l'environnement donné.

--------------------
# Annexe 2 - principales équations de Bellman et de Q-learning, ainsi que leur relation 
----------------



1. Équation de Bellman pour la fonction valeur V :

$$V(s) = \max_a \{R(s,a) + \gamma \sum_{s'} P(s'|s,a)V(s')\}$$

2. Équation de Bellman pour la fonction action-valeur Q :

$$Q(s,a) = R(s,a) + \gamma \sum_{s'} P(s'|s,a)\max_{a'} Q(s',a')$$

3. Équation de mise à jour de Q-learning :

$$Q(s,a) \leftarrow Q(s,a) + \alpha [R + \gamma \max_{a'} Q(s',a') - Q(s,a)]$$

Relation entre ces équations :

- L'équation de Bellman pour Q est une version plus détaillée de l'équation de Bellman pour V, en décomposant la valeur d'un état en fonction des actions possibles.

- L'équation de Q-learning est une approximation stochastique de l'équation de Bellman pour Q, où :
  - On remplace l'espérance par un échantillon (R + γ max Q(s',a'))
  - On utilise un taux d'apprentissage α pour mettre à jour progressivement les valeurs

- Q-learning converge vers la solution de l'équation de Bellman pour Q lorsque toutes les paires état-action sont visitées un nombre infini de fois et que le taux d'apprentissage décroît de manière appropriée.

Ces équations montrent comment Q-learning implémente de manière itérative et sans modèle le principe d'optimalité de Bellman pour apprendre la fonction action-valeur optimale.



--------------------
# Annexe 3 - principales équations de Bellman et de Q-learning, ainsi que leur relation 
----------------


#### ==>  les deux représentations de l'équation de mise à jour de Q-learning, incluant la version en termes de (1-α) :

1. Équation standard de mise à jour de Q-learning :

$$Q(s,a) \leftarrow Q(s,a) + \alpha [R + \gamma \max_{a'} Q(s',a') - Q(s,a)]$$

2. Équation de mise à jour de Q-learning en termes de (1-α) :

$$Q(s,a) \leftarrow (1-\alpha)Q(s,a) + \alpha(R + \gamma \max_{a'} Q(s',a'))$$

Ces deux équations sont mathématiquement équivalentes. La deuxième forme met en évidence que la nouvelle valeur Q est une combinaison pondérée de l'ancienne valeur Q et de la cible d'apprentissage (R + γ max Q(s',a')).

Interprétation :

- Dans la première équation, on ajoute à la valeur Q actuelle une fraction α de la différence entre la cible d'apprentissage et la valeur Q actuelle.
- Dans la deuxième équation, on prend (1-α) de l'ancienne valeur Q et on y ajoute α fois la cible d'apprentissage.

Cette représentation en termes de (1-α) est particulièrement utile pour comprendre comment le taux d'apprentissage α équilibre l'importance donnée à l'ancienne estimation par rapport à la nouvelle information


-------------------
# Rappel et résumé
-----------------


#### ===> les équations de Bellman et de Q-learning, avec leurs versions en termes de (1-α) lorsque c'est applicable :

1. Équation de Bellman pour la fonction valeur V :

$$V(s) = \max_a \{R(s,a) + \gamma \sum_{s'} P(s'|s,a)V(s')\}$$

Cette équation n'a pas de version en termes de (1-α) car elle ne concerne pas directement la mise à jour itérative.

2. Équation de Bellman pour la fonction action-valeur Q :

$$Q(s,a) = R(s,a) + \gamma \sum_{s'} P(s'|s,a)\max_{a'} Q(s',a')$$

De même, cette équation n'a pas de version en termes de (1-α) car elle décrit la relation d'optimalité, pas la mise à jour.

3. Équation de mise à jour de Q-learning :

Version standard :
$$Q(s,a) \leftarrow Q(s,a) + \alpha [R + \gamma \max_{a'} Q(s',a') - Q(s,a)]$$

Version en termes de (1-α) :
$$Q(s,a) \leftarrow (1-\alpha)Q(s,a) + \alpha(R + \gamma \max_{a'} Q(s',a'))$$

Ces deux formes de l'équation de mise à jour de Q-learning sont mathématiquement équivalentes. La version en termes de (1-α) met en évidence que la nouvelle valeur Q est une combinaison pondérée de l'ancienne valeur Q et de la cible d'apprentissage (R + γ max Q(s',a')).

- La relation entre ces équations reste la même que précédemment expliquée. 
- L'équation de mise à jour de Q-learning, dans ses deux formes, est une approximation stochastique des équations de Bellman, permettant un apprentissage itératif et sans modèle de la fonction action-valeur optimale.
