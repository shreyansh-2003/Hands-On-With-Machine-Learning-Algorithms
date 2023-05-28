
# Creating Preprocessing/Evaluation Metrics From Scratch
<img width="1343" alt="ss_main_Creating Preprocessing:Evaluation Metrics From Scratch" src="https://github.com/shreyansh-2003/Hands-On-With-Machine-Learning-Algorithms/assets/105413094/4bffc5b4-950a-4c3f-a2a4-20a2f4e324ef">

---
__Author Name : Shreyansh Padarha__<br>
__Email : mailto:shreyansh.padarha@hotmail.com__

---

> # Introduction

## Overview

The ```sklearn.preprocessing package``` provides several common utility functions and transformer classes to change raw feature vectors into a representation that is more suitable for the downstream estimators.

Usually, we use Data Preprocessing Functions like "Label Encoder", "Min Max Scaler", etc. without understanding the actual implementation of it. It is nothing complex but a set of mathematical/logical procedures that defines those functions.

Before we move on with complex machine learning implementations, we have to understand how are certain Preprocessing Techniques implemented in the Python Code. Therefore, this lab notebook aims at doing the same.

## Dataset Description 
There are 3 sheets- Dataset1, Dataset2, and Dataset3. Dataset1 and Dataset2 are identical in nature, except for the number of entries. Assume that the features "True_Value" and "Predicted_Value" are Labels and Predictions of a Regression Model. In the Dataset3, there is another feature named as "Result", which is a Binary Categorical Variable (assumption is that the minimum marks to clear the exam is 70% [35 Marks]).

## Tasks

#### A) From the attached file, load the three different sheets as df1, df2, and  df3 onto the memory of Jupyter Notebook, as Python DataFrames.

#### B) Write the user defined functions for the implementation of following -

1. To find the measures of central tendency. Another function parameter can select what type of value should be returned.
    - Mean
    - Median
    - Mode
2. To scale a list of Numerical Values between 0 and 1 (minimum and maximum will be respectively 0, and 1)
3. Given a number and a set of values (in a list), find the percentile of the number in that array set.
4. Given a set of values, categorise the datapoints into - LEFT_OUTLIER, MIN, Q1, Q2, Q3, MAX, RIGHT_OUTLIER, and plot the above values onto an axis
5. Given two sets of values, find the correlation between them
6. To encode and decode a Categorical Variable into a Numerical Representation.
7. To check the goodness of fit for the Regression Model using Evaluation Metrics. The evaluation metrics can be selected based on a parameter ("R2", "MSE", "MAE").
    - R-Squared (R² or the coefficient of determination)
    - Mean Squared Error
    - Mean Absolute Error
        
#### C) Make use of the above user-defined functions, and illustrate the results. In addition that, perform the below tasks -
1. Test the User Defined Functions that you code for various functionalities, and verify its validity by comparing with functions in sklearn.preprocessing 
2. Find the percentile of the number "last two digits of your register number + 10" in df2.
3. Check whether the dataset size affects the values of Regression Evaluation Metrics
4. Is there any relationship between the Squared Pearson Correlation Coefficient and R2 value?

---
> # Objectives  

To Understand what goes behind the easy-to-use transformation and data pre-processing libraries, and be able to replicate that without other llibraries or in-built functions.

---
> # Problem Statement

Applying logical thinking, statistical formulas to create user-defined functions that mimmic the working of methods of libraries like sklearn, statistics, etc.

---
> # Approach / Methods 

### Question 1

___From the attached file, load the three different sheets as "df1", "df2", and "df3" onto the memory of Jupyter Notebook, as Python DataFrames.___

The datasetes are imported through pandas ```read_excel()``` method. To import different sheets of the same excel file a second parameter called 'sheet_name' is passed, and the sheet name is specified in the same.

The datasetes shape has been retrieved through the ```.shape()``` method, and its evident as rows, column for each dataset.

### Question 2

___Write the user defined functions for the implementation of following -___



___1) To find the measures of central tendency. Another function parameter can select what type of value should be returned.(Mean/Median/Mode)___

I created a user defined function to calculate the measures of tendancy. A keyword argument called method is passed, which enables the user to pass `"Mode" / "Median" / "Median"` and the function calculates the same. The function makes use of other smaller user defined functions, for each task. The processes used for each tendency are as follows:

    1. Median (arr_median) : For calculating the median, a bubble sort enabling function is created, which sorts the array post which the standard median formula is used to find the required index. The index formula changes depending on whether the number of elements are even or odd.
    
    2. Mode (arr_mode) : For calculating the mode, we create a dictionary, which contains the frequency of each value in the array. Then we calculate the highest frequency. We use that frequency along with list comprehension to create an array of values, which all have the highest frequency. We return the first highest repetitive value as the mode.
    
    3. Mean : For calculating the mean, we initialise a total integer variable. Then, we loop through the array, and summate / keep adding the individual iterated value to the toal. In the end we, divide the total variable with the length of the array.


