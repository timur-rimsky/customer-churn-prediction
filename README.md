# Customer Churn Prediction

## Project Overview

This project focuses on predicting customer churn using machine learning models.

Customer churn prediction is an important business task because it helps identify customers who are likely to leave a service. Early detection of such customers allows a company to take retention actions in advance, such as offering support, discounts, personalized communication, or improved service conditions.

The target variable in this project is `Churn`.

* `0` — customer did not churn
* `1` — customer churned

The main goal of this project is to compare several machine learning models and select the best one for identifying customers at risk of churn.

---

## Dataset

This project uses the Telco Customer Churn dataset.

The dataset is available on Kaggle:

[Telco Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

The dataset contains customer information such as:

* demographic information;
* contract type;
* payment method;
* internet service type;
* monthly charges;
* total charges;
* customer tenure;
* additional services;
* churn status.

The original dataset contains 7043 rows and 21 columns.

Due to licensing and redistribution considerations, the dataset file is not included in this repository. To reproduce the project, download the dataset from Kaggle and place the file in the project folder with the following name:

```text
Telco-Customer-Churn.csv
```

During data cleaning, the `TotalCharges` column was converted from object type to numeric format. After conversion, 11 missing values appeared. Since this was a very small part of the dataset, these rows were removed.

The final dataset contains 7032 rows.

---

## Tools and Libraries

The project was completed using Python and the following libraries:

* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn

Main scikit-learn tools used:

* `train_test_split`
* `LogisticRegression`
* `DecisionTreeClassifier`
* `RandomForestClassifier`
* `accuracy_score`
* `precision_score`
* `recall_score`
* `f1_score`
* `classification_report`
* `confusion_matrix`

---

## Project Workflow

The project includes the following steps:

1. Project overview
2. Data loading
3. Data overview
4. Exploratory data analysis
5. Data cleaning and feature preparation
6. Target encoding
7. Categorical feature encoding
8. Train/test split
9. Baseline model
10. Logistic Regression
11. Decision Tree
12. Limited-depth Decision Tree
13. Random Forest
14. Limited-depth Random Forest
15. Model comparison
16. Feature importance analysis
17. Final conclusions

---

## Exploratory Data Analysis

During exploratory data analysis, several churn patterns were identified.

Customers with month-to-month contracts had the highest churn rate. Customers with one-year and two-year contracts were less likely to churn.

Customers using fiber optic internet service had a higher churn rate compared to other internet service groups.

Customers using electronic check as a payment method also showed a higher churn rate.

Senior citizens had a higher churn rate compared to non-senior customers.

These findings suggest that contract type, internet service type, payment method, and customer group may be important factors for churn prediction.

---

## Data Cleaning and Feature Preparation

Several preprocessing steps were completed before model training:

* `TotalCharges` was converted from object type to numeric format;
* missing values were removed;
* the target variable `Churn` was encoded into numeric format;
* `customerID` was removed because it is only a technical identifier;
* categorical variables were encoded using one-hot encoding;
* the dataset was split into training and test sets using an 80/20 ratio;
* stratification was applied to preserve the original churn class distribution.

---

## Models Used

The following models were trained and compared:

1. Baseline model
2. Logistic Regression
3. Decision Tree
4. Limited-depth Decision Tree
5. Random Forest
6. Limited-depth Random Forest

The baseline model always predicts the majority class. It was used as a reference point to show why accuracy alone can be misleading in an imbalanced classification task.

---

## Model Results

The models were evaluated using the following metrics:

* accuracy
* precision
* recall
* F1-score

Since the target classes are imbalanced and the main business goal is to identify customers who are likely to churn, recall was treated as the most important metric.

Logistic Regression achieved the best overall performance among the trained models. It showed the strongest balance between accuracy, recall, F1-score, and interpretability.

---

## Best Model

The selected best model is:

**Logistic Regression**

Logistic Regression was selected because:

* it achieved the highest recall among the trained models;
* it had the best F1-score;
* it performed better than Decision Tree and Random Forest models on the most important churn metric;
* it is easier to interpret than tree-based ensemble models.

In a churn prediction task, recall is especially important because the business wants to identify as many customers at risk of leaving as possible. A model with low recall may miss many customers who are actually likely to churn.

---

## Feature Importance

Feature analysis was performed using Logistic Regression coefficients.

Positive coefficients are associated with a higher probability of churn.
Negative coefficients are associated with a lower probability of churn.

Features associated with higher churn probability included:

* `InternetService_Fiber optic`
* `StreamingTV_Yes`
* `StreamingMovies_Yes`
* `MultipleLines_Yes`
* `PaymentMethod_Electronic check`

Features associated with lower churn probability included:

* `Contract_Two year`
* `Contract_One year`
* `OnlineSecurity_Yes`
* `TechSupport_Yes`
* `Dependents_Yes`

These findings are consistent with the exploratory data analysis. Customers with fiber optic internet service, electronic check payment method, and short-term contracts were more likely to churn. Customers with longer contracts, online security, and tech support were less likely to churn.

---

## Key Findings

The main findings of the project are:

* customers with month-to-month contracts have the highest churn risk;
* customers with one-year and two-year contracts are less likely to churn;
* fiber optic internet service is associated with higher churn probability;
* electronic check payment method is associated with higher churn probability;
* senior citizens have a higher churn rate compared to non-senior customers;
* Logistic Regression performed best among the tested models;
* recall is more important than accuracy for this churn prediction task.

---

## Final Conclusions

This project shows that customer churn can be predicted using machine learning models and customer behavior data.

The baseline model demonstrated that accuracy alone can be misleading in an imbalanced classification problem. Although most customers did not churn, a model that always predicts the majority class cannot identify customers at risk.

Several machine learning models were trained and compared. Logistic Regression showed the best overall performance for this task, especially in terms of recall and F1-score. It was selected as the final model because it provides a strong balance between predictive performance and interpretability.

The project also showed that customer churn is strongly associated with contract type, internet service type, payment method, and additional services. These insights can help a business better understand customer behavior and design more effective retention strategies.

---

## Future Improvements

Possible future improvements include:

* tuning model hyperparameters;
* adjusting the classification threshold to improve recall;
* applying feature scaling;
* testing additional models such as Gradient Boosting or XGBoost;
* using cross-validation for more stable model evaluation;
* applying techniques for class imbalance, such as class weights or oversampling;
* analyzing probability scores instead of only class predictions;
* creating customer risk segments based on predicted churn probability.

---

## How to Run This Project

1. Clone this repository:

```bash
git clone https://github.com/timur-rimsky/customer-churn-prediction.git
```

2. Download the Telco Customer Churn dataset from Kaggle:

[Telco Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

3. Place the downloaded dataset file in the project folder with the following name:

```text
Telco-Customer-Churn.csv
```

4. Open the notebook:

```text
customer_churn_prediction.ipynb
```

5. Run all cells from top to bottom.

---

## Repository Structure

```text
customer-churn-prediction/
│
├── customer_churn_prediction.ipynb
├── README.md
└── .gitignore
```

The dataset file `Telco-Customer-Churn.csv` is not included in this repository. It should be downloaded separately from Kaggle and placed in the project folder before running the notebook.

---

## Author

Project completed as part of Data Science portfolio training.
