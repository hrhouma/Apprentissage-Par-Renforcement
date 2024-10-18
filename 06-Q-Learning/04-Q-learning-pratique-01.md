Chers étudiant.e.s,

Dans cette séance, vous allez travailler sur **quatre algorithmes de Q-Learning** appliqués au problème **MountainCar-v0**. Chaque algorithme est conçu pour vous permettre de **tester, comprendre et analyser** l'impact des **différents taux d'apprentissage (alpha)** dans l'entraînement d'un agent. 

L'objectif de cet exercice est de vous guider étape par étape à travers les différents algorithmes et de vous permettre de **visualiser les résultats** à travers des simulations et des graphiques.

---

## 📜 **Instructions Générales :**
1. **Clonez les quatre projets GitHub**.
2. **Exécutez les algorithmes** pour chacun des dépôts.
3. **Interprétez les résultats** à partir des simulations et des graphiques fournis.
4. **Posez-vous les bonnes questions** sur l'impact d'**alpha**, et tentez d'identifier les différences entre chaque version.

---

### **1 - RLCode2-1** :
- **Ce que fait l'algorithme :** 
  - Ce premier code utilise une **seule valeur de taux d'apprentissage (alpha = 0.5)**. Il entraîne un agent Q-Learning sur **2000 épisodes** et l'évalue sur **10 essais**. 
  - Vous observerez une simulation visuelle en **temps réel** de la voiture dans l'environnement **MountainCar-v0**. À la fin des essais, des **graphes récapitulatifs** affichent le succès de l'agent et le nombre de pas nécessaires.
- **Rendu visuel :** Oui.
- **Graphiques :** Oui (succès/échecs et nombre de pas).
  
**Commandes d'exécution :**
```bash
git clone https://github.com/hrhouma/RLCode2-1.git
cd RLCode2-1
pip install venv
# Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force 
python3.11 -m venv mountain_car_env
#source mountain_car_env/bin/activate
mountain_car_env\Scripts\activate
pip install -r requirements.txt
python main.py
deactivate
```

-------------------
# Troubleshooting
-------------------

#### 1 -  Exécutez le terminal en tant qu'administrateur
#### 2 -  La vesrsion de python utilisée dans le cadre de ce projet est la suivante Python 3.11.9

Si vous avez plusieurs versions de Python installées sur votre système et que vous souhaitez spécifiquement utiliser Python 3.11, exécutez la commande suivante pour créer un environnement virtuel avec cette version :

```bash
python3.11 -m venv mountain_car_env
```

### ==> Cela forcera l'utilisation de Python 3.11 pour l'environnement virtuel `mountain_car_env`."

