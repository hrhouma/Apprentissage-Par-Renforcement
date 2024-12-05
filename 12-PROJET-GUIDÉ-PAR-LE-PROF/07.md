### Tutoriel détaillé : Comprendre les épisodes et les métriques dans l'apprentissage de DQN pour Pong

Dans ce tutoriel, nous allons explorer chaque élément des métriques affichées pendant l’entraînement d’un agent DQN (Deep Q-Network) pour jouer à Pong. Nous analyserons en profondeur les épisodes, les scores, les paramètres comme epsilon et steps, et leur rôle dans l’apprentissage.

---

### **1. Les Épisodes : Le cadre de l’apprentissage**

#### Qu’est-ce qu’un épisode ?
- Un **épisode** dans le contexte du jeu Pong correspond à une **partie complète**.
- Il débute quand la balle est lancée et se termine lorsqu’un joueur (l’agent ou l’adversaire) atteint **21 points**.
- Un épisode est une unité d’entraînement pour l’agent, où il joue et apprend de ses actions.

#### Exemple de résultat :
- **Score : -21.0** signifie que l’agent a perdu en encaissant 21 points avant de marquer quoi que ce soit.
- Si l’agent marque des points, le score final pourrait être, par exemple, **-10** (l’adversaire gagne 21 à 10).

---

### **2. Les Métriques affichées**

Les métriques servent à surveiller la progression de l’agent pendant l’entraînement. Voici une analyse détaillée de chacune :

#### **a) Le Score**
- **Définition** : C’est la différence entre les points marqués par l’agent et ceux marqués par l’adversaire à la fin de chaque épisode.
- **Valeurs négatives** :
  - Au début, l’agent perd souvent, donc les scores sont généralement autour de **-21**.
- **Objectif** : Rapprocher les scores de **0**, voire atteindre des scores positifs, indiquant que l’agent gagne.

Exemple :
```
Episode 1 : Score = -20.0
Episode 2 : Score = -21.0
Episode 3 : Score = -19.0
```
- Ces scores montrent que l’agent perd, mais il peut parfois réduire l’écart (par exemple, -19.0).

---

#### **b) Average Score**
- **Définition** : Moyenne mobile des scores des **100 derniers épisodes**.
- **Pourquoi ?**
  - Cette métrique lisse les fluctuations des scores individuels et montre une **tendance générale**.
- **Indicateur de progression** :
  - Si la moyenne passe de **-21.0** à **-18.5**, cela signifie que l’agent s’améliore.

Exemple :
```
Average Score = -20.0 (épisode 1)
Average Score = -20.3 (épisode 2)
Average Score = -20.5 (épisode 3)
```
- Ici, l’average score montre une dégradation légère, ce qui est normal dans les premières phases d’apprentissage.

---

#### **c) Epsilon (ε)**
- **Définition** : Paramètre clé dans la stratégie d’**epsilon-greedy**, qui détermine le comportement de l’agent.
  - **Exploration** : L’agent choisit une action **aléatoire**.
  - **Exploitation** : L’agent choisit l’action avec la meilleure valeur Q estimée (d’après ce qu’il a appris).
- **Valeurs initiales** :
  - Au début, epsilon est élevé (par exemple, **1.0 ou 0.98**), favorisant l’exploration.
- **Diminution progressive** :
  - Epsilon diminue (par exemple, **0.98 → 0.97 → 0.96**) pour encourager l’agent à exploiter ses connaissances au fur et à mesure qu’il apprend.

**Pourquoi epsilon est important ?**
- Exploration est essentielle pour découvrir de nouvelles stratégies et éviter que l’agent ne reste bloqué dans un comportement sous-optimal.
- Exploitation est cruciale pour maximiser les récompenses basées sur les apprentissages.

Exemple :
```
Episode 1 : Epsilon = 0.98
Episode 2 : Epsilon = 0.97
Episode 3 : Epsilon = 0.96
```
- Cela montre que l’agent réduit progressivement sa prise de risques.

---

#### **d) Steps**
- **Définition** : Nombre total d’actions prises par l’agent depuis le début de l’entraînement.
- **Pourquoi est-ce suivi ?**
  - Les steps augmentent avec chaque action effectuée, indiquant que l’agent accumule de l’expérience.
  - Ce n’est pas directement un indicateur de performance, mais cela montre la quantité d’interactions de l’agent avec l’environnement.

Exemple :
```
Steps (total) = 1923 (épisode 1)
Steps (total) = 2687 (épisode 2)
Steps (total) = 3629 (épisode 3)
```
- Plus le nombre de steps est élevé, plus l’agent a eu d’occasions d’apprendre.

---

### **3. Progression de l’apprentissage**

#### Étapes clés dans la progression de l’agent :
1. **Phase d’exploration initiale :**
   - L’agent joue de manière aléatoire, donc les scores restent faibles (souvent autour de **-21.0**).
   - Epsilon est élevé, ce qui favorise l’exploration.

2. **Accumulation d’expérience :**
   - L’agent stocke chaque expérience (état, action, récompense, nouvel état) dans une **mémoire replay**.
   - Il commence à apprendre en ajustant son réseau de neurones sur ces expériences.

3. **Phase de transition :**
   - Epsilon diminue progressivement, réduisant la quantité d’exploration aléatoire.
   - L’agent commence à exploiter ses apprentissages pour choisir des actions plus stratégiques.

4. **Amélioration des scores :**
   - Avec le temps, l’agent marque plus de points.
   - Les scores deviennent moins négatifs (par exemple, **-18.0**, **-15.0**) et peuvent devenir positifs à terme.

---

### **Illustration détaillée des métriques**

| **Métrique**      | **Signification**                                                                                             | **Exemple de progression**                 |
|--------------------|-------------------------------------------------------------------------------------------------------------|--------------------------------------------|
| **Score**          | Performance de l’agent dans un épisode.                                                                     | -21.0 → -20.0 → -19.0                      |
| **Average Score**  | Moyenne des 100 derniers scores.                                                                            | -20.0 → -20.3 → -20.5                      |
| **Epsilon (ε)**    | Niveau d’exploration (probabilité de choisir une action aléatoire).                                         | 0.98 → 0.97 → 0.96                         |
| **Steps**          | Nombre total d’actions effectuées par l’agent depuis le début de l’entraînement.                           | 1923 → 2687 → 3629                         |

---

### **4. Pourquoi ces scores négatifs sont normaux ?**

1. **Manque de stratégie initiale :**
   - L’agent commence avec aucune connaissance, donc ses actions sont presque aléatoires.
   - Il ne sait pas comment interagir efficacement avec la balle ou l’adversaire.

2. **Exploration aléatoire :**
   - Une grande partie des actions initiales sont aléatoires (epsilon élevé), ce qui conduit à des performances médiocres.

3. **Complexité du jeu :**
   - Pong est un jeu dynamique nécessitant des décisions rapides et précises.
   - L’agent doit apprendre non seulement à frapper la balle, mais aussi à anticiper les mouvements de l’adversaire.

---

### **5. Conclusion et clés pour l’amélioration**

- Les **scores négatifs constants** sont normaux dans les premiers épisodes d’entraînement.
- Avec le temps, l’agent accumule des expériences utiles dans sa mémoire replay.
- L’**epsilon décroissant** permet une transition entre exploration et exploitation.
- Les **steps croissants** montrent que l’agent continue de jouer et d’apprendre activement.

À terme, l’agent peut atteindre des scores positifs, surpassant l’adversaire et maîtrisant le jeu Pong !
