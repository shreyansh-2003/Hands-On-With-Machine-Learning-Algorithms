# Linear Regression Models Comparitive Study on carDekho Cleaned Dataset
<img width="1232" alt="ss_main_Linear Regression Models Comparitive Study on carDekho Cleaned Dataset" src="https://github.com/shreyansh-2003/Hands-On-With-Machine-Learning-Algorithms/assets/105413094/25a4a8cf-38ee-48e4-b778-e1b8c6450870">

---
**Author Name :** Shreyansh Padarha<br>
**Email : mailto:shreyansh.padarha@hotmail.com**

---
>## Introduction 

This notebook aims at importing the previously cleaned dataset, performing an EDA on it, and using different manual hyperparameters to create different linear regression models and comparing them. The tasks on a broader scale include:

- Import the Dataset that you created as part of the ```Data Preperation, EDA and Feature Engineering for ML Solutions``` LAB .
- Perform basic EDA on the same
- Perform Linear Regression with the SKLearn Library
- Use different variations of Linear Regression as available in statsmodels library
- Compare the results of various models

---
> # Objectives  

- To be able to import the previously cleaned dataset, inverse transform it and perform a basic EDA on it.
- To Perform Linear regression using SKLearn Library.
- To implement various linear regression models available on statsmodels.
- Comapre the results of the different models, and playing around with their hyperparameters.
- Predict the price, using the best available model, for a given user input.


---
> # Problem Statement

Comparing the different available models on sci-kit learn and statsmodels library, and analysing their implementation and reults in a nutshell

---
> # Approach / Methods 

### 1. Importing the dataset

Using pandas inbuilt method __```read_csv()```__ to import the previously transformed, ready for linear regression and cleaned dataset of Lab 1.

### 2. Inverse Transforming the dataset for EDA__

I used __```pickle```__ library to mantain byte stream through different Python sessions (Lab 1 --> Lab 3). As i saved the encoded objects as pickle in Lab 1, I loaded those same pickle files, in this .ipynb file. Then, I used sklearn's __```inverse_transform()```__ to decode the features, which were label encoded, ordinal encoded, one-hot encoded and minMax scalled. I transformed and decoded the values in a copy of the imported dataframe, called ```eda_df```.

### 3. EDA related__

- Using seaborn's  __```.heatmap()```__ along with panda's __```.corr()```__ to plot a correlation heatmap.

- Using seaborn's __```.regplot()```__ along with matplotlib's __```.subplot()```__ to plot multiple regression plots for Odometer Reading of cars.

- Using seaborn's __```.catplot()```__ along with parameter _```kind = 'box'```_ to plot a boxplot of different brands and their price.

- Using seaborn's __```.catplot()```__ along with parameter _```kind = 'bar'```_ and _```row = 'DealingType'```_  to plot three barplots (each row --> one plot), to compare the daealing type with the brands and prices

### 4. Linear Regression Using SKLearn

- Importing Sklearn libraries
- Creating a dataframe _`resutls_dataframe_sk`_ to store the different model permutations and their results. The features of the dataframe are:
    1. Library
    2. Model
    3. Features
    4. FeatureCount
    5. RandomState
    6. TestingSize 
    7. Object
    8. Accuracy_R2_Score
- Using Slicing and Multiple for loops to extract all possible feature combinations, to feed in the model's as independent variables. (There are 55 possible unique combination of features, that can be considered as independent variables)
- Creating a user defined function __```performSKLearnLR()```__, that takes in, X,y, random state and testing split as parameters, and returns the R2 accuracy score and the model object.

Then using a for loop, I iterate through an array of combinations, testing split, random states, and pass them through my user-defined function, and appending the different model combinations in my results_dataframe_sk dataset. I also created a new column _```FeaturesExcluded```_, to store the features that were'nt included in the model.

### 5. Linear Regression Using statsmodels

- Importing stastsmodels.api library
- Creating a dictionary of mehtods and model name
- Iterating through the dictionary and possible combinations array created earlier, to generate different linear regression models. Appending those models and their accuracy scores to _```results_dataframe_sm```_ dataframe.

### 6. Comparing SKLearn vs OLS Results

- Merging statsmodels, sk-learn model results dataset using __```pd.concat()```__, while dropping additional hyperparameters of sklearn dataframe like _Testing Sixe_, _Random State_.

### 7. Predicting the car price based on 'user input'

- For predicting the price based on user input I Created user-defined functions to encode the variables again and feed back to the model.


