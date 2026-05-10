--- 
layout: post 
title: "Online Payment Fraud Detection Using Machine Learning" 
date: 2026-05-10 
--- 

![Online Fraud Detection](/assets/img/posts/What-is-Online-Payment-Frauds.jpg) 

Hello 👋🏾, Angelina here! 

This past week I've been working on a project that is detecting fraudulent online payment transactions through big data and Machine Learning. This project was developed using ***Python*** and ***Jupyter Notebook*** and ***VScode*** as an IDE (Integrated Development Environment). I've used multiple Machine Learning algorithms such as the ***Logistic Regression***, ***XGBoost Classifier*** and ***Random Forest Classifier*** to detect patterns and suspicious behavior in online payment transactions. Since online fraud detection is becoming a very important topic in cybersecurity and financial technology, I wanted to create a project that is not only using `Machine Learning algorithms`, but is also solving a real-world problem. In the next few (or maybe a little more lines), I will explain the project in more details, just so I can report and present the project better. 

### Project Description 

In the beginning, I downloaded and imported the dataset as a `CSV` file into the `Jupyter Notebook`. This particular data set I got from [Kaggle](https://kaggle.com). I did find Kaggle very helpful as it has a lot of projects that can be used by beginners and intermediate, and also allows to not only have datasets, but a lot of information that are very helpful. 
The second step is to import all the libraries that are going to be used during the project: 
1. [Pandas](https://pypi.org/project/pandas/) 
2. [Numpy](https://pypi.org/project/numpy/) 
3. [Matplotlib](https://pypi.org/project/matplotlib/) 
4. [Seaborn](https://pypi.org/project/seaborn/) 
5. [Scikit-learn](https://pypi.org/project/scikit-learn/) 
6. [XGBoost](https://pypi.org/project/xgboost/) 

After importing all the libraries, I started inspecting the dataset using `.head()`, `.info()` and `.describe()` in order to understand the structure of the data better. The dataset contained: 
- Transaction types 
- Transaction amount 
- Sender and receiver information 
- Fraud labels 
- Transaction steps/time 

### Data Cleanup & Processing 

After reading and understanding the dataset, I started separating the variables into categorical, integer and floating-point variables in order to better understand the data structure and prepare it for the Machine Learning models. The next thing that I wanted to do is visualize the transaction data and identify possible patterns related to fraudulent behavior. Using `Seaborn` and `Matplotlib`, I created several visualizations including: 
- Count Plot for transaction types

![Transaction Type Count Plot](/assets/img/posts/bar_chart1.png)

- Bar Plot for transaction amounts 

![Transaction Amount Bar Plot](/assets/img/posts/bar_chart2.png)

- Distribution Graph for transaction steps

 ![Distribution of Transaction Steps](/assets/img/posts/distribution_of_step.png)

- Heatmap Correlation Matrix 

![Correlation Heatmap](/assets/img/posts/heatmap.png)

The `Count Plot` helped me visualize which transaction types are appearing more often in the dataset, while the `Bar Plot` allowed me to compare the average transaction amounts depending on the transaction type. 
Another graph that I created was a distribution graph for the transaction steps. This graph helped me understand how the transactions are distributed over time and whether fraudulent transactions are happening more frequently during specific periods. 
After visualizing the data, I created a `Heatmap Correlation Matrix` using `Seaborn`. The heatmap helped me identify correlations between the different variables and determine which features may be more connected to fraud detection. The next step was preprocessing the data before training the Machine Learning models. Since the type column was categorical, I used `pd.get_dummies()` to convert the transaction types into numerical values that the Machine Learning algorithms can understand and process. 
After converting the categorical variables, I removed the unnecessary columns such as: 
- nameOrig 
- nameDest 
- type 
Those columns were not directly helping the prediction process and could create unnecessary complexity during training. 

After all, the target variable for the project was:
 - isFraud 

The rest of the columns were used as feature variables for the Machine Learning models. 

### Machine Learning Models 

The next step was importing and training multiple Machine Learning models in order to compare their performance and determine which model is performing better in fraud detection. 
The models that I used were `Logistic Regression`, `XGBoost Classifier`, `Random Forest Classifier`. 
I divided the dataset into training and testing data using `train_test_split()` and started training each model separately. 
To compare the performance of the models, I used: 
- ROC-AUC Score 
- Accuracy 
- Precision 
- Recall 
- F1-score 
- Confusion Matrix 

One thing that I noticed very quickly is that the dataset has a very large class imbalance. 
The dataset contained: 
* Around 6.3 million non-fraud transactions 
* Around 8 thousand fraud transactions 

Because of this imbalance, accuracy alone was not enough to properly evaluate the models. This is why `Recall` and `F1-score` became extremely important during the project. 

### Random Forest Optimization 

After comparing the different models, I focused more on improving the `Random Forest Classifier` because it was giving very promising results. To improve the fraud detection sensitivity, I used: `class_weight='balanced'` This helped the model focus more on the minority fraud class instead of mostly predicting normal transactions. 

After balancing the classes I got few outcomes:
1. Recall improved from 0.42 to 0.71 
2. F1-score improved significantly 
3. Precision remained high 
This was a huge improvement because the model became much better at detecting fraudulent transactions. 

### Threshold Adjustment 

Since Machine Learning classifiers usually use a default probability threshold of 0.5, I wanted to experiment with lowering the threshold in order to make the model more sensitive to fraud transactions. 
I lowered the threshold from: `0.5 → 0.3` 
This slightly increased the number of false positives, but improved the fraud detection sensitivity even more, which is extremely important in fraud prevention systems. 

### Precision-Recall Curve 

After optimizing the model, I created a `Precision-Recall Curve` to better visualize the relationship between Precision and Recall. 

![Precision-Recall Curve](/assets/img/posts/output.png)

The graph showed strong results: 
- High Recall → the model is detecting most fraud cases 
- High Precision → most detected fraud cases are actually fraud 
This visualization helped confirm that the `Random Forest model` was performing very well after optimization. 

### Conclusion 

The project successfully created a Machine Learning fraud detection system capable of identifying suspicious online payment transactions with strong accuracy and sensitivity. Through the use of multiple Machine Learning algorithms and optimization techniques, I was able to improve the fraud detection performance despite the highly imbalanced dataset. One of the biggest achievements in the project was improving the `Random Forest Classifier` by balancing the class weights and adjusting the prediction threshold. 
This significantly improved the Recall score from `0.42 to 0.71`, which means the model became much better at detecting fraudulent transactions instead of missing them. The Precision and F1-score also remained strong, showing that the predictions were still highly accurate while increasing fraud sensitivity. The `Heatmap Correlation Matrix` and the `Precision-Recall Curve` helped me better understand the relationships between the variables and evaluate how well the model performs in distinguishing fraud from legitimate transactions. Another successful outcome of the project was handling a very large and imbalanced dataset containing over 6 million normal transactions and around 8 thousand fraud transactions. Even with this imbalance, the final optimized model was able to detect fraud efficiently and produce reliable prediction results. 

Link to the coding of this project: https://github.com/imangelinak/online_payment_fraud_detection

#### ***Till Next Time!*** # 
*Angelina Katrandzhiyska*