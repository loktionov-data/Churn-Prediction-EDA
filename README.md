# Churn Prediction EDA

This project is an analytical pipeline aimed at building a predictive model to identify customer churn in a bank. The dataset contains customer-level information and the target variable `Exited`, indicating whether the customer left the bank.

---

## Project Structure

- `eda.ipynb`: Exploratory Data Analysis (EDA)
- `preprocessing.py` / `preprocessing.ipynb`: Feature engineering, encoding, and outlier removal
- `model_creation.ipynb`: Model training, evaluation (XGBoost, Random Forest), and performance comparison

---

## Dataset

The dataset includes the following features:

- `CreditScore`, `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`
- Target variable: `Exited` — 1 if the customer left, 0 if they stayed.

---

## EDA Highlights

During the EDA phase:

- Removed unused columns: `RowNumber`, `CustomerId`, `Surname`
- Filtered out unrealistic `Age` values (<20 or >65)
- Removed customers with `Tenure = 0`
- Explored distributions, correlations, and patterns in customer churn
- Key insights:
  - Gender distribution is almost balanced, but slightly more men are present across all countries
  - Most churned users are **females aged 35–54** from Germany and France
  - Users aged 25–44 form the majority of the customer base
  - Users with 1–2 products dominate; higher product counts are more common among females

---

## Preprocessing

Main preprocessing steps:

1. **Dropping redundant columns** — removed `age_cohort` column created in EDA as no longer needed
2. **Splitting numeric and categorical features**
3. **Encoding categorical data** — applied one-hot encoding for `Geography` and `Gender`
4. **Outlier removal** — filtered `CreditScore` values below 400
5. **Saved clean dataset** — stored as `preprocessed_data.csv` for modeling

---

## Model Creation

Two classification models were trained and compared:

### 1. **XGBoost Classifier**
- Parameters: `n_estimators=500`, `max_depth=12`, `learning_rate=1`, `objective="binary:logistic"`
- Applied **SMOTE** on training data to address class imbalance
- Achieved **Accuracy: 0.84**, **AUC: 0.85**
- Most important features:
  - Gender
  - User Activity (`IsActiveMember`)
  - Number of Products
  - Geography

### 2. **Random Forest Classifier**
- Used default parameters with `random_state=42`
- Achieved **Accuracy: 0.85**, **AUC: 0.85**
- Most important features:
  - Age
  - Balance
  - Estimated Salary

**Model Selection:**  
Since both models showed identical AUC scores, Random Forest was chosen as the final model due to slightly better interpretability for this dataset.

---

## Visualizations

- Boxplots of numeric features and outlier analysis (`img/boxplots/`)
- Correlation heatmap (`img/data_correlation.png`)
- Feature importance plots for both models
- ROC curves comparing model performance

---

## Images

All visualizations are saved in the `img/` folder for reporting and presentation purposes.
