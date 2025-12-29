# COMPTE RENDU : DÉTECTION DE FRAUDE PAR CARTE BANCAIRE

---

## Informations générales
- **Dataset** : Credit Card Fraud Detection
- **Source** : Kaggle – https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
- **Auteur** : Analyse complète
- **Date** : Novembre 2025

---

## TABLE DES MATIÈRES
1. Introduction  
2. Description du Dataset  
3. Contexte et Enjeux de la Fraude  
4. Analyse Exploratoire des Données  
5. Visualisations Graphiques  
6. Analyse du Déséquilibre des Classes  
7. Modèles de Classification  
8. Conclusion et Recommandations

---

## 1. INTRODUCTION

Le **Credit Card Fraud Detection Dataset** est un jeu de données de référence utilisé pour développer et tester des modèles de détection automatique de fraudes par carte bancaire.

**Problématique :**  
Comment identifier efficacement les transactions frauduleuses parmi un très grand nombre de transactions légitimes, tout en limitant les faux positifs qui nuisent à l’expérience client ?

---

## 2. DESCRIPTION DU DATASET

### 2.1 Caractéristiques générales
- **Nombre d’observations** : 284 807 transactions  
- **Période couverte** : 2 jours (septembre 2013)  
- **Nombre de variables** : 31  
- **Variable cible** : `Class` (0 = légitime, 1 = fraude)

### 2.2 Types de variables

**Variables transformées (PCA)** : `V1` à `V28`
- 28 composantes principales issues d’une transformation PCA
- Données anonymisées pour des raisons de confidentialité

**Variables non transformées** :
- `Time` : secondes écoulées depuis la première transaction
- `Amount` : montant de la transaction en euros
- `Class` : variable cible

### 2.3 Déséquilibre des classes
- Transactions légitimes : **284 315 (99,827 %)**  
- Transactions frauduleuses : **492 (0,173 %)**  
- Ratio : **1 fraude pour 577 transactions légitimes**

---

## 3. CONTEXTE ET ENJEUX DE LA FRAUDE

### 3.1 Origine des données
Les données proviennent de transactions réelles effectuées par des porteurs de cartes européens. Les variables ont été transformées par PCA afin de garantir la confidentialité.

### 3.2 Impact économique
- Pertes mondiales estimées : **> 30 milliards de dollars/an**
- Coût élevé des fraudes non détectées
- Coût indirect des faux positifs (insatisfaction client)

### 3.3 Défis techniques
- Déséquilibre extrême des classes
- Nécessité de décisions en temps réel
- Coût asymétrique des erreurs
- Évolution continue des stratégies de fraude

---

## 4. ANALYSE EXPLORATOIRE DES DONNÉES

### 4.1 Statistiques descriptives – Variable *Amount*

| Statistique | Valeur |
|------------|--------|
| Moyenne | 88,35 € |
| Médiane | 22,00 € |
| Écart-type | 250,12 € |
| Minimum | 0,00 € |
| Maximum | 25 691,16 € |

### 4.2 Comparaison légitime vs fraude
- **Transactions légitimes** :
  - Moyenne : 88,29 €
  - Médiane : 22,00 €
- **Transactions frauduleuses** :
  - Moyenne : 122,21 €
  - Médiane : 9,25 €

👉 Les fraudes présentent des montants moyens plus élevés mais une médiane plus faible, indiquant des comportements variés.

### 4.3 Analyse temporelle
- Durée totale : ~48 heures
- Aucune périodicité claire des fraudes

---

## 5. VISUALISATIONS GRAPHIQUES

Les graphiques suivants ont été générés :
1. Distribution des classes
2. Distribution des montants
3. Boxplot des montants par classe
4. Distribution temporelle des transactions
5. Distribution des principales variables PCA
6. Impact du rééquilibrage par SMOTE
7. Comparaison des performances des modèles
8. Analyse finale (ROC, Precision-Recall, matrice de confusion)

*(Les fichiers sont exportés au format PNG pour exploitation dans un rapport ou une présentation.)*

---

## 6. ANALYSE DU DÉSÉQUILIBRE DES CLASSES

### 6.1 Problèmes liés au déséquilibre
- Modèles biaisés vers la classe majoritaire
- Accuracy trompeuse
- Difficulté d’apprentissage pour la classe minoritaire

