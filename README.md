# Credit Risk Assessment for Lending Institutions
## Building a Predictive Model for Loan Decision Making

## CONTENTS

1. Introduction

   a. Objective
   
   b. Plan of Action
3. Business Aspect of the Problem
4. Introduction to Data
5. Exploratory Data Analysis
6. Feature Engineering

   a. Feature Selection
   
   b. Feature Transformation
7. Modeling and Evaluation
8. Decision Logic
9. Conclusion
10. Citations

## 1. INTRODUCTION
### a. Objective:
The primary objective of this project is to evaluate the creditworthiness of loan applications to maximize profitability within a specific budget the bank has which can be given as loans. This will be achieved through the development of a highly accurate predictive model capable of thoroughly assessing the credit risk associated with potential borrowers in various lending institutions. The project entails a comprehensive analysis of customer financial data, credit history, employment details, and loan repayment records, all of which will contribute to the construction of a robust credit risk assessment model. Ultimately, the aim is to make well-informed loan decisions that not only mitigate risks but also maximize profitability for the lending institution.

### b. Plan of action:
The loan approval process involves a comprehensive evaluation of various factors to assess the suitability of a customer's loan application. These factors include the customer's credit score, age, loan type, loan amount, and other relevant information. By carefully considering these factors, we assign a credit risk value to each customer within a range of 0 to 1. Our aim is to train a robust model using a comprehensive dataset that incorporates all these features. Through this training, we seek to develop an accurate credit risk assessment model that can effectively evaluate and rate the risk associated with each customer. This model will provide lending institutions with valuable insights to make well-informed loan decisions. By leveraging customer financial data, credit history, employment information, and loan repayment history, we strive to optimize the loan approval process while safeguarding the institution's financial interests. Ultimately, our goal is to strike a balance between approving viable loan applications and ensuring the lending institution's profitability and sustainability.

Following are the steps we’ll follow:

**Step 1**: Extract data.

**Step 2**: Clean the data.

**Step 3**: Analyze the data.

**Step 4**: Feature selection.

**Step 5**: Train and test different models.

**Step 6**: Implement the business requirements on the best model. 

**Step 7**: Repeat from step 5.

## 2. BUSINESS ASPECT
In the subsequent step of the risk assessment process, the model will assign a range of values (confidence in the fact that they should be given a loan for each instance. This allows loans to be granted exclusively to customers whose associated risk falls below the specified threshold.

Default Risk: **Defaulting** on a loan means failing to pay it back, so each person’s probability that
they’ll fail to pay back their loan is called their **default risk**.

While minimizing defaults can be done just with this information, it is important to note that our primary objective is to maximize profitability within a specific budget the bank has which can be given as loans. Thus, we employ various mathematical formulae that incorporate factors such as minimizing default credit rates, total budget, and more. These calculations are designed to optimize profitability and achieve the best possible outcomes.
One approach involves determining an expected value from the loan portfolio by considering both the anticipated return from successful loans and the expected loss resulting from defaults. To calculate this, we utilize the following mathematical formula:
Expected Value = (1 – risk) * Interest + risk * credit amount where,

• risk: The probability that a person will default on a loan (1 – confidence).

• interest: The calculated value of applicable interest, assuming the loan is given,
calculated by incorporating the associated risk.

• Credit amount: Requested loan amount.

By leveraging this formula, we can determine the best model and threshold values that lead to optimal profitability. This comprehensive approach ensures that our efforts go beyond solely minimizing defaults and focus on making well-informed decisions that maximize profitability while effectively managing credit default rates.

## 3. INTRODUCTION TO DATA

Here is a screenshot of the dataset (sourced from Kaggle) we are looking to use and the features we will be considering for the business proposition mentioned above:

<div align="center">
<img width="1440" alt="Screenshot 2023-12-21 at 1 50 44 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/0f0f9aab-6314-4509-b597-211de8ef5663">
</div>

The following are the attributes taken into consideration:


## 4. EXPLORATORY DATA ANALYSIS
All the data was initially analyzed, wherein it was deduced that there were no null values, we had 7 continuous and 13 categorical attributes with a total of 1000 instances. We used class as the target variable with many good loans, the count being 700 good and 300 bad, which implies that there is a slight disproportion in the data.

<div align="center">
<img width="517" alt="Screenshot 2023-12-21 at 1 58 14 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/703d5828-9978-434c-955d-e86e915ef0e0">
</div>

It can be observed that the maximum credit loan amounts were around $0-$5000, with the highest frequency around $2500.

<div align="center">
<img width="517" alt="Screenshot 2023-12-21 at 1 59 26 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/1fc283ef-4a62-46f2-8cd5-fc7aa4aff695">
</div>

From the employment bar chart, we realized that people who were either unemployed or were employed for less than a year had a higher tendency to default. Moreover, it was the unemployed people who had requested the biggest and highest requested credit amounts. Both points suggest a better prediction mechanism to ensure that the loans are correctly given.

<div align="center">
<img width="486" alt="Screenshot 2023-12-21 at 2 00 07 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/f41dccf2-5a0d-4b82-9778-89a1d90147e7">
</div>

Interestingly most of the loans were taken for household appliances like Radio and TV which having relatively low costs seem to be better loans.

<div align="center">
<img width="532" alt="Screenshot 2023-12-21 at 2 00 51 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/8bf67351-1127-4da0-b0d2-02ab1a7e539e">
</div>

On the other hand, loans given out for new cars seemed to have relatively stronger tendencies to default. Moreover, a large amount of loans were given to customers with no checking accounts suggesting that having a checking amount may not always be necessary to provide loans.
We can see from the scatterplot below that most requested loans are from people between ages 20-40 with a requested credit amount between $0-$5000.


