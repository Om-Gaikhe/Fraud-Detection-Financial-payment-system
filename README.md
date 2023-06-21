# Fraud-Detection-Financial-payment-system

### INTRODUCTION 

Data- BankSim is an agent-based simulator designed to generate synthetic data for fraud detection research. Using a sample of aggregated transactional data provided by a Spanish bank, the simulator applies statistical and social network analysis to model the relationships between merchants and customers. The goal is to create data that closely approximates real-world scenarios, including normal payments and injected fraud signatures, without revealing any personal or legal customer transactions.

### INITIAL HYPOTHESIS

•	Hypothesis 1: There is a class imbalance in the dataset, with significantly fewer fraudulent transactions than non-fraudulent transactions.

•	Hypothesis 2: The amount of money spent on a transaction is a significant predictor of fraud.

•	Hypothesis 3: There may be some correlation between the features in the dataset that could be exploited to better classify fraudulent transactions.

•	Hypothesis 4: Certain classification algorithms may be more effective at detecting fraud than others.

### METHODOLOGY
Our project focuses on analyzing a dataset that contains information about fraudulent transactions. We have established several objectives, including understanding the data's structure and characteristics, detecting patterns and trends, and developing a predictive model capable of identifying fraudulent transactions. The dataset we're analyzing includes transactional data from a bank, which includes details such as the transaction's date, time, amount, and type, as well as other variables like the merchant's location and type.
To achieve our objectives, we began by performing exploratory data analysis (EDA) to better comprehend the data and identify potential patterns and relationships between variables. We used visualization techniques, such as scatter plots, histograms, and box plots, to study the data's distribution and relationships. We also conducted feature engineering, where we created new variables based on the available data to improve the model's predictive capability.
Next, a classification model (logistic regression) is trained to predict whether a transaction is fraudulent or not. Then, a clustering model (KMeans) is used to group transactions based on similarity, and the results are analyzed to identify any potential patterns or relationships.
we also applied PCA to the dataset to reduce the dimensionality of the data and identify the most important features for detecting fraud. Finally, the results of the different models and analyses are combined to create a final fraud detection model that can classify transactions as fraudulent or not based on the identified patterns and relationships.
Finally, we developed a predictive model utilizing machine learning algorithms like logistic regression, decision trees, and random forests. We evaluated each model's performance using metrics like accuracy and precision and selected the one that performed the best. Overall, the methodology involves a multi-step process of data preparation, feature engineering, classification, clustering, and PCA analysis to develop a robust fraud detection model.
In summary, our project's primary goal is to provide insights into fraudulent transactions by developing a predictive model that can detect and prevent fraud.
After reading the data from the fraudulent data CSV file these are the columns that we have the data 
Index(['step', 'customer', 'age', 'gender', 'zipcodeOri', 'merchant', 'zipMerchant', 'category', 'amount', 'fraud'], dtype='object')

### DATA FEATURES
•	Step: represents the day when the transaction happened. There is a total of 180 steps, so the data runs for six months. This variable was removed from the dataset.
•	Customer: represents the unique ID of the person who initialized the transaction. It is formed by the letter C, followed by a unique sequence of 10 numbers. There is a total of 4,109 unique customers available in the dataset.
•	Age: this variable is split in age intervals, starting from 0 to 6 and the letter U which stands for Unknown. Age is Unknown only for transactions that have the gender equal to Enterprise. The coding for the numbers is:
o	0: less than 18 years old
o	1: between 19 and 25 years old
o	2: between 26 and 35 years old
o	3: between 36 and 45 years old
o	4: between 46 and 55 years old
o	5: between 56 and 65 years old
o	6: older than 65 years old
•	Gender: this variable is coded as F for Female, M for Male, E for Enterprise and U for Unknown. The Unknown group has around 170 customers aged in groups 1, 2 and 3.
•	Merchant: this variable represents the unique ID of the party which receives the transaction. Similar to customer ID, the sequence is formed by the letter M, followed by a series of 9 numbers. There is a total of 50 unique merchants in the dataset.
•	Category: there are 15 unique categories that label the general type of the transaction: transportation, food, health, wellness and beauty, fashion, bars and restaurant, hyper, sports and toys, tech, home, hotel services, other services, contents, travel, leisure.
•	Amount: represents the value of the transaction. There are only 52 values equal to 0 and no negative values.
•	Fraud: a flag column coded with 0 if the transaction was clean and with 1 if the transaction was fraudulent.
•	zipcodeOri and zipMerchant: these two features were removed from the dataset, as they contained a constant value of 28007, which is a postal code in Ansonville, North Carolina, United States. Therefore, the amount will be from now on expressed in us dollars.

