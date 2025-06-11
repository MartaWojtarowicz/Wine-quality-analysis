# 🍷 Wine Quality Analysis

This project analyzes the quality of **white** and **red** "Vinho Verde" wines based on physicochemical properties. The goal is to identify key factors influencing wine quality and compare classification strategies for imbalanced quality classes.

## 📂 Dataset

- Source: [UCI Machine Learning Repository – Wine Quality](https://archive.ics.uci.edu/ml/datasets/wine+quality)  
- Records:  
  - 4898 samples of **white wine**  
  - 1599 samples of **red wine**  
- Features: 11 numerical variables (e.g., pH, acidity, alcohol)  
- Target: `quality` (scores from 3 to 9; no 0–2 or 10 values)

### 📊 Class Distribution (Quality Scores)

#### White Wine:
| Quality Score | Count |
|---------------|-------|
| 3             | 20    |
| 4             | 163   |
| 5             | 1457  |
| 6             | 2198  |
| 7             | 880   |
| 8             | 175   |
| 9             | 5     |

#### Red Wine:
- Similar analysis performed and used for visualization and heatmaps.

---

## 🔬 Exploratory Data Analysis (EDA)

1. Distribution plots (KDE + histograms) of pH and alcohol comparing red and white wines.  
2. Correlation heatmaps for both wine types (features vs. quality).  
3. Feature importance analysis based on absolute correlation with quality — alcohol has the strongest influence, followed by pH and density.

**Key EDA insights:**  
- Alcohol content is the most strongly correlated with quality in both wine types.  
- pH and density have moderate effects, with differences between red and white wines.

---

## ⚙️ Handling Imbalanced Classes

Due to severe class imbalance (e.g., only 5 samples with quality 9 in white wine), three classification approaches were tested:

1. **SMOTE Oversampling** — synthetic minority oversampling (Accuracy ~0.68)  
2. **Class Filtering** — removing classes with fewer than 100 samples (Accuracy ~0.70)  
3. **Class Combination** — merging rare/close classes into 4 groups (Accuracy ~0.78)

---

## 🤖 Model

- **Algorithm:** Random Forest (`n_estimators=100`, `random_state=999`)  
- **Validation:** stratified 80/20 train/test split  
- **Metrics:** Accuracy and classification report

---

## 📌 Requirements

```bash
pip install pandas seaborn matplotlib scikit-learn imbalanced-learn
