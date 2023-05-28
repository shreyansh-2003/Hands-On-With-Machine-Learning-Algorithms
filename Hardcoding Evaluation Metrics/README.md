# Hardcoding Evaluation Metrics 
<img width="1098" alt="ss_main_Hardcoding Evaluation Metrics" src="https://github.com/shreyansh-2003/Hands-On-With-Machine-Learning-Algorithms/assets/105413094/e9da683c-3646-45c5-bc57-5ab289a05031">

---
__Author Name : Shreyansh Padarha__<br>
__Email : mailto:shreyansh.padarha@hotmail.com__

---

># Introduction

This notebook, is a short implementation (from scratch) of the evaluation metrics listed below. It involves creating user defined functions for creating the following for a ```binary classification problem```, when y_pred and y_test is given -

- Confusion Matrix
- Accuracy Score
- Precision
- Recall
- F1 Score

---
> # Approach / Method

The simple approach I used was, to create a Class named ```evaluation_metrics``` which has all the different evaluation metrics within it.  
__All the methods and process are elaboratively mentioned via comments__

---
> # Observations 

The created user defined methods within the class return the same values as sklearn's metrics methods.

> # Learnings

This lab made by concepts on recall, tradeoff f1 score, roc and auc absolutely crystal clear. It was important as i had missed the theory classes for the same.

---

> # Theory

![overall](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/f6e3878a-54f1-4d82-9c5a-3d96ef29c10d)

## Precision:
Precision is the proportion of true positive predictions over the total number of positive predictions made.<br>
__Precision = TP / (TP + FP)__

## Recall:
Recall is the proportion of true positive predictions over the total number of actual positive examples.<br>
__Recall = TP / (TP + FN)__

## F1 Score:
The F1 score is a weighted average of precision and recall. It provides a single measure of a classifier's performance that takes into account both precision and recall.<br>
__F1 Score = 2 * (Precision * Recall) / (Precision + Recall)__

## Confusion Matrix

A confusion matrix is a table or visual represntaion that summarizes the classification performance of a ML model on a set of test data. The matrix is used to evaluate the performance of a classification alogrith. It does this by calculating the number of __true positive__, __true negative__, __false positive__ and __false negative__. 

Here's a breif about the afermentioned terms:

1. __True Positive (TP)__: The number of positive instances/values that are correctly predicted as positive.
2. __False Positive (FP)__: The number of negative instances/values that are incorrectly predicted as positive.
3. __True Negative (TN)__: The number of negative instances/values that are correctly predicted as negative.
4. __False Negative (FN)__: The number of positive instances/values that are incorrectly predicted as negative.

__Visual Representation of a Confusion Matrix__

|   | __Predicted Positive__ | __Predicted Negative__ |
| --- | --- | --- |
|__Actual Positive__| True Positive (TP) | False Positive(FP) |
|__Actual Negative__| False Positve (FP) | True Negative(TN) |

<br><center>**Confusion Matrix**<center>

---

  ![img](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/8ba9a82c-2788-4433-9d4c-de3b4af8d8a2)

    
<br><center>**fig2.**<center>

  ## Plotting points on an AUC Curve:
The AUC (Area Under the Curve) curve is a graphical representation of the performance of a binary classification model. It shows the trade-off between sensitivity (recall) and specificity (1 - false positive rate) for different classification thresholds.<br>
To plot points on an AUC curve, you need to calculate the __false positive rate (FPR)__ and __true positive rate (TPR)__ for different classification thresholds.<br>

__Steps Involved__

1. The FPR is calculated as FP / (FP + TN).<br> 
2. The TPR ism calculated as TP / (TP + FN).<br>
3. Then, you can plot the TPR on the y-axis and the FPR on the x-axis for different classification thresholds. 
4. The AUC is the area under the curve.<br>

![auc](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/c7d467ae-a261-4610-98e8-885ef2f4363b)

  
---
> # References

__Fig 1__<br> 
Yuexiong Ding, City University Of HK, Analyzing the Leading Causes of Traffic Fatalities Using XGBoost and Grid-Based Analysis: A City Management Perspective
  
__Fig 2__<br> 
Anuganti Suresh, Medium : https://medium.com/analytics-vidhya/what-is-a-confusion-matrix-d1c0f8feda5
    
__Fig 3__<br> 
Sarang Narkhede, Medium, Understanding AUC - ROC Curve : https://towardsdatascience.com/understanding-auc-roc-curve-68b2303cc9c5
    
__Heart Disease Dataset__<br>
https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset<br>

1. Matplot Library Documnentaion: https://matplotlib.org/
2. StackOverflow: https://stackoverflow.com/ 
3. sklearn: https://scikit-learn.org/stable/


---   
> # Completion Status:

| Question | Status |
| --- | --- |
| Confusion Matrix | __Completed__ |
| Accuracy Score | __Completed__ |
| Precision| __Completed__ |
| Recall| __Completed__ |
| F1 Score | __Completed__ |
  
  
