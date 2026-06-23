# 🍷 Wine Quality Prediction Model

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Random%20Forest-Classifier-228B22?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge"/>
</p>

<p align="center">
  A machine learning project that predicts the <strong>quality of red wine</strong> (Good or Bad) based on its physicochemical properties, using a <strong>Random Forest Classifier</strong> on the UCI Wine Quality Dataset.
</p>

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Model Details](#-model-details)
- [Results](#-results)
- [Technologies Used](#-technologies-used)
- [Getting Started](#-getting-started)
- [How to Run](#-how-to-run)
- [Key Concepts Covered](#-key-concepts-covered)
- [Author](#-author)

---

## 🧠 Overview

This project builds a **binary classification model** to predict whether a red wine sample is of **Good Quality** or **Bad Quality** based on its measurable chemical properties. The model uses the **Random Forest Classifier** — a powerful ensemble learning method that combines multiple decision trees for robust and accurate predictions.

The complete data science pipeline is implemented: from exploratory data analysis and feature engineering to model training, hyperparameter understanding, and evaluation.

---

## 🎯 Problem Statement

Wine quality assessment traditionally relies on expert sommeliers and sensory evaluation — a costly, subjective, and time-consuming process. By leveraging machine learning on physicochemical test data, we can build an objective, scalable model to:

- **Automate** wine quality grading
- **Assist** winemakers in identifying quality-impacting chemical factors
- **Reduce** reliance on expensive manual tasting panels

This project frames wine quality as a **binary classification task**: given the chemical composition of a wine sample, classify it as **Good (quality ≥ 7)** or **Bad (quality < 7)**.

---

## 📊 Dataset

**`winequality-red_dataset.csv`** — UCI Red Wine Quality Dataset.

| Property          | Details                                      |
|-------------------|----------------------------------------------|
| Total Samples     | 1,599 red wine samples                       |
| Input Features    | 11 physicochemical properties                |
| Original Target   | Quality score (0–10 scale)                   |
| Derived Target    | Binary — Good (≥7) or Bad (<7)              |
| Task Type         | Binary Classification                        |
| Source            | UCI Machine Learning Repository / Kaggle     |
| No Missing Values | ✅ Clean dataset                             |

### Feature Description

| Feature                  | Description                                                    |
|--------------------------|----------------------------------------------------------------|
| `fixed acidity`          | Non-volatile acids that contribute to wine tartness            |
| `volatile acidity`       | Acetic acid content — too high leads to unpleasant vinegar taste|
| `citric acid`            | Adds freshness and flavor to wines                             |
| `residual sugar`         | Sugar remaining after fermentation (g/L)                       |
| `chlorides`              | Salt content in the wine                                       |
| `free sulfur dioxide`    | Free form of SO₂ — prevents microbial growth & oxidation       |
| `total sulfur dioxide`   | Total amount of SO₂ (free + bound forms)                       |
| `density`                | Wine density, correlated with alcohol and sugar content        |
| `pH`                     | Acidity level on the pH scale (lower = more acidic)            |
| `sulphates`              | Additive contributing to SO₂ levels; acts as antimicrobial     |
| `alcohol`                | Percentage of alcohol by volume                                |
| `quality`                | **Original target** — expert rating score from 0 to 10         |

### Target Variable (Derived)
```
quality >= 7  →  Good Wine  (1)
quality  < 7  →  Bad Wine   (0)
```

---

## 📁 Project Structure

```
Wine_Quality_Prediction_Model/
│
├── Wine_Quality_Prediction_Model.ipynb
│   ├── 1. Import Libraries
│   ├── 2. Load & Explore Dataset
│   ├── 3. Exploratory Data Analysis (EDA)
│   ├── 4. Feature Engineering — Label Binarization (Good/Bad)
│   ├── 5. Check Class Distribution & Balance
│   ├── 6. Feature-Target Correlation Analysis
│   ├── 7. Train-Test Split
│   ├── 8. Train Random Forest Classifier
│   ├── 9. Model Evaluation (Accuracy, Confusion Matrix, Report)
│   └── 10. Predictions on New Wine Samples
│
├── winequality-red_dataset.csv    ← Red wine physicochemical dataset
└── README.md
```

---

## 🤖 Model Details

### Algorithm: Random Forest Classifier

**Random Forest** is an ensemble learning method that builds multiple decision trees during training and outputs the class that is the **mode of the predictions** of individual trees. It is highly effective for structured/tabular data and naturally handles:

- Non-linear feature relationships
- Feature importance ranking
- Overfitting resistance through bagging

**Training Configuration:**

| Parameter          | Value                          |
|--------------------|--------------------------------|
| Algorithm          | Random Forest Classifier       |
| Number of Trees    | 100 (n_estimators)             |
| Evaluation Metric  | Accuracy                       |
| Train-Test Split   | 80% Train / 20% Test           |
| Random State       | 3                              |

### Feature Engineering

| Step                         | Details                                                   |
|------------------------------|-----------------------------------------------------------|
| Quality Binarization         | `quality >= 7 → 1 (Good)`, `quality < 7 → 0 (Bad)`      |
| No missing value imputation  | Dataset has no null values                                |
| No scaling required          | Random Forest is scale-invariant                          |
| Feature importance           | Extracted from trained Random Forest model                |

---

## 📈 Results

| Metric              | Score      |
|---------------------|------------|
| Training Accuracy   | ~99–100%   |
| Test Accuracy       | ~92–94%    |

### Key Findings from Feature Importance
The most influential features for predicting wine quality are:

1. 🥇 **Alcohol** — Higher alcohol content strongly correlates with better quality
2. 🥈 **Volatile Acidity** — Lower volatile acidity associated with better wines
3. 🥉 **Sulphates** — Higher sulphate levels improve quality ratings
4. **Citric Acid** — Positively associated with freshness and quality
5. **Total Sulfur Dioxide** — Higher levels can negatively impact taste

---

## 🛠️ Technologies Used

| Technology       | Purpose                                    |
|------------------|--------------------------------------------|
| Python 3.8+      | Programming Language                       |
| Scikit-Learn     | Random Forest, Train-Test Split, Metrics   |
| Pandas           | Data Loading, Manipulation, EDA            |
| NumPy            | Numerical Computations                     |
| Matplotlib       | Visualizations & Feature Importance Plots  |
| Seaborn          | Correlation Heatmap & Distribution Plots   |
| Jupyter Notebook | Interactive Development Environment        |

---

## 🚀 Getting Started

### Prerequisites

Make sure Python 3.8+ is installed, then install the required libraries:

```bash
pip install scikit-learn pandas numpy matplotlib seaborn jupyter
```

### Clone the Repository

```bash
git clone https://github.com/AliRaza-Dev678/Wine_Quality_Prediction_Model.git
cd Wine_Quality_Prediction_Model
```

---

## ▶️ How to Run

1. Launch Jupyter Notebook:

```bash
jupyter notebook
```

2. Open the notebook:

```
Wine_Quality_Prediction_Model.ipynb
```

3. Run all cells from top to bottom using **Kernel → Restart & Run All**.

> Make sure `winequality-red_dataset.csv` is in the **same folder** as the notebook before running.

---

## 📚 Key Concepts Covered

- ✅ **EDA on Chemical Data** — Distributions, outlier detection, quality score analysis
- ✅ **Feature Binarization** — Converting multi-class quality scores into binary Good/Bad labels
- ✅ **Correlation Heatmap** — Understanding relationships between physicochemical features and quality
- ✅ **Class Imbalance Awareness** — Analyzing the Good vs Bad wine distribution
- ✅ **Random Forest Classifier** — Ensemble learning with multiple decision trees
- ✅ **Feature Importance** — Identifying which chemical properties impact quality the most
- ✅ **Model Evaluation** — Accuracy, confusion matrix, and classification report
- ✅ **Real-world Predictions** — Predicting quality of new unseen wine samples

---

## 👨‍💻 Author

**Ali Raza**

- GitHub: [@AliRaza-Dev678](https://github.com/AliRaza-Dev678)

---

## 📄 License

This project is licensed under the **MIT License** — feel free to use, modify, and distribute it.

---

<p align="center">
  ⭐ If you found this project helpful, please give it a star! ⭐
</p>
