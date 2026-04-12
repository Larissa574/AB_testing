# AB Testing - Analyse Comparative de Boutons Web

Ce projet analyse un test A/B pour comparer deux variantes d'une page web et déterminer laquelle convertit le mieux.

## 📊 Objectif

Mettre en place une démarche d'A/B testing rigoureuse pour :
- Comparer deux variantes d'une expérience digitale
- Mesurer l'impact réel sur le comportement utilisateur
- Prendre une décision marketing/produit basée sur l'analyse statistique

## 📈 Variantes Testées

- **Groupe A (Control)** : Bouton orange (ancienne version)
- **Groupe B (Treatment)** : Bouton vert (nouvelle version)

## 📚 Dataset

**[Website A/B Testing Dataset - Kaggle](https://www.kaggle.com/datasets/zeusdatasets/website-ab-testing-dataset)**

- **Taille** : 294,478 observations
- **Colonnes** : 
  - `user_id` : Identifiant utilisateur unique
  - `timestamp` : Date/heure de la visite
  - `group` : Groupe assigné (control/treatment)
  - `landing_page` : Version de la page (old_page/new_page)
  - `converted` : Conversion (0/1)

## 🔍 Méthodologie

### 1. Analyse Exploratoire (EDA)
- Compréhension des données
- Détection des valeurs manquantes et doublons
- Distribution des variables
- Détection des outliers

### 2. Sanity Check
- Vérification de l'assignation groupe/page
- Équilibre des groupes
- Nettoyage des données mal assignées

### 3. Analyse Statistique
- Vérification de la normalité (Théorème Central Limite)
- Test d'égalité des variances (Levene)
- **Test statistique** : Z-test bilatéral (grands échantillons)

### 4. Hypothèses Statistiques
- **H0** : Pas de différence significative entre les taux de conversion
  - p_control = p_treatment
- **H1** : Différence significative existe
  - p_control ≠ p_treatment
- **Seuil de signification** : α = 0.05

### 5. Calcul des Métriques
- Taux de conversion par groupe
- Différence absolue
- Lift relatif
- P-value et intervalle de confiance

## 📋 Livrables

✅ Notebook propre avec commentaires détaillés  
✅ Préparation et nettoyage des données  
✅ Analyse exploratoire avec visualisations  
✅ Test statistique et interprétation  
✅ Recommandations business  

## 🛠️ Installation

```bash
# Créer un environnement virtuel
python -m venv venv
venv\Scripts\activate  # Windows

# Installer les dépendances
pip install -r requirements.txt

# Lancer Jupyter
jupyter notebook ab_testing.ipynb
```

## 📁 Structure du Projet

```
AB_testing/
├── ab_testing.ipynb          # Notebook principal
├── ab_data.csv               # Dataset
├── requirements.txt          # Dépendances Python
├── README.md                 # Ce fichier
└── images/                   # Graphiques générés
    ├── distribution_converted.png
    └── conversion_by_group.png
```

## 🎯 Résultats Clés

| Métrique | Groupe Control | Groupe Treatment | Différence |
|----------|---|---|---|
| **Taux de conversion** | 12.04% | 11.88% | -0.16 pp |
| **Lift relatif** | - | - | -1.31% |
| **P-value** | - | - | 0.1897 |
| **Significatif ?** | Non ❌ | - | - |

**Conclusion** : Le bouton vert n'apporte pas de gain statistiquement significatif. Recommandation : garder le bouton orange.

## 🚀 Technologies Utilisées

- **Python 3.13**
- **Pandas** : Manipulation des données
- **NumPy** : Calculs numériques
- **Matplotlib & Seaborn** : Visualisations
- **Scikit-learn** : Détection des outliers
- **SciPy & StatsModels** : Tests statistiques
- **Jupyter** : Notebook interactif

## 📝 Notes

- Grande taille d'échantillon autorise l'utilisation du Z-test au lieu du t-test
- Problème d'assignation détecté : certains utilisateurs ont reçu la mauvaise variante
- Nettoyage effectué : 3,643 observations supprimées



