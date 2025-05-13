Détection Automatique des Données Sensibles (Loi 09-08)

## Description

Ce projet a pour objectif de concevoir un système de **détection automatique des données sensibles** dans des jeux de données médicaux, en conformité avec la **loi marocaine 08-09** sur la protection des données à caractère personnel.  
Il repose sur l’utilisation de plusieurs algorithmes d’apprentissage automatique, comparés selon différents critères de performance.

---

## Contexte Légal

La loi 08-09 stipule que les données dites « sensibles » incluent :
- Les informations médicales
- Les données d’identité (âge, nom, date de naissance…)
- Les données biométriques ou génétiques
- Les numéros d’identification (dossier médical, téléphone…)
- Les informations relatives à la vie privée

Dans ce projet, un individu est considéré comme « sensible » s’il :
- A un âge supérieur à **65 ans**
- Ou un **montant de facturation** supérieur au troisième quartile

---

## Données

- **Source :** [Kaggle - Healthcare Dataset](https://www.kaggle.com/datasets/prasad22/healthcare-dataset)
- **Format :** CSV (~1000 enregistrements)
- **Prétraitement :**
  - Nettoyage des doublons
  - Standardisation des noms de colonnes
  - Encodage des variables catégorielles
  - Création de la variable cible `is_sensitive`
  - Gestion du déséquilibre avec **SMOTE**

---

## Algorithmes utilisés

| Modèle                | Justification principale |
|-----------------------|--------------------------|
| Random Forest         | Robuste, interprétable, efficace sur données déséquilibrées |
| XGBoost               | Très performant, adapté aux données déséquilibrées |
| SVM                   | Efficace pour la séparation complexe des classes |
| Régression Logistique | Baseline simple et interprétable |
| Naive Bayes           | Rapide et efficace sur des jeux de petite taille |

Tous les modèles sont intégrés dans un **pipeline** incluant :
- Normalisation (`StandardScaler`)
- Suréchantillonnage (`SMOTE`)
- Entraînement et évaluation

---

## Évaluation des performances

Les modèles sont évalués sur un jeu de test via les métriques suivantes :
- **Accuracy**
- **Précision**
- **Rappel**
- **F1-score**
- **AUC ROC**

### Résultats obtenus (extrait) :

| Modèle                | Accuracy | Précision | Rappel | F1-score | AUC |
|-----------------------|----------|-----------|--------|----------|-----|
| Random Forest         | 0.823    | 1.000     | 0.625  | 0.769    | 0.825 |
| XGBoost               | 0.823    | 0.999     | 0.625  | 0.769    | 0.818 |
| SVM                   | 0.792    | 0.867     | 0.659  | 0.749    | 0.813 |
| Naive Bayes           | 0.738    | 0.724     | 0.716  | 0.720    | 0.814 |
| Régression Logistique | 0.724    | 0.696     | 0.733  | 0.714    | 0.815 |

---

## Recommandations

- **Modèles globaux recommandés :** `Random Forest`, `XGBoost`
- **Modèles à privilégier pour un meilleur rappel :** `Naive Bayes`, `Régression Logistique`
- **Compromis équilibré :** `SVM`

---

## Visualisations

- **Matrice de confusion**
- **Courbes ROC comparées**
- **Importance des variables (Random Forest)**
- **Barres de comparaison des performances**

---

## Prérequis

- Python 3.7+
- Bibliothèques :
  - `pandas`, `numpy`
  - `matplotlib`, `seaborn`
  - `scikit-learn`
  - `xgboost`
  - `imbalanced-learn`

> Installer les dépendances :
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost imbalanced-learn
```

---



---

## 📚 Références

- [Loi 08-09 sur la protection des données personnelles (CNDP)](https://www.cndp.ma)
- [Kaggle Dataset utilisé](https://www.kaggle.com/datasets/prasad22/healthcare-dataset)
