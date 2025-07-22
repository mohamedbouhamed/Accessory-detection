# Classification binaire d’images avec minimisation du Half-Total Error Rate (HTER)

## Description  
Ce projet vise à développer un modèle de classification d’images binaire pour détecter des classes sur un jeu de données comportant 100k images d’entraînement et 20k images de validation. L’objectif principal est de minimiser le Half-Total Error Rate (HTER).

Le modèle repose sur l’utilisation de réseaux de neurones convolutifs (CNN) pré-entraînés, notamment VGG16 et MobileNetV2, adaptés à notre tâche de classification binaire.

---

## Base de données  
- Jeu d’entraînement : 100 000 images dans le dossier `train_img`.  
- Jeu de validation : 20 000 images dans le dossier `val_img`.  
- Labels : fichier `label_train.txt` contenant les labels binaires correspondant aux images d’entraînement.  
- Les images sont nommées par numéro, correspondant à la ligne dans le fichier de labels.

---

## Fonctionnalités principales  

### Prétraitement des données  
- Chargement et redimensionnement des images à 224×224 pixels, format adapté aux architectures pré-entraînées.  
- Application de data augmentation (rotations, flips, zooms) pour enrichir le jeu d’entraînement et améliorer la robustesse du modèle.

### Modélisation  
- Utilisation de modèles CNN pré-entraînés sur ImageNet, notamment **VGG16** et **MobileNetV2**, avec suppression de la tête originale.  
- Ajout de nouvelles couches denses personnalisées pour la classification binaire avec activation sigmoïde.  
- Gel des couches convolutionnelles lors du fine-tuning pour conserver les connaissances pré-apprises.

### Entraînement  
- Optimisation via la fonction de perte **Binary Crossentropy**.  
- Early stopping pour prévenir l’overfitting.  
- Suivi des performances par les métriques d’accuracy et loss.

### Ensemble learning et fusion des modèles  
- Observation que chaque modèle a des biais différents (certains prédisaient plus de 0, d’autres plus de 1).  
- Création d’une stratégie d’**ensemble** combinant plusieurs modèles pour améliorer la robustesse :  
  - Intersection ou union des prédictions.  
  - Vote majoritaire pondéré avec différents seuils.  
- Cette approche a permis de réduire le Half-Total Error Rate en combinant les forces complémentaires des modèles.

---

## Livrables  
- Fichier `label_val.txt` : prédictions des labels pour les 20 000 images de validation, dans l’ordre fourni.  
- Code commenté et organisé dans le notebook `colab.ipynb`.

---

## Remarques  
- Les images et poids des modèles ne sont pas fournis, conformément aux consignes du projet.  
- Le code est conçu pour être facilement lisible et réutilisable.

---

*Projet réalisé avec TensorFlow/Keras dans un cadre de vision par ordinateur et apprentissage supervisé.*
