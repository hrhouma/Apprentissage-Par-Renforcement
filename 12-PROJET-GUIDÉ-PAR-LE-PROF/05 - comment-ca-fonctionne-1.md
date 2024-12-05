-----------
# 01 - **Schéma de l'Apprentissage par Renforcement avec DQN**
-----------

##### Représentation simple pour expliquer comment fonctionne un **DQN (Deep Q-Network)** dans le cadre de l'apprentissage par renforcement pour un jeu comme Pong :

```
+-----------------+        +--------------------+        +------------------+
|  État actuel    | ----->| Réseau de Neurones | -----> | Actions possibles |
| (Image du jeu)  |        |   (Deep Q-Network) |        | (Monter/Descendre)|
+-----------------+        +--------------------+        +------------------+
         ^                                                         |
         |                                                         v
         |                                                 +------------------+
         |                                                 |   Environnement  |
         |                                                 |    (Pong)       |
         |                                                 +------------------+
         |                                                         |
         |                                                         v
         +<------------------------------------------------ +------------------+
                             Récompense (Score) et Nouvel État
```

-----------
# 02 - **Concepts Importants**
-----------

#### 1. **États**
Un **état** représente une observation du jeu à un moment donné. 
- Dans Pong, l'état correspond à une image du terrain de jeu (balle, raquettes, etc.).
- Pour simplifier, cette image est :
  - Convertie en niveaux de gris.
  - Redimensionnée à 84x84 pixels.
  - Normalisée (valeurs entre 0 et 1).
  - Empilée (4 images consécutives) pour capturer le mouvement.

#### 2. **Q**
La fonction **Q** (ou **Valeur-Q**) évalue la qualité d'une action donnée dans un état spécifique :
- **Q(s, a)** : Représente la valeur estimée de la récompense cumulée future si on prend l'action `a` dans l'état `s`.
- Exemple dans Pong :
  - Si la balle se dirige vers la raquette, Q("monter") pourrait être élevé car cela peut éviter de perdre un point.

#### 3. **Pourquoi DQN ?**

##### **Problème avec Q-Learning classique :**
- Le Q-Learning stocke la table Q dans une matrice (`Q[state, action]`).
- Pour un jeu comme Pong, le nombre d'états possibles (images du terrain) est immense, impossible à représenter dans une table.

##### **Avantage du DQN :**
- Au lieu d'une table, le DQN utilise un **réseau de neurones** pour approximer la fonction Q.
- Il peut traiter des **données continues** comme des images.
- Il est adapté aux environnements complexes avec de grands espaces d'état.

#### 4. **Pourquoi pas TD-Learning ou SARSA ?**
- **TD-Learning** et **SARSA** sont similaires au Q-Learning mais nécessitent également une table Q, ce qui est inefficace pour des environnements visuels comme Pong.
- DQN surmonte cette limitation grâce à l'utilisation de **réseaux de neurones profonds**.


-----------
# 03 - **Fonctionnement Étape par Étape**
-----------

#### 1. **Épisode**
Un **épisode** correspond à une partie entière de Pong :
- L'agent commence à un état initial (ex. : balle au centre, raquettes en position).
- Il interagit avec l'environnement en effectuant des actions (ex. : monter/descendre la raquette).
- L'épisode se termine lorsque l'un des joueurs marque 21 points.

#### 2. **Récompense**
La **récompense** est un retour quantifiant la qualité de l'action prise par l'agent :
- **+1** : Si l'agent marque un point.
- **-1** : Si l'agent encaisse un point.
- **0** : Sinon.

#### 3. **Exploration vs Exploitation**
L'agent utilise une stratégie **epsilon-greedy** :
- **Exploration** : L'agent prend des actions aléatoires (ε élevé, au début).
- **Exploitation** : L'agent prend des actions basées sur la prédiction de son réseau de neurones (ε faible, après entraînement).

#### 4. **Réseau DQN**
Le DQN reçoit en entrée l'état du jeu (image) et prédit les **valeurs Q** pour chaque action possible. Exemple :
- Entrée : Image du jeu.
- Sortie : 
  - Q(monter) = 0.8.
  - Q(descendre) = 0.5.
- Action choisie : **Monter**, car Q(monter) est plus élevé.

---

# **Pourquoi DQN Est-il Puissant ?**

1. **Approximation des Valeurs Q :**
   - DQN utilise un réseau de neurones profond pour approximer les valeurs Q.
   - Cela permet de traiter des espaces d'état complexes (images, vidéos).

2. **Mémoire Replay :**
   - L'agent stocke ses expériences (état, action, récompense, état suivant) dans une mémoire.
   - Pendant l'entraînement, il échantillonne des expériences aléatoires pour éviter la **corrélation temporelle**.

3. **Double Réseau Q (Stabilité) :**
   - Utilise deux réseaux de neurones :
     - **Réseau principal :** Prédit les valeurs Q.
     - **Réseau cible :** Fournit les valeurs cibles pour l'entraînement.

4. **Récompenses différées :**
   - Le DQN prend en compte les récompenses futures grâce au facteur d'actualisation **γ** :
     - \( Q(s, a) = R + \gamma \max Q(s', a') \).

-----------
# 04 - **Résumé des Concepts Clés**
-----------


| **Concept**            | **Description**                                                                                 |
|-------------------------|-----------------------------------------------------------------------------------------------|
| **État (State)**        | Représentation de l'environnement (image du terrain).                                          |
| **Action**              | Décision prise par l'agent (ex. : monter ou descendre).                                         |
| **Récompense (Reward)** | Retour reçu après une action (ex. : +1 pour un point, -1 pour une défaite).                     |
| **Q(s, a)**             | Valeur estimée de la récompense cumulée future en prenant une action `a` dans un état `s`.      |
| **DQN**                 | Réseau de neurones qui approxime la fonction Q.                                                |
| **Épisode**             | Une partie complète du jeu.                                                                    |
| **Exploration**         | Prendre des actions aléatoires pour découvrir de nouvelles stratégies.                          |
| **Exploitation**        | Prendre des actions optimales basées sur les connaissances actuelles.                           |

-----------
# 05 - **Conclusion**
-----------

- **Pourquoi DQN ?** Le DQN est essentiel pour résoudre des problèmes où l'espace d'état est trop grand pour les méthodes traditionnelles.
- **Comment ça marche ?** Le DQN utilise un réseau de neurones pour approximer les valeurs Q, permettant à l'agent d'apprendre à jouer en maximisant les récompenses.
- **Résultats attendus :** Au fil des épisodes, l'agent devient de plus en plus performant, passant de scores négatifs à des scores positifs.

Ce modèle est une base puissante pour l'apprentissage par renforcement et peut être appliqué à des environnements encore plus complexes comme des jeux 3D ou des robots.
