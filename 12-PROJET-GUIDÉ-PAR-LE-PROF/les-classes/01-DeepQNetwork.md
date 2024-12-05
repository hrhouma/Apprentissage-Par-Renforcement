

### **Classe `DeepQNetwork`**
Cette classe définit un réseau de neurones convolutif (CNN) utilisé pour approximations des valeurs Q dans un algorithme DQN. Le réseau apprend à mapper les états du jeu à des actions optimales.

---

#### **Diagramme ASCII de la classe `DeepQNetwork`**
```
+------------------------------------------------------+
|                 DeepQNetwork(nn.Module)             |
+------------------------------------------------------+
| Attributes:                                         |
| - checkpoint_dir: str (répertoire des checkpoints) |
| - checkpoint_file: str (fichier checkpoint)        |
| - conv1: nn.Conv2d (1ère couche convolutionnelle)  |
| - conv2: nn.Conv2d (2ème couche convolutionnelle)  |
| - conv3: nn.Conv2d (3ème couche convolutionnelle)  |
| - fc1: nn.Linear (couche entièrement connectée)    |
| - fc2: nn.Linear (sortie avec n_actions)           |
| - optimizer: optim.RMSprop (optimiseur)            |
| - loss: nn.MSELoss (fonction de perte)             |
| - device: T.device (CPU ou GPU utilisé)            |
+------------------------------------------------------+
| Methods:                                           |
| - __init__: Initialise le réseau                   |
| - calculate_conv_output_dims: Calcule les sorties  |
| - forward: Propagation avant (feedforward)         |
| - save_checkpoint: Sauvegarde du modèle           |
| - load_checkpoint: Chargement du modèle           |
+------------------------------------------------------+
```

---

#### **Attributs**

1. **`checkpoint_dir` et `checkpoint_file`**
   - Utilisés pour sauvegarder ou charger les paramètres du modèle.
   - `checkpoint_dir` est le dossier, et `checkpoint_file` est le chemin complet vers le fichier.

2. **Convolutions (`conv1`, `conv2`, `conv3`)**
   - Ces couches extraient des caractéristiques à partir des états (images du jeu) en appliquant des filtres convolutifs.
   - Chaque couche réduit la taille des entrées tout en augmentant la profondeur pour capturer les motifs.

3. **Fully Connected Layers (`fc1`, `fc2`)**
   - **`fc1`** : Transforme les caractéristiques extraites en vecteurs de taille fixe.
   - **`fc2`** : Produit un vecteur de taille `n_actions`, représentant les valeurs Q pour chaque action possible.

4. **Optimiseur (`optimizer`)**
   - Utilise **RMSprop** pour ajuster les poids du réseau.
   - Apprend à réduire la fonction de perte.

5. **Fonction de Perte (`loss`)**
   - Utilise une perte quadratique moyenne (**MSELoss**) pour comparer les valeurs Q estimées avec les cibles calculées.

6. **Appareil (`device`)**
   - Définit si le modèle utilise le **GPU** ou le **CPU**.
   - Facilite le transfert automatique vers le bon appareil.

---

#### **Méthodes**

1. **`__init__(self, lr, n_actions, name, input_dims, chkpt_dir)`**
   - Initialise les couches convolutionnelles et entièrement connectées.
   - Prépare l’optimiseur et la fonction de perte.
   - Configure le chemin pour sauvegarder les checkpoints.

   **Entrées :**
   - `lr` : Taux d’apprentissage.
   - `n_actions` : Nombre total d’actions possibles.
   - `input_dims` : Dimensions de l’entrée (canaux, hauteur, largeur).
   - `name` : Nom du fichier checkpoint.
   - `chkpt_dir` : Répertoire pour sauvegarder les checkpoints.

---

