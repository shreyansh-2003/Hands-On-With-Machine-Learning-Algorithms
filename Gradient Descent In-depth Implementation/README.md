# Explainable AI:  Using Multiple Linear Regression Gradient Descent (GD) to understand complicated models
---
__Author Name : Shreyansh Padarha__<br>
__Email : mailto:shreyansh.padarha@hotmail.com__<br>

---
> # Introduction 

This notebook aims as following and implementing the underlying tasks below:

- Implement Linear Regression with Gradient Descent.
- Use necessary visualisations, plots, and other relevant factors to prove that the model's loss is converging to the minima. 
- Check whether the number of iterations (epochs) or learning rate change the way in which the algorithm is trained. 
- Compare the trained model with any OLS based linear regression model and comment on your learnings.
- ADDITIONAL: Implement Multiple Linear Regression based on Gradient Descent. Once done, fit the Boston House Prices dataset using the user-defined functions that you created. Once done, compare it with any OLS based model, and provide your comments.

---
> # Problem Statement

Hardcoding and implementing Gradient Descent for Simple and Multiple linear regression, and understanding how hyperparameters like learning rate and epochs effect model's performance.

---
> # Approach / Methods 

The simple approach I used was, to create as many generalisable user-defined function. For Multiple Linear regresion, I needed to create seperate Y_pred, and weights change function, but except that, the functions created were similar. I also created a hyperparameter comparitive analysi function. __All the methods and process are elaboratively mentioned via comments__


---
> # Observations 

## Simple Linear Regression using Gradient Descent

### Converging Loss function

- The loss initially is at 0.24, and it drastically decreases to 0.05 in about 500 epochs, then slowly converging in about another 800 epochs.

- The bias value starts from 0 initially, jumps to 0,38 in about 300 epochs, then it decreases in a concave manner, and finally looks to be converging.
The weight starts off from 0, then increases and till 2500, then converging at about 3000 epochs.

- The predicted values from the gradient descent model are almost identical to the true values.

### Changing Hyperparametrs (Learning Rate & Epochs) (Simple Linear Regression)

#### Changing Learning Rate while keeping Epoch (Iterations) Constant

- It can be seen that a higher learning rate of 0.1, or above causes the curve (Loss Function) to converge. But a too high learning rate, of 1.8 casued the model to overshoot, and the loss curve to increase rampantly. 
- The learning rates below 0.1 (0.01,0.001) take a long amount of time to converge, but the curve is smooth and good for generalization. 
- The learning rate of 0.0001 and 0.00001 doesn't cause a smooth converging curve, infact its too slow for the model, to reach the optimum error/loss value.

#### Hyperparameter Tuning Comparitive Analysis (Gradient Descent for SLR)
##### Comparing Loss with respect to different hyperparameters
- As the learning rate increases the iteartions (epochs) required for the loss function to converge, decrease significantly too.
- The most smooth curves that proceed to converge (0.25 --> 0) have the following hyperparameters:
    1. ```Learning Rate = 1``` | ```Epochs = 50```
    2.``` Learning Rate = 0.3``` | ```Epochs = 100```
    3. ```Learning Rate = 0.1``` | ```Epochs = 250```
    4. ```Learning Rate = 0.01``` | ```Epochs = 3000```
- It can be seen that there is a direct relationship between the learning rate and epochs (iterations). A too low learning rate requires significantly more epochs, while a high learning rate requires too few iterations and epochs. This can also be dangerous as there can be a shoot up in the loss, if the learning rate is set too high.
- At Learning rate 0.0001 and 0.00001 the rate of learning is too low,  although the loss value is decreasing, its decreasing at an extremely slow pace, and even after 3000 iterations the model, is only able to descent from 0.2652 to a minimum of 0.2500 (α -> 0.00001) and 0,1600 (α -> 0.0001).<br>

##### Comparing Weights with respect to different hyperparameters
- Similar to the loss function a learning rate of 0.0001 or 0.0001 causes too little of a change in the weight values, even after 3000 epochs. 
- At a learning rate of 0.1, most weights are smoothly reaching their optimum weights, at all epoch values.

##### Comparing Bias with respect to different hyperparameters
- Similar to the loss function and weights a learning rate of 0.0001 or 0.0001 causes too little of a change in the bias values, even after 3000 epochs. 
- The bias seem to increase and then suddenly decrease in almost all possible hyperparameter combinations except where learning rate <= 0.0001. The most smooth curves obtained are with the following hyperparameter values:
    1. ```Learning Rate = 0.3``` | ```Epochs = 100```
    2.``` Learning Rate = 0.1``` | ```Epochs = 500```

#### Comparing my Gradient Descent model with Standard OLS model

__Q-Q Plot (Actual vs Predicted Values)__

- The values predicted by both the models are extremely similar in nature, but there's a trend of increasing difference between both the model's predictions, as the magnitude of the values increases.
- If taken as QQ plot, the graph shows that the data is normally distributed and is closely packed to the 45-degree line, indicating towards a good model.


__Residual Plot (Predicted Value vs Residual Plot)__
- The high chunk of negative residual values (lying below the zero residual line) indicates that both the models are over-predicting the variables, and are over fitting.
- The predicted values of OLS and Gradient descent, are quite spread out. On the contrary, the amount of residual is very minimalistic.
Residual Distribution Plot
- The distribution of residuals is almost normally distributed. The residuals are platykurtic in nature.
- The OLS model residuals are highly concentrated between 0 and -0.02, followed by an even distribution of residuals between -0.05 and -0.09
- The Gradient Descent model residuals are highly concentrated and evenly distributed from -0.05 to +0.02.

### OLS vs GD

