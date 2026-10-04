# gym-churn-prediction-clustering

Customer churn prediction and segmentation for a gym chain using logistic regression, random forest and K-means clustering, with data-driven retention recommendations.

## Project Overview

Model Fitness, a gym chain, wants to build a data-driven customer retention strategy. A customer is considered churned if they have not visited the gym for a month.

The goals of this project are to:

- Predict the probability of churn (for the following month) for each customer
- Build profiles of typical customers by identifying the most distinct groups
- Analyze the factors that most impact churn
- Draw conclusions and recommend measures to reduce churn

## Dataset

`data/gym_churn_us.csv` contains customer data for a given month, plus information about the previous month.

| Column | Description |
|---|---|
| `Churn` | Whether the customer churned in the month in question (target) |
| `gender` | Customer gender |
| `Near_Location` | Whether the customer lives or works near the gym |
| `Partner` | Whether the customer is an employee of a partner company |
| `Promo_friends` | Whether the customer signed up through a "bring a friend" offer |
| `Phone` | Whether the customer provided a phone number |
| `Age` | Customer age |
| `Lifetime` | Months since the customer first came to the gym |
| `Contract_period` | Contract length: 1, 6 or 12 months |
| `Month_to_end_contract` | Months remaining until the contract expires |
| `Group_visits` | Whether the customer takes part in group sessions |
| `Avg_class_frequency_total` | Average weekly visits over the customer's lifetime |
| `Avg_class_frequency_current_month` | Average weekly visits in the current month |
| `Avg_additional_charges_total` | Total spent on other gym services (café, merchandise, massage, etc.) |

## Project Structure

```
gym-churn-prediction-clustering/
├── data/
│   └── gym_churn_us.csv
├── notebooks/
│   ├── 01_data_preparation_eda.ipynb
│   ├── 02_churn_prediction.ipynb
│   └── 03_customer_clustering.ipynb
├── requirements.txt
└── README.md
```

## Methods

- **Exploratory data analysis:** descriptive statistics, feature distributions by churn status, correlation matrix
- **Classification:** logistic regression and random forest, evaluated on accuracy, precision and recall
- **Clustering:** hierarchical clustering (dendrogram) to estimate the number of clusters, followed by K-means (n=5) on standardized features

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/gym-churn-prediction-clustering.git
cd gym-churn-prediction-clustering
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

Activate it:

```bash
# Windows (PowerShell)
.venv\Scripts\Activate.ps1

# Windows (Git Bash)
source .venv/Scripts/activate

# macOS / Linux
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Run the notebooks

```bash
jupyter notebook
```

Open the notebooks in the `notebooks/` folder and run them in order (01 → 02 → 03).

## Key Findings

_To be completed._

## Recommendations

_To be completed._

## Tools

Python · pandas · NumPy · Matplotlib · seaborn · scikit-learn · SciPy · Jupyter
