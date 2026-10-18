# Gym Churn Prediction and Customer Segmentation

This project analyzes customer churn for a gym chain and builds a retention strategy using data-driven modeling and segmentation.

## Project goal

Model Fitness wants to identify which customers are most likely to leave in the next month and understand which types of customers are most at risk. The analysis combines:

- Exploratory data analysis (EDA)
- Churn prediction with machine learning
- Customer segmentation with clustering
- Business recommendations for retention

A customer is considered churned when they have not visited the gym for a month.

## Business context

The main objective is to help the gym reduce churn by identifying high-risk customers before they leave. The project focuses on a few practical questions:

- Which customer characteristics are most associated with churn?
- Which model best predicts churn in this context?
- What customer groups exist, and which are more likely to churn?
- What actions can reduce churn in the first months of the customer lifecycle?

## Repository structure

```text
gym-churn-prediction-clustering/
├── data/
│   ├── gym_churn_clean.csv
│   └── gym_churn_us.csv
├── notebooks/
│   ├── 01_data_preparation_eda.ipynb
│   ├── 02_churn_prediction.ipynb
│   └── 03_customer_clustering.ipynb
├── requirements.txt
├── README.md
└── .venv/
```

## Datasets

The project uses two CSV files in `data/`:

- `gym_churn_us.csv`: raw customer dataset
- `gym_churn_clean.csv`: prepared dataset used by the predictive and clustering notebooks

The dataset contains customer-level behavioral and contractual features, with `Churn` as the target variable. Key variables include:

- `gender`
- `Near_Location`
- `Partner`
- `Promo_friends`
- `Phone`
- `Age`
- `Lifetime`
- `Contract_period`
- `Month_to_end_contract`
- `Group_visits`
- `Avg_class_frequency_total`
- `Avg_class_frequency_current_month`
- `Avg_additional_charges_total`

## Workflow

### 1. Data preparation and EDA
Notebook: `notebooks/01_data_preparation_eda.ipynb`

This notebook:

- loads the data
- checks for missing values, duplicates and data quality issues
- normalizes column naming
- explores churn patterns by feature
- identifies the strongest churn drivers

Main EDA findings:

- The dataset has 4,000 customers and no missing values or duplicates.
- The strongest churn signals are lifetime, current-month visit frequency, age and contract period.
- Customers who churn are usually new members, on 1-month contracts, younger and visiting less often.
- Gender and phone number are not meaningfully related to churn.
- The first weeks after joining are a critical retention period.

### 2. Churn prediction
Notebook: `notebooks/02_churn_prediction.ipynb`

This notebook trains and compares two classification models:

- Logistic regression
- Random forest

The models are evaluated on accuracy, precision and recall. For this retention problem, recall is especially important because it is more costly to miss a customer who is about to churn than to contact someone who would have stayed.

Model performance:

- Logistic regression: accuracy 0.92, precision 0.85, recall 0.84
- Random forest: accuracy 0.91, precision 0.85, recall 0.77

Conclusion:

- Logistic regression is the preferred model because it has the higher recall and is easier to interpret for business stakeholders.
- The strongest features in the churn model are lifetime, contract period, current-month visit frequency and age.
- The model suggests that commitment and engagement are the major retention drivers.

### 3. Customer clustering
Notebook: `notebooks/03_customer_clustering.ipynb`

This notebook groups customers using hierarchical clustering and K-means to find distinct customer profiles and compare their churn rates.

Result:

- Five customer clusters were created.
- High-risk groups:
  - Cluster 0: churn rate 0.58
  - Cluster 3: churn rate 0.41
- Loyal groups:
  - Cluster 4: churn rate 0.00
  - Cluster 1: churn rate 0.03
  - Cluster 2: churn rate 0.13

The analysis shows that the highest-risk customers are often new, low-engagement members, while the most loyal groups are older, longer-tenured and more engaged customers.

## Key findings

1. New members are the highest churn risk.
   - Churn is concentrated in the first months after joining.
   - Lifetime is the single strongest churn predictor.

2. Contract length matters a lot.
   - Short contracts (1 month) are strongly associated with higher churn.
   - Longer contracts are linked to lower churn.

3. Visit frequency is a leading early warning signal.
   - Customers who visit less often, especially if they are dropping off in the current month, are more likely to churn.

4. Engagement and social connection reduce churn.
   - Group visits, partner-company membership and the bring-a-friend referral offer are associated with lower churn.

5. Gender and phone number do not materially affect churn.
   - These attributes are not useful for retention targeting in this dataset.

## Recommendations

1. Protect the first months after signup
   - Offer a free trainer session during the first two weeks.
   - Reach out to every new customer at the end of month one to collect feedback and solve issues.

2. Encourage longer commitments
   - Offer discounts or incentives to upgrade from 1-month to 6- or 12-month contracts.
   - Make the value of longer-term contracts more visible during sign-up.

3. Monitor visit frequency monthly
   - Use the churn model each month to flag high-risk members.
   - Send personalized reminders, classes or promotions to at-risk customers.

4. Build community and loyalty
   - Promote group sessions and referral programs.
   - Expand partner-company and bring-a-friend offers to increase retention.

5. Prioritize customer segments strategically
   - Focus retention campaigns on Cluster 0 and Cluster 3 first.
   - Use loyalty rewards for long-tenured members in high-retention clusters.

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

Windows (PowerShell):

```powershell
.venv\Scripts\Activate.ps1
```

macOS / Linux:

```bash
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

Open the notebooks in `notebooks/` in order:

1. `01_data_preparation_eda.ipynb`
2. `02_churn_prediction.ipynb`
3. `03_customer_clustering.ipynb`

## Tech stack

- Python
- pandas
- NumPy
- matplotlib
- seaborn
- scikit-learn
- SciPy
- Jupyter Notebook

## Summary

This project demonstrates a complete churn analytics workflow for a gym business: data exploration, predictive modeling, segmentation and actionable retention recommendations. The strongest business insight is that early member engagement and long-term commitment are the clearest levers for reducing churn.
