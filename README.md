# Bank Marketing Campaign Analysis

## Links
- [Dashboard](https://lookerstudio.google.com/reporting/3f25786a-fe18-41ea-9d61-16b640088ba4)

  **If you want to try the prediction directly, check out the link below:**  
- [Streamlit](https://kelompokalpha.streamlit.app/)  
  - You can test it using `X_test1` **(Download the file from GitHub link provided).**

  **If you want to deploy manually using Flask, follow the "Local Deployment" steps at the end of this README.**  

## Business Understanding

### Context
**Term Deposits**  
A term deposit is a primary funding source for banks and a stable, safe investment option for customers. Customers deposit a certain amount for a fixed term and cannot withdraw it before maturity. The bank lends this money to other customers at a higher interest rate, generating revenue from the interest margin.

Telemarketing is a common method used to promote term deposits to customers. However, conversion rates are often low, necessitating a more effective approach.

### Problem Statement
Bank HAN in Portugal has telemarketing campaign data from 2008-2013. The conversion rate from these campaigns is only 11.8%, meaning most calls result in rejection. The bank aims to improve campaign efficiency by identifying potential customers and reducing telemarketing costs.

### Goals
1. Understand the overall telemarketing campaign performance.
2. Identify potential customers likely to open a term deposit.
3. Optimize marketing budget to increase profitability.

### Analytical Approach
- **Target Variable**:  
  - `0`: Customer does not open a term deposit.  
  - `1`: Customer opens a term deposit.  

- **Evaluation Metrics**:  
  - **True Positive (TP)**: Predicted to open and actually opens.  
  - **False Positive (FP)**: Predicted to open but does not open.  
  - **True Negative (TN)**: Predicted not to open and actually does not open.  
  - **False Negative (FN)**: Predicted not to open but actually opens.  

- **Priority Metric**: Recall to minimize False Negatives (losing potential customers).

---

## Data Understanding
Dataset: [Bank Marketing Campaigns Dataset | Opening Deposit](https://archive.ics.uci.edu/ml/datasets/bank+marketing)  
Source: S. Moro, P. Cortez, and P. Rita. *A Data-Driven Approach to Predict the Success of Bank Telemarketing*. Decision Support Systems, Elsevier, 62:22-31, June 2014.

### Input Variables
| No  | Variable          | Description |
|-----|-------------------|-------------|
| 1   | age               | Age (numeric) |
| 2   | job               | Type of job (categorical) |
| 3   | marital           | Marital status (categorical) |
| 4   | education         | Level of education (categorical) |
| 5   | default           | Has credit in default? (categorical) |
| 6   | housing           | Has a housing loan? (categorical) |
| 7   | loan              | Has a personal loan? (categorical) |
| 8   | contact           | Contact communication type (categorical) |
| 9   | month             | Last contact month (categorical) |
| 10  | day_of_week       | Last contact day of the week (categorical) |
| 11  | duration          | Last contact duration in seconds (numeric) |
| 12  | campaign          | Number of contacts during this campaign (numeric) |
| 13  | pdays             | Number of days since last contact (numeric) |
| 14  | previous          | Number of previous contacts (numeric) |
| 15  | poutcome          | Outcome of the previous marketing campaign (categorical) |

### Social & Economic Variables
| No  | Variable          | Description |
|-----|-------------------|-------------|
| 16  | emp.var.rate      | Employment variation rate (numeric) |
| 17  | cons.price.idx    | Consumer price index (numeric) |
| 18  | cons.conf.idx     | Consumer confidence index (numeric) |
| 19  | euribor3m         | Euribor 3-month rate (numeric) |
| 20  | nr.employed       | Number of employees (numeric) |

### Output Variable (Target)
| No  | Variable | Description |
|-----|----------|-------------|
| 21  | y        | Did the client subscribe to a term deposit? ("yes" or "no") |

---

## Exploratory Data Analysis (EDA)
Complete analysis is available in the notebook.

---

## Preprocessing
Preprocessing steps include:
1. Removing duplicate data
2. Filling missing values
3. Encoding categorical variables
4. Feature scaling
5. Oversampling

---

## Methodology (Modeling)
Complete analysis is available in the notebook.

---

## Model Limitation
The model is applicable within the following data ranges:

| Variable          | Range / Categories |
|------------------|------------------|
| **Age** | 17 to 98 years |
| **Age Group** | 15-19, 20-24, ..., 85 and more |
| **Campaign** | 1 to 43 contacts |
| **Pdays** | 0 to 27 or 999 = Not contacted |
| **Previous** | 0, 1, 2, ..., 7 |
| **Poutcome** | "failure", "nonexistent", "success" |
| **Emp.var.rate** | -3.4 to 1.4 |
| **Cons.price.idx** | 92.201 to -26.9 |
| **Cons.conf.idx** | -50.8 to 94.767 |
| **Euribor3m** | 0.634 to 5.045 |
| **Nr.employed** | 4963.6 to 5228.1 |
| **Job** | "admin.", "blue-collar", ..., "unknown" |
| **Marital** | "divorced", "married", "single", "unknown" |
| **Education** | "basic.4y", ..., "unknown" |
| **Housing** | "no", "yes", "unknown" |
| **Loan** | "no", "yes", "unknown" |
| **Contact** | "cellular", "telephone" |
| **Month** | "jan", "feb", ..., "dec" |
| **Day_of_week** | "mon", "tue", ..., "fri" |

---

## Conclusion and Recommendation

### Conclusion
1. **Campaign Overview**: Focus on customers with potential demographic and interaction history.
2. **Identifying Potential Customers**: The model successfully identified 919 potential customers out of 6231 contacted, reducing telemarketing costs by 35.3%.
3. **Profitability Increase**: Cost-to-profit ratio reduced from 8.85% to 6.95%.

### Recommendations
1. **Best Contact Time & Frequency**: Focus on March, April, September, October, and December. Prioritize Thursdays.
2. **Customer Segmentation**: Focus on young customers (15-24 years) and older customers (above 60 years).
3. **Telemarketing Strategy**: Optimal call duration is 3-5 minutes.
4. **Economic Factors**: Leverage economic conditions like high interest rates to boost deposit offerings.

---

## Local Deployment
1. **Save the Machine Learning Model**  
Save the trained model as `.pkl` format using pickle.

2. **Create a Directory for the Model**  
Create a folder `Test_Model_ML` to store the model and related files.

3. **Create requirements.txt**  
Inside `Test_Model_ML`, create `requirements.txt` to store dependencies.

4. **Create static/ and templates/**  
Inside `Test_Model_ML`, create:
   - `static/` → Stores CSS, JavaScript, or images.
   - `templates/` → Stores HTML files.

5. **Save Model File**  
Move `model.pkl` into `Test_Model_ML`.

6. **Create CSV_Baca_py.py**  
Write a Flask app in `CSV_Baca_py.py`.

7. **Create index.html in templates/**  
Place `index.html` in `templates/`.

8. **Run Flask App**
```sh
python CSV_Baca_py.py
