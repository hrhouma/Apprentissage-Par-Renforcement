
# Quiz sur le Q-learning

1. **Qu'est-ce que le Q-learning ?**
   - a) Une méthode supervisée d'apprentissage
   - b) Un algorithme de renforcement
   - c) Un algorithme de classification
   - d) Un réseau de neurones

2. **Dans Q-learning, que représente la fonction Q ?**
   - a) La récompense immédiate
   - b) La valeur de la combinaison action-état
   - c) Le taux d'apprentissage
   - d) Le taux de dépréciation (gamma)

3. **Quelle est l'équation de mise à jour de Q dans Q-learning ?**
   - a) ```latex
     Q(s,a) = Q(s,a) + \alpha [r + \gamma \max Q(s',a') - Q(s,a)]
     ```
   - b) ```latex
     Q(s,a) = r + \gamma \max Q(s',a')
     ```
   - c) ```latex
     Q(s,a) = \alpha [r + \gamma Q(s',a')]
     ```
   - d) ```latex
     Q(s,a) = \max \alpha [r + Q(s,a)]
     ```

4. **Que signifie le paramètre alpha (α) dans Q-learning ?**
   - a) La récompense
   - b) Le taux de dépréciation
   - c) Le taux d'apprentissage
   - d) Le taux d'exploration

5. **Lequel des éléments suivants décrit l'exploration dans Q-learning ?**
   - a) L'utilisation des connaissances actuelles pour maximiser la récompense
   - b) La recherche de nouvelles actions qui pourraient améliorer la politique
   - c) Le calcul de la fonction de récompense
   - d) L'apprentissage des états finaux

6. **Lequel des éléments suivants décrit l'exploitation dans Q-learning ?**
   - a) Essayer des actions aléatoires pour découvrir de nouvelles solutions
   - b) Utiliser la meilleure action connue à partir de l'information actuelle
   - c) Maximiser l'exploration de l'environnement
   - d) Réduire l'apprentissage pour accélérer l'exécution

7. **Que signifie le terme "épisode" dans Q-learning ?**
   - a) Une séquence complète de décisions dans l'environnement
   - b) Une seule mise à jour de la table Q
   - c) Une boucle d'exploration continue
   - d) Une politique optimisée

8. **Quel est le rôle du facteur gamma (γ) dans Q-learning ?**
   - a) Il contrôle l'importance des récompenses futures
   - b) Il ajuste la fréquence d'exploration
   - c) Il affecte la précision de la fonction Q
   - d) Il influence la vitesse de convergence

9. **Qu'est-ce que la politique ε-greedy dans Q-learning ?**
   - a) Une politique où les actions sont choisies aléatoirement
   - b) Une politique où l'exploration est favorisée à chaque étape
   - c) Une politique qui choisit l'action optimale avec probabilité 1 - ε et explore avec probabilité ε
   - d) Une politique qui exclut les actions non optimales

10. **Comment se nomme la méthode qui équilibre l'exploration et l'exploitation en ajustant ε au fil du temps ?**
    - a) Décroissance linéaire
    - b) Apprentissage dynamique
    - c) Politique softmax
    - d) Décroissance épisodique

11. **Que se passe-t-il si le paramètre γ (gamma) est trop proche de 1 dans Q-learning ?**
    - a) Le modèle devient trop concentré sur les récompenses immédiates
    - b) Le modèle donne trop d'importance aux récompenses futures
    - c) Le modèle converge rapidement
    - d) Le modèle se désynchronise de l'environnement

12. **Quelle est la différence principale entre Q-learning et SARSA ?**
    - a) Q-learning est un algorithme en ligne, SARSA est hors ligne
    - b) Q-learning prend en compte la meilleure action possible, SARSA prend en compte l'action réellement suivie
    - c) SARSA utilise une table, tandis que Q-learning utilise un réseau de neurones
    - d) Il n'y a pas de différence, ce sont des algorithmes équivalents

13. **Dans le contexte du Q-learning, que signifie la convergence ?**
    - a) L'agent atteint un point où la politique ne change plus significativement
    - b) L'agent explore toujours l'environnement
    - c) La fonction de récompense reste constante
    - d) L'agent cesse d'exploiter l'environnement

14. **Quel problème peut survenir si ε reste élevé tout au long de l'apprentissage ?**
    - a) L'agent ne découvrira jamais les meilleures actions
    - b) L'agent explorera trop, empêchant la convergence
    - c) L'agent se concentrera uniquement sur les actions optimales
    - d) Il n'y a pas de problème, une exploration élevée est bénéfique

15. **Quel est l'effet d'un faible taux d'apprentissage (α) ?**
    - a) L'agent apprendra rapidement les bonnes actions
    - b) L'agent mettra du temps à ajuster ses estimations Q
    - c) L'agent ne prendra en compte que les récompenses futures
    - d) L'agent ne se soucie pas des récompenses passées

16. **Pourquoi le Q-learning est-il appelé un algorithme "off-policy" ?**
    - a) Il apprend une politique basée uniquement sur des actions optimales
    - b) Il apprend la politique indépendamment de la politique suivie
    - c) Il apprend une politique uniquement basée sur les actions exploratoires
    - d) Il n'utilise pas de table Q pour l'apprentissage

17. **Quelles sont les deux principales méthodes pour stocker la fonction Q ?**
    - a) Table et réseau de neurones
    - b) Table et fonction linéaire
    - c) Réseau de neurones et arbre de décision
    - d) Politique softmax et fonction d'action

18. **Comment s'appelle l'extension du Q-learning qui utilise des réseaux de neurones pour approximer la fonction Q ?**
    - a) Apprentissage par transfert
    - b) SARSA
    - c) Deep Q-learning (DQN)
    - d) Exploration aléatoire

19. **Dans Q-learning, qu'est-ce qui déclenche la mise à jour de la fonction Q ?**
    - a) Une exploration réussie
    - b) Une interaction avec l'environnement
    - c) Une décision prise par l'agent
    - d) L'atteinte d'une récompense maximale

20. **Pourquoi Q-learning est-il considéré comme robuste aux environnements stochastiques ?**
    - a) Parce qu'il ne dépend pas de la transition précise entre états
    - b) Parce qu'il n'utilise pas de réseau de neurones
    - c) Parce qu'il ajuste continuellement la politique en fonction des variations
    - d) Parce qu'il ne dépend pas des récompenses
