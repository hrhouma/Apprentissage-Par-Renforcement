# Exemples d'applications

| Méthode         | Caractéristiques                                        | Cas d'utilisation                                         | Exemple en Météo                                                | Exemple en Finance                         | Exemple en Santé                                         |
|-----------------|---------------------------------------------------------|-----------------------------------------------------------|------------------------------------------------------------------|-------------------------------------------|-----------------------------------------------------------|
| **TD(0)**       | - Utilise une seule étape pour la mise à jour.<br>- Mise à jour en temps réel sans attendre la fin de l'épisode.<br>- Approprié pour les tâches où l'environnement est stable. | - Utilisation lorsque des estimations rapides sont nécessaires.<br>- Environnements où les états changent rapidement mais sont liés à l'état précédent. | Prédiction de la météo du jour suivant en utilisant les conditions actuelles et les prévisions pour demain. | Prédiction du prix d'une action pour le lendemain en utilisant le cours actuel et les fluctuations immédiates. | Surveillance en temps réel de la fréquence cardiaque d'un patient, en se basant sur le dernier relevé pour prédire la valeur suivante. |
| **TD(1)**       | - Utilise deux étapes (récompenses immédiate et suivante).<br>- Permet une prise en compte des informations de deux transitions.<br>- Plus précis que TD(0), mais légèrement plus lent. | - Utilisation dans des environnements modérément dynamiques.<br>- Utile lorsque l'état actuel dépend des dernières deux transitions. | Prédiction de la météo à deux jours en prenant en compte la météo actuelle, celle prévue pour demain et après-demain. | Prédiction du cours d'une action à deux jours en utilisant la tendance du jour et celle prévue pour le lendemain. | Suivi de l'évolution de la température corporelle pour prédire les pics de fièvre dans les prochaines 48 heures. |
| **TD(2)**       | - Utilise trois étapes (récompenses des trois prochaines transitions).<br>- Meilleure précision que TD(0) et TD(1).<br>- Convient aux environnements où l'état actuel dépend de trois étapes. | - Environnements plus dynamiques où des informations de plusieurs transitions sont nécessaires.<br>- Cas où les dépendances s'étendent sur plusieurs étapes. | Prédiction de la météo pour trois jours en prenant en compte les prévisions pour aujourd'hui, demain et le jour suivant. | Estimation de la volatilité d'un actif financier sur trois jours, en utilisant les tendances des jours précédents. | Prédiction de la glycémie pour les patients diabétiques en tenant compte des trois dernières mesures de glucose. |
| **TD(n)**       | - Généralise le nombre de transitions prises en compte (paramètre \( n \)).<br>- Converge vers les méthodes de Monte Carlo lorsque \( n \to \infty \).<br>- Plus \( n \) est grand, plus la méthode devient précise mais lente. | - Environnements dynamiques nécessitant des prévisions à long terme.<br>- Utile pour des situations avec des dépendances complexes entre les états. | Prédiction de la météo pour une semaine en utilisant les données sur plusieurs jours consécutifs, afin de capturer des tendances météorologiques à long terme. | Prédiction des cours de la bourse sur une semaine, en utilisant les tendances sur plusieurs jours pour évaluer la probabilité d'une hausse ou baisse continue. | Anticipation des symptômes d'une maladie chronique en observant les tendances de l'état de santé du patient sur plusieurs jours. |
| **Monte Carlo** | - Utilise un épisode entier pour la mise à jour.<br>- Précision plus élevée car elle prend en compte l'ensemble du parcours.<br>- Converge vers la valeur réelle si un grand nombre d'épisodes est utilisé.<br>- Équivalent de TD(n) lorsque \( n \to \infty \). | - Utile dans des environnements où des données complètes sur les épisodes sont disponibles.<br>- Approprié pour des situations avec des épisodes indépendants et non trop longs. | Prédiction de la météo en analysant l'ensemble des tendances météorologiques sur une période complète (par exemple, toutes les données météorologiques d’une saison). | Estimation de la performance d’un portefeuille d’investissement en observant l’évolution complète sur un trimestre ou une année pour calculer les rendements moyens. | Évaluation de l'efficacité d'un traitement en suivant l'ensemble des symptômes et des signes vitaux d’un patient pendant un cycle de traitement. |
| **SARSA**       | - Méthode sur-politique.<br>- Met à jour la fonction de valeur en utilisant l'action choisie par la politique actuelle.<br>- Sensible aux changements dans la politique d'exploration. | - Environnements où la politique peut être conservatrice (peu d'exploration).<br>- Convient lorsque l'agent suit une politique stable et n'explore que rarement. | Prédiction de la météo avec une approche prudente : suit une politique conservatrice, par exemple en restant près de la moyenne historique pour éviter les erreurs. | Choix d'investissements sûrs et conservateurs en fonction de la politique d'investissement (ex. rester sur des obligations d'État). | Suivi des patients avec une politique conservatrice de traitement pour minimiser les risques de complications. |
| **Q-Learning**  | - Méthode hors-politique.<br>- Met à jour la fonction de valeur en utilisant l'action optimale dans l'état suivant.<br>- Apprentissage plus agressif que SARSA, plus explorateur. | - Environnements où l'agent peut explorer et profiter des récompenses maximales.<br>- Cas où des actions risquées peuvent apporter des bénéfices à long terme. | Prédiction de la météo en utilisant des modèles plus exploratoires : permet des prédictions basées sur des valeurs extrêmes, par exemple en anticipant des événements météorologiques rares. | Stratégie d'investissement agressive avec exploration des actions à forte volatilité pour maximiser les gains potentiels. | Traitement personnalisé basé sur des thérapies expérimentales pour des patients à haut risque ou en situation critique. |

