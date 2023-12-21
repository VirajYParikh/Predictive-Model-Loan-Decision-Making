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

<div align="center">
<img width="532" alt="Screenshot 2023-12-21 at 2 55 17 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/cfcbb1b7-8982-49b4-9b27-ed9fdf7f5fd3">
</div>


## 5. FEATURE ENGINEERING
As we analyzed the data, going further, we need to select and prepare our features to train the model.

a. Feature Selection
There were certain categorical features (other_parties, foreign_worker, own_telephone, other_payment_plans and class), which were directly converted into binary variables. Post that, we plotted the correlation matrix between the available continuous variables and the target variable (class).

<div align="center">
<img width="532" alt="Screenshot 2023-12-21 at 2 56 56 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/b70e95c8-31b5-415e-9807-26463e689274">
</div>

From the correlation matrix we can see that there are multiple features with very low correlation value with the target class, so we eliminated any feature which has a correlation < | 0.1 | with ‘class’ , as they don’t contribute much to it.
After, we had selected the continuous features, we had to check how much do the categorical variables contribute to the formulation of the target variable. To do this, we performed a Chi-Squared test, to get the Chi-Square metric and the corresponding p- value. By analyzing the chi-square statistic and corresponding p-values, we can identify features that exhibit strong associations with the target class. The chi-square statistic measures the difference between the observed frequencies and the expected frequencies
  
under the assumption of independence. The corresponding p-value indicates the probability of obtaining such an extreme or more significant result if there were no association between the variables.
Choosing features based on the chi-square statistic and p-value is essential for training a predictive model. Features with high chi-square statistics suggest a substantial association with the target class. This indicates that the feature provides valuable discriminatory information that can help differentiate between different classes of the target variable. Features with low p-values indicate a high level of statistical significance, suggesting that the observed association is unlikely to occur by chance. Therefore, when selecting features for model training, it is advisable to prioritize those with both high chi-square statistics and low corresponding p-values. These features are more likely to contribute significantly to the predictive power of the model and capture important patterns related to the target class. By incorporating such features into the model, we can potentially improve its accuracy and performance in predicting the target variable.

So, we selected the features which have a chi-square statistic greater than 10 and a corresponding p-value being lesser than 0.05.

**The finally selected features are: checking_status, credit_history, purpose, savings_status, employment, housing, other_payment_plans, credit_amount, property_magnitude and duration.**

And we can see here that out of all the features, the selected ones are the most relevant to acquiring a loan.

b. Feature Transformation

Now, that we have selected the features, we still need to transform them into being suitable as training input of the model.
We converted the categorical features into One-Hot representations. About the categorical variables, as you can see in the code, both credit_amount and duration were positively skewed and we used Box-Cox transformation to transform them.

<div align="center">
<img width="600" alt="Screenshot 2023-12-21 at 3 01 35 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/0a18db5f-26fc-4485-8464-f270ded712df">
</div>


<div align="center">
<img width="600" alt="Screenshot 2023-12-21 at 3 01 54 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/b93f4446-5cd5-4ba0-ad51-a0cbbaf7b8f6">
</div>

This ensures that we filter out any outliers which would lead to a skewed prediction.
To get a better representation of the purpose of the loans we grouped all the loan types mentioned in the dataset under 4 broad loan categories:

1. Personal Loan:
   
• Repairs

• Retraining

• Furniture/Equipment

• Other

• Domestic Appliances

2. Auto Loan:
   
• New car

• Old car

3. Business Loan
 
5. Education Loan

## 6. MODELING AND EVALUATION
Now, that we have the data ready to be input into the model, we proceed with modeling.
Since the target variable is a yes or a no (good loan or bad loan / 1 or 0), we would be using classification models to train and test the data on.

We split the data into training and testing with a split of 80% for training and 20% for testing. We worked on two classifiers:
• Random-Forest Classifier: Tested the model for min_samples_leaf values: [1, 2, 4, 8, 16, 32, 64, 128] and tree depth ranging from 1 to 10.

• Logistic Regression Classifier: Tested the model for C values: [0.001, 0.01, 0.1, 1, 10, 100].

After finding the best set of hyperparameters for both models, we plotted the ROC curve for both of those.

<div align="center">
<img width="425" alt="Screenshot 2023-12-21 at 3 05 21 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/58fba2fc-eb9d-4b9e-9d05-1bf6400c9b8a">
</div>


Different evaluation metrics:
• Random Forest: f1 score = 0.85, accuracy = 0.76, AUC = 0.80

• Random Forest: f1 score = 0.85, accuracy = 0.78, AUC = 0.82

The evaluation metric we considered to choose between classifiers is AUC (Area Under the Curve). As we can see from the ROC plot the **Logistic Regression Classifier** performs better than the Random Forest Classifier with an AUC of 0.82.

## 7. DECISION LOGIC

Now that we have the best classifier to use, we calculate the confidence (probability), to see which applicants have a better credit standing to be eligible for the loan. The objective here is not only to identify the bad loans, but also to identify good loans to get the best profits and the least credit default risks, which is generally a tradeoff. There may be instances where the risks associated to a loan are slightly high yet producing good profits. We calculate the risk based on the confidence levels we found previously.

Determining somebody’s default risk is important since it helps to calibrate their interest rates to
mitigate the risk of lending money to them.

There are multiple ways we can mitigate risks associated with loans:

1. Increasing everyone’s interest rates to make up for the losses.
   
2. Only accepting safe borrowers
 
3. Charging people interest rates proportional to their default risk.

We have worked on the 3rd method as according to us it is the most promising and rewarding, giving us more flexibility to maximize profit.
We combined various purposes into 4 types of loan, and we set the base rates (set the values based on averages found on the internet):

<div align="center">
<img width="425" alt="Screenshot 2023-12-21 at 3 21 55 PM" src="https://github.com/VirajYParikh/Predictive-Model-Loan-Decision-Making/assets/67093208/54b6c070-9733-42b6-8cd7-ca9fd35ae342">
</div>