- The model i selected for predictions, considered all the features, had a training testing split of 70:30, and the random state as 0.

---
> # Observations 

### 1. EDA

- Price (Target Variable), does'nt have a strong positive or negative correlation with any feature. But it is heavily dependednt (positive correlation) on Age of the car. It also has weak negative correlation with Distance, Fuel Type and Number of owners.
- It can be observed that the Age of the Car and Number of Owners have a Positive relationship with the distance travelled by the car. This supports logical reasoning that, as the car gets older and the more number owners it goes through, the more distance the car travels. Similarly, it can be observed that as the car travels longer, the price listing decreases. It again supports basic understanding that due to depreciation, wear & tear through distance travelled, the listed price of the car also decreases.
- It can be seen that Audi has the Costliest car, followed by Mercedes-Benz.
- BMW, Mercedes-Benz, Volvo, Landrover and Jaguar's cars are pricier than their competitors, which makes sense as these company has a lineup of luxury sedans, luxury SUVs, CSUVs.
- Barring a few companies, almost all have many outliers in theri price listing. This shows that prices of cars are not as much brand dependent as they are on other factors.
- KIA and MG have one of the least number of listings on this webscrapped dataset. This might be because, KIA and MG are relatively new entrants in the Indian market, and people might have just bought the cars.
- Trustmark Broker is only reserved for Ford, Mahindra, Toyota, Hyundai, Maruti, Honda and Renault. These brands generally target the average consumer / mass.
- Direct Owner, covers almost all different brands and also different vantage points.

### 2. Linear Regression Using SKLearn

- __Highest Accuracy Score (SKLearn):__ 0.4928
    + _Feature Count:_ 9
    + _Features not considered:_ 'Automatic'
    + _Random Stae:_ 0
    + _Training Testing Split:_ 70:30


- __Total Models Simulated (SKLearn):__  1540
    + _Models with Negative Accuracy (R2 Scores):_  5
    + _Models with Accuracy>0.1 (R2 Scores):_ 1174
    + _Models with Accuracy>0.2 (R2 Scores):_ 836
    + _Models with Accuracy>0.3 (R2 Scores):_ 307
    + _Models with Accuracy>0.4 (R2 Scores):_ 136  
  
  
- The top 10 highest accuracy models, all have a random state of either __0 or 10__. Their feature counts range from __8 to 10__. The testing sizes of the top 10 models are varied in nature, but mostly __80:20__, __70:30__ or the rare __60:40__.
- Out of the top 10 highest accuracy models, __7__ have excluded either __'Brand', 'Automatic' or 'Brand'__ and 'Automatic' as a feature to be considered.

- It is observed that the feature count __9__ has the highest average accuracy score, followed by __10 and 8__. The worst performing feature count is __4__.
- When the Random State is set to __0 or 10__, the models have better accuracy. Other than that, all the random states give relatively similar accuracy score.
- It can be understood that test size, doesn't have a significant impact on the accuracy of the model. All models hav similar accuracy at varied test sizes, although __70:30__ and __80:20__, seems to be the most optimum split
- It can be observed that excluding the following feature/s, has a __positive impact__ on the accuracy of the model:_
    - Brand
    - Brand, Automatic
    - Automatic   
- It can also be deduced that the ```Age of the car``` and the ```odometer``` have a major impact on the accuracy of the model, and must be included as variables while training the model.


### 3. Linear Regression Using statsmodels

- __Highest Accuracy Score (statsmodels):__ 0.456451
    + _Feature Count:_ 10
    + _Features not considered:_ None
    + _Random Stae:_ NA
    + _Testing Training Split:_ NA


- __Total Models Simulated (statsmodels):__  220
    + _Models with Negative Accuracy (R2 Scores):_  0
    + _Models with Accuracy>0.1 (R2 Scores):_ 168
    + _Models with Accuracy>0.2 (R2 Scores):_ 116
    + _Models with Accuracy>0.3 (R2 Scores):_ 53
    + _Models with Accuracy>0.4 (R2 Scores):_ 24

    
- The top 10 highest accuracy models, have features considered count ranging from __8 to 10__. The feature that is generally excluded in the 10 best models are __Automatic__.
   
- Similar to SKLearn library, the statsmodels lr models, also indicate that the optimum feature count range from __8 to 10__. In _OLS, GLS, WLS,_ the feature count and the accuracy score have ___positive progressive relationship__.

