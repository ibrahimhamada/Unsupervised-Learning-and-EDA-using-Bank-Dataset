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

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/886618d8-e7e7-4e8b-bcd1-e7e1da18aedc)


Outliers in age:
- There are some negative ages which need to be dropped.
- The legal age for loans is 21 years.
- So, all ages less than 21 years will be dropped.

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/2f89644e-21eb-4f46-94f4-861a2c4caabb)

### Total Loan Amount:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/a8184031-567e-47d4-949d-ed7e70d2d519)

Outliers in total loan amount:
- Abu Dhabi Commercial Bank (ADCB) Website says that the minimum value for a loan is 10K EGP.
- So, all amounts less than 10K EGP will be dropped.
- Also, it can be noted that there is an outlier with Loan Amount equals 25 Million EGP, so Loans greater than 15 Million will be dropped.

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/62f8c8d8-071a-4682-9492-aac855c78391)

### Loan Term in Month:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/426ec047-3497-4ea0-9c4b-def08764ba96)

### Days past dues: 

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/d5d1f522-3ba5-493e-b97c-0f288eeaf500)



### Number of Males and Females:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/df0b6629-42a9-413e-b50a-812a23f06c50)

### Number of Customers in each Segment:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/6757bb39-52cd-4969-bcf3-357ef9625256)


### Customer Segments And Gender:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/404825f3-3829-4e85-b2b6-a9263225f6a5)

### Number of Loans that were booked per each day of the week:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/ee060985-7def-4f90-828e-9eb122f41a5f)

### Number of Loans that were booked in each Month: 

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/9009c1a9-7a97-4f00-986a-4f3b11bd4fce)

### Correlation Matrix:

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/32b08466-feee-4c8a-b998-4721436e7201)




## Clustering (K-Means):
- The K-means algorithm aims to choose centroids that minimize the inertia, or within-cluster sum-of-squares criterion.
- Using the Elbow method to choose the best K value which is the number of clusters.

![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/562d9a7e-f38d-4967-99be-42cf03738a75)

- The best K value is 4 but let's compare between the average silhouette score of 3, 4, 5, and 6 clusters.
- Using The silhouette samples and score to visualize the scaled data:
- For n_clusters = 3 The average silhouette_score is : 0.31220752106783983
- For n_clusters = 4 The average silhouette_score is : 0.1949636970359901
- For n_clusters = 5 The average silhouette_score is : 0.18870629751290185
- For n_clusters = 6 The average silhouette_score is : 0.19566370179644024


![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/c4f1dc05-33da-45bb-a55d-cc88e49ff2c8)


![image](https://github.com/ibrahimhamada/Unsupervised-Learning-and-EDA-using-Bank-Loans-Dataset/assets/58476343/fbfeee68-ae39-491b-9ea0-053903e8b1fa)


In the left figures, the thickness of each cluster label represents the number of examples in this group. While in the right figure, the numbers represent the cluster label and the coordinates are the centroid of each group to illustrate the distances between the centroids of each group.

Therefore according to the average silhouette coefficient, the best number of clusters is 3 clusters. This means that the bank clients should be classified into three categories which are: accepted, rejected, and under_investigation.

