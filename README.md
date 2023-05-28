# Hands On With Machine Learning Algorithms

---
__Author Name : Shreyansh Padarha__<br>
__Email : mailto:shreyansh.padarha@hotmail.com__
---

># Overview
This repository contains a collection of labs that explore various machine learning algorithms and techniques. Each lab focuses on a specific topic and provides detailed explanations, code examples, and analysis. The labs cover clustering, classification and regression algos, hyperparameter tuning, data-preprocessing and various evaluation metrics.

__Coverage__
- The algorithms covered within the repository are Linear Regression OLS, Linear Regression with Gradient Descent, Logistic Regression, Decision Tree, Random Forest, SVM (Support Vector Machines), KMeans Clustering, Hierarchichal Clustering (AGNES).
- The labs also cover various feature engineering, scaling, generating and encoding techniques that help in getting the data prepared for ML solutions.
- Most Labs also include manual Hyperparameter Tuning (not GridSearchCV), as it helps in better understanding the optimal parameters and their workaround.

- All Lab Directories have these files:
  1. ```main_notebook.ipynb``` that are jupyter notebooks for those particular labs and contain all the relevant code and its outputs, with detailed line-by line comments.
  2. ```pdf_notebook.pdf``` that are pdf versions of the jupyter notebook
  3. ```README.md``` are detailed markdowns, containing an introduction, tasks, methods, results and observations in-line with the labs.
  4. Additional ```excel```,```csv```,```pickled``` files w.r.t. the lab.

![image](https://github.com/shreyansh-2003/Hands-On-With-Machine-Learning-Algorithms/assets/105413094/11121bb9-a799-4aa6-b241-da51f1e47763)

---
> # Directories And Algorithms
Given below are the directories within the repository with their different objectives and sample output screenshots.

---

> ## Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets
__Brief__<br>
This lab aims to analyze the effectiveness of clustering algorithms in simplifying large datasets for machine learning. The specific focus is on comparing KMeans and Agglomerative Clustering methods. The objectives of this lab include:
- Downloading the "Car Evaluation" dataset from the UCI Repository.
- Finding the optimal number of clusters using the Elbow and Silhouette methods.
- Comparing KMeans and Agglomerative Clustering methods for clustering the dataset.
- Validating the optimal number of clusters.
- Tuning hyperparameters for KMeans (n_clusters, max_iter, init, algorithm).
- Tuning hyperparameters for Agglomerative Clustering (n_clusters, metric, linkage).
- Plotting the hierarchical clustering dendrogram.
- Comparing the better clustering algorithm with a classification algorithm.

__Sample Output Screenshots__<br>

---
> ## Creating Preprocessing:Evaluation Metrics From Scratch
__Brief__<br>
This lab focuses on understanding and implementing common preprocessing techniques and evaluation metrics from scratch. The objectives of this lab are:
- Loading different sheets of a dataset as Python DataFrames.
- Implementing user-defined functions for measures of central tendency (mean, median, mode).
- Scaling a list of numerical values between 0 and 1.
- Finding the percentile of a number in a given array.
- Categorizing data points into different categories and plotting them.
- Finding the correlation between two sets of values.
- Encoding and decoding a categorical variable into a numerical representation.
- Checking the goodness of fit for a regression model using evaluation metrics.
- Testing the user-defined functions and comparing them with sklearn.preprocessing functions.
- Performing additional tasks such as finding percentiles in a dataset, analyzing the impact of dataset size on - regression evaluation metrics, and exploring the relationship between squared Pearson correlation coefficient and R2 value.

__Sample Output Screenshots__<br>

---
> ## Customer Churn Analysis for Improving Customer Retention
__Brief__<br>
In this lab, the focus is on customer segmentation and analysis to optimize marketing strategies. The objectives of this lab include:
- Identifying distinct customer segments based on characteristics and behaviors.
- Determining the optimal number of clusters using evaluation techniques like Silhouette analysis and the Elbow method.
- Evaluating the quality and validity of customer segmentation through measures such as silhouette scores.
- Utilizing Random Forest for classifying customers into different segments and identifying key differentiating features.

__Sample Output Screenshots__<br>

---
> ## Data Preperation, EDA and Feature Engineering for ML Solutions
__Brief__<br>
This lab involves using a webscraped dataset from carDekho to perform exploratory data analysis (EDA) and feature engineering. The objectives of this lab include:
- Feature scaling and encoding/transformation.
- Performing statistical data analysis on the dataset.
- Pickling transformations for future inverse transformations.
- Conducting EDA and formulating questions based on the dataset.
- Preparing the dataset for applying a linear regression model.

__Sample Output Screenshots__<br>

---
> ## Decision Tree Implementation
__Brief__<br>
This lab focuses on implementing decision tree classifiers using Sklearn's DecisionTreeClassifier. The tasks include:
- Performing classification on the Titanic dataset.
- Commenting on the accuracy of the model and the impact of different parameters.
- Comparing the results with a Dummy Classifier using different parameters.
__Sample Output Screenshots__<br>

---
> ## Gradient Descent In-depth Implementation
__Brief__<br>
This lab dives into the implementation of linear regression using gradient descent. The objectives of this lab include:
- Implementing linear regression with gradient descent
- Visualizing the convergence of the model's loss to the minima
- Analyzing the effects of the number of iterations (epochs) and learning rate on the training process
- Comparing the model with ordinary least squares (OLS) based linear regression

__Sample Output Screenshots__<br>


---
> ## Hardcoding Evaluation Metrics
__Brief__<br>
In this lab, you will find a comprehensive implementation of evaluation metrics for binary classification problems. The evaluation metrics implemented from scratch include:
- Confusion matrix
- Accuracy score
- Precision
- Recall
- F1 score

__Sample Output Screenshots__<br>

---
> ## Linear Regression Models Comparitive Study on carDekho Cleaned Dataset
__Brief__<br>
This lab focuses on a comparative study of linear regression models using the carDekho cleaned dataset. The objectives of this lab include:
- Performing exploratory data analysis (EDA) on the dataset
- Implementing linear regression using the scikit-learn library
- Exploring various variations of linear regression available in the statsmodels library
- Comparing the results of different models
- Predicting car prices using the best model

__Sample Output Screenshots__<br>

---
> ## Logist Regression and SVM
__Brief__<br>
In this lab, we delve into the world of logistic regression and support vector machines (SVMs) for classification tasks. The objectives of this lab include:
- Creating classification datasets with informative features
- Applying feature scaling techniques to enhance model performance
- Comparing the suitability of logistic regression and SVMs on the datasets
- Evaluating the impact of applied transformations on the classification results

__Sample Output Screenshots__<br>

---
