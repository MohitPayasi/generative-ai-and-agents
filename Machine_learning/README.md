# 🤖 Machine Learning Track

Practical implementations, exploratory data analysis, mathematical foundations, and end-to-end regression projects using Python, NumPy, Pandas, Scikit-Learn, and Seaborn.

---

## 📌 Direct GitHub Notebook Links

Quickly access individual classes and end-to-end projects:

| Module / Topic | Notebook / File | Core Concepts Covered | Key Libraries |
| :--- | :--- | :--- | :--- |
| **Class 02: Statistics** | [`class_2.ipynb`](./class/class_2.ipynb) | **Descriptive Statistics**: Mean, median, mode, variance, standard deviation, student dataset creation & summary metrics. | `numpy`, `pandas`, `statistics` |
| **Class 03: EDA** | [`class_3.ipynb`](./class/class_3.ipynb) | **Exploratory Data Analysis**: Multi-feature correlation, distributions, data frames, and Seaborn visual relationships. | `pandas`, `seaborn`, `matplotlib` |
| **Class 04: Feature Engineering** | [`class_4.ipynb`](./class/class_4.ipynb) | **Encoding & Preprocessing**: Categorical encoding using `LabelEncoder`, one-hot encoding, and feature inspection on the Tips dataset. | `pandas`, `seaborn`, `scikit-learn` |
| **Class 05: Outlier Detection** | [`class_5.ipynb`](./class/class_5.ipynb) | **Outlier Analysis & Cleaning**: Anomaly detection using Boxplots, Z-scores, and IQR filtering. | `numpy`, `scipy.stats`, `matplotlib` |
| **Class 06: Simple Linear Regression** | [`class_6.ipynb`](./class/class_6.ipynb) | **Univariate Regression**: Feature reshaping (`reshape(-1, 1)`), line of best fit, OLS concepts, and basic prediction. | `scikit-learn`, `matplotlib`, `numpy` |
| **Class 07: Multiple Linear Regression** | [`class_7.ipynb`](./class/class_7.ipynb) | **Multivariate Modeling**: Train-test split, weights ($W_1, W_2$), intercept, and error metrics ($R^2$, MSE, RMSE). | `scikit-learn`, `pandas`, `numpy` |
| **Class 08: Gradient Descent** | [`class_8.ipynb`](./class/class_8.ipynb) | **Optimization from Scratch**: Implementing Gradient Descent for Multiple Linear Regression, Epochs, MSE loss gradients, and parameter updates. | `numpy` |
| **Class 09: Multicollinearity & VIF** | [`class_9.ipynb`](./class/class_9.ipynb) | **Feature Collinearity**: Variance Inflation Factor (VIF), severe multicollinearity diagnosis, and feature elimination. | `pandas`, `statsmodels`, `numpy` |
| **End-to-End Project** | [`Used_Bike_Resale_Price_Estimation.ipynb`](./project/Linear_regression/Used_Bike_Resale_Price_Estimation.ipynb) | **Industry Analysis**: Full data audit, text extraction, cleaning, EDA, regression modeling, and model serialization (`.joblib`). | `pandas`, `scikit-learn`, `joblib`, `seaborn` |

---

## 🗂️ Directory Structure

```text
Machine_learning/
├── class/                                # Lecture & concept notebooks
│   ├── class_2.ipynb                     # Descriptive statistics & distributions
│   ├── class_3.ipynb                     # Exploratory Data Analysis & visual plots
│   ├── class_4.ipynb                     # Feature engineering, categorical & label encoding
│   ├── class_5.ipynb                     # Outlier detection with IQR and Z-scores
│   ├── class_6.ipynb                     # Simple Linear Regression (Scikit-Learn)
│   ├── class_7.ipynb                     # Multiple Linear Regression & metrics (R2, MSE)
│   ├── class_8.ipynb                     # Gradient Descent algorithm built from scratch
│   └── class_9.ipynb                     # Multicollinearity detection using VIF
│
├── project/
│   └── Linear_regression/                # Complete used-bike pricing project
│       ├── Used_Bike_Resale_Price_Estimation.ipynb  # End-to-end data audit, EDA & modeling
│       ├── bikes.csv                     # Raw used-bike marketplace dataset
│       ├── bikes_cleaned.csv             # Processed dataset with cleaned numerical attributes
│       ├── bike_price_linear_regression.joblib      # Serialized trained Scikit-Learn model
│       └── bike_price_predictions.csv    # Model inference predictions & evaluation outputs
│
└── README.md                             # Machine Learning module documentation
```

---

## 🚀 Key Modules Breakdown

### 1. Mathematical Foundations & Algorithms
* **Descriptive & Inferential Statistics**: Population vs. sample metrics, central tendency, variance, and standard deviations.
* **Gradient Descent from Scratch (`class_8.ipynb`)**:
  * Implemented iterative weight updates: $W := W - \alpha \cdot \frac{\partial \text{MSE}}{\partial W}$
  * Evaluated loss trajectory across 1,000 epochs to observe convergence to global minima.
* **Multicollinearity & VIF (`class_9.ipynb`)**:
  * Calculated Variance Inflation Factor ($\text{VIF} = \frac{1}{1 - R_i^2}$) for each feature to diagnose high variance and prevent unstable regression weights.

### 2. End-to-End Project: Used Bike Resale Price Estimation
* **Business Goal**: Predict fair resale values for pre-owned two-wheelers based on age, mileage, engine power, and brand.
* **Data Engineering**:
  * Custom string parsing (`get_number`) to sanitize dirty columns with units (`kms_driven`, `mileage`, `power`).
  * Managed non-positive prices and missing records.
* **Production Deployment Artifacts**:
  * Pipeline exported to disk using `joblib` for low-latency inference in web services.

---

## 🛠️ Setup & Prerequisites

Install required packages:
```bash
pip install numpy pandas matplotlib seaborn scikit-learn scipy statsmodels joblib jupyter
```

Launch Jupyter Notebook:
```bash
jupyter notebook
```
