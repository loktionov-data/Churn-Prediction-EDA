# Churn Prediction EDA

This project is a first analytical step towards building a predictive model to identify customer churn in a bank. The dataset contains customer-level information and the target variable `Exited`, indicating whether the customer left the bank.

---

## Project Structure

- `eda.ipynb`: Exploratory data analysis (you are here)
- `preprocessing.py / preprocessing.ipynb`: Feature engineering and encoding
- `model.py / model.ipynb`: Model training, evaluation (XGBoost, metrics, etc.)

---

## Dataset

The dataset includes the following features:

- `CreditScore`, `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`, and the target `Exited`.

---

## Preprocessing during EDA

- Removed unused columns: `RowNumber`, `CustomerId`, `Surname`
- Filtered out unrealistic `Age` values (<20 or >65)
- Removed customers with `Tenure = 0`

---

## Key Insights

- Gender distribution is almost balanced, but slightly more men are present across all countries.
- Male users tend to have slightly higher estimated salaries and bank balances.
- Users aged **25–44** form the majority of the customer base.
- Most churned users are **females aged 35–54** from Germany and France.
- The most active users are also in the **25–44** age group, mostly from France.
- Product purchases: most users buy 1–2 products; higher purchases (3+) are more common among women.
- Users with longer tenure are concentrated in the 25–44 age groups.

---

## Next Steps

- Encode categorical features (`Geography`, `Gender`)
- Apply SMOTE if class imbalance is detected
- Train XGBoost model
- Evaluate using ROC curve, confusion matrix, and feature importance

---

## Images

Visualizations saved in the `img/` folder for use in reports or presentations.

---
