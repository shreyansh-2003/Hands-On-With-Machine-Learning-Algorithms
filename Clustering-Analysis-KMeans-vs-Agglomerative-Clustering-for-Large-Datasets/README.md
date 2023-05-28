# Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets

---
**Author Name :** Shreyansh Padarha<br>
**Email : mailto:shreyansh.padarha@hotmail.com**
---

># Introduction

This repo explores KMeans and Agglomerative Clustering effectiveness in simplifying large datasets for ML. Goals include dataset download, finding optimal clusters via Elbow and Silhouette methods, comparing clustering techniques, validating optimal clusters, tuning hyperparameters. Detailed explanations and analysis are provided.
    
> # Problem Statement 

To critically analyse the effectiveness of clustering in simplifying large datasets for machine learning, this lab aims to compare KMeans and Agglomerative Clustering algorithms and evaluate their performance against a classification algorithm.

---

> # Objectives

- To Download the "Car Evaluation" Dataset from UCI Repository.
- To Find the optimal number of clusters using Elbow and Silhouette Method. 
- To Compare KMeans and Agglomerative Clustering methods for clustering the instances in the above dataset.
- To Validate the optimal number of clusters found out in the previous question.
- To Find what hyperparameters are suitable in KMeans (n_clusters, max_iter, init, algorithm)
- To Find what hyperparameters are suitable in Agglomerative Clustering (n_clusters, metric, linkage)
- To Plot Hierarchical Clustering (Dendrogram) [Source]
- To Compare the better clustering algorithm with any classification algorithm, and write notes on the same.

---
> # Sample Notebook Output Screenshots