![image](https://github.com/user-attachments/assets/52d8a2b1-fe5c-4bba-a42e-42171fd219fc)



#### 3 -  Vous pouvez avoir une erreur à cette étape (powershell)
  
```bash
mountain_car_env\Scripts\activate
```

### Voici l'erreur 

```bash
mountain_car_env\Scripts\activate
mountain_car_env\Scripts\activate : Impossible de charger le fichier
C:\Users\rehou\Documents\RLCode2-1\mountain_car_env\Scripts\Activate.ps1, car
l’exécution de scripts est désactivée sur ce système. Pour plus d’informations,
consultez about_Execution_Policies à l’adresse
https://go.microsoft.com/fwlink/?LinkID=135170.
Au caractère Ligne:1 : 1
+ mountain_car_env\Scripts\activate
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : Erreur de sécurité : (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

### Solution 

```bash
Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force
```

---

### **2 - RLCode2-2** :
- **Ce que fait l'algorithme :** 
  - Dans cette version, l'agent est **entraîné et évalué** avec plusieurs valeurs d'alpha : **0.1, 0.5, 0.9**.
  - Le programme affiche une **simulation en temps réel** où vous verrez plusieurs voitures (agents) bouger simultanément, chacune utilisant une valeur différente d'**alpha**.
  - Des **graphes récapitulatifs** à la fin montrent les **succès/échecs** ainsi que le **nombre moyen de pas** pour chaque alpha.
- **Rendu visuel :** Oui (affichage via `pygame`).
- **Graphiques :** Oui (récompenses, taux de succès, nombre moyen de pas).

**Commandes d'exécution :**
```bash
git clone https://github.com/hrhouma/RLCode2-2.git
cd RLCode2-2
python3 -m venv mountain_car
source mountain_car/bin/activate
pip install -r requirements.txt
python main1-pygame-alphas.py  # Avec rendu visuel
python main2-matplotlib-alphas.py  # Sans rendu visuel
deactivate
```

---

### **3 - RLCode2-3** :
- **Ce que fait l'algorithme :** 
  - Ce code exécute plusieurs expériences avec des valeurs d'**alpha** différentes : **0.1, 0.3, 0.5, 0.7, 0.9**.
  - Après chaque simulation, les résultats sont enregistrés dans un fichier **`.pkl`**. Ensuite, un second script génère des graphiques qui montrent l'impact des différentes valeurs d'**alpha** sur la **récompense moyenne** de l'agent.
  - C'est une version plus axée sur l'analyse post-entraînement, sans rendu visuel.
- **Rendu visuel :** Non.
- **Graphiques :** Oui (récompenses moyennes au fil des épisodes).

**Commandes d'exécution :**
```bash
git clone https://github.com/hrhouma/RLCode2-3.git
cd RLCode2-3
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python experiment.py
python visualize_results.py
deactivate
```

---

### **4 - RLCode2-4** :
- **Ce que fait l'algorithme :** 
  - Cette dernière version est similaire à **RLCode2-2**, mais elle **compare plusieurs valeurs d'alpha** en générant des visualisations à la fois **avec et sans rendu visuel**.
  - Chaque version teste différentes stratégies pour entraîner l'agent dans l'environnement **MountainCar**. 
  - Le programme compare les performances de l'agent avec des graphiques montrant le **nombre de pas nécessaires** pour atteindre le sommet ainsi que le **taux de succès**.
- **Rendu visuel :** Oui.
- **Graphiques :** Oui (nombre de pas, taux de succès).

**Commandes d'exécution :**
```bash
git clone https://github.com/hrhouma/RLCode2-4.git
cd RLCode2-4
python3 -m venv mountain_car
source mountain_car/bin/activate
pip install -r requirements.txt
python main.py
deactivate
```

---

## 📊 **Tableau comparatif des algorithmes :**

| **Version**       | **Rendu Visuel** | **Graphiques**           | **Alpha(s) Testé(s)**         | **Objectif Principal**                    |
|-------------------|------------------|--------------------------|-------------------------------|-------------------------------------------|
| **RLCode2-1**      | Oui              | Succès/Échecs, Pas        | α = 0.5                       | Démonstration avec un seul alpha.         |
| **RLCode2-2**      | Oui (Pygame)     | Succès/Échecs, Pas        | α = 0.1, 0.5, 0.9             | Comparaison avec plusieurs alphas.        |
| **RLCode2-3**      | Non              | Récompense Moyenne        | α = 0.1, 0.3, 0.5, 0.7, 0.9   | Comparaison des alphas via récompenses.   |
| **RLCode2-4**      | Oui              | Succès, Pas               | α multiples (à définir)        | Analyse combinée avec/sans visualisation. |

---

### 🎯 **Questions à vous poser :**

1. **Quel est l'impact d'alpha sur la performance de l'agent ?**
2. **Quelle valeur d'alpha donne les meilleurs résultats en termes de stabilité et de rapidité d'apprentissage ?**
3. **Quels sont les avantages et les inconvénients des différentes approches ?**

### 🔍 **Conclusion :**

Prenez le temps de bien comprendre chaque version, de tester les différents scripts, d’analyser les graphiques produits et de **comparer les performances**. N'oubliez pas de **documenter vos observations** et de **poser des questions** à la fin de chaque pratique.

Bonne chance à tous,  
**Votre professeur**
