


# Annexe 1 - Value-based VS Policy-based


## Méthodes basées sur la valeur (Value-based)

Les méthodes basées sur la valeur se concentrent sur l'estimation de la "valeur" de chaque état ou paire état-action dans l'environnement. Cette valeur représente la récompense totale attendue à partir de cet état ou de cette action.

**Caractéristiques principales :**

- Apprennent une fonction de valeur qui estime la récompense future pour chaque état ou paire état-action
- Utilisent cette fonction de valeur pour dériver une politique optimale
- Conviennent mieux aux espaces d'action discrets
- Nécessitent souvent des stratégies d'exploration explicites (comme ε-greedy)

**Exemples d'algorithmes :**
- Q-Learning
- Deep Q-Network (DQN)
- SARSA

## Méthodes basées sur la politique (Policy-based)

Les méthodes basées sur la politique apprennent directement la meilleure action à prendre dans chaque état, sans passer par l'estimation d'une fonction de valeur intermédiaire.

**Caractéristiques principales :**

- Apprennent directement une politique optimale
- Peuvent gérer naturellement les espaces d'action continus
- Intègrent souvent l'exploration dans la politique stochastique
- Garantissent généralement au moins une convergence vers un optimum local

**Exemples d'algorithmes :**
- REINFORCE
- Actor-Critic
- Proximal Policy Optimization (PPO)

## Principales différences

1. **Approche d'apprentissage :**
   - Value-based : Apprennent indirectement une politique via une fonction de valeur
   - Policy-based : Apprennent directement une politique optimale

2. **Représentation :**
   - Value-based : Estiment la valeur des états ou des actions
   - Policy-based : Modélisent directement la distribution de probabilité des actions

3. **Exploration :**
   - Value-based : Nécessitent souvent des stratégies d'exploration explicites
   - Policy-based : Peuvent intégrer l'exploration dans la politique stochastique

4. **Espace d'action :**
   - Value-based : Plus adaptées aux espaces d'action discrets
   - Policy-based : Peuvent gérer naturellement les espaces d'action continus

5. **Stabilité et convergence :**
   - Value-based : Peuvent avoir des problèmes de convergence dans certains cas
   - Policy-based : Généralement plus stables et garantissent au moins une convergence vers un optimum local

6. **Complexité de mise en œuvre :**
   - Value-based : Souvent plus simples à implémenter pour des problèmes de base
   - Policy-based : Peuvent être plus complexes mais offrent plus de flexibilité

Le choix entre ces deux approches dépend souvent de la nature spécifique du problème à résoudre, de la complexité de l'environnement et des objectifs de l'agent.


# Annexe 2 - Explication simplifiée de la différence entre **Value-Based** et **Policy-Based** en apprentissage par renforcement.

### 1. **Value-Based : On apprend combien une action vaut**
Imagine que tu joues à un jeu, et tu veux savoir si une action est bonne ou mauvaise. Dans l'approche **Value-Based**, tu vas essayer d’**évaluer chaque action** en fonction de la récompense totale que tu pourrais obtenir en la choisissant. 

- **Exemple** : Si tu joues à un jeu vidéo, tu calcules combien de points tu gagneras (ou perdras) si tu choisis de tourner à gauche ou à droite. Tu **choisis alors l’action** qui semble rapporter le plus de points. 
- **But** : Tu ne cherches pas directement à savoir quoi faire, mais tu essaies d'apprendre la "valeur" de chaque action et ensuite, tu choisis celle qui semble la meilleure. C’est comme si tu faisais des tests pour voir quelle action te rapporte le plus.

### 2. **Policy-Based : On apprend directement quoi faire**
Dans l’approche **Policy-Based**, tu ne te soucies pas de savoir combien vaut chaque action, mais tu apprends directement **quelle est la meilleure action à prendre** dans chaque situation. Ici, tu n’évalues pas chaque action, tu **te concentres directement sur la meilleure stratégie**.

- **Exemple** : Dans un jeu vidéo, au lieu de calculer combien de points tu vas gagner à chaque action (tourner à gauche ou à droite), tu apprends directement qu'il faut tourner à gauche pour gagner le jeu. Tu construis une sorte de plan d'action optimal sans tester chaque option.

### Résumé
- **Value-Based** : Tu testes différentes actions et apprends combien elles valent, puis tu choisis celle qui semble la meilleure.
- **Policy-Based** : Tu apprends directement la meilleure stratégie sans passer par l'évaluation de chaque action.

En gros, **Value-Based** te fait dire "Quel est le meilleur choix ici ?" alors que **Policy-Based** te fait dire "Voilà ce que je dois faire dans cette situation !"


# Annexe 3 - Résumé


### Différence entre **Value-Based** et **Policy-Based** en Apprentissage par Renforcement

1. **Value-Based (ex: Q-Learning)** :
   - **But** : Apprendre une **fonction de valeur** qui évalue les actions en termes de récompense attendue.
   - **Question** : *Comment* l'agent doit-il se comporter dans un état donné ?
   - **Objectif** : Maximiser la récompense totale en optimisant indirectement la politique. La politique découle de la fonction de valeur.

2. **Policy-Based** :
   - **But** : Apprendre directement une **politique optimale** qui dicte les actions à prendre.
   - **Question** : *Quelle* est la meilleure action à prendre dans un état donné ?
   - **Objectif** : Optimiser la politique directement, sans passer par une fonction de valeur.

En résumé : **Value-Based** optimise la politique via la fonction de valeur, tandis que **Policy-Based** optimise directement la politique.
