 Fraudulent Transaction Prediction
Predicting whether a financial transaction is fraudulent using machine learning.

## Project Goal
To detect fraudulent transactions in financial data, enabling financial institutions to flag and prevent suspicious activity in real-time.

## Dataset
The dataset contains anonymized transaction information with key features such as:

- **step**: Time step of the transaction (in hours)
- **type**: Transaction type (e.g., CASH_IN, CASH_OUT, DEBIT, PAYMENT, TRANSFER)
- **amount**: Transaction amount
- **oldbalanceOrg**: Initial balance of the sender before transaction
- **newbalanceOrig**: New balance of the sender after transaction
- **oldbalanceDest**: Initial balance of the receiver before transaction
- **newbalanceDest**: New balance of the receiver after transaction
- **isFraud**: Target variable (1 = fraudulent transaction, 0 = legitimate transaction)

**Sample Data:**
| step | type     | amount   | oldbalanceOrg | newbalanceOrig | oldbalanceDest | newbalanceDest | isFraud |
|------|----------|----------|---------------|----------------|----------------|----------------|---------|
| 1    | PAYMENT  | 9839.64  | 170136.00     | 160296.36      | 0.00           | 0.00           | 0       |
| 1    | PAYMENT  | 1864.28  | 21249.00      | 19384.72       | 0.00           | 0.00           | 0       |
| 1    | TRANSFER | 181.00   | 181.00        | 0.00           | 0.00           | 0.00           | 1       |

## Method
1. **Data Cleaning & Preprocessing**
   - Removed irrelevant columns (e.g., IDs if present)
   - Handled missing values
   - Capped outliers using IQR method
   - Checked multicollinearity using VIF

2. **Feature Scaling**
   - Standardized numeric features using `StandardScaler`

3. **Class Imbalance Handling**
   - Applied **SMOTE** to oversample minority (fraud) class

4. **Model Training**
   - Logistic Regression
   - Random Forest Classifier

5. **Model Evaluation**
   - Accuracy, Precision, Recall, F1-score, ROC-AUC
   - Confusion Matrix

## Results
- **Best Model**: Random Forest Classifier
- **Performance** (example — replace with your actual results):
  - Accuracy: 99.69%
  - Precision: 97%
  - Recall: 95%
  - ROC-AUC: 0.99
- **Insights**:
  - Certain transaction types (e.g., TRANSFER, CASH_OUT) are more prone to fraud
  - Large transaction amounts with zero destination balance raise suspicion

## How to Run
1. Clone this repository:
```bash
git clone https://github.com/HarshVardhan-DSAI/fraudulent-transaction-prediction.git
