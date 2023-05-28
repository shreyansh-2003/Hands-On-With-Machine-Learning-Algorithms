# Implementinh Decision Trees

---
__Author Name : Shreyansh Padarha__<br>
__Email : mailto:shreyansh.padarha@hotmail.com__<br>

---

># Introduction

This notebook involves implementing Sklearn's Decision Tree Classifier with hyperparameter tuning by making use of relevant visualisations, comments and explanations wherever deemed necessary during the execution. Relevant Evaluation Metrics are used and illustrated through the execution of the lab. Comments for the same are mentioned as well. The tasks within the 


<u><b>PART A - Linear Regression Library</b></u>

Import the sklearn.tree.DecisionTreeClassifier, and perform classification on the TItanic Dataset. The train and test datasets are given separately, due to which there is no need of train_test_split function.

Comment on the accuracy of the model on prediction. Comment on the accuracy, when the following parameters are modified - Criterion (gini / entropy / log_loss), max_depth, max_leaf_nodes, and random_state

<u><b>PART B - Dummy Classifier</b></u>

Compare your results with Dummy Classifier with the following parameters - most_frequent, prior, uniform, constant, and comment on the results.

---

># Objectives 

- To understand the implementation of decison tree with regards to binary classification problems.
- To compare and tune decison tree models using different parameters.
- To understand the usage and implementation of a Dummy Classifier

---

># Problem Statement
    
Performing Classification and regression using Decison Tree, conducting a parameteric analysis on the same and understanding the use case of Dummy Classifiers.
  
---

># Method 

1. Using in-built Sklearn library methods to perform decison tree classification, and creating dummy classifiers.
2. Comparing different models of decison tree by tuning various parameters
3. Using pandas dataframe to store the results and combinations. 
4. Comparing the accuracy scores with regards to the model's changing parameters.


---

># Observatoins 

### Part A
- It can be seen that there is no gini impurity in criteria, for the highest accuracy models.
- It can also be seen that the maximum leaf nodes for the highest accuracy models are all 10.
- The ideal combination, which requires the lowest time according to me will be of the following parameters:
    1. Criteria = log_loss/entropy
    2. Max_Depth = 6
    3. Max_Leaf_Nodes = 10
    4. Random State = Any 

__Comparitive Analysis__<br>
- As the max depth of the tree increases, understandably the accuraacy of the models increase, this plateaus after 4 levels, in the case of Titanic dataset.
- From 2 to 4 leaf nodes the model accuracy decreases steadilty from 0.8 to 0.78. Post which, as the number of maximum leaf nodes increase so does the model accuracy.
- As expected, the random state values hardly affect the outcome (accuracy) of the model.
- Surprisingly, Gini Index as a method had a volatile response to parameters after a certain extent. log_loss and entropy resulted in better, stable and more efficient models.

### Part B

The ```Dummy Classifier``` is a baseline model that predicts classes using simple rules, such as the most frequent class or a random class. Our model should perform better than this baseline in order to be considered useful.<br>
Based on the dummy classifier comparitive analysis, it appears that our model (Decison Tree entropy, with 0.84 accuracy) is performing better than the Dummy Classifier in any of the strategies that were tried.

---

># Results

1. The decision treee model can be tuned with relevant parameters.
2. The decision tree model has better accuracy than dummy classifiers.


----

># References

__StatQuest by Josh__: https://www.youtube.com/watch?v=_L39rN6gz7Y<br>
__Stackoverflow__: https://stackoverflow.com<br><br>
__Sklearn__<br>
https://scikit-learn.org/stable/modules/tree.html<br>
https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html

---

># Sample Notebook Output Screenshots

![image](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/7a5d9c7c-354c-417f-9748-f18f9d0fddba)


<br>

![image](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/aeca33cf-1611-4713-a90b-8c20ed0a0c6a)


<br>

![image](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/8ee0c47a-a499-4d52-bed2-0d2b0ec6a7cf)