### Explications des cas d'utilisation et des exemples dans différents domaines :



*Ces exemples concrets montrent comment chaque méthode peut être utilisée dans divers contextes, en fonction de la stabilité de l'environnement, du besoin d'exploration ou d'exploitation, et du niveau de risque acceptable.*



# exemples dans différents domaines :

- *TD(0)* : Convient aux prédictions en temps réel et aux environnements stables. Exemple en finance : utilisation du dernier cours pour prédire le cours de l'action le lendemain, sans tenir compte des variations précédentes.

-----

- *TD(1)* et *TD(2)* : Ces méthodes prennent en compte les transitions sur plusieurs étapes, ce qui les rend adaptées aux environnements avec des dynamiques modérées. Par exemple, en santé, TD(1) et TD(2) peuvent être utilisés pour surveiller des signes vitaux tels que la température ou la fréquence cardiaque en prenant en compte les dernières évolutions pour anticiper les changements.

-----
- *TD(n)* : En considérant un nombre plus important d’étapes, TD(n) est utile pour des prévisions sur une période prolongée. En logistique, par exemple, on pourrait utiliser TD(n) pour prédire les besoins en ressources ou les délais de livraison sur une semaine, en tenant compte des tendances récentes.

-----
- *SARSA* : Une approche plus conservatrice adaptée aux environnements où l’on veut minimiser les risques. Exemple en finance : choisir des investissements sûrs selon la politique actuelle d'investissement, en évitant des actions risquées et en privilégiant des valeurs stables.

-----
- *Q-Learning* : Plus exploratoire, adapté aux situations nécessitant une optimisation agressive. Exemple en santé : dans le cas de traitements personnalisés ou de thérapies expérimentales, Q-Learning peut explorer des options plus risquées pour maximiser les chances de succès chez les patients en situation critique.

-----
- *TD(n)* et *Monte Carlo* : Lorsque $$ n \to \infty $$, TD(n) se rapproche de Monte Carlo car il prend en compte toutes les étapes d’un épisode complet. Monte Carlo est donc considéré comme l’équivalent de TD(n) avec \( n \) tendant vers l'infini. Monte Carlo se distingue par sa précision accrue, mais il nécessite que chaque épisode soit complet avant d'effectuer une mise à jour, ce qui peut ralentir le processus d'apprentissage.

-----
- *Monte Carlo* : Requiert un épisode complet pour mettre à jour les estimations, ce qui permet d’obtenir une vision plus globale des effets cumulatifs des actions.
    - **En météo** : Utilisation pour analyser l'ensemble des données météorologiques sur une saison pour prédire les tendances saisonnières, comme les températures moyennes ou les précipitations totales.
    - **En finance** : Utilisation pour évaluer la performance d’un portefeuille en prenant en compte tous les rendements au cours d’une période complète, par exemple pour un trimestre ou une année entière.
    - **En santé** : Suivre un cycle complet de traitement pour évaluer l’efficacité d’une thérapie sur un patient en tenant compte de l'évolution des symptômes et des réactions aux médicaments sur toute la durée du traitement.






