-----------------------------------------------------------------------------
# **Table des termes en Apprentissage par Renforcement (RL)**
-----------------------------------------------------------------------------

| **Terme**      | **Définition**                                                                 | **Exemple / Explication**                                                                                                                                                                      |
|----------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Agent**      | L'entité qui prend des décisions dans l'environnement.                                                             | Un robot, une voiture autonome ou une IA qui prend des actions dans un jeu vidéo.                                                                                                              |
| **Environnement (Environment)** | Le monde dans lequel l'agent évolue et interagit.                                                    | Le plateau de jeu dans l'image fournie, où l'agent peut se déplacer à travers des cases avec des obstacles, récompenses et pénalités.                                                          |
| **État (State)** | La situation actuelle de l'agent dans l'environnement, à un instant donné.                                          | Dans l'image, un état est une case particulière (comme \((3, 1)\)) où se trouve l'agent.                                                                                                        |
| **Action (Action)** | Ce que l'agent peut faire dans un état donné pour modifier son environnement.                                       | Se déplacer vers la gauche, la droite, le haut ou le bas dans l'environnement pour changer de case.                                                                                             |
| **Récompense (Reward)** | Feedback que l'agent reçoit après avoir pris une action. Il peut être positif ou négatif.                     | Dans l'image, +1 pour atteindre le diamant, -1 pour entrer dans une case avec une pénalité.                                                                                                     |
| **Transition**  | Le passage d'un état à un autre après avoir pris une action.                                                        | Si l'agent est en \((1, 1)\) et choisit d'aller à droite, il passe à l'état \((2, 1)\).                                                                                                        |
| **Politique (Policy)** | Stratégie de décision de l'agent pour choisir la meilleure action en fonction de l'état actuel.                 | "Toujours se déplacer vers le diamant en évitant les pénalités" serait une politique optimale dans l'image.                                                                                      |
| **Valeur (Value)** | Estimation de la récompense à long terme associée à un état, en tenant compte des actions futures.                  | Si l'agent est à un état proche du diamant, la valeur de cet état sera élevée car il est proche d'une récompense positive.                                                                       |
| **Valeur-Q (Q-Value)** | La qualité d'une action spécifique dans un état donné, tenant compte des récompenses futures attendues.          | La valeur-Q de se déplacer vers le diamant depuis un état proche sera élevée. Se déplacer vers une pénalité aura une valeur-Q basse.                                                            |
| **Exploration** | Processus par lequel l'agent essaie de nouvelles actions pour découvrir les récompenses ou pénalités dans l'environnement. | L'agent pourrait tester toutes les directions dans l'image jusqu'à trouver la récompense de +1.                                                                                                 |
| **Exploitation** | Processus par lequel l'agent utilise les connaissances acquises pour maximiser ses récompenses.                      | Une fois que l'agent a découvert la case avec la récompense de +1, il se déplacera toujours directement vers cette case.                                                                        |
| **Facteur de Réduction (Discount Factor)** | Paramètre qui mesure l'importance des récompenses futures par rapport aux récompenses immédiates.   | Un facteur de réduction faible signifie que l'agent préfère les récompenses immédiates ; un facteur élevé favorise les récompenses futures.                                                      |
| **Épisode (Episode)** | Un cycle complet d’interactions de l’agent avec l’environnement, de l'état initial jusqu'à l'état final.        | Dans l'image, un épisode commence à l'état "Start" \((1, 1)\) et se termine lorsque l'agent atteint le diamant ou tombe dans une pénalité.                                                      |
| **Fonction de Récompense** | Fonction qui attribue une récompense pour chaque action de l'agent dans un état donné.                       | Si l'agent se déplace dans la case \((4, 2)\), la fonction de récompense renverra -1. Si l'agent atteint \((4, 3)\), la fonction de récompense renverra +1.                                      |
| **Fonction de Transition** | Modélise comment les actions changent les états.                                                        | Dans l'image, l'action de se déplacer vers la droite de \((3, 1)\) conduit à \((4, 1)\).                                                                                                       |
| **Utilité (Utility)** | L’utilité d’un état représente la valeur que cet état offre à l'agent en tenant compte des récompenses futures probables. | Similaire à la **Valeur**, mais l’utilité prend en compte non seulement les récompenses immédiates, mais aussi la probabilité d’atteindre certains états à partir de cet état. |
| **Politique Optimale (Optimal Policy)** | La politique qui maximise la récompense attendue à long terme pour l’agent.                     | Si l’agent apprend que se déplacer vers la droite deux fois puis vers le haut une fois lui permet d’obtenir une récompense maximale, cela deviendrait sa politique optimale.                    |

-----------------------------------------------------------------------------
# **Termes importants à comprendre dès les premières séances :**
-----------------------------------------------------------------------------

1. **Agent** et **Environnement** : Décrire leur relation et interaction.
2. **État**, **Action**, et **Transition** : Expliquer comment l'agent se déplace dans l'environnement et passe d'un état à un autre.
3. **Récompense** : Présenter le concept de retour après une action.
4. **Politique** et **Politique Optimale** : Introduire l'idée de stratégie pour la prise de décisions.
5. **Valeur** et **Utilité** : Comparer les états en fonction de leur récompense à long terme.

-----------------------------------------------------------------------------
# **Séquence de termes** :
-----------------------------------------------------------------------------

## 1. Introduction à l'**agent**, l'**environnement**, les **états**, et les **actions**.
## 2. Exploration des notions de **récompenses**, de **transitions**, et introduction à la **politique**.
## 3. Discussions sur les **valeurs**, les **valeurs-Q**, et le concept d'**utilité** pour que les étudiants puissent comprendre comment l'agent évalue les états et optimise sa politique.

- Cela nous permettera de construire une progression logique pour comprendre les interactions de base dans un système d'apprentissage par renforcement.
