# Loan Approval Process Automation
A bank wants to automate their loan approval process. They have provided a semi-anonymized dataset containing 606 successful and 76 not successful loans along with their information and transactions. These loans are for existing clients. This could be used to pre-approve existing customers and market to them accordingly.

The dataset belongs to a Czech bank. The goal here is to produce a model that can predict whether client is probably going to default in paying back a loan or not.

The summary and presentation of the results: [link](https://github.com/arashag/Loan-Approval-Process-Automation/blob/master/loan_approval_process_automation_presentation.pdf)

The data dictionary for the columns name and other related information: [link](https://sorry.vse.cz/~berka/challenge/pkdd1999/berka.htm)

## Prerequisites
All the required packages along with their version are in the `requirements.txt`. They can be easily installed with following command:
```
pip3 install -r requirements.txt
```
## Analysis and Modelling
After merging and aggregating by the correct columns, each row should represent a customer's account. Some columns are created using feature engineering and some of them are the dataset original variables.
Two models have been created. First, a binary classifier created to judge whether default would happen and second a multi class classifier has been created for precisely determining the category of customers (i.e A,B,C,D)

## Models Results
SVM classifier with linear Kernel has been used for this modelling. For alleviating the effect of imbalance class sizes, `balanced` class weight used in SVM model. The person who pays back her loan is considered as a positive case in this model. Because the bank priority is not to lose money as far as possible, the precision score is much more important because we need low false positive. In other words, we want to be highly certain that a person who was predicted she would pay back her loan would eventually do that. We could reach the precision of 1 and recall of 0.98 for this problem.

### The Most Important Variables (Model Explainability)
The factors that contribute to the loan payment probability are in below sequence:
  1. Average Salary (A11)
  2. Credited Interest
  3. Received a money transfer

The factors that decrease the probability of loan payment are in below sequence:
  1. Sanction interest
  2. Gender
  3. Loan duration
  
Please consult the pdf file for more details.

### Multiclass Classification Model
In this section, the model is extended to predict the category that a customer fits in. It has the following benefits compared with the binary classifier for the business:
  * Categorize customers
  * The bank can design various loan packages for each category
  * It can produce more potential revenue for the bank
