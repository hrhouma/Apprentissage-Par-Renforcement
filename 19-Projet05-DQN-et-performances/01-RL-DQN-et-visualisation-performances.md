# **Apprentissage par Renforcement pour l'Environnement CartPole : Entraînement DQN en Temps Réel avec Visualisations de Performances**

---

## **Objectif du Projet**  
📍 *Former un agent DQN pour équilibrer une tige sur un chariot dans l'environnement CartPole-v1, en utilisant l'apprentissage par renforcement.*

### **But Visé :**
🛠️ *Développer un agent capable de maximiser le temps d'équilibre en prenant des décisions intelligentes basées sur des observations.*

---

## **Approche Utilisée**  
🧠 **Algorithme :** DQN avec *replay d'expérience* et *politique epsilon-greedy*, implémenté avec TensorFlow dans l'environnement CartPole d'OpenAI Gym.  
💡 **Techniques Clés :** DQN, Replay d'expérience, Politique epsilon-greedy.

### **Étapes Principales de l'Apprentissage par Renforcement**  
1. 📝 **Formulation du Problème**  
   🔽

2. 🌍 **Création de l'Environnement**  
   🔽

3. 🎁 **Définition des Récompenses**  
   🔽

4. 🤖 **Création de l'Agent**  
   🔽

5. 🏋️ **Entraînement de l'Agent**  
   🔽

6. 🧪 **Validation de l'Agent**  
   🔽

7. 🚀 **Déploiement de la Politique**  

---

## **Configuration des Hyperparamètres**  
- **Gamma (γ)** : 0.95
- **Epsilon** : 1.0 (décroît avec le temps)
- **Décroissance d'Epsilon** : 0.995
- **Minimum d’Epsilon** : 0.01
- **Taux d'apprentissage (α)** : 0.001

---

## **Fonctionnement de l'Environnement CartPole**  
🛒 **Environnement :** OpenAI Gym  
🎯 **Objectif de l'agent :** Garder la tige en équilibre sur le chariot.  
🏆 **Récompense :** Points pour chaque pas où la tige reste en équilibre; pénalité pour échec.  

---

## **Processus Étape par Étape**  

1. **Formuler le Problème**  
   - Objectif : Maximiser le temps d'équilibre de la tige.
   
2. **Créer l'Environnement**  
   - Utiliser OpenAI Gym pour simuler l'environnement de CartPole.
   
3. **Définir les Récompenses**  
   - Récompense positive pour chaque moment où la tige est en équilibre.  

4. **Créer l'Agent**  
   - Construction d'un réseau neuronal pour prédire les actions.

5. **Entraîner l'Agent**  
   - Entraînement à partir des interactions et des expériences re-jouées.

6. **Valider l'Agent**  
   - Tester les performances de l'agent dans l'environnement.

7. **Déployer la Politique**  
   - Finaliser et appliquer la politique formée.

---

## **Comparaison : Apprentissage par Renforcement vs. IA Symbolique**  
| **Aspect** | **IA Symbolique** | **Apprentissage par Renforcement** |
|------------|--------------------|-------------------------------------|
| **Approche de résolution** | Raisonnement déductif, règles | Essai-erreur, basé sur les récompenses |
| **Quand les utiliser** | Lorsque les règles sont claires | Lorsque l'exploration est nécessaire |
| **Exemple** | Diagnostic médical (Mycin) | Tesla Autopilot |

---

## **Exemples d'Environnements et d'Objectifs d'Apprentissage**  

- **CartPole-v1** : Équilibrer une tige sur un chariot en mouvement.  
- **MountainCar-v0** : Conduire une voiture en utilisant la force pour grimper une colline.  
- **LunarLander-v2** : Atterrir une navette lunaire en utilisant le carburant de manière optimale.  
- **Breakout-v0** : Détruire des briques avec une balle, en optimisant la précision et les réflexes.

---

## **Structure de Récompenses par Environnement**  

| **Environnement**   | **Récompense Positive**                     | **Description**                               |
|---------------------|---------------------------------------------|-----------------------------------------------|
| CartPole-v0         | Pour chaque instant où la tige est stable   | Encourage une durée d'équilibre prolongée     |
| MountainCar-v0      | Pour atteindre le drapeau, négative par pas | Motive la montée vers l'objectif              |
| LunarLander-v2      | Pour atterrissage réussi, négative sinon    | Équilibre entre sécurité d'atterrissage et fuel |

---

## **Estimation des Coûts sur AWS SageMaker**  
💰 **Instance recommandée :** p3.2xlarge  
💲 **Coût horaire :** 3,825 $/h  
💸 **Coût mensuel (estimé en USD)** : 2206,40 $

---

## **Modèles Utilisés et Méthodes d'Évaluation**  
- **Modèles d'Apprentissage par Renforcement** :
  - DDPG (Deep Deterministic Policy Gradient)
  - PPO (Proximal Policy Optimization)
  - DQN (Deep Q-Network)
  
- **Méthodes d'Évaluation** :
  - **Récompense par Épisode** : Total de points accumulés.
  - **Taux de Succès** : Pourcentage d'objectifs atteints.
  - **Temps de Survie** : Temps avant l'échec de l'agent.
  