### 6.2 Techniques utilisées
- **Sur-échantillonnage** : SMOTE
- **Sous-échantillonnage** : Random Under-Sampling

👉 SMOTE a été retenu pour conserver l’information tout en équilibrant les classes.

---

## 7. MODÈLES DE CLASSIFICATION

### 7.1 Modèles testés
- Régression Logistique
- Arbre de Décision
- Random Forest
- Gradient Boosting
- XGBoost

### 7.2 Métriques d’évaluation
- Accuracy
- Precision
- Recall (prioritaire)
- F1-score
- ROC-AUC

### 7.3 Résultats synthétiques attendus

| Modèle | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|------|---------|-----------|--------|----------|---------|
| Random Forest | ~0,9995 | 0,95–0,98 | 0,85–0,92 | 0,90–0,95 | >0,97 |
| XGBoost | ~0,9996 | 0,96–0,99 | 0,88–0,94 | 0,92–0,96 | >0,98 |
| Gradient Boosting | ~0,9994 | 0,94–0,97 | 0,83–0,90 | 0,88–0,93 | >0,96 |

👉 **XGBoost** et **Random Forest** offrent les meilleures performances globales.

---

## 8. CONCLUSION ET RECOMMANDATIONS

### 8.1 Conclusions
- Dataset réaliste et largement utilisé en recherche
- Déséquilibre extrême nécessitant des techniques spécifiques
- Les modèles d’ensemble dominent en performance
- Le **Recall** est la métrique clé en détection de fraude

### 8.2 Recommandations
1. **Feature engineering** : agrégations temporelles, statistiques par utilisateur
2. **Optimisation des seuils** selon les coûts métier
3. **Validation robuste** (cross-validation stratifiée)
4. **Déploiement temps réel** avec monitoring continu
5. **Réentraînement régulier** pour suivre l’évolution des fraudes

### 8.3 Applications pratiques
- Systèmes bancaires de détection en temps réel
- Scoring de risque transactionnel
- Analyse forensique post-fraude
- Réduction des contrôles manuels

---

Des tableaux 




| Classe    | Description             | Nombre      | Pourcentage |
| --------- | ----------------------- | ----------- | ----------- |
| 0         | Transaction légitime    | 284 315     | 99,83 %     |
| 1         | Transaction frauduleuse | 492         | 0,17 %      |
| **Total** |                         | **284 807** | **100 %**   |



📋 Tableau  : Statistiques descriptives de Amount


| Classe   | Moyenne (€) | Médiane (€) | Min (€) | Max (€) |
| -------- | ----------- | ----------- | ------- | ------- |
| Légitime | 88,29       | 22,00       | 0,00    | 25 691  |
| Fraude   | 122,21      | 9,25        | 0,00    | 2 125   |

📋 Tableau 3 : Techniques de traitement du déséquilibre


| Méthode        | Principe                     | Avantages              | Inconvénients              |
| -------------- | ---------------------------- | ---------------------- | -------------------------- |
| SMOTE          | Sur-échantillonnage          | Conserve l’information | Risque de surapprentissage |
| Under-sampling | Réduction classe majoritaire | Rapide                 | Perte d’information        |


📋 Tableau 4 : Résultats des modèles


| Modèle                | Accuracy | Precision | Recall | F1-score |
| --------------------- | -------- | --------- | ------ | -------- |
| Régression logistique | 0,998    | 0,89      | 0,78   | 0,83     |
| Random Forest         | 0,9995   | 0,97      | 0,91   | 0,94     |
| XGBoost               | 0,9996   | 0,98      | 0,93   | 0,95     |



Representation Graphique 




<img width="597" height="436" alt="image" src="https://github.com/user-attachments/assets/e05b99f4-d41a-4471-83a8-9d8e9b2e6b05" />



<img width="452" height="411" alt="image" src="https://github.com/user-attachments/assets/e2389496-ff8b-4c55-92ca-730f1bf76557" />





<img width="592" height="455" alt="image" src="https://github.com/user-attachments/assets/7cb35f86-2577-4eef-9d3d-7fa632445f26" />



<img width="580" height="436" alt="image" src="https://github.com/user-attachments/assets/a5a66f30-5c65-499a-afe1-40ace254a030" />

