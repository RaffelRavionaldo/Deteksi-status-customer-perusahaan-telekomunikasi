# Customer churn detection in telecommunications companies

# Disclaimer
I made this machine learning model during the stage of my learning process at the Fresh graduate academy bootcamp held by
Ministry of Communication and Information of the Republic of Indonesia in collaboration with Binar Academy.

# Notes : 
if the program has an error when you run it, then first install the required requirements, if it still has an error then:
1. If an error occurs while installing imbalanced-learn, open your Anaconda prompt and type: conda install -c conda-forge imbalanced-learn
2. If an error occurs when installing xgboost, open your Anaconda prompt and type: pip install xgboost

# machine learning Model
The machine learning models that I created are Xgboost and logistic regression, later these two models will be compared which one is better
by looking at accuracy, precision, F1-call and recall

In making this machine learning model, what I did was:
1. Conduct Exploratory Data Analysis
At this stage I did it to find out the columns and rows of the dataframe used. then check if the dataframe has
the column is null and duplicate, the result is that the dataframe does not have null and duplicate data.
then I checked the amount of churn and non-churn customer data,
the results for churn customer data have 3652 data and 598 customer data that do not churn, are quite different so there is a risk that the model will overfitting
so I decided to do some sampling before training the machine learning model.

2. Data Visualization
the process of making the data visualization that I did, I started by making a question first, namely:
which areas have the most churn customers and does the number of customer calls affect customer service churn?
result :

![image](https://user-images.githubusercontent.com/94748637/196013624-396b18b5-d639-4fae-9de2-4e64e3b84948.png)

It can be seen that most of our customers are in the 415 area but that area has the highest number of churned customers

![image](https://user-images.githubusercontent.com/94748637/196013648-8b68b75b-42fe-4fc5-a8a6-ac5e6c2c2e73.png)

From the graph above, information is obtained that the number of customers contacting a customer service call does not affect whether the customer will churn or not.

3. Data preprocessing
The first thing I did was change the categorical column which has 2 values to be numeric so I could find out the correlation between the categorical column and the churn column.

then I looked at the correlation between the columns and the churn column (because the churn column is the column you want to detect) and got the following results:

![image](https://user-images.githubusercontent.com/94748637/196013682-f3f1ff5d-e0f9-4d7b-bd0e-f867c72afefd.png)

It can be seen that the correlation between the columns and the churn column is quite low, the highest is at 0.25. so I decided to take a column with a correlation above 0.1

The next step is to standardize the numeric column and one-hot encoding for the categorical column to improve the quality of the machine learning model

4. Sampling
I did 2 kinds of sampling, namely oversampling using SMOTE and undersampling using a random under sampler. this is done to find out whether there is a difference to the model results
machine learning trained using oversampling and undersampling

5. Create machine learning models
The models I created were logistic regression and XGboost with oversampled and undersampled training data, so that in total I made 4 machine learning models

6. Evaluation of machine learning models
for the evaluation that I did was to look at accuracy, precision, recall and F1-score where it was found that the Xgboost model with the train data in oversampling had the best value. where these 4 parameters have values ​​above 90% so I decided on the xgboost model with oversampling train data which I used to detect test data
