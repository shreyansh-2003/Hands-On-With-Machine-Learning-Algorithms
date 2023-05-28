# Introductory EDA & Feature Engineering for ML Solutions

<img width="1387" alt="ss_main_Data Preperation, EDA and Feature Engineering for ML Solutions" src="https://github.com/shreyansh-2003/Hands-On-With-Machine-Learning-Algorithms/assets/105413094/d4aaaa11-4022-4041-9dff-5d5ac1433bb5">

---
**Author Name :** Shreyansh Padarha<br>
**Email : mailto:shreyansh.padarha@hotmail.com**
---

> ## Introduction 

This notebook aims at using the ```carDekho webscraped dataset``` to ilustrate:
1. Feature Scaling 
2. Encoding / Transformaton
3. Feature Engineering 
4. Feature Generation
5. Perform Statistical Data Analysis on the Dataset
6. Pickle all transformations (scaling, encoding) for future inverse transformation
7. Perform an EDA
8. Formulate and reverse engineer questions regarding the dataset.
9. Prepare the Dataset for applying Linear Regression Model, by making use of "Price" as the target variable. 
    
---
> ## Objectives  

- To be able to perform a lab program with neat documentation
- To encode and scale variables with logic and sense.
- To make a data ready for linear regression using data transformation
- To perform quick EDA based on a dataset.

---
> ## Problem Statement

Cleaning and transforming the webscrapped car selling website's dataset, prepping it for linear regression and performing statistical analysis and EDA on it.

---
> ## Approach / Methods 

1. Importing the dataset using panda's inbuilt method ```read_excel```.
2. Creating a user defined function that takes an object, and file name as arguments. It then uses ```pickle``` library's method ```.dump()``` to serialize the python byte data stream. Exporting the learners (encoders) using the created function.
3. Performing Label Encoding, MinMax Scalling, Oridnal Encoding and OneHot Encoding on all the features, so that the linear regression model can learn with ease. 
4. Performing Statistical Analysis using countplots, distribution plots and correlation heatmaps.
5. Crearting 6 interesting question and perfrorming and EDA in a visually appealing manner using line plots, scatter plots, pie charts, box plots, etc.
6. Exporting the transformed dataset into a csv file, for future linear regression.

---
> ## Observations 

### About the dataset

-This dataset contains 8 columns of information related to various car models, including the model name, age of the car, odometer reading, fuel type, gear system, and number of previous owners. The main focus of the dataset is the price of the cars, which is the target variable. During the process of feature selection, other variables that are relevant to predicting the price will be selected as well. Overall, this dataset provides a comprehensive description of different car models and their prices.

### STATISTICAL ANALYSIS

__Statistical Analysis on the dataset__

- There are no null values in the dataset.

- Price (Target Variable), does'nt have a strong positive or negative correlation with any feature. But it is heavily dependednt (positive correlation) on Age of the car. It also has weak negative correlation with Distance, Fuel Type and Number of owners.

- __Price Feature Spread__: Price data is highy concentrated around Rs. 1,00,000 - Rs. 15,00,000, and the data is extremely right skewed.

- __Age Of Car Feature Spread__: Although the car age data has a wide range, its highly concentrated from 5 to 12 years.


- __Odometer Feature Spread__:The odometer reading is highly concentrated between 20,000 kms and 160,000 Kms. The data is extremely right skewed.

- The graph is supporting basic common sense that when the car travels more, the car depreciates in value. There is a strong non-linear relationship between Price and OdoMeterReading.

- It can be observed that Maruti has the highest number of cars listed on teh website the data was webscrapped from followed by Hyundai, Tata and Mahindra. The proportion of Automatic to Non-Automatic cars is also steep in nature.

### EDA

__Does the age of the car affect the price ?__

- The age of car and price are inversely related, as the age of car increases the price its listed at decreases. Although, there is a small spike from 1 to 4 years, where the price surprisingly increases. This could be either because of well, maintanance or other market factors.


__Do the number of owners, that have owned a car impact its price ?__

- It can be understood from the dataset that as the car switches more hands, the price depreciates. The more the number of owners have been, the lesser the listed price. 

- Test drive cars have the highest average price, as they are probably the least used.

__What fuel type cars are mostly listed on the webscrapped dataset ?__

- It can be observed that majority of the cars run on "Diesel", closely followed by Petrol. The least number of cars run "Battery (electric)", i.e. only one car.


__Are there some particular brands that a dealer type sells?__

- Trustmark Broker is only reserved for Ford, Mahindra, Toyota, Hyundai, Maruti, Honda and Renault. These brands generally target the average consumer / mass.
- Direct Owner, covers almost all different brands and also different vantage points.

__How does the number of previous owners affect the selling price of the car?__

- Diesel Cars are slightly pricier than other cars. LPG and CNG cars seems to be listed with a cheaper price tag. What's interesting to note is that the most expensive car listed on the website is a petrol car, Its a seven year old, 2019 AUDI RS7 Sportback Performance Sports Car, listed at a whopping 1,11,25,000 rs on the website.


---
> ## Results 

There are no particular results from this lab. We have generated a transformed dataset, which is encoded into numeric values for easing further linear regeression. From exploring the dataset, we could see, although the correlation between the variables is low, there is high dependance of price on factors like age of the car, odometer reading and number of owners the car has passed through.

<br>__Initial Dataset__<br>

<img width="1000" alt="image" src="https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/503b3221-4f0f-47c5-8e62-0ca1e2a2ef67">

<br>__Linear Regression Ready Dataset (Cleaned)__<br>

<img width="887" alt="image" src="https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/0861dd41-fa9d-421f-8d1d-b8a5de229690">

---

> ## Learnings

The lab gave me an insight on how to prepare a dataset for linear regression using the available measures like encoding and scaling. It also helped me realise that my EDA skills have improved, and performing a quick EDA can be hassle free and seamless, this can be credited to my __previous semester's data analytics subject__, where i was expossed to __seaborn, matplotliib and pandas library__.

---
> ## References

1. Sklearn Documentation: https://scikit-learn.org/stable/
2. Matplot Library Documnentaion: https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.scatter.html 
3. GeeksForGeeks: https://www.geeksforgeeks.org/ 
4. StackOverflow: https://stackoverflow.com/ 

---
