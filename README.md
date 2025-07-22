# Classification binaire d’images avec minimisation du Half-Total Error Rate (HTER)

## 🎯 Objectif  
Développer un classifieur d’images binaire capable de minimiser le Half-Total Error Rate sur un dataset de 100k images d’entraînement et 20k images de validation.

---

## 🛠️ Méthodologie détaillée

### Préparation des données  
- Chargement des images depuis les dossiers `train_img` et `val_img`.  
- Lecture des labels binaires depuis `label_train.txt`.  
- Mise en forme des données en lots (batch) pour l’entraînement.  
- Application de **data augmentation** (rotations, flips horizontaux, zooms) pour enrichir le jeu d’entraînement et améliorer la généralisation.

### Modélisation  
- Utilisation de **modèles CNN pré-entraînés** (notamment VGG16 et MobileNetV2) via TensorFlow/Keras.  
- Remplacement de la tête (couche finale) du modèle par une architecture personnalisée : plusieurs couches denses avec activation ReLU, puis une couche finale sigmoïde pour la classification binaire.  
- Compilation avec la fonction de perte **Binary Crossentropy** et métriques adaptées.

### Entraînement  
- Fine-tuning sur les données d’entraînement avec validation sur un sous-ensemble.  
- Early stopping pour éviter le sur-apprentissage (overfitting).  
- Suivi des courbes de perte et métriques (accuracy, précision, rappel).

### Ensemble learning et fusion des modèles  
- Observation que chaque modèle a des biais différents (certains prédisaient plus de 0, d’autres plus de 1).  
- Création d’une stratégie d’**ensemble** combinant plusieurs modèles pour améliorer la robustesse :  
  - Intersection ou union des prédictions.  
  - Vote majoritaire pondéré avec différents seuils.  
- Cette approche a permis de réduire le Half-Total Error Rate en combinant les forces complémentaires des modèles.

---

## 📂 Livrables  
- `label_val.txt` : fichier contenant les prédictions pour les 20 000 images de validation, dans l’ordre donné.  
- Code commenté dans le notebook `colab.ipynb`.

---

## Remarques  
- Les images et les poids des modèles ne sont pas fournis, conformément aux consignes du projet.  
- Le code est organisé et commenté pour faciliter la compréhension et la reproductibilité.

---

*Projet développé avec TensorFlow/Keras dans un cadre d’apprentissage supervisé et de vision par ordinateur.*
