# Rapport d'Analyse du Dataset Wine Quality

## 1. Introduction

Ce rapport présente une analyse du dataset **Wine Quality** provenant du référentiel UCI Machine Learning Repository. Le code analysé permet de charger et d'explorer ce dataset qui contient des données sur la qualité des vins portugais "Vinho Verde".

## 2. Objectif du Dataset

Le dataset vise à modéliser la qualité du vin en se basant sur des tests physicochimiques. Il comprend deux variantes de vin : rouge et blanc, toutes deux provenant du nord du Portugal.

## 3. Description du Code

### 3.1 Installation de la Bibliothèque

```python
pip install ucimlrepo
```

Cette commande installe le package `ucimlrepo` qui permet d'accéder facilement aux datasets du référentiel UCI. Les dépendances déjà satisfaites incluent pandas, numpy, et certifi.

### 3.2 Chargement des Données

```python
from ucimlrepo import fetch_ucirepo
wine_quality = fetch_ucirepo(id=186)
```

Le dataset est récupéré directement depuis le référentiel UCI en utilisant son identifiant unique (186).

### 3.3 Extraction des Composantes

```python
X = wine_quality.data.features
y = wine_quality.data.targets
```

Les données sont séparées en deux composantes : les variables explicatives (features) stockées dans X et la variable cible (qualité) stockée dans y.

## 4. Caractéristiques du Dataset

### 4.1 Informations Générales

- **Nombre d'instances** : 4 898 échantillons de vin
- **Nombre de features** : 11 variables explicatives
- **Type de features** : Toutes continues (Real)
- **Variable cible** : Quality (score entre 0 et 10)
- **Valeurs manquantes** : Aucune
- **Année de création** : 2009

### 4.2 Variables Explicatives (Physicochimiques)

Le dataset comprend 11 variables basées sur des tests physicochimiques :

1. **Fixed acidity** (acidité fixe)
2. **Volatile acidity** (acidité volatile)
3. **Citric acid** (acide citrique)
4. **Residual sugar** (sucre résiduel)
5. **Chlorides** (chlorures)
6. **Free sulfur dioxide** (dioxyde de soufre libre)
7. **Total sulfur dioxide** (dioxyde de soufre total)
8. **Density** (densité)
9. **pH** (pH)
10. **Sulphates** (sulfates)
11. **Alcohol** (teneur en alcool)

### 4.3 Variable Cible

- **Quality** : Score de qualité basé sur des données sensorielles, variant de 0 à 10

### 4.4 Variable Supplémentaire

- **Color** : Variable catégorielle indiquant le type de vin (rouge ou blanc)

## 5. Type de Tâche

Le dataset peut être utilisé pour deux types de tâches :

- **Classification** : Prédire la catégorie de qualité du vin
- **Régression** : Prédire le score exact de qualité

## 6. Particularités du Dataset

### 6.1 Déséquilibre des Classes

Les classes ne sont pas équilibrées : il y a beaucoup plus de vins de qualité normale que de vins excellents ou médiocres. Cette caractéristique peut nécessiter des techniques spéciales de traitement du déséquilibre.

### 6.2 Classes Ordonnées

Les classes de qualité sont ordonnées, ce qui signifie qu'un vin de qualité 7 est objectivement meilleur qu'un vin de qualité 5.

### 6.3 Confidentialité des Données

Pour des raisons de confidentialité et logistiques, seules les variables physicochimiques et sensorielles sont disponibles. Les informations sur les cépages, la marque, le prix de vente, etc., ne sont pas incluses.

## 7. Applications Potentielles

### 7.1 Détection d'Outliers

Des algorithmes de détection d'anomalies pourraient être utilisés pour identifier les quelques vins excellents ou médiocres.

### 7.2 Sélection de Features

Toutes les variables d'entrée ne sont pas nécessairement pertinentes. Des méthodes de sélection de features pourraient être testées pour améliorer les modèles.

### 7.3 Modèles Prédictifs

Le dataset est idéal pour développer et comparer différents algorithmes de machine learning (régression, classification, arbres de décision, réseaux de neurones, etc.).

## 8. Référence Scientifique

**Article original** : "Modeling wine preferences by data mining from physicochemical properties"
- **Auteurs** : P. Cortez, A. Cerdeira, F. Almeida, T. Matos, J. Reis
- **Publication** : Decision Support Systems, 2009
- **DOI** : 10.24432/C56S3T

## 9. Conclusion

Le code présenté constitue une première étape essentielle dans l'analyse du dataset Wine Quality. Il permet de charger efficacement les données et de les préparer pour des analyses ultérieures. Ce dataset offre un excellent cas d'usage pour l'apprentissage automatique, combinant des variables physicochimiques objectives avec une évaluation sensorielle subjective de la qualité du vin.

Les prochaines étapes pourraient inclure l'analyse exploratoire des données (EDA), la visualisation des distributions, l'étude des corrélations entre variables, et le développement de modèles prédictifs.

---

**Source des données** : UCI Machine Learning Repository
**URL** : https://archive.ics.uci.edu/dataset/186/wine+quality
**Dernière mise à jour** : 15 novembre 2023
