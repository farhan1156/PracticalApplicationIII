# Comparing Classifiers

The dataset used in this application comes from the UC Irvine Machine Learning [here](https://archive.ics.uci.edu/ml/datasets/bank+marketing). The data is from a Portuguese banking institution and is a collection of the results of multiple marketing campaigns.

# Understanding the data 

According to the accompanying paper (Moro et al., 2014) and the dataset description, this data represents **17 marketing campaigns** conducted by a Portuguese banking institution between **May 2008 and November 2010**. The dataset contains **41,188 records** with **20 input features** and 1 binary target variable (`y`), tracking whether clients subscribed to a bank term deposit after being contacted via telephone.

# Understadning the data 
The primary business objective is to predict whether a banking client will subscribe to a term deposit based on their profile and historical data.

It is a binary classification problem, The data is imbalance as 11.26% clients subscribe for term deposit and rest did not subscribe.

Bank want to 
1. Improve Campign ROI by focus marketing on high probability clients
2. Identify the most promising clients
3. Reduce marketing cost by avoid market to those clients which are unlikely to subscribe. 

#Analysis 

I have used the Dummy Classifier for baseline analysis.
![baseline](/data/baseline.png)

## Logistic Regression confusion matrix
![Logistic Regression](/data/lr_confusionMatrix.png)

## Time and Accuracy Analysis
![Time and Accuracy](/data/timeAndAccuracy.png)

## Improving the models 

Tuning Logistic Regression...
Best params: {'C': 0.01, 'class_weight': 'balanced', 'solver': 'lbfgs'}
CV AUC: 0.6498
Test Acc: 0.5747 | Test AUC: 0.6499
Total time: 5.78s

Tuning K-Nearest Neighbors...
Best params: {'metric': 'manhattan', 'n_neighbors': 31, 'weights': 'uniform'}
CV AUC: 0.6229
Test Acc: 0.8875 | Test AUC: 0.6314
Total time: 46.68s

Tuning Decision Tree...
Best params: {'class_weight': 'balanced', 'max_depth': 7, 'min_samples_leaf': 20, 'min_samples_split': 50}
CV AUC: 0.6568
Test Acc: 0.6763 | Test AUC: 0.6606
Total time: 2.30s

Tuning Support Vector Machine...
Best params: {'C': 10.0, 'class_weight': 'balanced', 'kernel': 'rbf'}
CV AUC: 0.6546
Test Acc: 0.6252 | Test AUC: 0.6547
Total time: 763.72s

![analysis](/data/analysisForAllModels.png)

![confusionMatrix](/data/confusionMatrix.png)

## Overall Summary
| Model | Strengths | Weaknesses |
|---|---|---|
| **Logistic Regression** | Fast, interpretable, competitive AUC | Assumes linear decision boundary |
| **K-Nearest Neighbors** | Non-parametric, intuitive | Slow at prediction, sensitive to irrelevant features |
| **Decision Tree** | Interpretable, handles non-linearity | Prone to overfitting without pruning |
| **SVM** | Strong generalization, handles high-dimensional data | Slow to train on large datasets, less interpretable |