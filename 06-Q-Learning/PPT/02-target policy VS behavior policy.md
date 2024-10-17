# Target policy VS behavior policy

En apprentissage par renforcement, la **target policy** et la **behavior policy** sont deux concepts importants, particulièrement dans les méthodes d'**apprentissage hors-policy** comme le Q-Learning.

# 1. **Behavior Policy (Politique de comportement)**

La **behavior policy** est la politique que l'agent suit pour explorer l'environnement. Elle définit la manière dont l'agent choisit ses actions pendant l'apprentissage. Son but principal est d'explorer l'environnement de manière efficace, en trouvant des informations sur les différentes actions possibles dans différents états. 

- **Objectif :** Explorer l'environnement et récolter des informations.
- **Exploration :** L'agent utilise souvent une stratégie d'exploration comme **ε-greedy**, qui permet de choisir parfois des actions aléatoires pour explorer de nouvelles possibilités (exploitation vs exploration).
- **Utilisation :** On utilise cette politique pour interagir avec l'environnement pendant l'entraînement.

# 2. **Target Policy (Politique cible)**

La **target policy** est la politique optimale ou la politique que l'agent cherche à apprendre. Elle définit les actions que l'agent devrait idéalement prendre pour maximiser la récompense à long terme. 

- **Objectif :** Maximiser la récompense totale.
- **Exploitation :** L'agent choisit les actions qui semblent les plus prometteuses pour maximiser la valeur (souvent basé sur une fonction de valeur comme \( V(s) \) ou \( Q(s, a) \)).
- **Utilisation :** Cette politique est celle que l'agent finit par utiliser une fois l'entraînement terminé (ou proche de la fin).

# **Différence clé :**

- **Behavior Policy** est utilisée pour explorer l'environnement et générer des expériences d'apprentissage.
- **Target Policy** est celle que l'agent cherche à apprendre et à optimiser pour maximiser les récompenses.

# Exemple :

Supposons que l'agent utilise une stratégie **ε-greedy** pour explorer l'environnement. Pendant 90 % du temps, il choisit l'action qui semble la meilleure (politique optimale), mais pendant 10 % du temps, il choisit une action aléatoire pour explorer de nouvelles options. 

- La **behavior policy** ici est la stratégie **ε-greedy** : elle permet à l'agent d'explorer et de découvrir de nouvelles actions.
- La **target policy** serait la politique purement **greedy** qui choisit toujours l'action la plus optimale (sans exploration), une fois que l'agent a appris la meilleure politique. 

En résumé, la **behavior policy** est utilisée pour **explorer**, et la **target policy** est utilisée pour **exploiter** les informations apprises et maximiser les récompenses.