| OLS| GRADIENT DESCENT |
| --- | --- |
| OLS is a __closed form solution___ and uses a pre-defined formula that involves matrices. To find the right coefficients (weights), ols tries to minimise the sum of square of errors i.e predicted values - true values. (Implement Linear Regression with Gradient Descent) |Gradient Descent on the other hand is an optimisation technique which is an ___iterative solution___, that  iteratively updates coefficients to minimize cost(loss) function to achieve convergance.|
| __OLS Formula__: $\hat{{\beta}}=\left(\mathbf{X}^{\top} \mathbf{X}\right)^{-1} \mathbf{X}^{\top} \mathbf{y}$ | __GD Algorithm:__ Until Convergance: Calculate loss function, update weight, update bias |

## Multiple linear regression using Gradient Descent
__Boston Housing Data
Learning Rate: 0.02
Epochs: 1500__

- Loss Converges after about 300 epochs, starting initially from 600.
- It can be observed that the weights all initially start from 0 and keep changing until the loss function converges. 
1.	RM has the most amount of weight, and has had the biggest positive delta, starting from 0 and moving to +15, this means that the Feature Average number of dwellings per room (RM) has a significant impact on the predicted variable RENT.
2.	LSTAT has changed the most in the negative direction, starting from 0 and moving to a -10 coefficient value.
3.	The features that have the least weight, starting from 0 and ending in the range of -2 to 2 after 1500 epochs are INDUS, DIS, TAX, NOX. The features mentioned below incidentaly have the least values as coefficients in the gradient model generated by us, this tells us they have the lowest impact on RENT amongst all the other features.
    - TAX: Full-value property tax rate per USD 10,000
    - INDUS: Proportion of non-retail business acres per town
    - NOX: Nitric oxide concentration (parts per 10 million)
    - DIS: Weighted distances to five Boston employment centers

- Bias Value steeply rises till about 180 epochs and then the rate of change in bias decreases, eventually converges after about 1400 epochs.

### Comparative Hyperparameter Analysis for Loss (Boston Housing Data)

- The comparative hyper tuning analysis of the Boston housing dataset is self-explanatory. The learning rate of 0.01 is optimum for all epochs (100,500,1000,3000). 

- The learning rate of 0.0001 is too slow (loss reduction-wise) for epochs upto 3000, maybe increasing the iterations will help.

- 0.2 and 0.1 are very high learning rates for the Boston housing dataset. They require only 100 to 120 epochs to make the loss function converge


### Comparative Hyperparameter Analysis for Weights (Boston Housing Data)
- Similar to the loss function hyperparameter analysis, the weights reach their optimum weights very quickly when the gradient descent has a learning rate of 0.1 or 0.2. 
- At learning rate of 0.01, for the boston housing dataset, there need to be at least 3000 iterations for the weights to reach optimum coefficeient values.

### Comparative Hyperparameter Analysis for Bias (Boston Housing Data)
- There is not much that can be understood from the hyperparameter analysis for bias, its very clear that learning rates of 0.1 and 0.2, cause the bias value to reach upto 25, while a learning rate of 0.01 can only take the bias value upto 12, even after 3000 epochs.



---
> # Results 

Gradient Descent, involves many unique elements like that of hyperparameter tuning which a practitioner must keep in mind. Comparing it with OLS, gives us valuable insights into the same

| OLS| GRADIENT DESCENT |
| --- | --- |
| OLS is a __closed form solution___ and uses a pre-defined formula that involves matrices. To find the right coefficients (weights), ols tries to minimise the sum of square of errors i.e predicted values - true values. (Implement Linear Regression with Gradient Descent) |Gradient Descent on the other hand is an optimisation technique which is an ___iterative solution___, that  iteratively updates coefficients to minimize cost(loss) function to achieve convergance.|
| __OLS Formula__: $\hat{{\beta}}=\left(\mathbf{X}^{\top} \mathbf{X}\right)^{-1} \mathbf{X}^{\top} \mathbf{y}$ | __GD Algorithm:__ Until Convergance: Calculate loss function, update weight, update bias |


---

> # Learnings

This lab made by concepts on Gradient Descent, Loss function and hyperparameters absolutely crystal clear.
__Extra:__ I discovered ressidual distribution and QQ plots, for comparing models, and how to interpret the same.

---
> # References

1. statmsodel Documentation: https://www.statsmodels.org/stable/index.html
2. Matplot Library Documnentaion: https://matplotlib.org/
3. GeeksForGeeks: https://www.geeksforgeeks.org/ 
4. StackOverflow: https://stackoverflow.com/ 
5. sklearn: https://scikit-learn.org/stable/

---
> # Completion Status:

| Question | Status |
| --- | --- |
| __Objective 1__ (Implement Linear Regression with Gradient Descent) | __Completed__ |
| __Objective 2__ (Prove that the loss is converging to the minima) | __Completed__ |
| __Objective 3__ (Compare the impact of learning rate and epoch on the model)| __Completed__ |
| __Objective 4__ (Compare gradient descent with OLS model)| __Completed__ |
| __Objective 5__ (__Additional:__ Implement Gradient Descent on multiple linear regression.) | __Completed__ |

---
> # Notebook Sample Screenshots

<br>

![Screenshot 2023-05-28 at 8 15 40 PM](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/8d41565f-22f3-4092-9bed-94d9c107749b)

<br>

![Screenshot 2023-05-28 at 8 17 37 PM](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/b482c682-fec9-4c93-9a85-c8672daab415)

<br>

![image](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/2a850cdd-01b3-4d1e-bab9-810ec3cbcf46)

![Screenshot 2023-05-28 at 8 17 37 PM](https://github.com/shreyansh-2003/Hands-on-ML/assets/105413094/b482c682-fec9-4c93-9a85-c8672daab415)


