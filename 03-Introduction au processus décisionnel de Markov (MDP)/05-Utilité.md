
# Redéfinir l'apprentissage par renforcement dans le contexte de la récompense cumulative:

- L'apprentissage par renforcement (RL) est une technique d'apprentissage automatique où un agent apprend à interagir avec un environnement pour ***maximiser une récompense cumulative.*** 

# ==> points clés sur son utilité :

# 1 - **Utilité de l'apprentissage par renforcement**

- **Optimisation des performances** : L'objectif principal est d'améliorer les performances de l'agent en maximisant les récompenses positives ***à long terme.***
- **Prise de décision séquentielle** : RL est utilisé pour résoudre des problèmes où la prise de décision est séquentielle et les actions ont des conséquences à long terme, comme dans les jeux ou la robotique.
- **Exploration et exploitation** : L'agent doit trouver un équilibre entre explorer de nouvelles actions pour découvrir des récompenses potentielles et exploiter les actions connues qui offrent des récompenses élevées.

# 2 - **Récompense cumulative**

- **Valeur cumulative** : Plutôt que de se concentrer sur une seule action ou récompense, RL cherche à maximiser la somme des récompenses sur le temps. Cela signifie que l'agent évalue les actions non seulement par leur impact immédiat mais aussi par leur contribution future aux objectifs.

- **Stratégies optimales** : En apprenant quelles actions mènent aux meilleures récompenses cumulatives, l'agent développe une stratégie optimale pour naviguer dans son environnement.


# 3 - Voir les slides de 11 à 14
# 4 - Voir les problèmes avec les utilités (Slide 15)

- Ces dispositives fournissent des informations sur l'apprentissage par renforcement (RL) et les défis liés aux récompenses infinies dans des environnements où le jeu ou la tâche pourrait durer indéfiniment.

## **Infinite Utilities**

- **Problème** : Si un jeu ou une tâche dure éternellement, comment gérer les récompenses infinies ?
  
- **Solutions** :
  - **Horizon fini** : Terminer les épisodes après un nombre fixe de pas pour éviter des politiques non stationnaires.
  - **Actualisation (Discounting)** : Utiliser un facteur d'actualisation $$\gamma$$ (0 < $$\gamma$$ < 1) pour donner plus d'importance aux récompenses immédiates et réduire l'impact des récompenses futures. Cela aide à calculer une valeur cumulative finie.
  - **État absorbant** : Garantir qu'un état terminal soit éventuellement atteint pour chaque politique.


En résumé, l'apprentissage par renforcement est crucial pour développer des systèmes autonomes capables de s'adapter et d'apprendre dans des environnements dynamiques et incertains.