![image](https://github.com/shreyansh-2003/Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets/assets/105413094/2576cee8-8f04-4a5e-a700-3575a55f7f72)

<br>

![image](https://github.com/shreyansh-2003/Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets/assets/105413094/30e54dc9-75cb-4430-a74e-4fbac779cfcb)
 

<br>

![image](https://github.com/shreyansh-2003/Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets/assets/105413094/492e7b74-782b-4aa5-a797-7c489b69912a)


----
> # Theory

## Finding Optimal 'k' clusters

### 1. Elbow Method
The elbow method, is a graphical representation of finding the _optimal 'k' (number of clusters)_ while conducting a clustering Analysis

__Axises__

- __X Axis:__ Number of Clusters (k)<br>
- __Y_Axis:__ Variation (variability) in each cluster / WCSS (Within Cluster Sum of Squares)<br>

__Within Cluster Sum Of Squares (WCSS) Formula__

Distance between $d_i$ (ith data point) , $c_i$ (ith data point's centroid)

$WCSS$ = {\sum{(d_i,c_i)^2}}$ 

![elbow plot](https://github.com/shreyansh-2003/Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets/assets/105413094/07691282-4ef7-49bc-970d-547c50d9f38b)


### 2. Silhouette Method
The silhouette Method is also a method to find the _optimal number of clusters_ while aiding interpretation and validation of consistency within clusters of data.<br>
The silhouette method computes __silhouette coefficients__ of each point that measure how much a point is similar to its own cluster compared to other clusters.

__Formula (Silhoette Coefficient)__

Computing s(i) — silhouette coefficient or i’th point using below mentioned formula.

$s(i) = \frac{b(i) - a(i)}{\max\{a(i),b(i)\}}$

1. __Compute a(i)__: The average distance of that point with all other points in the same clusters.
2. __Compute b(i)__: The average distance of that point with all the points in the closest cluster to its cluster.

__Silhoutte Analysis Plot__

_Example_

![silh_plot](https://github.com/shreyansh-2003/Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets/assets/105413094/04cc1fe1-48f2-4442-9108-96d4733de7ae)


## Hierarchical Clustering (Linkages, Denrogram)

__Linkage__: The method in which the distance between two datapoints is calculated and the method used for deciding which two data points to connect in Hierarchical Clustering

__Dendrogram__: A herarchichal tree and method that plots and depicts hierarchical Clustering.

<img width="342" alt="dendro" src="https://github.com/shreyansh-2003/Clustering-Analysis-KMeans-vs-Agglomerative-Clustering-for-Large-Datasets/assets/105413094/f13257db-5774-47ff-b308-6e43aee8fe67">


__Types of linkages__:

1. __Single linkage:__ This method tends to create long, stretched-out clusters. It can also result in clusters being merged incorrectly, leading to poor results.

2. __Complete linkage:__ This method tends to create tight, compact clusters. It is less sensitive to outliers than single linkage and tends to perform well in practice.

3. __Average linkage:__ This method is a compromise between single and complete linkage. It tends to create well-balanced clusters that are not too stretched out.

4. __Weighted linkage:__ This method is similar to average linkage, but it gives more weight to larger clusters. This can help to prevent small clusters from being merged too early.

5. __Centroid linkage:__ This method is based on the distance between cluster centroids. It tends to create balanced clusters that are not too stretched out. However, it can be sensitive to outliers.

6. __Median linkage:__ This method is similar to centroid linkage, but it uses the median distance between points instead of the mean. It tends to be more robust to outliers than centroid linkage.

7. __Ward linkage:__ This method minimizes the sum of squared differences within each cluster. It tends to create tight, compact clusters and is often used for hierarchical clustering.

---

> # Processes/Methods

The process and methods have been extensively explained in each code chunk, with the help of single line comments. <br>In case of any queries, please contact me at shreyansh.padarha@bhds.christuniversity.in .

---

> # Observation
## Elbow Method & Silhouette method to find optimum K value.
### Elbow Method
It can be seen through the ```elbow method```, that the optimal nunmber of k clusters are ```4```.<br>
The Within Cluster Sum of Squares for k = 4, is aproximately ```1100```.

### Silhouette Method

#### Silhouette Score Comparison (Using my K-means Algo)
It can be seen through the silhouette method, that the optimal nunmber of k clusters are ```4```.<br>
The silhouette coefficient for k = 4, is ```0.136```.
#### Silhouette Score Comparison & Elbow Plot (Using SKlearn Library's KMeans)
Similar to the Elbow method and Silhouette comparer method used for my algorithm, SKlearn's KMeans also identifies 4 as the ideal number of clusters. Its evident from the plots that, at k = 3 and k = 4, most of the data is being representated with a high silhouette coefficient score.

## Comparing Agglomerative and KMeans Clustering

### Cluster Spread Analysis (KMeans VS Agglomerative VS Class Values)

Considering PC1 and PC2's spread of clusters, after dimensionality reduction from 6 features. It can be observed that:
- The spread of the class value (quality --> categorical variables) is heterogeneous in nature, implying too scatered to incoperate all 6 features. This hypothetically suggests, the quality of the car was adjourned in a subjectie manner, where attributes like door, weren't taken as a major contributing factor.
- For k = 4, KMeans has a better cluster allocation, and more homogeneous than Agglomerative Clustering.
- The colour coded nature of the scatter plot, also helps us understand how differently were the data points clustered. 
    - Eg. Graphically, Agglomerative has vertically clubbed the data points into a cluster, while KMeans has horizontally clubbed the data points.
    
### Comparing the  number of data points per cluster
- Both Kmeans and Agglomerative have a different spread of clusters.
    - Agglomerative Clustering has spread/clustered the data points more unevenly.
    - KMeans has created clusters in a "very" proportionally distributed manner.

- Understandablly, both Kmeans and Agglomerative Clustering are not a representative of the true clss values.

### Cross Table Analysis (KMeans vs Agglomerative Clustering)
- The distribution of class values across clusters is different for agglomerative and k-means clustering. For example, in agglomerative clustering, cluster 0 has the highest count of "unacc" class values, while in k-means clustering, cluster 2 has the highest count of "unacc" class values.

- In botb Agglomerative and KMeans Cluster 1 and 3 have 0 instances of vgood quality cars.

In general, it is difficult to compare the performance of agglomerative and k-means clustering based on the given count of clusters vs Class values. However, we can say that both methods have produced different cluster distributions and class value counts, which may have implications for further analysis and decision making.


## Hyperparameter Tuning --> KMeans Clustering

__GridSearchCV__

Upon using GridSearchCV, the hypertuning parameters obtained were inept. 
__Values:__
```
Best parameters:  {'init': 'random', 'max_iter': 250, 'n_clusters': 10}
Best score:  -204.5976727420548
```
These values are inaccurate, as the GridSearchCV is deploying an accuracy Score, from the sklearn.metrics library, for a clustering problem.

__Manual Hyperparameter tuning__
The method used for judging the optimum hyperparameters in Kmeans is silhouette score.<br>
It can be seen post a thorough hyperparameter comparative analysis that, for the given/selected dataset:<br>
1. __k (Number of Clusters)__<br>
- As K (number of clusters) increase, the silhouette score increses, resulting in better clustering
- At k = 4, we achieve the highest clustering score, of 0.137245.
2. __n_init__<br>
- As n_init, increases the silhoette score tends to increase. This makes sense, when compared to the definition of n_init
    - Its the number of times the k-means algorithm is run with different centroid seeds. The final results is the best output of n_init consecutive runs in terms of inertia.
3. __max_iter__<br>
- The maximum number of iterations don't matter in this dataset, the silhouette score is similar amongst all different permutations. 
- The highly likely reason for the same is, that for this dataset the centroids stop changing after few iterations, resulting in the algorithm assigning same clusters to the data point till the maximum iterations are achieved.
4. __init (initialisation method)__<br>
- Both random and kmeans++, give similar silhouette scores, and clusters. Random is a bit more over the place, while k_means is less spread out, and more linear in fashion. Looking at the difference between them theoretically can help us better understand the observation:
    - ‘k-means++’ : selects initial cluster centroids using sampling based on an empirical probability distribution of the points’ contribution to the overall inertia.
    - ‘random’: choose n_clusters observations (rows) at random from data for the initial centroids.
    
__Optimum set of parameters for KMeans Clustering Algorithm__



|k	| init(method) |max_iterations |	n_init	| silhouette_score|
|-|-|-|-|-|
|4	 | k-means++	 | 100 | 5	| 0.137245 |
| 4	 | k-means++	 | 100 | 10	| 0.137245 |
| 4	 | k-means++	 | 500 | 5	| 0.137245 |
|  4	 | k-means++	 | 500 | 10	| 0.137245 |
|4	 | k-means++	 | 1000	| 5	| 0.137245 |
| 4	 | k-means++	 | 1000	| 10	| 0.137245 |

__Suggested parameters__<br>
As seen from the analysis that for the given dataset the init values and iterations don't contribute significantly. Therefore, we will chose the lower limit of these values in order to decrease computation time and increase efficiency.
```
n_clusters = 4 
init = 'k-means++' 
max_iter = 100
n_init = 5
```

## Hyperparameter Tuning --> Agglomerative Clustering

The method used for judging the optimum hyperparameters in Agglomerative clustering is silhouette score.<br>
The main three hyperparameters in Agglomerative clustering are ```n_clusters```, ```affinity (distancing measure)```, ```linkage type```. The rest are related to reducing computation time and increasing efficiency.
These are the hyperparametric observations for the selected datast:

1. __K (number of clusters)__
- Generally, at __k=2__, the silhouette score was extremely hig when compared to other k values. 
- Silhouette Score was higher at 2,3,4 than any other k value
- Silhouette score __gradually decreased__ from 2 to 5 for __ward__ and __average__ linkage, then plateauing.
- Silhouette scored __decreased minimalistically__ from 2 to 4, for __complete __linkage, then plateauing.
- Silhouette scored __decreased rapidly__ from 2 to 6, almost dopping to zero for __single__ linkage then increasing gradually till k = 10
2. __Affinity (distancing measure)__
- Silhouette score was similar for l1, l2 and manhattan distancing measures (affinity)
- Silhouette score was slightly better for euclidean distancing measure.
3. __Linkage Type__
- Ward Linkage is significantly better than all other measures.
- Average linkage has the second best average silhouette score amongs the linkage methods.
- Single linkage method, has the worst silhouette.

__Interesting Notes__<br>
a) ward method only works with euclidean method of distancing<br>
b) cosine affinity cant be applied for datasets which have 0, as a value.


__Suggested parameters (highest silhouette score)__<br>
```
k (number of clusters) = 2, linkage	= "ward",	affinity = "euclidean"
```

## Dendrogram (Linkages)
The plots, support the the definitions of the types of linkages in the theory section. It is evident that different linkage methods provide different hierarchical structures. Its also interesting to note that, different linkage methods provide different optimum clusters to be taken. For the 25 sample data points taken from the dataset:
- __Ward__,__Complete__,__Average__ linkage dendrograms provide a clean, intricate segregation of clusters.
- __Median__, __Single__, __Centroid__ produce dendrograms have complicated and further apart linkages.


## Classification vs Clustering

### Decision Tree (Classification) vs KMeans (Clustering)s

Although not directly comparable, the accuracy or more fitting model for the given dataset will be the Decision tree. The accuracy score between 0,1 came out to be __0,827__ for the decision tree which is relatively very high. On the other hand the silhouette coefficient score for the KMeans algo was __0.137__ (between -1,1).

To give a broader perspective, my understanding post using both the algorithms extensively on the given dataset is:
__Interpretability__ 
- Decision Tree models are often more interpretable than K-Means models since they can provide a clear decision-making process based on the features of the input data.
- K-Means provides cluster assignments without any clear interpretation.

__Scalability__ 
- K-Means is typically faster and more scalable than Decision Tree, especially for large datasets. Therefore, if you have a large dataset, K-Means may be a better option.

__Data Characteristics__ 
- K-Means may not work well with high-dimensional or sparse data
- Decision Tree may not be robust to noisy data.

__Use case__ <br>
Finally, the use case and problem you are trying to solve should also be considered. If you want to group similar data points together, K-Means may be a better option. If you want to predict the class of a new data point, Decision Tree may be a better option.

---

># Notebook Objectives Status


|Question No.|Description||Status|
|---|---|---|---|
|__Q1)__|*__Downloading__ the "Car Evaluation" Dataset*||__Completed__|
|__Q2)__|*Find optimal number of clusters (__Elbow__ & __Silhouette Mehod__)*||__Completed__|
|__Q3)__|*Compare & Validate __KMeans__ and Agglomerative Clustering methods*|| __Completed__|
|__Q4)__|*__Hyperparameter Tuning__ (Manually) for __Kmeans__* || __Completed__|
|__Q5)__|*__Hyperparameter Tuning__ (Manually) for __Agglomerative Clustering_* || __Completed__|
|__Q6)__|*Plotting Hierarchical Clustering (__Dendrogram__)* || __Completed__|
|__Q7)__|*Comparing the __clustering__ algorithms with any __classification__ algorithm* || __Completed__|


