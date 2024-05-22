==Unsupervised learning is a branch of [machine learning](https://www.geeksforgeeks.org/machine-learning/) that deals with unlabeled data. Unlike supervised learning, where the data is labeled with a specific category or outcome, unsupervised learning algorithms are tasked with finding patterns and relationships within the data without any prior knowledge of the data’s meaning. This makes unsupervised learning a powerful tool for [exploratory data analysis](https://www.geeksforgeeks.org/exploratory-data-analysis-in-python/), where the goal is to understand the underlying structure of the data.==

![[Pasted image 20240508020828.png]]
### ==Unsupervised Learning Algorithms==

There are mainly 3 types of Algorithms which are used for Unsupervised dataset.

- Clustering
- Association Rule Learning
- Dimensionality Reduction

#### ****Clustering****

[Clustering](https://www.geeksforgeeks.org/clustering-in-machine-learning/) in unsupervised machine learning is the process of grouping unlabeled data into clusters based on their similarities. The goal of clustering is to identify patterns and relationships in the data without any prior knowledge of the data’s meaning.

Broadly this technique is applied to group data based on different patterns, such as similarities or differences, our machine model finds. These algorithms are used to process raw, unclassified data objects into groups. For example, in the above figure, we have not given output parameter values, so this technique will be used to group clients based on the input parameters provided by our data.

Some common clustering algorithms

- [K-means Clustering](https://www.geeksforgeeks.org/k-means-clustering-introduction/): Partitioning Data into K Clusters
- [Hierarchical Clustering](https://www.geeksforgeeks.org/ml-hierarchical-clustering-agglomerative-and-divisive-clustering/): Building a Hierarchical Structure of Clusters
- [Density-Based Clustering (DBSCAN)](https://www.geeksforgeeks.org/dbscan-clustering-in-ml-density-based-clustering/): Identifying Clusters Based on Density
- [Mean-Shift Clustering](https://www.geeksforgeeks.org/ml-mean-shift-clustering/): Finding Clusters Based on Mode Seeking
- [Spectral Clustering](https://www.geeksforgeeks.org/ml-spectral-clustering/): Utilizing Spectral Graph Theory for Clustering

#### ****Association Rule Learning****

[Association rule learning](https://www.geeksforgeeks.org/association-rule/) is also known as association rule mining is a common technique used to discover associations in unsupervised machine learning. This technique is a rule-based ML technique that finds out some very useful relations between parameters of a large data set. This technique is basically used for market basket analysis that helps to better understand the relationship between different products. For e.g. shopping stores use algorithms based on this technique to find out the relationship between the sale of one product w.r.t to another’s sales based on customer behavior. Like if a customer buys milk, then he may also buy bread, eggs, or butter. Once trained well, such models can be used to increase their sales by planning different offers.

- [Apriori Algorithm](https://www.geeksforgeeks.org/apriori-algorithm/): A Classic Method for Rule Induction
- [FP-Growth Algorithm](https://www.geeksforgeeks.org/frequent-pattern-growth-algorithm/): An Efficient Alternative to Apriori
- [Eclat Algorithm](https://www.geeksforgeeks.org/ml-eclat-algorithm/): Exploiting Closed Itemsets for Efficient Rule Mining
- [Efficient Tree-based Algorithms](https://www.geeksforgeeks.org/introduction-to-tree-data-structure-and-algorithm-tutorials/): Handling Large Datasets with Scalability

#### ****Dimensionality Reduction****

Dimensionality reduction is the process of reducing the number of features in a dataset while preserving as much information as possible. This technique is useful for improving the performance of machine learning algorithms and for data visualization. Examples of dimensionality reduction algorithms includeDimensionality reduction is the process of reducing the number of features in a dataset while preserving as much information as possible.

- [Principal Component Analysis (PCA)](https://www.geeksforgeeks.org/principal-component-analysis-pca/): Linear Transformation for Reduced Dimensions
- [Linear Discriminant Analysis (LDA)](https://www.geeksforgeeks.org/ml-linear-discriminant-analysis/): Dimensionality Reduction for Discrimination
- [Non-negative Matrix Factorization (NMF](https://www.geeksforgeeks.org/non-negative-matrix-factorization/)): Decomposing Data into Non-negative Components
- [Locally Linear Embedding (LLE)](https://www.geeksforgeeks.org/locally-linear-embedding-in-machine-learning/): Preserving Local Geometry in Reduced Dimensions
- Isomap: Capturing Global Relationships in Reduced Dimensions

### Challenges of ****Unsupervised Learning****


- ****Evaluation:**** 
- ****Interpretability:**** 
- ****Overfitting:**** 
- ****Data quality:**** 
- ****Computational complexity:**** 

### Advantages of Unsupervised learning

- ****No labeled data required:**** 
- ****Can uncover hidden patterns:****
- ****Can be used for a variety of tasks:**** 
- ****Can be used to explore new data:**** 
### Disadvantages of Unsupervised learning

- ****Difficult to evaluate:**** I
- ****Can be difficult to interpret:**** 
- ****Can be sensitive to the quality of the data:**** 
- ****Can be computationally expensive:****

### Applications of Unsupervised learning

- ****Customer segmentation:**** 
- ****Fraud detection:****
- ****Recommendation systems:****
- ****Natural language processing (NLP):**** 
- image analysis