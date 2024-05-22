1. What is the Rand index
  
The Rand index measures how similar two clusterings are by comparing pairs of points: those in the same cluster in both clusterings, those in different clusters in both, those in the same cluster in one but different clusters in the other, and vice versa. It gives a score between 0 and 1, where 1 means perfect agreement and 0 means no agreement.

1. How Rand index is used to evaluate clustering algorithms
  
The Rand index helps evaluate clustering algorithms by comparing their results to a known clustering. Higher scores mean better alignment with the known clustering.

1. What is the Fowlkes-Mallows index

  
The Fowlkes-Mallows index measures the similarity between two clusterings by comparing pairs of data points. It gives a score between 0 and 1, where 1 means perfect agreement and 0 means no agreement.

1. How Fowlkes-Mallows index is it used to evaluate clustering
  
The Fowlkes-Mallows index is used to evaluate clustering by comparing two sets of clusters. It calculates the similarity between the pairs of data points assigned to clusters in both sets. A higher index score suggests better agreement between the clusterings.

3. What is the k-means clustering algorithm, and how does it work?
  
K-means clustering divides a dataset into K clusters by iteratively assigning data points to the nearest cluster centroid and updating the centroids based on the mean of the assigned points. It repeats this process until the centroids stabilize.


5. What is regression?
Regression is a statistical method used to understand and predict the relationship between variables. It helps in predicting the value of one variable based on the values of others.

7. Describe various type of regression
  
Sure, here are some common types of regression:

1. **Linear Regression**: It models the relationship between a dependent variable and one or more independent variables by fitting a linear equation to the observed data. It's used when the relationship between variables is linear.
    
2. **Polynomial Regression**: It extends linear regression by fitting a polynomial equation to the data. It's useful when the relationship between variables is nonlinear.
    
3. **Logistic Regression**: Unlike linear regression, logistic regression is used for binary classification problems. It models the probability of a binary outcome based on one or more independent variables.
    
4. **Ridge Regression**: It's a regularized version of linear regression that adds a penalty term to the cost function to prevent overfitting. It's useful when multicollinearity (high correlation among independent variables) is present.
    
5. **Lasso Regression**: Similar to ridge regression, lasso regression also adds a penalty term to the cost function, but it uses the absolute values of the coefficients instead of their squares. It's useful for feature selection as it tends to shrink coefficients of less important features to zero.
    
6. **ElasticNet Regression**: It combines the penalties of ridge and lasso regression, allowing for both variable selection and regularization. It's useful when there are many variables and some of them are highly correlated.
    
7. **Bayesian Regression**: It incorporates Bayesian methods into regression analysis, allowing for the estimation of uncertainty in the model parameters. It's useful when prior knowledge about the parameters is available or when dealing with small datasets.+

9. What is LASSO regression?
LASSO regression is a linear regression technique that adds a penalty term to the cost function, encouraging sparsity in the coefficient estimates and performing variable selection by setting some coefficients to zero.
11. What is Ridge Regression ?
Ridge regression is a linear regression method that adds a penalty term to the ordinary least squares (OLS) cost function. This penalty term helps prevent overfitting by penalizing large coefficients, resulting in more stable and generalized models.
13. What is Agglomerative Clustering?
 Agglomerative clustering is a hierarchical clustering technique used to group similar data points together based on their distance or similarity. It starts with each data point as a separate cluster and then iteratively merges the closest clusters until only one cluster remains.

Here's how it works:

1. **Initialization**: Start with each data point as a singleton cluster.
    
2. **Merge**: Find the two closest clusters based on a chosen distance metric (e.g., Euclidean distance) and merge them into a single cluster.
    
3. **Update Distance Matrix**: Recalculate the distances between the new cluster and all remaining clusters.
    
4. **Repeat**: Continue merging the closest clusters and updating the distance matrix until only one cluster remains.
    

Agglomerative clustering produces a hierarchy of clusters, known as a dendrogram, which can be cut at different levels to obtain different numbers of clusters. The choice of distance metric and linkage criterion (method for determining the distance between clusters) can impact the resulting clusters.
15. What are the advantage and disadvantage of k-mean clustering algorithm ?
16. Give an example of an application for k-mean clustering algorithm.Explain in brief
17. Using k-means clustering , cluster the following data in two clusters. Show each step{2,4,10,12,3,20,30,11,25}
18. Apply k-mean algorithm in given data for k=2. Use C1(80), C2(250) as initial
     cluster centers.Data : 234,123,456,23,34,56,78,90,150,116,117,118,199
15. Apply k-mean clustering for the datasets given table for two clusters.Tabulate
all the assignments.
![[Pasted image 20240430000443.png]]