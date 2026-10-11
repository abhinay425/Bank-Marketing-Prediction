# Bank Marketing Subscription Prediction

## Project Overview
This project uses machine learning to predict whether a customer will subscribe to a bank term deposit as part of a bank marketing campaign.

The project uses the Portuguese Bank Marketing dataset and follows a data-science workflow covering data cleaning, exploratory data analysis (EDA), preprocessing, model training, evaluation, and business recommendations.

## Objectives
- Explore customer and campaign characteristics through EDA.
- Clean and preprocess the dataset.
- Handle the imbalance between customers who subscribed (`yes`) and did not subscribe (`no`).
- Train and compare classification models.
- Tune model hyperparameters using stratified cross-validation.
- Identify important features and provide recommendations for the bank marketing team.

## Dataset
Expected dataset path:

```text
Data/
└── bank-additional/
    └── bank-additional-full.csv
```

The dataset contains customer, campaign, and economic information. The target column is `y`, which indicates whether the customer subscribed to a term deposit.

**Dataset note:** Check the dataset's license and sharing terms before redistributing it. If redistribution is not permitted, download it from the original source and place it at the path shown above.

## Technologies Used
- Python
- Jupyter Notebook
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- XGBoost

## Project Workflow
1. Load the dataset and inspect its structure.
2. Check duplicates and review unknown categorical values.
3. Perform EDA, including target distribution, feature distributions, category comparisons, correlation analysis, and outlier analysis.
4. Prepare the features and target variable.
5. Split the data using stratified train-test splitting.
6. Apply numerical scaling and categorical one-hot encoding through preprocessing pipelines.
7. Address class imbalance using class weights or `scale_pos_weight`, where applicable.
8. Train and compare classification models.
9. Tune selected models with `GridSearchCV` and stratified cross-validation.
10. Evaluate models using accuracy, precision, recall, F1-score, ROC-AUC, classification reports, and diagnostic curves.
11. Examine feature importance and consider business implications.
12. Recommend strategies for targeting potential subscribers.


## Model Results
The tuned Random Forest model achieved the following test-set results in this project:

| Metric | Result |
|---|---:|
| Accuracy | 85.41% |
| Precision | 40.62% |
| Recall for the `yes` class | 63.90% |
| F1-score | 49.66% |
| ROC-AUC | 81.47% |

Random Forest was selected as the recommended model because it achieved the highest ROC-AUC and F1-score among the tuned models. XGBoost achieved slightly higher recall for the `yes` class, while Gradient Boosting achieved higher accuracy but lower recall. Model selection should reflect the bank's business priorities and the cost of false-positive and false-negative predictions.

## Key Challenges
- Unknown values in categorical columns.
- Imbalanced target classes.
- Avoiding data leakage from `duration`, which is only known after a call.
- Encoding categorical features and scaling numerical features.
- Strong correlations among some economic variables.
- Balancing precision and recall when selecting a model.

## Business Recommendations
- Rank customers using predicted subscription probabilities.
- Prioritize likely subscribers while considering marketing capacity and campaign costs.
- Use previous campaign outcomes and customer segments to inform outreach.
- Avoid excessive repeated contacts.
- Monitor real campaign outcomes and reassess model performance over time.

## Limitations and Future Improvements
The model still produces false-positive predictions, and the F1-score for the minority `yes` class remains modest. Possible next steps include:
- Select the decision threshold using validation data or cross-validation, then evaluate it on a held-out test set.
- Explore probability calibration and additional feature engineering.
- Compare further model and sampling strategies where appropriate.
- Monitor performance over time and retrain when customer behavior or economic conditions change.

## How to Run
1. Clone or download this repository.
2. Install the dependencies listed in `requirements.txt`.
3. Place `bank-additional-full.csv` in `Data/bank-additional/`, or update the dataset path in the notebook.
4. Start Jupyter Notebook or JupyterLab.
5. Open `Bank_Marketing_Prediction.ipynb` and run the cells in order.

Install dependencies:

```bash
python -m pip install -r requirements.txt
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

## Repository Contents
```text
Bank-Marketing-Prediction/
├── Bank_Marketing_Prediction.ipynb
├── README.md
├── requirements.txt
├── Data/
│   └── bank-additional/
│       └── bank-additional-full.csv   # Add locally if permitted
└── images/                            # Optional project charts
```

## Disclaimer
This project is for educational and portfolio purposes. Predictions should support, not replace, business judgment. Confirm data licensing and privacy requirements before using or publishing any dataset.
