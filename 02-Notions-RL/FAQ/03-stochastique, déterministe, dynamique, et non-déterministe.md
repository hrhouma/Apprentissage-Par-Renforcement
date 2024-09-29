#  **Table explicative** des différents concepts liés à **stochastique**, **déterministe**, **dynamique**, et **non-déterministe** :

| **Concept**       | **Définition**                                                                                                        | **Exemple**                                                                                           |
|-------------------|----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Stochastique**  | Un environnement où les résultats des actions sont influencés par une part de **hasard** ou de **probabilité**.      | Lancer un dé : même si tu le lances de la même manière, le résultat est aléatoire et varie à chaque lancer. |
| **Déterministe**  | Un environnement où chaque action a un **résultat fixe** et prévisible. Le résultat d'une action est toujours le même. | Un jeu d'échecs : chaque mouvement mène toujours à un résultat exact et prévisible.                    |
| **Dynamique**     | Un environnement qui **change** avec le temps, souvent de manière imprévisible.                                        | La conduite sur la route : les conditions de circulation changent constamment (trafic, feux, etc.).    |
| **Non-déterministe** | Un environnement où il est **impossible** de prédire exactement l'issue des actions, soit à cause de l'incertitude soit parce que plusieurs actions peuvent avoir des résultats différents. | La météo : même avec des données, il y a toujours une incertitude sur ce qu'il va se passer exactement demain. |

### Résumé des différences :

1. **Stochastique** vs **Déterministe** :
   - **Stochastique** : il y a une **incertitude** dans le résultat des actions, influencée par des probabilités (le hasard joue un rôle).
   - **Déterministe** : chaque action produit un **résultat prévisible** et fixe. Il n'y a pas de hasard.

2. **Dynamique** vs **Non-déterministe** :
   - **Dynamique** : l'environnement **évolue** avec le temps, et l'agent doit s'adapter aux **changements** constants (pas nécessairement aléatoires).
   - **Non-déterministe** : le résultat des actions n'est pas forcément prévisible, car l'environnement est soit trop **complexe**, soit il y a plusieurs résultats possibles pour une même action, mais cela ne repose pas forcément sur du hasard pur.

### Quelques combinaisons :
- **Stochastique et Dynamique** : L'environnement change continuellement et les résultats des actions sont **influencés par des probabilités**. Exemple : conduire une voiture dans des conditions météorologiques variables.
- **Déterministe et Dynamique** : L'environnement change au fil du temps, mais les actions mènent toujours à des résultats **prédictibles**. Exemple : Un système de trafic où les feux de signalisation changent selon des règles préprogrammées, mais de manière régulière.
- **Stochastique et Statique** : L'environnement reste fixe, mais les résultats des actions sont **influencés par des probabilités**. Exemple : Lancer un dé dans une pièce fermée.
- **Déterministe et Statique** : L'environnement ne change pas et chaque action mène à un résultat **prévisible**. Exemple : Un puzzle, où chaque pièce a un emplacement unique.

Cette table permet de distinguer clairement chaque concept, et comment ils interagissent dans différents contextes. 
