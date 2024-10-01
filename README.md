# Apprentissage-Par-Renforcement

---------------------------------
# Séance 1 
---------------------------------

## Récap - théorie

- Mots clés liés aux processus de Markov dans le contexte de l’apprentissage par renforcement (RL) :

1. **Processus markovien** :
   - Un processus stochastique où la probabilité de transition vers l’état suivant ne dépend que de l’état actuel, et non de l’historique des états précédents (propriété de Markov).

2. **État (State)** :
   - La représentation actuelle d'une situation dans l'environnement. L'état contient toutes les informations nécessaires pour prendre une décision à ce moment-là.

3. **Récompense (Reward)** :
   - Un signal de rétroaction reçu après avoir exécuté une action dans un certain état. Il indique la qualité de l'action choisie.

4. **Environnement (Environment)** :
   - Le monde extérieur dans lequel l'agent évolue. C'est l'entité avec laquelle l'agent interagit en prenant des actions et en recevant des états et des récompenses.

5. **Agent** :
   - L’entité qui prend des décisions (choisit des actions) dans l’environnement dans le but d’optimiser une fonction de récompense.

6. **Action** :
   - Un choix fait par l’agent dans un certain état qui conduit à un nouvel état. L'agent choisit une action en fonction d'une **policy**.

7. **Policy (Politique)** :
   - Une règle ou une stratégie que l'agent suit pour choisir une action en fonction de l'état actuel. La politique peut être déterministe ou stochastique.

8. **Utilité (Utility)** :
   - La valeur attendue à long terme d’un état, souvent représentée par la somme pondérée des récompenses futures. Dans l'apprentissage par renforcement, cela peut correspondre à la **fonction de valeur**.

9. **Discount (Facteur d'actualisation)** :
   - Un facteur (généralement noté γ) utilisé pour réduire l’importance des récompenses futures par rapport aux récompenses immédiates. Il permet d’équilibrer l'exploration et l'exploitation des états.

Ces termes sont essentiels pour comprendre les bases de l'apprentissage par renforcement et comment un agent interagit avec son environnement dans le cadre des processus markoviens.

---------------------------
## Pratiques
----------------------------

- Pratique 01 dans le dossier 01-introduction-au-RL
- Pratique 02 dans le dossier 02-notions-RL
- Pratique 03 (Document 06-Discounting.md) dans le dossier 03-introduction au proccessus décisionnel de Markov
- Toutes les pratiques dans le dossier 04-EvaluationsFormatives