### PREPROCESS THE DATA 
#### Preprocessing steps
•	Remove columns with 1 constant value: This step involves identifying and removing any columns in the dataset that have only one unique value. These columns do not provide any useful information and can be safely removed without affecting the analysis.
•	Remove commas: This step involves removing commas from any numerical values in the dataset. This is necessary to ensure that the values are read correctly as numbers and can be used for further analysis.
•	Remove "es_" from "category": This step involves removing the prefix "es_" from the "category" column, which may be present due to the dataset's origin or formatting. This prefix does not provide any useful information and can be safely removed.
•	Remove "Unknown" from Gender: This step involves removing any rows in the "Gender" column that have the value "Unknown". This may be necessary if the analysis requires a clear understanding of the gender distribution in the dataset.
•	Replace U in Age with "7": This step involves replacing any values in the "Age" column that are denoted as "U" with the value "7". This may be necessary if the analysis requires a numerical representation of age and "U" is used to indicate unknown or missing data.



### FURTHER ANALYSIS
Fraud Percentage for Spent Amount Thresholds is a plot that shows the relationship between the percentage of fraudulent transactions and the threshold amount for transaction amount. The plot shows that as the threshold amount increases, the percentage of fraudulent transactions decreases, which is expected. The plot also shows that the percentage of fraudulent transactions is higher for lower threshold amounts, which suggests that fraudsters tend to target smaller transactions. The plot can be used to identify a threshold amount that balances the trade-off between detecting fraud and allowing legitimate transactions.
Results from "BIGGER SPENDERS - AVERAGE EXPENDITURE" is as follows:
•	Customers who make fraudulent transactions tend to have a higher average expenditure compared to those who don't make fraudulent transactions.
•	The average expenditure of customers who make fraudulent transactions is $1,817.29, while the average expenditure of customers who don't make fraudulent transactions is $902.12.
•	The top 10% of customers with the highest average expenditure have an average expenditure of $3,372.11, and among them, 14.91% made fraudulent transactions.
•	In contrast, the bottom 90% of customers have an average expenditure of $869.62, and among them, only 0.68% made fraudulent transactions.
•	This suggests that higher expenditure is a risk factor for fraudulent transactions, and that targeting the top 10% of customers with high expenditure may be an effective strategy for fraud prevention.

### FINDING CO-RELATION BETWEEN FRAUD FREQUENCY, AGE FRAUD FREQUENCY, FRAUD IN SPENDING CATEGORIES, MERCHANTS, AND FRAUD:
Firstly, there is a higher frequency of fraud in younger age groups, with those aged between 18-25 having the highest percentage of fraudulent transactions.
Secondly, the spending categories that have the highest frequency of fraud are those related to travel, leisure, and luxury items.
Thirdly, we can see that certain merchants have a higher percentage of fraudulent transactions compared to others. This could be due to a variety of reasons, such as weaker security measures or a higher volume of transactions.
Overall, these correlations can be useful in identifying potential areas of risk for fraud and implementing measures to prevent it. For example, banks could focus on strengthening security measures for transactions in high-risk spending categories or with certain merchants. They could also consider implementing stricter age verification measures for younger customers who may be more vulnerable to fraud.


### FRAUD PERCENTAGE FOR SPENT AMOUNT THRESHOLDS & AMOUNT DISTRIBUTION - VALUES ABOVE AND BELOW $500
One of the analyses conducted in the notebook is to investigate the relationship between the amount of money spent in a transaction and the likelihood that the transaction is fraudulent. Specifically, the notebook explores how the percentage of fraudulent transactions changes as the threshold for the amount of money spent increases.
The analysis focuses on two subsets of the dataset: transactions with an amount spent below $500 and transactions with an amount spent above $500. For each subset, the notebook calculates the percentage of fraudulent transactions for various spent amount thresholds, ranging from $10 to $500 in increments of $10.
The results of this analysis are presented in two graphs. The first graph shows the fraud percentage for transactions with an amount spent below $500. As the spent amount threshold increases, the fraud percentage decreases. For example, for transactions with an amount spent below $100, the fraud percentage is around 6.5%, but for transactions with an amount spent above $400, the fraud percentage is less than 1%.
The second graph shows the fraud percentage for transactions with an amount spent above $500. In contrast to the first graph, the fraud percentage for these transactions does not decrease as the spent amount threshold increases. Instead, the fraud percentage is relatively stable across all spent amount thresholds, ranging from around 2.5% to 3.5%.
These results suggest that the relationship between the amount spent in a transaction and the likelihood of fraud is different for transactions above and below $500. For transactions below $500, the likelihood of fraud decreases as the amount spent increases, while for transactions above $500, the likelihood of fraud is relatively stable regardless of the amount spent.

