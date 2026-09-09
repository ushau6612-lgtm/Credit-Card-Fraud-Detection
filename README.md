# Credit-Card-Fraud-Detection
Credit Card Fraud Detection is a machine learning classification project that identifies potentially fraudulent credit card transactions. 
# Credit Card Fraud Detection

## Overview

Credit Card Fraud Detection is a machine learning classification project designed to identify potentially fraudulent credit card transactions.

The project analyzes transaction characteristics and uses machine learning to classify each transaction as either a normal transaction or a potentially fraudulent transaction.

This project demonstrates a complete binary classification workflow, including data loading, data cleaning, class distribution analysis, feature preparation, model training, prediction, evaluation, probability estimation, feature analysis, and visualization.

## Objective

The main objective of this project is to build a machine learning model that can identify potentially fraudulent transactions based on transaction characteristics.

The project aims to:

* Analyze credit card transaction data
* Explore normal and fraudulent transaction patterns
* Handle missing values
* Examine transaction class distribution
* Prepare transaction features for machine learning
* Address class imbalance during model training
* Train a binary classification model
* Predict potentially fraudulent transactions
* Calculate fraud probability
* Evaluate classification performance
* Identify influential transaction features
* Generate useful data visualizations

## Dataset

The project uses a synthetic credit card transaction dataset created for educational and classroom machine learning practice.

### Dataset Features

| Feature               | Description                                                      |
| --------------------- | ---------------------------------------------------------------- |
| transaction_id        | Unique identifier for each transaction                           |
| amount                | Transaction amount                                               |
| hour                  | Hour at which the transaction occurred                           |
| distance_from_home_km | Distance of the transaction from the customer's home             |
| merchant_risk_score   | Risk score associated with the merchant                          |
| transactions_last_24h | Number of transactions made during the previous 24 hours         |
| card_present          | Indicates whether the physical card was present                  |
| international         | Indicates whether the transaction was international              |
| online_transaction    | Indicates whether the transaction was made online                |
| fraud                 | Target variable indicating whether the transaction is fraudulent |

### Target Variable

`fraud`

The target variable contains two classes:

```text
0 = Normal Transaction
1 = Fraudulent Transaction
```

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn

## Machine Learning Algorithm

The project uses **Logistic Regression** for binary classification.

Logistic Regression is appropriate for this project because the target variable contains two possible outcomes: normal transaction and fraudulent transaction.

The model is configured with `class_weight="balanced"` to give additional consideration to the minority class. This is particularly useful for fraud detection, where fraudulent transactions may occur less frequently than normal transactions.

## Features Used for Prediction

The following transaction features are used by the model:

* Amount
* Hour
* Distance from home
* Merchant risk score
* Number of transactions in the last 24 hours
* Card present status
* International transaction status
* Online transaction status

The `transaction_id` column is excluded because it is only an identifier and does not provide meaningful predictive information.

## Data Preparation

The project performs the following data preparation steps:

1. Load the transaction dataset using Pandas.
2. Display the first five records.
3. Check the dataset shape.
4. Check for missing values.
5. Fill missing numerical values using median values.
6. Display the transaction class distribution.
7. Calculate the percentage of fraudulent transactions.
8. Separate features from the target variable.
9. Remove the transaction identifier.
10. Split the dataset into training and testing data.
11. Standardize the features using `StandardScaler`.

## Train-Test Split

The dataset is divided into:

* 80% training data
* 20% testing data

A `random_state` of 42 is used to ensure reproducibility.

The split uses `stratify=y` so that the proportion of normal and fraudulent transactions is maintained across the training and testing datasets.

## Model Pipeline

A Scikit-learn Pipeline is used to combine feature scaling and model training.

The pipeline contains:

1. `StandardScaler`
2. `LogisticRegression`

The Logistic Regression classifier uses:

```text
class_weight = balanced
max_iter = 2000
random_state = 42
```

Class balancing helps the model give appropriate consideration to fraudulent transactions when the dataset contains unequal class frequencies.

## Model Evaluation

The project evaluates the model using several classification metrics.

### Accuracy

Accuracy represents the percentage of correctly classified transactions among all transactions.

### Precision

Precision measures how many transactions predicted as fraudulent are actually fraudulent.

High precision means the model produces fewer false fraud alerts.

### Recall

Recall measures how many actual fraudulent transactions are successfully detected by the model.

Recall is particularly important in fraud detection because failing to identify fraudulent transactions can be costly.

### Classification Report

The classification report provides precision, recall, F1-score, and support for both normal and fraudulent transaction classes.

### Confusion Matrix

The confusion matrix shows:

* True Negatives
* False Positives
* False Negatives
* True Positives

These values provide a detailed view of the model's classification performance.

## Fraud Probability Prediction

The model can calculate the probability that a transaction is fraudulent using `predict_proba()`.

The project includes an example transaction with the following characteristics:

```text
Amount: 950.00
Hour: 2
Distance from Home: 120 km
Merchant Risk Score: 0.90
Transactions in Last 24 Hours: 9
Card Present: 0
International: 1
Online Transaction: 1
```

