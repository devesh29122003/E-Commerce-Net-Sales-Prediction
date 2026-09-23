# E-Commerce Net Sales Prediction

Machine learning regression project that predicts order-level **net sales** for an e-commerce
platform from order, customer, and payment attributes.

Submitted as part of the **IBM SkillsBuild Data Analytics with AI Academic Internship Program**,
conducted by **BharatCares** in association with **AICTE**.

## Project Description

E-commerce platforms generate large volumes of order-level transactional data. This project
builds and compares several regression models to predict the **net sales value of an order**
using features such as sales channel, customer segment, payment method, discounts, shipping
cost, product cost, and customer purchase history.

The workflow covers the full data science pipeline: exploratory data analysis (EDA), data
cleaning, feature engineering (with explicit handling of data leakage), model training,
evaluation, and interpretation via feature importance.

**Models compared:** Linear Regression, Ridge Regression, Random Forest Regressor, XGBoost Regressor
**Best model:** XGBoost Regressor — **R² = 0.9965**, **MAE ≈ 25.3**, **RMSE ≈ 70.0** on a held-out test set

## Dataset

- **File:** `ecommerce_sales_customer_analytics_150k-selected-columns.csv`
- **Rows:** 66,849 orders · **Columns:** 25
- **Target variable:** `net_sales`
- Fields include order details (date, time, status, channel), customer demographics and
  segment, payment method/status, currency, discounts, tax, shipping cost, product cost,
  profit, customer lifetime value, and repeat-customer flags.
- Note: this CSV was provided as part of the internship assignment; if you are sourcing your
  own copy, replace this section with the dataset's original link (e.g. Kaggle).

> ⚠️ `profit` and `profit_margin_percentage` are excluded from the model features because they
> are mathematically derived from `net_sales`, which would otherwise leak the target into the
> model.

## Technologies Used

| Category | Tools |
|---|---|
| Language | Python 3 |
| Data handling | pandas, numpy |
| Visualization | matplotlib, seaborn |
| Machine learning | scikit-learn (Linear/Ridge Regression, Random Forest, preprocessing pipeline), XGBoost |
| Environment | Jupyter Notebook |
| Model persistence | joblib |

## Project Structure

```
.
├── YourName_ProjectName.ipynb     # Full analysis + modeling notebook (code + outputs)
├── requirements.txt                # Python dependencies
├── YourName_ProjectReport.docx     # Full written project report
├── README.md                       # This file
└── ecommerce_sales_customer_analytics.csv   # Dataset (place in same folder as notebook)
```

## Setup & Run Instructions

1. **Clone / download** this project folder and place the dataset CSV alongside the notebook
   (rename it to match the path used in the notebook, or update the `pd.read_csv(...)` path).

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv venv
   source venv/bin/activate      # Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter and run the notebook**
   ```bash
   jupyter notebook YourName_ProjectName.ipynb
   ```
   Then run all cells (`Kernel → Restart & Run All`).

5. **Output:** the notebook prints EDA summaries, model comparison metrics, generates
   visualizations, and saves the best-performing model pipeline to `best_net_sales_model.pkl`.

## Key Results

| Model | MAE | RMSE | R² Score |
|---|---|---|---|
| Linear Regression | 133.97 | 194.88 | 0.9726 |
| Ridge Regression | 133.98 | 194.88 | 0.9726 |
| Random Forest | 27.63 | 82.37 | 0.9951 |
| **XGBoost (Best)** | **25.34** | **70.04** | **0.9965** |

The strongest predictors of net sales were order-level financial fields — `product_cost`,
`shipping_cost`, `tax_amount`, and `discount_amount` — consistent with typical e-commerce
pricing structure.

## Author

[Your Name] — IBM SkillsBuild Data Analytics with AI Academic Internship Program
