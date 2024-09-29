-----------------------------
# Pratique 01
-----------------------------


### Situation 1 : **Détection de fraudes bancaires**
Une banque souhaite détecter les transactions frauduleuses dans son système. Elle dispose d’un grand volume de données historiques sur les transactions, où chaque transaction est étiquetée comme « frauduleuse » ou « normale ».

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage supervisé**.  
  - **Pourquoi ?** : Les données sont déjà étiquetées (frauduleuse ou normale), et l’objectif est de prédire à partir de nouvelles données si une transaction est frauduleuse.

---

### Situation 2 : **Regroupement de clients d’un supermarché**
Un supermarché souhaite regrouper ses clients en fonction de leurs habitudes d’achat pour offrir des promotions ciblées. Ils n’ont pas d’étiquettes indiquant des catégories précises de clients, mais ils disposent d’un grand ensemble de données sur les achats réalisés.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage non supervisé**.  
  - **Pourquoi ?** : Il n’y a pas d’étiquettes ou de catégories prédéfinies. L’objectif est de découvrir des groupes ou des clusters basés sur les données des habitudes d’achat.

---

### Situation 3 : **Entraînement d’un robot à éviter des obstacles**
Un robot doit apprendre à se déplacer dans un environnement rempli d’obstacles. À chaque fois qu’il se cogne contre un objet, il reçoit une pénalité, et à chaque fois qu’il trouve une trajectoire dégagée, il reçoit une récompense.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage par renforcement (RL)**.  
  - **Pourquoi ?** : Le robot doit apprendre en interagissant directement avec son environnement, en prenant des décisions pour éviter les obstacles et maximiser sa récompense.

---

### Situation 4 : **Reconnaissance de visages sur des photos**
Une entreprise souhaite développer un système capable de reconnaître les visages des employés à partir de photos. Elle dispose de milliers d’images d’employés, chacune avec le nom de l’employé correspondant.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage supervisé**.  
  - **Pourquoi ?** : Chaque image est étiquetée avec le nom de l’employé, ce qui permet d’entraîner un modèle pour faire des prédictions basées sur de nouvelles images.

---

### Situation 5 : **Optimisation des feux de circulation dans une ville**
Une ville souhaite optimiser ses feux de signalisation pour réduire les embouteillages. Le système doit ajuster les durées des feux en temps réel, en fonction du flux de circulation à différents moments de la journée.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage par renforcement (RL)**.  
  - **Pourquoi ?** : Le système interagit en temps réel avec l’environnement (les voitures, le trafic) et doit apprendre à ajuster les feux de circulation pour maximiser la fluidité du trafic.

---

### Situation 6 : **Segmentation d’images médicales**
Un hôpital souhaite analyser des images médicales pour identifier des tumeurs ou anomalies. Le but est de segmenter les images en zones d’intérêt. Les images sont fournies sans étiquettes ni informations préalables sur les zones d’intérêt.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage non supervisé**.  
  - **Pourquoi ?** : Aucune information ou étiquette n’est disponible pour guider la segmentation des images. Le modèle doit découvrir automatiquement les régions importantes.

---

### Situation 7 : **Système de recommandation pour une plateforme de streaming**
Une plateforme de streaming souhaite recommander des vidéos aux utilisateurs en fonction de leurs habitudes de visionnage. Le système doit s’adapter aux nouvelles interactions des utilisateurs pour améliorer les recommandations au fil du temps.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage par renforcement (RL)**.  
  - **Pourquoi ?** : Le système doit apprendre en continu à partir des interactions des utilisateurs, en ajustant les recommandations pour maximiser l’engagement des utilisateurs (comme cliquer sur les vidéos recommandées).

---

### Situation 8 : **Classement d’emails en spam et non-spam**
Un fournisseur de services email souhaite créer un système pour classer automatiquement les emails entrants en spam et non-spam. Il dispose d’un grand ensemble d’emails, chacun étiqueté comme « spam » ou « non-spam ».

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage supervisé**.  
  - **Pourquoi ?** : Les emails sont déjà étiquetés, ce qui permet de former un modèle pour classifier de nouveaux emails.

---

### Situation 9 : **Jeu de stratégie en temps réel**
Un jeu vidéo de stratégie souhaite créer une intelligence artificielle capable de jouer contre des humains en prenant des décisions en temps réel pour maximiser ses chances de victoire.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage par renforcement (RL)**.  
  - **Pourquoi ?** : L’intelligence artificielle doit apprendre à interagir avec l’environnement du jeu et à ajuster ses décisions pour maximiser ses chances de victoire.

---

### Situation 10 : **Clustering de documents pour une analyse de texte**
Une entreprise souhaite regrouper automatiquement des articles de presse en différents sujets sans disposer d’étiquettes prédéfinies pour chaque sujet.

- **Choix : Supervisé, Non Supervisé ou RL ?**
- **Réponse attendue** : **Apprentissage non supervisé**.  
  - **Pourquoi ?** : L’entreprise n’a pas d’étiquettes pour chaque sujet, et elle souhaite découvrir les thèmes ou les groupes d’articles automatiquement.
