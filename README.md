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

## 📊 Results

### Final Model Performance
- **RMSE**: 0.098 (after hyperparameter optimization)


### Key Insights
- Sequence structural features significantly impact degradation rates
- BPP entropy and maximum values are highly predictive features
- External loop types show higher reactivity compared to other structures

## 🚀 Installation & Usage

### Prerequisites
```bash
python>=3.8
pandas
numpy
scikit-learn
xgboost
matplotlib
seaborn