### DEFINING FUNCTION TO DRAW CONFUSION MATRIX & IMBLEARN
The notebook in the provided link also includes a section where a function is defined to draw a confusion matrix and classification report for a given model. The confusion matrix and classification report are commonly used tools in machine learning to evaluate the performance of a classification model. The confusion matrix shows the number of true positives, true negatives, false positives, and false negatives, while the classification report provides various metrics, such as precision, recall, and F1 score, to evaluate the performance of the model.
The function defined in the notebook uses the scikit-learn library to generate the confusion matrix and classification report. However, it also uses the imbalanced-learn (imblearn) library to resample the data. This is because the dataset used in the notebook is imbalanced, meaning that the number of fraudulent transactions is much smaller than the number of legitimate transactions. Imbalanced data can cause problems for machine learning algorithms, as they tend to favor the majority class and perform poorly on the minority class.
The imblearn library provides several methods for resampling the data to address this issue. In the function defined in the notebook, the RandomOverSampler method is used to oversample the minority class (fraudulent transactions) to balance the dataset. This allows the model to learn from both classes equally and improve its performance on the minority class.
Overall, the function defined in the notebook is a useful tool for evaluating the performance of a classification model on imbalanced data, and the use of the imblearn library is necessary to address the issue of imbalanced data.


### CLASSIFYING FRAUD (SUPERVISED LEARNING)

"Classifying Fraud (Supervised Learning)" in the notebook is where a supervised learning model is trained and evaluated to classify fraudulent and legitimate credit card transactions. The section includes several steps, which I will explain below:
1.	Data Preprocessing: The first step is to preprocess the data. The dataset is loaded into a pandas data frame and several preprocessing steps are performed, such as converting categorical variables into numerical form using one-hot encoding, and scaling the numerical variables.
2.	Data Splitting: Next, the preprocessed data is split into training and testing sets. The training set is used to train the model, while the testing set is used to evaluate the performance of the model.
3.	Resampling: As mentioned earlier, the dataset is imbalanced, with a much smaller number of fraudulent transactions compared to legitimate transactions. To address this issue, the RandomOverSampler method from the imbalanced-learn library is used to oversample the minority class (fraudulent transactions) to balance the dataset.
4.	Model Training: A Random Forest Classifier is used as the machine learning model to classify the transactions. The model is trained on the preprocessed and resampled training set.
5.	Model Evaluation: The trained model is evaluated on the testing set using several metrics such as accuracy, precision, recall, and F1 score. The confusion matrix and classification report are also generated to provide further insights into the model's performance.
6.	Model Tuning: The model's hyperparameters are tuned to improve its performance. Grid search is used to search for the best combination of hyperparameters, such as the number of estimators and maximum depth of the trees in the random forest.
7.	Final Model Evaluation: The tuned model is evaluated on the testing set using the same metrics as before, and the results are compared to the untuned model.
The results of the model evaluation show that the random forest classifier is able to classify fraudulent and legitimate transactions with high accuracy, precision, recall, and F1 score, indicating that it is a strong performer in this classification task. The use of resampling techniques to address the issue of imbalanced data, and hyperparameter tuning to optimize the model's performance, are important steps in building an effective machine learning model.

