
-----------------------
# Structure
-----------------------

```
DQN/
├── utils.py
│   ├── plot_learning_curve : Trace les courbes d'apprentissage (epsilon, score).
│   ├── RepeatActionAndMaxFrame : Wrapper pour répéter les actions et empiler les frames.
│   ├── PreprocessFrame : Convertit les frames en niveaux de gris, redimensionne et normalise.
│   ├── StackFrames : Empile plusieurs frames pour capturer le mouvement.
│   └── make_env : Combine les wrappers pour configurer l'environnement de jeu.
├── replay_memory.py
│   ├── ReplayBuffer : Stocke les expériences de l'agent (état, action, récompense, état suivant, done).
│   └── sample_buffer : Tire des échantillons aléatoires pour l'entraînement.
├── dqn_agent.py
│   ├── DQNAgent : Classe principale implémentant l'algorithme Deep Q-Learning.
│   ├── choose_action : Choisit une action avec la stratégie epsilon-greedy.
│   ├── learn : Entraîne l'agent avec le buffer de replay et les mises à jour Q-learning.
│   ├── store_transition : Enregistre les expériences dans le buffer de replay.
│   └── replace_target_network : Met à jour le réseau Q cible.
├── deep_q_network.py
│   ├── DeepQNetwork : Définit le réseau neuronal pour l'approximation des Q-valeurs.
│   ├── Couches : Convolutives (Conv2D) et entièrement connectées pour l'extraction des caractéristiques.
│   └── save_checkpoint/load_checkpoint : Sauvegarde et charge les poids du modèle.
├── main_dqn.py
│   ├── Initialise l'environnement avec make_env.
│   ├── Crée un agent (DQNAgent).
│   ├── Boucle d'entraînement pour un nombre spécifié de parties.
│   └── Sauvegarde les progrès (métriques, checkpoints du modèle).
├── tf2/
│   ├── agent.py : Implémentation de DQNAgent avec TensorFlow.
│   ├── network.py : Définition du réseau neuronal avec TensorFlow/Keras.
│   ├── replay_memory.py : Implémente le buffer de replay avec TensorFlow.
│   └── utils.py : Gère la mémoire GPU et fournit des outils de visualisation.
├── test_env.py
│   ├── Joue des parties tests dans l'environnement pour vérifier la configuration.
│   └── Affiche les scores et rend le jeu en option.
```

### Concepts clés
- **utils.py** : Prétraitement de l'environnement et visualisation.
- **replay_memory.py** : Stockage et échantillonnage des expériences.
- **dqn_agent.py** : Implémente l'algorithme Deep Q-Learning.
- **deep_q_network.py** : Réseau neuronal pour la prédiction des Q-valeurs.
- **main_dqn.py** : Relie tous les éléments pour l'entraînement et l'évaluation.