2. **`calculate_conv_output_dims(self, input_dims)`**
   - Calcule la sortie des couches convolutives en fonction de l’entrée.
   - Utilise des tenseurs factices pour estimer les dimensions après convolutions.

   **Fonctionnement :**
   - Passe un tenseur d’entrée (taille zéro) à travers `conv1`, `conv2`, `conv3`.
   - Retourne le produit des dimensions (hauteur × largeur × filtres).

---

3. **`forward(self, state)`**
   - Effectue une propagation avant pour prédire les valeurs Q des actions.

   **Étapes :**
   - Passe l’état (image du jeu) à travers :
     1. `conv1`, suivi de l’activation ReLU.
     2. `conv2`, suivi de l’activation ReLU.
     3. `conv3`, suivi de l’activation ReLU.
   - Aplatie la sortie convolutive.
   - Applique `fc1` (ReLU) pour créer un vecteur caché.
   - Applique `fc2` pour produire les valeurs Q.

---

4. **`save_checkpoint(self)`**
   - Sauvegarde les paramètres du modèle (poids et biais) dans un fichier.
   - Utilise `torch.save` pour écrire dans le chemin `self.checkpoint_file`.

---

5. **`load_checkpoint(self)`**
   - Charge les paramètres du modèle à partir du fichier checkpoint.
   - Utilise `torch.load` pour récupérer les poids.

---

### **Résumé des couches et de leur fonction**

| Couche      | Type            | Fonction                                                                                     |
|-------------|-----------------|---------------------------------------------------------------------------------------------|
| `conv1`     | Convolution 2D  | Extraire des motifs simples (bords, formes basiques) dans les images d’entrée.              |
| `conv2`     | Convolution 2D  | Identifier des motifs plus complexes (textures, zones d’intérêt).                          |
| `conv3`     | Convolution 2D  | Combiner les motifs pour comprendre des structures significatives.                         |
| `fc1`       | Fully Connected | Intègre les caractéristiques extraites pour produire une représentation dense.             |
| `fc2`       | Fully Connected | Génère les valeurs Q, une pour chaque action possible.                                      |

---

### **Pourquoi cette architecture est efficace ?**
1. **Traitement visuel** :
   - Les convolutions simplifient les données complexes (images) en caractéristiques significatives.

2. **Généralisation** :
   - Les couches entièrement connectées permettent d’associer ces caractéristiques à des actions optimales.

3. **Flexibilité** :
   - Convient pour des jeux où l’observation est visuelle (comme Pong).

4. **Rendement** :
   - Optimiseur RMSprop avec MSELoss permet un entraînement stable.


# Annexe : **Code  et explication des composants :**

#### **Importations :**
```python
import os
import torch as T
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim
import numpy as np
```
- **`os`** : Gère les chemins de fichiers pour les checkpoints.
- **`torch`** : Framework de deep learning utilisé pour construire et entraîner le modèle.
- **`torch.nn`** : Contient les modules nécessaires pour construire des couches neurales (comme convolutions, fully connected, etc.).
- **`torch.nn.functional`** : Fournit des fonctions d'activation comme `relu`.
- **`torch.optim`** : Fournit des optimisateurs comme RMSprop.
- **`numpy`** : Utilisé pour les opérations mathématiques, notamment pour manipuler les tenseurs ou calculer des dimensions.

---

### **Classe `DeepQNetwork` :**
```python
class DeepQNetwork(nn.Module):
```
- Hérite de **`torch.nn.Module`**, ce qui permet d'utiliser toutes les fonctionnalités de PyTorch pour définir et entraîner un réseau de neurones.

---

#### **Méthodes et fonctions :**

##### **1. `__init__` : Constructeur**
```python
def __init__(self, lr, n_actions, name, input_dims, chkpt_dir):
```
- Initialise les paramètres et les couches du réseau.
- **Paramètres** :
  - `lr` : Taux d'apprentissage (learning rate).
  - `n_actions` : Nombre d'actions possibles (sorties du réseau).
  - `name` : Nom du fichier de checkpoint.
  - `input_dims` : Dimensions de l'entrée (ex. : canaux, hauteur, largeur des images).
  - `chkpt_dir` : Répertoire pour sauvegarder les checkpoints.
