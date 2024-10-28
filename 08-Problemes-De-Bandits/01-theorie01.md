# Cours : Les Problèmes de Bandits 

---

## Table des Matières

1. <a href="#intro">Introduction aux Problèmes de Bandits</a>
2. <a href="#principes-simples">Problèmes de Bandits Simples</a>
   - <a href="#principe-general">Principe Général des Problèmes de Bandits</a>
   - <a href="#applications-industrielles">Applications Industrielles des Bandits</a>
   - <a href="#algorithmes-principaux">Les Algorithmes Principaux des Bandits</a>
   - <a href="#comparaison-algorithmes">Comparaison des Algorithmes de Bandits</a>
   - <a href="#parametres-hyperparametres">Paramètres vs Hyper-paramètres</a>
3. <a href="#implementation">Implémentation des Algorithmes de Bandits Simples</a>
   - <a href="#simulation">Simulation de l’Environnement Statique et Processus Stochastiques</a>
   - <a href="#choix-algorithme">Principe de Sélection de l’Algorithme</a>
   - <a href="#algorithmes-valeur">Algorithmes de Bandits avec Fonctions de Valeurs</a>
   - <a href="#algorithmes-gradient">Algorithmes de Bandits par Gradients</a>
4. <a href="#problemes-complexes">Problèmes de Bandits Complexes</a>
   - <a href="#definition-complexes">Définition : Bandits Combinatoires et Contextuels</a>
   - <a href="#applications-complexes">Applications Industrielles des Bandits Complexes</a>
   - <a href="#defis-limites">Défis et Limites des Bandits Complexes</a>

---

## <a id="intro">1. Introduction aux Problèmes de Bandits</a>

Les **problèmes de bandits** sont des situations où l’on doit choisir parmi plusieurs options (ou actions) pour maximiser les récompenses. Un exemple classique est celui des **machines à sous** au casino : chaque machine (ou "bras") peut donner des gains, mais on ignore lequel est le plus rentable. Faut-il essayer de nouvelles machines (exploration) ou jouer sur celles qui ont donné des gains (exploitation) ?

