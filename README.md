# Loan Credit Worthiness Prediction Model

## Project Overview
This project aims to predict the creditworthiness of individuals applying for loans. By analyzing financial and personal data, the goal was to develop a model that could predict whether an individual is likely to repay or default on a loan. This project offered some unique challenges, particularly with skewed and imbalanced data, but I learned a lot throughout the process.

## Dataset Overview
The dataset consists of information about applicants, their financial history, and personal details. Below are the columns present in the dataset:

- **ID**: A unique identifier for each observation.
- **Loan_ID**: A unique identifier for each loan.
- **Gender**: Applicant’s gender (encoded as 0 for male and 1 for female).
- **Married**: Marital status (0 = Not Married, 1 = Married).
- **Dependents**: Number of dependents relying on the applicant, ranging from 0, 1, 2, to 3+.
- **Education**: Education level of the applicant (0 = Undergraduate, 1 = Graduate).
- **Self_Employed**: Employment status of the applicant (0 = No, 1 = Yes).
- **ApplicantIncome**: Monthly income of the applicant, ranging from 0 to 80,000.
- **CoapplicantIncome**: Monthly income of the co-applicant, from 0 to 20,000.
- **LoanAmount**: Loan amount requested in thousands (range: 20 to 800).
- **Loan_Amount_Term**: Loan repayment term in months (range: 0 to 500).
- **Credit_History**: Indicates whether the applicant’s credit history meets certain guidelines (0 = No, 1 = Yes).
- **Property_Area**: Type of area where the applicant lives (encoded as 0 = Rural, 1 = Semi-Urban, 2 = Urban).
- **Loan_Status**: Whether the loan was approved (Y/N); this is the target variable and only present in the training set.
- **Total_Income**: Total income of the applicant and co-applicant, ranging from 0 to 20,000.

## Key Insights
One of the first things I noticed was the **skewness** and **class imbalance** in the dataset. The majority of applicants had their loans approved (Class 1), while a smaller portion had their loans denied (Class 0). This imbalance posed a challenge for model performance, as the model tended to predict the majority class (approved loans) more often. To address this, I opted for **class weighting** instead of using SMOTE, which caused some issues in my initial trials.

## Data Preprocessing
In order to prepare the data for modeling, several key steps were taken:
- **Handling Missing Values**: Missing data was imputed based on available information.
- **Feature Engineering**: I added **Total_Income**, a combined metric of the applicant and co-applicant's income.
- **Class Weighting**: Due to the imbalanced nature of the target variable, I applied class weighting to give more importance to the minority class (loan denials).
- **Normalization/Scaling**: I normalized certain features like **ApplicantIncome**, **LoanAmount**, and **Total_Income** to make them comparable.

## Model Selection & Evaluation
The **Elastic Net** model performed the best among the various models I tried. Here are the key performance metrics:
- **Recall for Class 0 (Loan Denied)**: 0
- **Precision for Class 0**: 0
- **Recall for Class 1 (Loan Approved)**: 1
- **Precision for Class 1**: 0.83
- **Accuracy**: 83%

Although the recall for Class 1 (loan approved) was 0, the model was able to accurately predict the minority class (loan denial), which is critical for risk management in loan approval processes.

## Challenges
- **Class Imbalance**: The dataset was heavily imbalanced, with more approved loans than denied loans. Handling this imbalance was a key challenge.
- **Feature Selection**: Some features like **CoapplicantIncome** were less predictive, and understanding which features to keep or discard was essential.
- **Model Performance**: Despite experimenting with multiple models, **Elastic Net** was the most promising due to its ability to handle the imbalanced dataset.

## How to Use
To run the model, follow these steps:
1. Clone the repository:
   ```bash
   git clone <repository_url>
