Fraudulent Transaction Prediction
A machine learning project to detect fraudulent banking transactions by analyzing transaction records. The system uses data preprocessing, feature engineering, and machine learning models (Logistic Regression & Random Forest) to classify transactions as fraud or legitimate.

Project Goal
To proactively identify fraudulent transactions so that banks can block them in real-time and reduce financial losses.

Dataset
The dataset contains 6.3M+ anonymized bank transactions with the following key features:

step – time step in hours

type – type of transaction (PAYMENT, TRANSFER, CASH_IN, CASH_OUT, etc.)

amount – amount transferred

nameOrig – origin account ID (removed for modeling)

oldbalanceOrg/newbalanceOrig – origin account balance before & after transaction

nameDest – destination account ID (removed for modeling)

oldbalanceDest/newbalanceDest – destination account balance before & after transaction

isFraud – target variable (1 = fraudulent, 0 = legitimate)

isFlaggedFraud – flagged by the bank's rule-based system

Sample rows:

step	type	amount	oldbalanceOrg	newbalanceOrig	oldbalanceDest	newbalanceDest	isFraud
1	PAYMENT	9839.64	170136.00	160296.36	0.00	0.00	0
1	TRANSFER	181.00	181.00	0.00	0.00	0.00	1
1	CASH_OUT	181.00	181.00	0.00	21182.00	0.00	1
Methodology
Data Cleaning

Verified no missing values.

Outliers capped using IQR method for key features (amount & balances) to prevent loss of crucial fraud cases.

Removed multicollinear features (VIF > 10).

Feature Engineering

Removed high-cardinality IDs (nameOrig, nameDest).

One-hot encoded transaction type.

Standardized numeric features for Logistic Regression.

Handling Class Imbalance

Applied SMOTE to oversample fraud cases.

Model Training

Logistic Regression – baseline interpretable model.

Random Forest Classifier – higher complexity, better performance.

Evaluation Metrics

Accuracy, Precision, Recall, F1-score, ROC-AUC.

Special focus on Recall to minimize missed fraud.

Results
Model	Accuracy	Precision	Recall	F1 Score	ROC-AUC
Logistic Regression	95.26%	95.61%	94.86%	95.24%	0.991
Random Forest	99.80%	99.69%	99.92%	99.80%	0.9998
Random Forest outperformed Logistic Regression in all metrics, especially Recall & ROC-AUC, making it the preferred choice.

Key Insights
Fraudsters most commonly use TRANSFER and CASH_OUT types.

Fraud transactions often involve large amounts & sudden account balance drops.

Recommendations
Implement real-time alerts for high-risk transactions.

Require multi-factor authentication for large transfers and cash-outs.

Monitor sudden, unusual changes in balances.

Regularly retrain the model to detect evolving fraud patterns.


📜 About
A complete fraud detection system built using Python & Machine Learning, from data preprocessing to model evaluation, ready for integration into banking infrastructure.