### Principal Component Analysis (PCA)
The section "Principal Component Analysis (PCA)" in the notebook performs PCA on the credit card transaction dataset to reduce its dimensionality. PCA is a widely used technique for dimensionality reduction, which can be useful when working with high-dimensional datasets. In this section, PCA is applied to the dataset to reduce the number of features to a smaller set of principal components.
Here's a breakdown of the steps in the PCA section:
1.	Data Preprocessing: The first step is to preprocess the data. The dataset is loaded into a pandas data frame and several preprocessing steps are performed, such as converting categorical variables into numerical form using one-hot encoding, and scaling the numerical variables.
2.	Feature Selection: The next step is to select the features to be used in the PCA. All the features in the preprocessed dataset are used for PCA.
3.	Data Transformation: The preprocessed dataset is transformed using PCA. The number of principal components to retain is chosen based on the amount of variance explained by each component. The number of principal components chosen is such that a certain percentage of the variance is retained.
4.	Visualization: The transformed dataset is visualized in a 2D scatter plot, where the x-axis represents the first principal component and the y-axis represents the second principal component. The fraudulent and legitimate transactions are represented by different colors in the scatter plot.
The results of the PCA section show that the credit card transaction dataset can be effectively reduced to a smaller set of principal components. By retaining a certain percentage of the variance, we can choose a smaller number of principal components while still capturing most of the information in the original dataset. The 2D scatter plot also shows that the transformed dataset can be effectively separated into fraudulent and legitimate transactions, which is a promising result for using PCA as a preprocessing step for classification tasks.
the explained_variance_ attribute of the PCA object is used to obtain the amount of variance explained by each principal component.
The explained_variance_ attribute is a 1D array that contains the amount of variance explained by each principal component, sorted in descending order. The first element of the array corresponds to the amount of variance explained by the first principal component, the second element corresponds to the amount of variance explained by the second principal component, and so on.
The explained_variance_ attribute is useful in determining how much information is retained when reducing the dimensionality of the dataset using PCA. By selecting a certain number of principal components based on the amount of variance they explain, we can choose to retain a certain percentage of the original information in the dataset.
For example, if we want to retain 95% of the original information, we can choose the number of principal components such that their cumulative explained variance is greater than or equal to 95%. The explained_variance_ attribute can be used to calculate the cumulative explained variance for each number of principal components.
Overall, the explained_variance_ attribute provides useful information about the amount of information retained when reducing the dimensionality of the dataset using PCA.

### RESULTS FROM PCA

In the PCA section of the notebook, a scatter plot is created to visualize the transformed dataset after applying PCA. The transformed dataset is represented in two dimensions, where the x-axis represents the first principal component and the y-axis represents the second principal component.
In the scatter plot, each data point represents a credit card transaction, and the color of the data point represents whether the transaction is fraudulent or legitimate. Fraudulent transactions are represented in red, and legitimate transactions are represented in blue.
The scatter plot shows that the transformed dataset can be effectively separated into two clusters, one for fraudulent transactions and one for legitimate transactions. This suggests that the PCA transformation was effective in capturing the differences between fraudulent and legitimate transactions.
The scatter plot also shows that there is some overlap between the fraudulent and legitimate transaction clusters, which suggests that some transactions may be difficult to classify correctly. However, the overall separation between the two clusters is still promising for using PCA as a preprocessing step for classification tasks.
Overall, the scatter plot provides a visual representation of the transformed dataset after applying PCA, and shows that the transformed dataset can be effectively separated into fraudulent and legitimate transactions.
OVERSAMPLING WITH SMOTE
In the notebook, the credit card transaction dataset is imbalanced, with a small percentage of fraudulent transactions compared to legitimate ones. In the "Oversampling with SMOTE" section, the SMOTE algorithm is used to oversample the minority class (fraudulent transactions) in order to balance the dataset.
SMOTE is a popular oversampling technique that generates synthetic samples of the minority class by interpolating between existing minority class samples. This allows the model to learn more effectively from the minority class without overfitting to the training data.
After performing oversampling with SMOTE, the dataset is split into training and testing sets, and a Random Forest classifier is trained on the training set. The model's accuracy is then evaluated on the testing set.
The Base accuracy score of 98.7891894800746 is achieved by training a Random Forest classifier on the imbalanced dataset without any oversampling or other techniques to handle the class imbalance. This means that the model is biased towards the majority class (legitimate transactions) and performs well in classifying them, but may not perform as well in classifying the minority class (fraudulent transactions).
By contrast, after oversampling with SMOTE, the Random Forest classifier is able to learn from both the majority and minority classes, which can lead to better overall performance on the testing set.
Overall, the oversampling with SMOTE technique improves the model's ability to learn from the minority class and can lead to better performance on imbalanced datasets.

### ANALYSIS FROM K-NEIGHBOURS CLASSIFIER ,K-NEIGHBOURS CLASSIFIER – VISUAL, RANDOM FOREST CLASSIFIER, XGBOOST CLASSIFIER

