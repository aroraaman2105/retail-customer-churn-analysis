# Retail Customer Churn Analysis

An end-to-end data science project for identifying retail customers at risk of churn. It explores transaction data, builds a customer-level churn model, and presents churn patterns and predictions in an interactive Streamlit dashboard.

## Why this project?

Retail teams can use early churn-risk signals to prioritize customer outreach and tailor retention offers. This project demonstrates one way to turn purchase history into those signals.

## Dataset and churn definition

The project uses the [Online Retail II dataset](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci), a record of purchases made by a UK-based online retailer between December 2009 and December 2011. The data includes invoice, product, quantity, price, date, customer, and country information.

The source dataset does not include a churn label. This project defines churn as customer inactivity during a three-month observation window after the analysis period.

The raw and processed CSV files used by the project are included under `data/`. If you replace or download the source data, keep it in `data/raw/` and confirm that it matches the format expected by the notebooks.

## Workflow

1. **Explore and clean:** Inspect transactions, remove or handle invalid records, and explore purchasing patterns.
2. **Prepare customer features:** Build customer-level measures such as Recency, Frequency, Monetary value, Tenure, and country group.
3. **Train and evaluate:** Compare classification models and evaluate churn predictions using standard classification metrics.
4. **Explore results:** Use the notebooks and Streamlit dashboard to examine churn rates, model drivers, and customers flagged as at risk.

## Project structure

```text
.
├── data/
│   ├── raw/                 # Source transaction data
│   └── processed/           # Cleaned data, customer features, and predictions
├── documentation/           # Notes covering the project phases
├── models/                  # Saved churn model
├── notebooks/               # Analysis, feature engineering, and modeling workflow
├── src/
│   └── visualization_app.py # Streamlit dashboard
├── requirements.txt
└── README.md
```

## Tools

- Python
- pandas and NumPy
- scikit-learn and joblib
- Matplotlib, Seaborn, and Plotly
- Jupyter notebooks and Streamlit

## Get started

Clone the repository and open a terminal in its folder:

```bash
git clone https://github.com/aroraaman2105/retail-customer-churn-analysis.git
cd retail-customer-churn-analysis
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

On Windows:

```powershell
.venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

Install the project dependencies:

```bash
pip install -r requirements.txt
```

To run the notebooks, launch Jupyter from the project root. If it is not installed in your environment, install it first with `pip install jupyterlab`.

```bash
jupyter lab
```

Run the notebooks in workflow order:

1. `notebooks/eda.ipynb`
2. `notebooks/feature_engineering.ipynb`
3. `notebooks/model_training_and_evaluvation.ipynb`
4. `notebooks/dashboard_insights.ipynb`

The dashboard notebook generates customer predictions. The Streamlit app also expects the processed prediction data and saved model in `data/processed/` and `models/`.

Start the dashboard from the project root:

```bash
streamlit run src/visualization_app.py
```

## Model results and interpretation

The existing project notes report the following test-set results for the selected Gradient Boosting classifier:

| Metric | Score |
|---|---:|
| Accuracy | 0.7419 |
| Precision | 0.7815 |
| Recall | 0.7553 |
| F1 score | 0.7682 |
| ROC-AUC | 0.8107 |

The recorded confusion matrix is `[[415, 158], [183, 565]]`. Treat these figures as the results documented for the current model; rerun the modeling notebook to validate them if the data or training workflow changes.

The project examines Recency, Monetary value, Frequency, Tenure, and country-related features as potential churn signals. These are associations in the model, not proof that any one factor causes churn.

