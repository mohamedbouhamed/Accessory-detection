# Détection d’Accessoires sur Images de Personnes

## 🎯 Objectif du projet
Ce projet a pour but de développer un algorithme de vision par ordinateur capable de détecter automatiquement différents accessoires portés par des personnes sur des images (lunettes, chapeaux, sacs, etc.) grâce à des techniques d’apprentissage profond.

## 🛠️ Méthodologie

### 1. Exploration du jeu de données
- Chargement d’un dataset d’images annotées.
- Analyse de la distribution des classes (types d’accessoires).

### 2. Prétraitement
- Redimensionnement des images.
- Normalisation des pixels.
- Encodage des labels en multi-label (One-hot).

### 3. Modélisation
- Utilisation d’un modèle CNN (ResNet, MobileNet, ou personnalisé).
- Détection multi-label (plusieurs accessoires peuvent être détectés sur une même image).
- Fonction de perte adaptée : Binary Cross Entropy.

### 4. Entraînement
- Séparation des données en ensembles train / validation / test.
- Suivi des performances via courbes de perte et d’accuracy.
- Mise en place d’un early stopping pour éviter l’overfitting.

### 5. Évaluation
- Calcul des métriques : F1-score, précision, rappel.
- Visualisation d’exemples d’images bien ou mal classées.
- Affichage des courbes d’apprentissage.

## 🚀 Améliorations possibles
- Application de data augmentation.
- Utilisation de modèles pré-entraînés (transfer learning).
- Optimisation des hyperparamètres.
