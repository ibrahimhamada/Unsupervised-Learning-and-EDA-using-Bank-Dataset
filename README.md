# Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset
Project of the Machine Learning Course Offered in Fall 2021 @ Zewail City

This project aims to use Unsupervised learning and Exploratory Data Analysis on a dummy bank loans dataset. 




## Dataset:

The datset utilized is a dummy bank loans dataset composed of the following features:

- Total O/S: Total loan amount
- TENOR_@Booking: Duration in months for the loan
- Loan Term: Duration in years
- Booking Date: The date on which the loan data is entered
- Maturity_Date: the date on which a borrower's final loan payment is due.
- DPD: Days past dues, a metric that indicates whether a customer has been consistent in his/her repayments and if he/she has missed any, how many installments did the customer miss, and by how many days.
- DOB: Date of Birth of the client
- Age: The age of the client.
- Gender: The gender of the client.
- Customer Segment: classification of the customer based on the type of employment


## Data Preprocessing: 

- 279 nulls were found and dropped.
- 798 duplicates were found and dropped.
- Loan Term (Duration in years) was dropped because it doesn't add new information since TENOR_@Booking is the Duration in months for the loan.
- Drop DOB Feature since we have Age feature, so DOB is not needed anymore.
- Age at maturity column was dropped and recalculated(age+loan term in years) as a number instead of date(DD/MM/YYYY).
- Naming issues in the gender column were fixed, possible values were (MALE, Male, FEMALE, Female) and were changed to (Male, Female).
- Customer segment and gender were one-hot encoded.


## Data Visualization:

### Age Distibution:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/40906f98-1fb0-4d01-bcd8-b2ed62a09729)

Outliers in age:
● There are some negative ages which need to be dropped.
● The legal age for loans is 21 years.
● So, all ages less than 21 years will be dropped.

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/f1c5c422-ac83-4b42-9cc0-be036afc07f7)

### Total Loan Amount:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/00edea18-5d67-4212-943b-a45697a5e0f8)

Outliers in total loan amount:
● Abu Dhabi Commercial Bank (ADCB) Website says that the minimum value for a loan is 10K EGP.
● So, all amounts less than 10K EGP will be dropped.
● Also, it can be noted that there is an outlier with Loan Amount equals 25 Million EGP, so Loans greater than 15 Million will be dropped.

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/1c8a9d59-e637-4858-a182-f8f2adeafc9a)

### Loan Term in Month:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/ea4c98cc-7d8a-40b3-a0bf-f6d68a2d056a)



![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/06e42e4b-4918-4e04-9695-add6f1775e16)



### Days past dues: 

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/b5dbd579-ee7a-42b6-ae3f-d276ed147245)


![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/d0c1dbbf-6df4-42fc-9a55-38cfa4971c4e)

















## Model Selection:

These models were selected as they have proven to be efficient when used in binary classification problems.

* Logistic regression.
* Random forest.
* Decision tree.
* AdaBoost
* Bagging

## Results:

Since it is important for us to detect true fraud transactions, we used recall and F1 scores to assess the models preformance. Bagging model achieved higher performance.

- Accuracy = 99.81
- Recall = 82.517
- F1-score = 83.21
- Precision = 83.91