The model predicts whether this transaction is potentially fraudulent and calculates its estimated fraud probability.

## Feature Importance Analysis

The project uses Logistic Regression coefficients to identify influential transaction features.

Each feature receives a regression coefficient.

* Positive coefficients indicate a positive relationship with the fraud class.
* Negative coefficients indicate a negative relationship with the fraud class.
* Larger absolute coefficient values indicate stronger influence within the standardized feature space.

The program displays the transaction features along with their coefficients and ranks them based on their absolute importance.

## Visualizations

The project generates two visualization files.

### 1. Fraud Transaction Analysis

File:

```text
fraud_transaction_analysis.png
```

This scatter plot examines the relationship between transaction amount and merchant risk score while distinguishing normal and fraudulent transactions.

### 2. Fraud Class Distribution

File:

```text
fraud_class_distribution.png
```

This bar chart displays the number of normal and fraudulent transactions in the dataset.

## Project Structure

```text
Credit_Card_Fraud_Detection/
│
├── README.md
├── credit_card_fraud_detection.py
├── credit_card_transactions.csv
├── requirements.txt
│
├── fraud_transaction_analysis.png
└── fraud_class_distribution.png
```

The visualization files are generated when the Python program is executed.

## Installation

Make sure Python is installed on your computer.

Install the required dependencies using:

```bash
pip install -r requirements.txt
```

## Requirements

The project requires the following Python libraries:

```text
pandas
numpy
matplotlib
scikit-learn
```

## How to Run

Open a terminal or command prompt in the project directory.

Install the required packages:

```bash
pip install -r requirements.txt
```

Run the Python script:

```bash
python credit_card_fraud_detection.py
```

The program will:

1. Load the transaction dataset.
2. Display the first five records.
3. Display the dataset shape.
4. Check for missing values.
5. Clean missing numerical values.
6. Display the transaction class distribution.
7. Calculate the fraud percentage.
8. Prepare features and target variables.
9. Split the dataset into training and testing sets.
10. Scale the transaction features.
11. Train the Logistic Regression model.
12. Generate fraud predictions.
13. Calculate accuracy, precision, and recall.
14. Display the classification report.
15. Display the confusion matrix.
16. Predict a new transaction.
17. Calculate the fraud probability of the new transaction.
18. Display influential transaction features.
19. Generate fraud analysis visualizations.

## Machine Learning Workflow

```text
Credit Card Transaction Dataset
              |
              v
        Data Loading
              |
              v
       Data Exploration
              |
              v
     Missing Value Handling
              |
              v
    Class Distribution Analysis
              |
              v
      Feature Preparation
              |
              v
       Train-Test Split
              |
              v
       Feature Scaling
              |
              v
      Logistic Regression
              |
              v
          Prediction
              |
              v
       Model Evaluation
              |
       +------+------+------+
       |      |      |      |
       v      v      v      v
   Accuracy Precision Recall Confusion
                              Matrix
              |
              v
     Fraud Probability
              |
              v
     Feature Analysis
              |
              v
        Visualization
```

## Key Learning Outcomes

This project provides practical experience with:

* Binary classification
* Fraud detection
* Logistic Regression
* Data cleaning
* Missing-value handling
* Class distribution analysis
* Class imbalance handling
* Feature scaling
* Train-test splitting
* Stratified sampling
* Classification metrics
* Confusion matrices
* Probability prediction
* Logistic Regression coefficients
* Data visualization
* Scikit-learn pipelines

## Why Precision and Recall Matter

Accuracy alone may not provide a complete picture of fraud-detection performance, particularly when fraudulent transactions are less common than normal transactions.

Precision helps measure the reliability of fraud alerts, while recall measures the model's ability to detect actual fraudulent transactions.

For a real-world fraud detection system, both metrics should be considered along with business costs associated with false positives and false negatives.

## Limitations

This project uses a synthetic dataset and a relatively simple Logistic Regression model.

Real-world credit card fraud detection systems may require:

* Much larger datasets
* More transaction history
* Advanced feature engineering
* Time-based transaction patterns
* Customer spending behavior
* Merchant behavior analysis
* Real-time transaction monitoring
* Advanced machine learning models
* Continuous model retraining
* Fraud investigation workflows

The model should therefore be considered an educational demonstration rather than a production-ready fraud detection system.

## Dataset Disclaimer

The included transaction dataset is synthetic and created for educational and classroom machine learning practice.

It does not contain real credit card numbers, real customer information, or actual banking transactions.

## Security and Privacy

No real payment-card information should be added to this project.

Never use real credit card numbers, CVV codes, PINs, passwords, or other sensitive financial information in the dataset.

## Conclusion

This project demonstrates how machine learning can be applied to credit card fraud detection using transaction-level information.

It covers the complete classification workflow, including data cleaning, class distribution analysis, feature scaling, class balancing, Logistic Regression training, prediction, evaluation, probability estimation, feature analysis, and visualization.

The project provides a practical foundation for understanding how machine learning can be used to identify potentially fraudulent transactions.

## Author

Credit Card Fraud Detection Machine Learning Project