- _GLS,WLS,OLS,GlSAR_ all give the exact same accuracy score for the varying data and models.

- Compared to SKLearn the features excluded in statsmodels LR, dont impact the accuracy score as much. But still similar to SKLEarn when 'Brand', 'Brand, Automatic' and 'Automatic' are excluded from the features for modelling, the accuracy is higher.

### 4. Comparing Models of sci-kit learn and statsmodels library

- It can be seen that across the various model permuattions of both the libraries, statsmodels has a slightly better average accuracy in the models it generates. But, as there is _customisability in test splits and random state in sci-kit learn library_, __the top 10 highest accuracy models are all generated throught sci-kit simple linear regression.__

- All the models generated with an accuracy over 0.46 belong to sci-kit learn.
- Highest Accuracy:
    1. sci-kit learn: 0.49 (features considered = 9)
    2. statsmodels: 0.46 (features considered = 10)
 
This discrepency can be pinned down to two things, sci-kit learns's more offerings when it comes to ```hypertuning parameters```, and the fact that we weren't able to try other LR models provided by statsmodels library.

There is a linear relationship between the features considered and the accuracy of the models, irrespective of the library used. statsmodels data points, are more proportional, while sc-kit learn has more scattered data points. This is because, external factors like testing_size and random_state also affected the R2 score in sci-kit learn models.


---
> # Results 

The price of the car is heavily dependent on the age of the car and has weak negative correlation with distance, fuel type and number of owners. Audi has the costliest car, followed by Mercedes-Benz, and BMW, Mercedes-Benz, Volvo, Landrover, and Jaguar's cars are pricier than their competitors. KIA and MG have one of the least number of listings on this web-scrapped dataset. Trustmark Broker is only reserved for Ford, Mahindra, Toyota, Hyundai, Maruti, Honda and Renault, while Direct Owner covers almost all different brands and also different vantage points.


The highest accuracy score achieved in linear regression using the SKLearn library is 0.4928 with nine features and excluding the 'Automatic' feature. The optimum feature count for the SKLearn library ranges from 8 to 10, and the most critical features are age of the car and odometer.

<img width="1005" alt="image" src="https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/23448d3c-cc91-4fd4-9a7c-30a7150a107d">


The highest accuracy score achieved in linear regression using the statsmodels library is 0.456451 with ten features and none excluded. The optimum feature count for the statsmodels library ranges from 8 to 10, and the feature that is generally excluded is 'Automatic.'

__Comparing the libraries and their models (specific to this dataset)__

Comparing the performance of the two linear regression models, it can be observed that the SKLearn model generally performs better than the statsmodels model in terms of accuracy, with the highest accuracy score of 0.4928, while the highest accuracy score of the statsmodels model is 0.4565.
However, the statsmodels model has the advantage of providing more detailed statistical information, such as p-values and t-statistics, which can be used to assess the significance of individual features in the model.

---

> # Learnings

This lab program, made me realise that there are a vast variety of linear regression models that are out there, out of which, a data scientist, ml engineer or statistician needs to understand which model, and which hyperparameters are supossed to be selected and fine-tuned to give the desired accuracy and result.

From a coding POV, I made use of as many user-defined functions as I could, and it was fun to render so many different permutations of LR models in such short amount of time.

---
> # References

1. Sklearn Documentation: https://scikit-learn.org/stable/
2. statmsodel Documentation: https://www.statsmodels.org/stable/index.html
3. Matplot Library Documnentaion: https://matplotlib.org/
4. GeeksForGeeks: https://www.geeksforgeeks.org/ 
5. StackOverflow: https://stackoverflow.com/ 
6. Seaborn Documentation: https://seaborn.pydata.org/api.html#objects-api

---
> # Completion Status:

| Question | Status |
| --- | --- |
| __Objective 1__ (Importing the dataset) | __Completed__ |
| __Objective 2__ (Performing a basic EDA) | __Completed__ |
| __Objective 3__ (Linear Regression with SKLearn Library)| __Completed__ |
| __Objective 4__ (Linear Regression"s" with statsmodel Library)| __Completed__ |
| __Objective 5__ (Comparing LR Model Results) | __Completed__ |

---

> # Sample Notebook Output Screenshots

<img width="987" alt="image" src="https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/30d7d70b-c2fd-4554-8b10-d67a09ef6a6e">

<br>

<img width="985" alt="image" src="https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/66da4722-2276-45e4-bd2a-e611d63c8ecf">