- **Tâches réalisées** :
  - Création des couches convolutives et entièrement connectées.
  - Initialisation de l'optimiseur et de la fonction de perte.
  - Configuration de l'appareil d'entraînement (GPU ou CPU).

---

##### **2. `calculate_conv_output_dims` : Calcul des dimensions de sortie des convolutions**
```python
def calculate_conv_output_dims(self, input_dims):
```
- Utilise un tenseur vide pour simuler le passage à travers les couches convolutives (`conv1`, `conv2`, `conv3`).
- Retourne la dimension totale (produit des dimensions de sortie) après convolutions.

---

##### **3. `forward` : Propagation avant**
```python
def forward(self, state):
```
- Définit la logique de passage avant du réseau.
- **Étapes** :
  1. Les données passent à travers les trois couches convolutives, avec une activation ReLU après chaque couche.
  2. Les sorties convolutives sont aplaties (réduction en un vecteur).
  3. Le vecteur aplati passe dans deux couches entièrement connectées (`fc1` et `fc2`).
  4. La dernière couche (`fc2`) génère un vecteur de taille `n_actions`, où chaque valeur correspond à une estimation Q pour une action.

---

##### **4. `save_checkpoint` : Sauvegarder le modèle**
```python
def save_checkpoint(self):
```
- Sauvegarde les paramètres du modèle dans un fichier défini par `self.checkpoint_file`.
- Utilise la méthode PyTorch `torch.save`.

---

##### **5. `load_checkpoint` : Charger le modèle**
```python
def load_checkpoint(self):
```
- Charge les paramètres du modèle à partir d'un fichier de checkpoint.
- Utilise la méthode PyTorch `torch.load`.

---

### **Visualisation ASCII des relations :**

```
+------------------------------------------+
|          Classe: DeepQNetwork            |
+------------------------------------------+
|                  Attributs               |
| - conv1: nn.Conv2d (8 filtres, stride=4) |
| - conv2: nn.Conv2d (64 filtres, stride=2)|
| - conv3: nn.Conv2d (64 filtres, stride=1)|
| - fc1: nn.Linear (512 unités cachées)    |
| - fc2: nn.Linear (n_actions sorties)     |
| - optimizer: RMSprop                     |
| - loss: MSELoss                          |
| - checkpoint_file: Path to checkpoint    |
+------------------------------------------+
|                  Méthodes                |
| - __init__: Initialisation               |
| - calculate_conv_output_dims: Sortie conv|
| - forward: Propagation avant             |
| - save_checkpoint: Sauvegarde du modèle  |
| - load_checkpoint: Chargement du modèle  |
+------------------------------------------+
```

---

### **Lien avec l’apprentissage par renforcement :**

- **Entrées du réseau (`state`)** : Une image de l’environnement (par exemple, un frame du jeu Pong).
- **Sorties du réseau (`actions`)** : Estimation des valeurs Q pour chaque action possible.
  - Ex. : Si l’agent peut aller **haut**, **bas**, ou **rester immobile**, il y aura 3 valeurs Q correspondantes.
- Le réseau est entraîné pour minimiser l’écart entre les valeurs Q prédites et les valeurs Q cibles calculées à l’aide de l’équation de Bellman.

---

### **Pourquoi cette architecture ?**
1. **Convolutions pour la vision** :
   - Les couches convolutives extraient des caractéristiques utiles (balle, raquettes) à partir des frames du jeu.
2. **Fully Connected pour la décision** :
   - Les couches entièrement connectées transforment les caractéristiques en estimations des actions optimales.
3. **Optimisation efficace** :
   - L’optimiseur RMSprop réduit les oscillations dans l’apprentissage, surtout avec des gradients non stationnaires.
4. **Modularité** :
   - Le modèle est facile à sauvegarder, recharger et tester grâce aux fonctions de checkpoint intégrées.