___2) To scale a list of Numerical Values between 0 and 1 (minimum and maximum will be respectively 0, and 1.___

I created a user defined function to create a min_max_scalled array from a given array. Using a previous user-defined function, I calculated the minimum and maximum value. I then iterated through the user provided array and applied the following formula, to each value, and appended it into a new array.

```Formula --> scalled_x = (x - minimum) / (minimum + maximum)```

Finally, I returned the scalled values in an array form.

___3) Given a number and a set of values (in a list), find the percentile of the number in that array set.___

I created a user defined function to convert the array's values to percentile ranks. We, iterate through the array and apply the formula below to calculate the rank of each value, and then create key value pairs, where the key is the value and the value is the percentile rank.

```Formula --> rank_x = (total values below 'x' / total values) X 100```

Finally, I returned the ranks in a dictionary format.

___4) Given a set of values, categorise the datapoints into - LEFT_OUTLIER, MIN, Q1, Q2, Q3, MAX, RIGHT_OUTLIER, and plot the above values onto an axis___

I created a user-defined function, to calculate ```Q1 | Median | Q3 | IQR | Right Outlier | Left Outlier | MIN | MAX | IQR``` and used the values to display a scatter plot that resembles a box plot.

- The left outliers are all the elements that fall below the lower IQR threshold, which is Q1 - 1.5 X IQR.

- The right outliers are all the elements that fall above the lower IQR threshold, which is Q3 + 1.5 X IQR.

For plotting the plot, we plot multiple scatter plots on one axis with different marker size, color and shape. We leave the y axis empty, and we define the legend in the order of the plots. 

___5) Given two sets of values, find the correlation between them.___

I created a user defined function, with two arguments, array 1 and array 2. Post doing that I applied the infamous ```spearman's rank correlation``` formula.

___6) To encode and decode a Categorical Variable into a Numerical Representation.___

I created a user defined function, which follows the following steps to label encode the values of an array:

    1. Sort the array in ascending order
    2. Find all the unique values, and map them to a unique encoded number and store it as key and value pairs. Eg. "Ant" --> 0, "Bat" --> 1,...
    3. Iterate through the original array and match the element with the mapping dictionary's keys, and assign them the encoded value.
    

___7) To check the goodness of fit for the Regression Model using Evaluation Metrics. The evaluation metrics can be selected based on a parameter ("R2", "MSE", "MAE").___

I created a user defined function, with three arguments, true values array, predicted values array and evaluation metrics array. After which I calculated the ```R2 SCORE | MSE SCORE | MAE SCORE``` using their formulas avaiable on the internet.

### Question 3

Question 3 Involved comparing the functions I created with the pre-existing python library methods, as well as applying the created functions on the dataset provided, to answer certain questions

---
> # Observations 

- The user-defined functions created by me, for measuring the evalutation metrics (R2|MSE|MAE), return the exact same value, as that of the 'sklearn.metrics' python library methods.

- The user-defined functions created by me, for measuring the measures of central tendancy (mean|median|mode), return the exact same value, as that of the 'statistics' python library methods.

- The user-defined functions created by me, for label encoding categorical variables, return the exact same value and order, as that of the 'sklearn.preprocessing' python library methods.

- The user-defined functions created by me, for minmax scaling, return the exact same values, as that of the 'sklearn.preprocessing' python library methods, except the highest value. The highest value in my scalled values is represented by 1, while the highest value in the sklearn.preprocessing module is 0.9999999.


- From the calculations conducted, it can be seen that the size of the dataset does not effect the evaluation metric values (R2 | MSE | MAE), till the datasts considered are identical. The values returned for different sized dataset were the same.

- R2 Score value is the square of the Pearson Correlation Coefficient (R).

---
> # Results 

The functions created by me, act in a similar manner to that of the sklearn library. The sklearn library has more customisability and is tailor-made for working with pandas dataframe objects.

<br>__Creating A Box Plot from Scratch__<br>

![image](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/0f1a5593-1afc-4155-99a3-6e59fd504028)


---

> # Learnings

This lab made me appreciate what goes behind the making of such elaborate libraries. It aslo improved my array manuvering skills and my logical application.

---
> # References

1. Sklearn Documentation: https://scikit-learn.org/stable/
2. Matplot Library Documnentaion: https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html 
3. GeeksForGeeks: https://www.geeksforgeeks.org/ 
4. StackOverflow: https://stackoverflow.com/ 

---
> # Completion Status:

| Question | Status |
| --- | --- |
| __Question 1__ | Completed |
| __Question 2__ | Completed |
| Question 2.1 | Completed |
| Question 2.2 | Completed |
| Question 2.3 | Completed |
| Question 2.4 | Completed |
| Question 2.5 | Completed |
| Question 2.6 | Completed |
| Question 2.7 | Completed |
| __Question 3__ | Completed |
| Question 3.1 | Completed |
| Question 3.2 | Completed |
| Question 3.3 | Completed |
| Question 3.4 | Completed |

---
