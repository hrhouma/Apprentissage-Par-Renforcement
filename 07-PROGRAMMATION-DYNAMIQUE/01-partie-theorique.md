# Cours : Programmation Dynamique et Apprentissage par Renforcement

---

#### Table des matières

1. [Introduction à la Programmation Dynamique (DP)](#introduction-dp)
2. [Estimation de l'Espérance](#estimation-esperance)
3. [Les Algorithmes de Programmation Dynamique](#algorithmes-dp)
4. [Itération de Valeur et Itération de Politique](#iteration-valeur-politique)
5. [DP Synchrone vs Asynchrone](#dp-synchrone-asynchrone)
6. [Estimation Monte Carlo des Valeurs d'Action](#estimation-monte-carlo)
7. [Approche de l'Apprentissage par Différence Temporelle (TD)](#apprentissage-td)
8. [Classification des Méthodes de Contrôle TD](#controle-td)
9. [Résumé et Récapitulatif](#resume)

---

<a name="introduction-dp"></a>
### 1. Introduction à la Programmation Dynamique (DP)

La **programmation dynamique** est une méthode pour résoudre des problèmes complexes en les décomposant en sous-problèmes plus simples. En mémorisant les résultats des calculs précédents, on économise du temps et des ressources.

#### Approches principales de DP :
1. **L'itération de la politique (Policy Iteration)** : On évalue une stratégie de manière répétée et on la modifie jusqu'à obtenir la meilleure stratégie.
2. **L'itération de la valeur (Value Iteration)** : On ajuste directement la "valeur" de chaque choix pour déterminer la meilleure décision dans chaque situation.

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="estimation-esperance"></a>
### 2. Estimation de l'Espérance

L'**espérance** d'une variable aléatoire \( X \) est la moyenne pondérée des valeurs possibles de \( X \), chaque valeur étant pondérée par sa probabilité d’occurrence. Elle est notée :

$$
E(X) = \sum_{i} x_i \cdot P(X = x_i)
$$

#### Points clés :
- Représente la valeur moyenne attendue.
- Fournit une estimation sur ce à quoi s'attendre si l’événement est répété plusieurs fois.

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="algorithmes-dp"></a>
### 3. Les Algorithmes de Programmation Dynamique

#### 1. Évaluation de politique (Policy Evaluation)
Évalue combien de récompenses on peut espérer en suivant une politique donnée dans chaque état :

$$
V_{\pi}(s) = \sum_{a} \pi(a|s) \sum_{s', r} P(s', r | s, a) \left[ r + \gamma V_{\pi}(s') \right]
$$

#### 2. Amélioration de politique (Policy Improvement)
Modifie la politique en choisissant les actions qui maximisent les récompenses :

![image](https://github.com/user-attachments/assets/d2531c5f-e343-46c9-a20c-262e3773d6b4)


### Explication

- **$$\pi'(s)$$** : Représente la nouvelle politique améliorée pour l'état $$s$$.
- **$$\text{argmax}_a$$** : Indique que l'on choisit l'action $$a$$ qui maximise l'expression suivante.
- **$$\sum_{s'} P(s'|s, a)$$** : Somme sur tous les états suivants $$s'$$, pondérée par la probabilité de transition $$P(s'|s, a)$$.
- **$$ R(s, a, s') + \gamma V_{\pi}(s') $$** : Représente la récompense immédiate $$R(s, a, s')$$ plus la valeur actualisée de l'état suivant $$V_{\pi}(s')$$, où $$\gamma$$ est le facteur de réduction des récompenses futures.



#### 3. Itération de politique (Policy Iteration)
Combine les étapes d’évaluation et d’amélioration de politique jusqu'à convergence vers une politique optimale.

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="iteration-valeur-politique"></a>
### 4. Itération de Valeur et Itération de Politique

#### Itération de Valeur
L'itération de valeur met à jour les valeurs d’états de manière itérative :

$$
V(s) = \max_a \sum_{s'} P(s'|s, a) \left[ R(s, a, s') + \gamma V(s') \right]
$$

#### Itération de Politique
Alternance entre l'évaluation et l'amélioration de politique pour converger vers une politique optimale.

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="dp-synchrone-asynchrone"></a>
### 5. DP Synchrone vs Asynchrone

- **Synchrone** : Mise à jour simultanée de toutes les valeurs d’état, coûteuse si le nombre d’états est élevé.
- **Asynchrone** : Mise à jour individuelle et aléatoire des états, ce qui réduit la complexité de calcul.

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="estimation-monte-carlo"></a>
### 6. Estimation Monte Carlo des Valeurs d'Action

Monte Carlo estime les valeurs des actions en fonction des expériences. Deux cas :
- **Avec Modèle** : Les valeurs d’état suffisent pour décider de la politique.
- **Sans Modèle** : Les valeurs d'action sont explicitement estimées pour chaque paire état-action.

#### Problème d'Évaluation des Politiques pour les Valeurs d'Action

$$
Q(s, a) = E_{\pi} \left[ \sum_{t=0}^{\infty} \gamma^t R_{t+1} | s_0 = s, a_0 = a \right]
$$

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="apprentissage-td"></a>
### 7. Approche de l'Apprentissage par Différence Temporelle (TD)

Le TD combine des éléments des méthodes Monte Carlo et de la programmation dynamique. La mise à jour est effectuée à chaque étape d'une séquence :

$$
V(S_t) \leftarrow V(S_t) + \alpha \left( R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right)
$$

où \( \alpha \) est le taux d'apprentissage, \( \gamma \) est le facteur de discount.

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="controle-td"></a>
### 8. Classification des Méthodes de Contrôle TD

#### SARSA (State-Action-Reward-State-Action)
Méthode on-policy qui met à jour la valeur d’action en suivant la politique actuelle :

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left( R_{t+1} + \gamma Q(S_{t+1}, A_{t+1}) - Q(S_t, A_t) \right)
$$

#### Q-Learning
Méthode off-policy qui utilise l'action avec la valeur \( Q \) maximale dans le nouvel état :

$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left( R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right)
$$

> **Retour à la [Table des matières](#table-des-matières)**

---

<a name="resume"></a>
### 9. Résumé et Récapitulatif

Ce cours couvre :
- Les principes de la **programmation dynamique**, y compris l'itération de politique et de valeur.
- La **méthode Monte Carlo** pour l'estimation des valeurs d'action.
- Les méthodes TD : **SARSA** (on-policy) et **Q-Learning** (off-policy).

> **Retour à la [Table des matières](#table-des-matières)**


# Annexe - Équations refactorisées avec \(1 - \alpha\)

1. **Mise à jour de la Valeur d'État (TD)**

L'équation standard de mise à jour de la valeur d'état est :
$$
V(S_t) \leftarrow V(S_t) + \alpha \left( R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right)
$$

Refactorisée avec \(1 - \alpha\) :
$$
V(S_t) \leftarrow (1 - \alpha) V(S_t) + \alpha \left( R_{t+1} + \gamma V(S_{t+1}) \right)
$$

2. **SARSA (State-Action-Reward-State-Action)**

L'équation SARSA pour la mise à jour de \(Q\)-valeur est :
$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left( R_{t+1} + \gamma Q(S_{t+1}, A_{t+1}) - Q(S_t, A_t) \right)
$$

Refactorisée avec \(1 - \alpha\) :
$$
Q(S_t, A_t) \leftarrow (1 - \alpha) Q(S_t, A_t) + \alpha \left( R_{t+1} + \gamma Q(S_{t+1}, A_{t+1}) \right)
$$

3. **Q-Learning**

L'équation de Q-Learning pour la mise à jour de \(Q\)-valeur est :
$$
Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha \left( R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) - Q(S_t, A_t) \right)
$$

Refactorisée avec \(1 - \alpha\) :
$$
Q(S_t, A_t) \leftarrow (1 - \alpha) Q(S_t, A_t) + \alpha \left( R_{t+1} + \gamma \max_{a} Q(S_{t+1}, a) \right)
$$


