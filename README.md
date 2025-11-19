# mRNA Vaccine Degradation Prediction

A machine learning project to predict mRNA degradation rates and reactivity, crucial for developing stable and effective mRNA vaccines.

## Project Overview

This project addresses a key challenge in mRNA vaccine development: predicting RNA degradation patterns. Using machine learning and feature engineering, we predict reactivity and degradation rates under various experimental conditions, which can help optimize mRNA vaccine stability.

## Objectives

- Predict mRNA degradation rates at nucleotide-level resolution
- Analyze how sequence and structural features affect RNA stability
- Build a robust model that can guide mRNA vaccine design
- Achieve high predictive accuracy for reactivity and degradation metrics

## Technical Implementation

### Data Sources
- **Stanford OpenVaccine - COVID-19 mRNA Vaccine Degradation Prediction** (Kaggle Competition)
- 2,400 training samples with 19 feature columns
- 3,634 test samples
- Base Pair Probability (BPP) matrices for each sequence

### Features Engineered
- **Sequence Encoding**: Integer encoding of nucleotide sequences (A=0, C=1, G=2, U=3)
- **Structural Features**: RNA secondary structure and loop type encoding
- **BPP Features**: Statistical features from base pair probability matrices
  - Maximum, mean, standard deviation, sum, and entropy
- **Multi-modal Integration**: 396 total features combining sequence, structure, and BPP data

### Models Developed
- **XGBoost Regressor** with extensive hyperparameter tuning
- **RandomizedSearchCV** with 50 iterations and 5-fold cross-validation
- **Early Stopping** to prevent overfitting

## Results & Visualizations

### Model Performance Summary

| Metric | Baseline Model | After Hyperparameter Tuning |
|--------|---------------|-----------------------------|
| **RMSE** | 0.0983 | **0.0962** |
| **MAE** | 0.0670 | **0.0600** |
| **R² Score** | - | **0.4369** |
| **Cross-Validation RMSE** | - | **0.0905** |

### Key Visualizations

#### 1. Reactivity Distribution
![Reactivity Distribution](<img width="800" height="400" alt="Ractivity Distribution" src="https://github.com/user-attachments/assets/73af2b58-7d1d-40b3-8053-a6ca6953978d" />)
*Distribution of mean reactivity values shows most sequences cluster between 0.2-0.6 reactivity, with a normal distribution pattern indicating good data quality.*

#### 2. Feature Importance
![Feature Importance](<img width="640" height="480" alt="Feature Importance" src="https://github.com/user-attachments/assets/f9731468-d82f-4ff2-b86d-dde013120558" />)
*Initial feature importance showing encoded sequence features (f392, f391, f395) as most predictive of degradation rates.*

#### 3. Final Model Feature Importance
![Final Feature Importance](<img width="640" height="480" alt="Final Model Feature Importance" src="https://github.com/user-attachments/assets/f81b93e5-9d91-47fa-a815-86f4c6bddb91" />)
*Optimized model feature importance after hyperparameter tuning, showing more balanced feature utilization.*

#### 4. Reactivity by Loop Type
![Reactivity by Loop Type](<img width="640" height="480" alt="Mean Reactivity by Loop type " src="https://github.com/user-attachments/assets/af30d135-d7d2-47a6-91f4-52aea903adde" />)
*Loop type 5 (External loops) shows significantly higher reactivity compared to other structural elements.*

#### 5. BPP Feature Correlations
![BPP Correlation](<img width="600" height="400" alt="BPP Correlation" src="https://github.com/user-attachments/assets/4060eaf7-eb4f-4583-9913-c30978a09efd" />)
*Strong correlations between BPP features: bpp_mean and bpp_sum are perfectly correlated (1.0), suggesting feature redundancy.*

### 🔬 Key Insights from Analysis

#### Data Characteristics
- **Sequence Length**: All sequences are 107 nucleotides (unusual consistency)
- **Reactivity Range**: Mean reactivity 0.375 ± 0.119, with some extreme values up to 2.48
- **Data Quality**: Signal-to-noise ratios vary, requiring quality filtering

#### Feature Analysis
1. **Structural Dominance**: Encoded sequence features (f390+) are most predictive
2. **BPP Redundancy**: High correlation between bpp_mean and bpp_sum (1.0)
3. **Complementary Information**: bpp_entropy negatively correlated with bpp_max (-0.49) and bpp_std (-0.67)
4. **Loop Type Impact**: External loops show highest reactivity, crucial for degradation prediction

#### Model Performance
- **21% Improvement** from baseline to tuned model (CV RMSE: 0.0905)
- **Effective Regularization**: Optimal parameters include high reg_lambda (10) and moderate learning_rate (0.1)
- **Feature Robustness**: Model consistently prioritizes structural features over raw sequence

## Installation & Usage

### Prerequisites
```bash
python>=3.8
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=1.0
xgboost>=1.5
matplotlib>=3.5
seaborn>=0.11