➡️ [Revenir en haut](#)

---

## <a id="principes-simples">2. Problèmes de Bandits Simples</a>

### <a id="principe-general">2.1 Principe Général des Problèmes de Bandits</a>

Un problème de bandit classique consiste à choisir une action parmi plusieurs sans savoir d'avance quelle action rapportera le plus. Par exemple :
- Choisir quel article recommander à un utilisateur pour augmenter les clics.
- Décider quelles publicités afficher pour maximiser les ventes.

L’objectif est de maximiser la récompense totale en équilibrant **exploration** et **exploitation**. 

➡️ [Revenir en haut](#)

---

### <a id="applications-industrielles">2.2 Applications Industrielles des Bandits</a>

Les problèmes de bandits ont des applications concrètes dans :
- **Publicité en ligne** : montrer des annonces pertinentes pour obtenir plus de clics.
- **Recommandation de produits** : suggérer des produits basés sur les préférences utilisateur.

**Exemple** : Une plateforme de streaming choisit quel film recommander en fonction de ce que l’utilisateur a aimé dans le passé, cherchant ainsi à maximiser le temps passé à regarder.

➡️ [Revenir en haut](#)

---

### <a id="algorithmes-principaux">2.3 Les Algorithmes Principaux des Bandits</a>

Les algorithmes principaux pour résoudre les problèmes de bandits incluent :
- **ε-greedy** : choisit aléatoirement une action avec une probabilité ε, sinon exploite la meilleure action connue.
- **Upper Confidence Bound (UCB)** : favorise les actions moins explorées en ajoutant un "bonus d’exploration".
- **Thompson Sampling** : approche bayésienne, prend en compte l’incertitude et choisit l’action la plus prometteuse.

| Algorithme         | Description                                   |
|--------------------|-----------------------------------------------|
| ε-greedy           | Utilise la probabilité pour explorer ou exploiter.|
| UCB                | Ajoute un bonus pour les actions peu explorées. |
| Thompson Sampling  | Choisit l’action la plus prometteuse statistiquement. |

➡️ [Revenir en haut](#)

---

### <a id="comparaison-algorithmes">2.4 Comparaison des Algorithmes de Bandits</a>

Voici un tableau simplifié pour comparer ces algorithmes :

| Algorithme         | Avantages                   | Inconvénients                   |
|--------------------|-----------------------------|---------------------------------|
| ε-greedy           | Simple à mettre en place    | Peut sous-explorer certaines options |
| UCB                | Exploration intelligente    | Complexité calculatoire         |
| Thompson Sampling  | Bien adapté aux changements | Complexité d'implémentation     |

➡️ [Revenir en haut](#)

---

### <a id="parametres-hyperparametres">2.5 Paramètres vs Hyper-paramètres</a>

- **Paramètres** : Changent au cours de l’apprentissage (par exemple, les valeurs de récompense estimées pour chaque action).
- **Hyper-paramètres** : Fixés avant l’apprentissage (par exemple, le facteur ε dans l’algorithme ε-greedy).

➡️ [Revenir en haut](#)

---

## <a id="implementation">3. Implémentation des Algorithmes de Bandits Simples</a>

### <a id="simulation">3.1 Simulation de l’Environnement Statique et Processus Stochastiques</a>

Pour simuler un environnement statique, on peut créer des distributions de récompenses pour chaque action (bras de la machine à sous). Ces récompenses peuvent être générées aléatoirement pour chaque action, simulant ainsi un environnement incertain.

➡️ [Revenir en haut](#)

---

### <a id="choix-algorithme">3.2 Principe de Sélection de l’Algorithme</a>

1. **Définir l’objectif** : Maximiser les gains, minimiser les pertes.
2. **Analyser le Contexte** : Si les récompenses sont stables, un algorithme simple (comme ε-greedy) peut être suffisant.
3. **Choisir l'Algorithme** : Selon les besoins en exploration (choix d’actions nouvelles) et en exploitation (actions rentables connues).

➡️ [Revenir en haut](#)

---

### <a id="algorithmes-valeur">3.3 Algorithmes de Bandits avec Fonctions de Valeurs</a>

- **ε-greedy** : Exploite la meilleure action connue avec une probabilité \(1 - ε\), sinon explore une action au hasard.
- **UCB** : Utilise un bonus d’exploration pour inciter l’agent à tester les actions moins explorées.

➡️ [Revenir en haut](#)

---

### <a id="algorithmes-gradient">3.4 Algorithmes de Bandits par Gradients</a>

Les algorithmes de **bandits par gradients** optimisent directement la récompense en ajustant les préférences des actions en fonction des récompenses reçues. Ce type d’algorithme est courant dans les réseaux neuronaux et permet des ajustements subtils des préférences.

➡️ [Revenir en haut](#)

---

## <a id="problemes-complexes">4. Problèmes de Bandits Complexes</a>

### <a id="definition-complexes">4.1 Définition : Bandits Combinatoires et Contextuels</a>

- **Bandits Combinatoires** : Choix simultané de plusieurs actions (par exemple, sélectionner plusieurs annonces pour une page web).
- **Bandits Contextuels** : Utilisent des informations contextuelles (par exemple, historique de l’utilisateur) pour optimiser les choix.

➡️ [Revenir en haut](#)

---

### <a id="applications-complexes">4.2 Applications Industrielles des Bandits Complexes</a>

Exemples :
- **Systèmes de Recommandation** : Sélection de produits personnalisés.
- **Optimisation de la Chaîne d’Approvisionnement** : Choisir des fournisseurs optimaux selon plusieurs critères.

➡️ [Revenir en haut](#)

---

### <a id="defis-limites">4.3 Défis et Limites des Bandits Complexes</a>

| Défis                | Explications                                           |
|----------------------|--------------------------------------------------------|
| Grande dimensionnalité| Trop d’actions à explorer simultanément.               |
| Convergence lente    | Nécessite plus de données pour ajuster les récompenses.|

➡️ [Revenir en haut](#)

