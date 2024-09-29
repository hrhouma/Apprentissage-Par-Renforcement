# **Interaction Agent-Environnement dans l'Apprentissage par Renforcement (RL)**

## **Introduction**

- L'interaction entre un **agent** et son **environnement** est au cœur de l'apprentissage par renforcement. 
- Un agent est une entité capable de percevoir son environnement et de prendre des décisions.
- L'objectif de l'agent est de maximiser ses **récompenses** au cours du temps en choisissant les bonnes **actions** dans chaque situation (ou **état**). 

![image](https://github.com/user-attachments/assets/8507b37f-0dbd-409d-8b7e-7e7e27d67aea)

- L'image ci-haut représente un environnement avec différentes cases, certaines étant des obstacles, d'autres associées à des récompenses (+1) ou des pénalités (-1). 
- L'agent (robot) commence à un point de départ et doit naviguer pour obtenir la meilleure récompense possible.

---

# **1. Notions de Base dans l'Interaction Agent-Environnement**

Dans un cadre d'apprentissage par renforcement, les notions clés à comprendre sont :

# **A. États (States)** :
Un état représente une configuration ou une situation dans laquelle se trouve l'agent à un moment donné dans l'environnement.

- **Dans l'image** : Chaque case est un état. Par exemple, le robot commence dans l'état \((1, 1)\) (en bas à gauche).

# **B. Actions (Actions)** :
Une action est une décision prise par l'agent dans un état donné. Les actions permettent à l'agent de se déplacer dans l'environnement ou d'interagir avec lui.

- **Dans l'image** : L'agent peut se déplacer vers la **gauche**, la **droite**, le **haut**, ou le **bas** à partir de sa position actuelle. Par exemple, s'il est dans l'état (3, 1), il peut choisir de se déplacer vers la droite (3, 2) ou vers le haut (3, 3).

# **C. Récompenses (Rewards)** :
Les récompenses sont des retours de l'environnement après qu'une action a été prise. Elles peuvent être positives (gain) ou négatives (perte). Elles guident l'agent pour qu'il apprenne à maximiser les bonnes décisions.

- **Dans l'image** :
  - La case (4, 3) contient une récompense de **+1**.
  - La case (4, 2) contient une pénalité de **-1**.

# **D. Transitions (Transitions)** :
Les transitions décrivent le passage d'un état à un autre en fonction de l'action choisie. Dans des environnements plus complexes, les transitions peuvent être probabilistiques, mais dans cet exemple, elles sont déterministes (chaque action mène toujours à un état spécifique).

- **Dans l'image** : Si l'agent est en (3, 1) et qu'il choisit d'aller vers le haut, il passera à l'état (3, 2).

---

# **2. Exécution d'un Épisode**

Un épisode en apprentissage par renforcement représente une séquence d'interactions entre l'agent et l'environnement, de l'état de départ jusqu'à un état terminal (fin de la tâche).

# **A. Exemple de parcours de l'agent :**

Supposons que l'agent commence dans l'état (1, 1) :

1. **Étape 1 :** L'agent est en (1, 1). Il choisit de se déplacer vers le **haut** pour aller à (2, 1).
   - Récompense : Aucune récompense pour cette action.
  
2. **Étape 2 :** L'agent est en (2, 1). Il choisit de se déplacer vers la **droite** pour aller à (3, 1).
   - Récompense : Aucune récompense pour cette action.

3. **Étape 3 :** L'agent est en (3, 1). Il choisit de se déplacer vers le **haut** pour aller à (3, 2).
   - Récompense : Aucune récompense pour cette action, mais l'agent se rapproche de la pénalité.

4. **Étape 4 :** L'agent est en (3, 2). Il choisit de se déplacer vers la **droite** pour aller à (4, 2).
   - Récompense : L'agent reçoit une pénalité de **-1**.

5. **Étape 5 :** L'agent est en (4, 2). Il réalise son erreur et se déplace vers le **haut** pour aller à (4, 3).
   - Récompense : L'agent reçoit une récompense de **+1**.

# **B. Stratégie de l'agent** :
À chaque épisode, l'agent apprend des actions qu'il a prises et des récompenses qu'il a reçues. Grâce à l'apprentissage, il pourrait modifier sa stratégie pour éviter la pénalité et se diriger plus rapidement vers la récompense (4, 3).

---

## **3. Concept de Politique (Policy)**

La **politique** est une stratégie que l'agent développe pour choisir la meilleure action à chaque état. Par exemple, l'agent peut apprendre à éviter la case \((4, 2)\) car elle a une récompense négative.

Dans notre exemple, une politique optimale pourrait être :

- Si l'agent est en (3, 1), il doit se déplacer vers le **haut** pour éviter la pénalité.
- Si l'agent est en (4, 2), il doit immédiatement se déplacer vers le **haut** pour atteindre la récompense.

---

# **4. Exploration et Exploitation**

Dans un environnement inconnu, l'agent doit **explorer** pour découvrir quelles actions mènent aux meilleures récompenses. Cependant, une fois qu'il a appris une bonne stratégie, il doit **exploiter** cette stratégie pour maximiser ses gains.

- **Exploration** : Essayer différentes actions pour découvrir quelles sont les meilleures. Par exemple, l'agent pourrait explorer toutes les directions dans l'image jusqu'à ce qu'il découvre la récompense à (4, 3).
- **Exploitation** : Utiliser ce qu'il a appris pour maximiser les récompenses. Après avoir découvert la récompense de (4, 3), l'agent pourrait toujours s'y diriger directement.

---

## **5. Conclusion**

L'apprentissage par renforcement repose sur l'interaction entre un agent et son environnement. L'agent apprend à partir des récompenses qu'il reçoit en fonction de ses actions, et au fil du temps, il développe une politique qui lui permet de maximiser ces récompenses. Dans l'exemple de l'image, l'agent doit naviguer dans un environnement simple avec des récompenses et des pénalités pour atteindre un objectif final.

Les concepts d'**état**, d'**action**, de **récompense**, et de **politique** sont essentiels à la compréhension de l'apprentissage par renforcement et sont appliqués dans des domaines réels tels que la robotique, la gestion de systèmes intelligents, et les jeux vidéo.

---

**Exercice pour vous :**
- Simulez plusieurs épisodes avec des décisions différentes pour l'agent et observez comment il peut optimiser son parcours pour maximiser la récompense finale de **+1** tout en évitant la pénalité de **-1**.