---

> # Results

1. Using both the Elbow and Silhouette methods, the optimal number of clusters for the dataset used is four.
2. The Within Cluster Sum of Squares for k = 4 is approximately 1100.
3. The Silhouette Score Comparison using K-means algorithm and SKlearn library's KMeans both suggest that k=4 is the ideal number of clusters.
4. KMeans clustering has better cluster allocation and is more homogeneous than Agglomerative Clustering for k=4.
5. Both KMeans and Agglomerative Clustering have a different spread of clusters. Agglomerative Clustering has spread/clustered the data points more unevenly, while KMeans has created clusters in a "very" proportionally distributed manner.
6. The distribution of class values across clusters is different for Agglomerative and KMeans clustering.
7. Hyperparameter tuning for KMeans clustering using GridSearchCV gave inept results.
8. Silhouette score was used to judge the optimum hyperparameters in KMeans.
9. As K (number of clusters) increases, the silhouette score increases, resulting in better clustering. At k=4, the highest clustering score of 0.137245 is achieved.
10. The optimum set of parameters for KMeans clustering algorithm are k=4, init (method)=k-means++, max_iterations=100, n_init=5 with a silhouette score of 0.137245.

Overall, these observations suggest that KMeans clustering performs better than Agglomerative Clustering for the given dataset, and the optimal number of clusters is four. It is also recommended to use Silhouette score as a means of judging the optimum hyperparameters in KMeans clustering.

---

> # Learnings 

This lab gave me valuable insights into how unsupervised learning can be utilised for classifying datasets into clusters without labels. There were also the usual, bugging-debugging conundrums which made my logical reasoning stronger. It also made me realise that, understanding an Unsupervised learning's accuracy or precision is extremely difficult, as there are no target values to compare with. In such a situation, knowledge about the domain, one is working in becomes critical.

---

> # References

Car Evaluation Dataset: https://archive.ics.uci.edu/ml/datasets/Car+Evaluation
1. Stackoverflow: https://stackoverflow.com/
2. SKlearn Documentation: https://scikit-learn.org/stable/
3. Yellowbrick Documentation: https://www.scikit-yb.org/en/latest/
4. Seaborn Documentation: https://seaborn.pydata.org/
5. Pandas Documentation: https://pandas.pydata.org/docs/
6. matplotlib Documentation: https://matplotlib.org/stable/index.html
7. Medium Blogs: https://medium.com/

---

