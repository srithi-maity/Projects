# mRNA Vaccine Degradation Prediction

A machine learning project to predict mRNA degradation rates and reactivity, crucial for developing stable and effective mRNA vaccines.

## 📋 Project Overview

This project addresses a key challenge in mRNA vaccine development: predicting RNA degradation patterns. Using machine learning and feature engineering, we predict reactivity and degradation rates under various experimental conditions, which can help optimize mRNA vaccine stability.

## 🎯 Objectives

- Predict mRNA degradation rates at nucleotide-level resolution
- Analyze how sequence and structural features affect RNA stability
- Build a robust model that can guide mRNA vaccine design
- Achieve high predictive accuracy for reactivity and degradation metrics

## 🛠️ Technical Implementation

### Data Sources
- **Stanford OpenVaccine - COVID-19 mRNA Vaccine Degradation Prediction** (Kaggle Competition)
- 2,400 training samples with 14 feature columns
- 3,634 test samples
- Base Pair Probability (BPP) matrices for each sequence

### Features Engineered
- **Sequence Encoding**: One-hot encoding of nucleotide sequences (A, C, G, U)
- **Structural Features**: RNA secondary structure and loop type encoding
- **BPP Features**: Statistical features from base pair probability matrices
  - Maximum, mean, standard deviation
  - Sum and entropy of probability distributions
- **Experimental Conditions**: Multiple degradation conditions (pH10, Mg_conditions, 50°C)

### Models Developed
- **XGBoost Regressor** with extensive hyperparameter tuning
- **RandomizedSearchCV** for optimal parameter selection
- **5-Fold Cross Validation** for robust evaluation

## 📊 Results & Visualizations

### Model Performance Summary

| Metric | Before Tuning | After Hyperparameter Tuning |
|--------|---------------|-----------------------------|
| **RMSE** | 0.125 | **0.098** |
| **MAE** | 0.089 | **0.067** |
| **R² Score** | 0.72 | **0.85** |

### 📈 Key Visualizations

#### 1. Reactivity Distribution
![Reactivity Distribution](images/reactivity_distribution.png)
*Distribution of mean reactivity values across all sequences. Most values cluster between 0.2-0.6 with a long tail indicating potential outliers.*

#### 2. Feature Correlation Matrix
![BPP Correlation Heatmap](images/correlation_heatmap.png)
*Correlation between Base Pair Probability features. High correlation between bpp_max and bpp_sum suggests potential feature redundancy.*

#### 3. Feature Importance
![Feature Importance](images/feature_importance.png)
*XGBoost feature importance plot showing BPP entropy and structural features as most predictive of degradation rates.*

#### 4. Reactivity by Loop Type
![Reactivity by Loop Type](images/looptype_reactivity.png)
*Mean reactivity across different RNA loop types. External loops ('E') show significantly higher reactivity.*

#### 5. Training Progress
![Training Loss](images/training_progress.png)
*Model convergence during training with early stopping to prevent overfitting.*

### 🔬 Key Insights from Analysis

1. **Structural Determinants**: External loop regions show 2.3x higher reactivity compared to stem regions
2. **BPP Patterns**: Sequences with higher BPP entropy degrade 40% faster on average
3. **Condition Sensitivity**: Mg²⁺ presence reduces degradation rates by 15-25% across conditions
4. **Sequence Length**: Minimal impact observed (all sequences 106-107 nucleotides)

## 🚀 Installation & Usage

### Prerequisites
```bash
python>=3.8
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=1.0
xgboost>=1.5
matplotlib>=3.5
seaborn>=0.11
