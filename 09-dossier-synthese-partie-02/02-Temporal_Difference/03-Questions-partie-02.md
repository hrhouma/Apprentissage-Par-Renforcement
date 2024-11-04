# **Quiz à choix multiples : Apprentissage par Différence Temporelle (TD), SARSA et Q-Learning**

1. **Qu'est-ce que l'apprentissage par différence temporelle (TD) ?**
   - A. Une méthode basée sur des épisodes complets
   - B. Une approche combinant Monte Carlo et programmation dynamique
   - C. Une méthode nécessitant un modèle de l'environnement
   - D. Une méthode de supervision directe

2. **Lequel des éléments suivants est un avantage des méthodes TD ?**
   - A. Elles nécessitent un modèle de l'environnement
   - B. Elles attendent la fin de l'épisode pour mettre à jour les valeurs
   - C. Elles peuvent fonctionner avec des épisodes incomplets
   - D. Elles ont besoin de calculs complexes

3. **Quelle est la règle de mise à jour TD(0) pour estimer la valeur d’un état ?**
   - A. $$ V(s) \leftarrow R_{t+1} $$
   - B. $$ V(s) \leftarrow \alpha [ R_{t+1} - V(s)] $$
   - C. $$ V(s) \leftarrow V(s) + \alpha [R_{t+1} + \gamma V(S_{t+1}) - V(s)] $$
   - D. $$ V(s) \leftarrow \gamma V(s) $$

4. **Dans les méthodes TD, que représente $$\gamma$$ ?**
   - A. Le taux d'apprentissage
   - B. La probabilité d'exploration
   - C. Le facteur d'actualisation
   - D. Le nombre d'actions possibles

5. **Pourquoi SARSA est-il considéré comme une méthode sur politique ?**
   - A. Il utilise une politique différente pour le comportement et la mise à jour
   - B. Il suit la même politique pour la prise d'action et la mise à jour
   - C. Il nécessite un modèle de l'environnement
   - D. Il ne dépend pas d'une politique d'apprentissage

6. **Quel est le rôle du paramètre $$\alpha$$ dans les méthodes TD ?**
   - A. Fixer la probabilité d'explorer
   - B. Ajuster la vitesse de mise à jour des estimations
   - C. Sélectionner la prochaine action
   - D. Déterminer la politique de récompense

7. **Dans une politique epsilon-greedy, que se passe-t-il si epsilon est proche de 1 ?**
   - A. L'agent choisit toujours l'action optimale
   - B. L'agent explore souvent de nouvelles actions
   - C. L'agent devient complètement aléatoire
   - D. L'agent ne met jamais à jour ses estimations

8. **Quelle est la règle de mise à jour pour SARSA ?**
   - A. $$ Q(s, a) \leftarrow \alpha [R_{t+1} + \gamma \max Q(S_{t+1}, a') - Q(s, a)] $$
   - B. $$ Q(s, a) \leftarrow Q(s, a) + \alpha [R_{t+1} + \gamma Q(S_{t+1}, A_{t+1}) - Q(s, a)] $$
   - C. $$ V(s) \leftarrow V(s) + \alpha R_{t+1} $$
   - D. $$ Q(s, a) \leftarrow \max Q(s, a) $$

9. **Pourquoi Q-Learning est-il considéré comme une méthode hors politique ?**
   - A. Il suit une politique unique pour la prise de décision
   - B. Il maximise les récompenses immédiates seulement
   - C. Il utilise une politique différente pour la prise d’action et la mise à jour
   - D. Il fonctionne sans connaître les états de l'environnement

10. **Dans Q-Learning, la mise à jour des valeurs est basée sur :**
    - A. L'action réellement entreprise
    - B. La moyenne des actions de l'état suivant
    - C. La valeur maximale de l'état suivant
    - D. La somme des valeurs de tous les états

11. **Que signifie "TD" dans l'apprentissage TD(0) ?**
    - A. Temps différentiel
    - B. Taux de décroissance
    - C. Différence temporelle
    - D. Décision temporelle

12. **Dans une politique epsilon-greedy, que signifie un epsilon proche de 0 ?**
    - A. L'agent explore fréquemment de nouvelles actions
    - B. L'agent exploite souvent les meilleures actions
    - C. L'agent ne prend que des actions aléatoires
    - D. L'agent ignore les valeurs de récompense

13. **Quelle affirmation est vraie concernant les méthodes TD ?**
    - A. Elles nécessitent des épisodes complets
    - B. Elles mettent à jour les estimations après chaque action
    - C. Elles nécessitent un modèle de transition
    - D. Elles ignorent la fonction de récompense

14. **Laquelle de ces méthodes utilise la valeur Q maximale pour la mise à jour ?**
    - A. SARSA
    - B. Q-Learning
    - C. TD(0)
    - D. Monte Carlo

15. **Quelle est la fonction de la variable $$\epsilon$$ dans une politique epsilon-greedy ?**
    - A. Réduire le facteur d'actualisation
    - B. Déterminer le taux d'apprentissage
    - C. Contrôler la probabilité d'exploration
    - D. Fixer la récompense à chaque étape

16. **Dans SARSA, que représente le terme $$ Q(S_{t+1}, A_{t+1}) $$ ?**
    - A. La valeur Q de l'action optimale à l'état suivant
    - B. La récompense cumulée à la fin de l'épisode
    - C. La valeur Q de l'action choisie par la politique à l'état suivant
    - D. La somme de toutes les valeurs Q précédentes

17. **Dans Q-Learning, le terme $$ \max_{a'} Q(S_{t+1}, a') $$ signifie :**
    - A. La moyenne des valeurs Q dans l'état suivant
    - B. La récompense de la prochaine action
    - C. La valeur maximale des actions possibles dans l'état suivant
    - D. La valeur Q minimale de l'état suivant

18. **En apprentissage hors politique, l'agent :**
    - A. Suit la même politique pour le comportement et la mise à jour
    - B. Utilise une politique de comportement différente de la politique de mise à jour
    - C. Ne met jamais à jour ses valeurs Q
    - D. Se base uniquement sur des épisodes complets

19. **Quel est l'effet de choisir un taux d'apprentissage ($$\alpha$$) très élevé ?**
    - A. Les valeurs Q convergent rapidement et restent stables
    - B. Les valeurs Q peuvent devenir instables et ne pas converger
    - C. Les valeurs Q sont ignorées
    - D. L'agent devient plus explorateur

20. **Dans SARSA, l'agent met à jour ses valeurs Q en fonction :**
    - A. De l'action optimale dans l'état suivant
    - B. De l'action réellement prise par la politique dans l'état suivant
    - C. De la moyenne des actions de l'état suivant
    - D. De l'intervalle de temps entre les actions

