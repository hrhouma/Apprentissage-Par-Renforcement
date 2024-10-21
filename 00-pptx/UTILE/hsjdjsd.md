$$
V^*(s) = \max_a \left( \sum_{s'} P(s' | s, a) \left[ r(s, a, s') + \gamma V^*(s') \right] \right)
$$


# Contenu de l'équation
content = """
$$
V^*(s) = \max_a \left( \sum_{s'} P(s' | s, a) \left[ r(s, a, s') + \gamma V^*(s') \right] \right)
$$

"""




**a) Fonction de récompense \( r(s, a, s') \) pour ce MDP :**

La fonction de récompense \( r(s, a, s') \) indique la récompense que l'agent reçoit en passant de l'état \( s \) à l'état \( s' \) en effectuant l'action \( a \). Voici la fonction de récompense pour chaque transition possible dans le labyrinthe :

- Si l'agent atteint l'état G (objectif), la récompense est \( +10 \).
- Si l'agent entre dans un piège, la récompense est \( -1 \).
- Si l'agent reste dans une case neutre ou se déplace vers une case neutre, la récompense est \( 0 \).
- Si l'agent tente de sortir de la grille, il reste dans le même état avec une récompense de \( 0 \).

Ainsi, la fonction de récompense est :

$$
r(s, a, s') = \begin{cases} 
+10, & \text{si } s' = G \\
-1, & \text{si } s' \text{ est une case piège} \\
0, & \text{si } s' \text{ est une case neutre ou sortie du labyrinthe}
\end{cases}
$$

---

**b) Calcul de la valeur optimale \( V^*(S) \) pour l'état initial \( S \) en utilisant l'équation de Bellman :**

L'équation de Bellman pour un état \( s \) est donnée par

$$
V^*(s) = \max_a \left( \sum_{s'} P(s' | s, a) \left[ r(s, a, s') + \gamma V^*(s') \right] \right)
$$

Nous allons calculer \( V^*(S) \) pour l'état initial \( S \). Les transitions possibles depuis \( S \) sont :

- Vers la droite (état neutre avec récompense 0)
- Vers le bas (case avec récompense -1)

Ainsi, l'équation de Bellman pour $$S$$ devient :

$$
V^*(S) = \max \left( 0 + 0.9 V^*(0), -1 + 0.9 V^*(-1) \right)
$$

Les états \( 0 \), \( -1 \), et \( G \) sont calculés en fonction de leurs voisins respectifs. En procédant itérativement, vous pourriez obtenir une approximation de \( V^*(S) \). Par exemple, si \( V^*(0) \approx 8 \) et \( V^*(-1) \approx -2 \), alors :

$$
V^*(S) = \max \left( 0 + 0.9 \times 8, -1 + 0.9 \times (-2) \right) = \max(7.2, -2.8) = 7.2
$$

Donc, \( V^*(S) \approx 7.2 \).

---

**c) Stratégie optimale pour ce MDP :**

La stratégie optimale consiste à maximiser la valeur de l'état suivant à chaque décision. Depuis l'état initial \( S \), la meilleure action est de se déplacer vers la droite pour éviter les pièges. En continuant à éviter les cases piégées et en se rapprochant de l'état but \( G \), l'agent minimise les pénalités de \( -1 \) et maximise la récompense de \( +10 \).

Justification :
- Se déplacer vers la droite permet de maintenir une valeur plus élevée (proche de \( 7.2 \)).
- Se déplacer vers le bas expose l'agent à une pénalité de \( -1 \), ce qui réduit la valeur de l'état.

---

**d) Environnement stochastique :**

Si l'environnement est stochastique, avec une probabilité de 0.2 que l'agent glisse et se déplace dans une direction aléatoire différente de celle choisie, cela affecte les transitions de l'agent. Il y a maintenant un risque que l'agent atterrisse dans un piège même s'il tente de suivre la stratégie optimale.

L'équation de Bellman serait modifiée pour tenir compte de la probabilité d'un mouvement aléatoire :

$$
V^*(s) = \max_a \left( 0.8 \sum_{s'} P(s' | s, a) \left[ r(s, a, s') + \gamma V^*(s') \right] + 0.2 \sum_{\text{aléatoire}} P(s' | s, a_{\text{aléatoire}}) \left[ r(s, a_{\text{aléatoire}}, s') + \gamma V^*(s') \right] \right)
$$

Cela rend le problème plus complexe car l'agent doit désormais tenir compte de la probabilité d'atterrir dans des pièges même en suivant la meilleure stratégie.


-----------




Je comprends votre préoccupation. Voici les équations corrigées avec le formatage LaTeX approprié :

**a) Fonction de récompense $$r(s, a, s')$$ pour ce MDP :**

La fonction de récompense $$r(s, a, s')$$ indique la récompense que l'agent reçoit en passant de l'état $$s$$ à l'état $$s'$$ en effectuant l'action $$a$$. Voici la fonction de récompense pour chaque transition possible dans le labyrinthe :

$$
r(s, a, s') = \begin{cases} 
+10, & \text{si } s' = G \\
-1, & \text{si } s' \text{ est une case piège} \\
0, & \text{si } s' \text{ est une case neutre ou sortie du labyrinthe}
\end{cases}
$$

**b) Calcul de la valeur optimale $$V^*(S)$$ pour l'état initial $$S$$ en utilisant l'équation de Bellman :**

L'équation de Bellman pour un état $$s$$ est donnée par :

$$
V^*(s) = \max_a \left( \sum_{s'} P(s' | s, a) \left[ r(s, a, s') + \gamma V^*(s') \right] \right)
$$

Pour l'état initial $$S$$, l'équation de Bellman devient :

$$
V^*(S) = \max \left( 0 + 0.9 V^*(0), -1 + 0.9 V^*(-1) \right)
$$

Si $$V^*(0) \approx 8$$ et $$V^*(-1) \approx -2$$, alors :

$$
V^*(S) = \max \left( 0 + 0.9 \times 8, -1 + 0.9 \times (-2) \right) = \max(7.2, -2.8) = 7.2
$$

**d) Environnement stochastique :**

L'équation de Bellman modifiée pour tenir compte de la probabilité d'un mouvement aléatoire :

$$
V^*(s) = \max_a \left( 0.8 \sum_{s'} P(s' | s, a) \left[ r(s, a, s') + \gamma V^*(s') \right] + 0.2 \sum_{\text{aléatoire}} P(s' | s, a_{\text{aléatoire}}) \left[ r(s, a_{\text{aléatoire}}, s') + \gamma V^*(s') \right] \right)
$$

Ces équations sont maintenant correctement formatées en LaTeX, utilisant les doubles signes dollar ($$) pour le mode mathématique en ligne.