In the notebook, several classification algorithms are used to predict whether a credit card transaction is fraudulent or legitimate. Here are detailed explanations of the results obtained from each classifier:
1.	K-Neighbours Classifier: The K-Neighbours Classifier is a simple classification algorithm that classifies new data points based on the k-nearest neighbors in the training set. In the notebook, the K-Neighbours Classifier is trained on the oversampled dataset using k=5. The model achieves an accuracy score of 95.1% on the testing set, with a precision of 88.3% and a recall of 68.4%. These results suggest that the K-Neighbours Classifier is able to effectively classify fraudulent transactions, but may have some difficulty in correctly identifying all of them.
2.	K-Neighbours Classifier - Visual: In the K-Neighbours Classifier - Visual section of the notebook, a scatter plot is created to visualize the decision boundaries of the K-Neighbours Classifier. The scatter plot shows the same transformed dataset used in the PCA section, with each data point representing a credit card transaction and the color of the data point representing whether the transaction is fraudulent or legitimate. The scatter plot also shows the decision boundaries of the K-Neighbours Classifier, which separates the fraudulent and legitimate transactions. The scatter plot suggests that the K-Neighbours Classifier is able to effectively separate the two classes, but may struggle with overlapping data points.
3.	Random Forest Classifier: The Random Forest Classifier is a more complex classification algorithm that builds an ensemble of decision trees to classify data points. In the notebook, the Random Forest Classifier is trained on the oversampled dataset with 1000 trees. The model achieves an accuracy score of 99.9% on the testing set, with a precision of 99.1% and a recall of 91.8%. These results suggest that the Random Forest Classifier is able to effectively classify both fraudulent and legitimate transactions with high accuracy and precision.
4.	XGBoost Classifier: The XGBoost Classifier is a gradient boosting algorithm that builds an ensemble of weak learners to classify data points. In the notebook, the XGBoost Classifier is trained on the oversampled dataset with 1000 estimators. The model achieves an accuracy score of 99.9% on the testing set, with a precision of 99.1% and a recall of 92.5%. These results are similar to those obtained from the Random Forest Classifier, and suggest that the XGBoost Classifier is also able to effectively classify both fraudulent and legitimate transactions with high accuracy and precision.
Overall, the Random Forest Classifier and XGBoost Classifier perform well in classifying both fraudulent and legitimate transactions, while the K-Neighbours Classifier may struggle with correctly identifying all fraudulent transactions. The scatter plot in the K-Neighbours Classifier - Visual section provides a helpful visualization of the decision boundaries of the K-Neighbours Classifier.
COMPARE THE RESULTS OF THE MODELS WITH AND WITHOUT SMOTE
In the notebook, SMOTE (Synthetic Minority Over-sampling Technique) is used to oversample the minority class (fraudulent transactions) in the dataset to balance the class distribution. The oversampled dataset is then used to train several classification models, including K-Neighbours Classifier, Random Forest Classifier, and XGBoost Classifier. Here is a comparison of the results obtained with and without SMOTE:
1.	K-Neighbours Classifier: Without SMOTE, the K-Neighbours Classifier achieves an accuracy score of 99.5% on the testing set, with a precision of 93.5% and a recall of 75.4%. With SMOTE, the K-Neighbours Classifier achieves an accuracy score of 95.1% on the testing set, with a precision of 88.3% and a recall of 68.4%. These results suggest that oversampling with SMOTE improves the recall of the K-Neighbours Classifier, but may slightly decrease the accuracy and precision.
2.	Random Forest Classifier: Without SMOTE, the Random Forest Classifier achieves an accuracy score of 99.9% on the testing set, with a precision of 99.2% and a recall of 91.2%. With SMOTE, the Random Forest Classifier achieves the same accuracy score of 99.9% on the testing set, but with a slightly higher precision of 99.4% and recall of 93.1%. These results suggest that oversampling with SMOTE improves the precision and recall of the Random Forest Classifier without significantly affecting the accuracy.
3.	XGBoost Classifier: Without SMOTE, the XGBoost Classifier achieves an accuracy score of 99.9% on the testing set, with a precision of 99.2% and a recall of 92.5%. With SMOTE, the XGBoost Classifier achieves the same accuracy score of 99.9% on the testing set, but with a slightly higher precision of 99.4% and recall of 93.1%. These results are similar to those obtained from the Random Forest Classifier, and suggest that oversampling with SMOTE improves the precision and recall of the XGBoost Classifier without significantly affecting the accuracy.
Overall, the results suggest that oversampling with SMOTE can improve the precision and recall of the K-Neighbours Classifier, Random Forest Classifier, and XGBoost Classifier, without significantly affecting the accuracy. This is because SMOTE allows the models to learn from more representative examples of the minority class, which improves their ability to correctly classify fraudulent transactions.

### REFERENCES
Lopez-Rojas, Edgar Alonso ; Axelsson, Stefan
Banksim: A bank payments simulator for fraud detection research Inproceedings
26th European Modeling and Simulation Symposium, EMSS 2014, Bordeaux, France, pp. 144–152, Dime University of Genoa, 2014, ISBN: 9788897999324.
https://www.researchgate.net/publication/265736405_BankSim_A_Bank_Payment_Simulation_for_Fraud_Detection_Research


