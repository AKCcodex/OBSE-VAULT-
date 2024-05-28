# Clustering techniques: 
### K-means Clustering

K-means is a popular unsupervised machine learning algorithm used for clustering data into distinct groups based on feature similarity. It partitions a dataset into K clusters, where each data point belongs to the cluster with the nearest mean value.

#### Key Concepts

1. **Clustering**: Grouping a set of objects in such a way that objects in the same group (cluster) are more similar to each other than to those in other groups.

2. **Centroid**: The mean of all the points in a cluster. It represents the center of the cluster.

3. **Algorithm Steps**:
   1. **Initialization**: Select K initial centroids randomly from the dataset.
   2. **Assignment**: Assign each data point to the nearest centroid, forming K clusters.
   3. **Update**: Recalculate the centroids of the clusters by taking the mean of all data points in each cluster.
   4. **Repeat**: Repeat the assignment and update steps until the centroids no longer change or the change is below a threshold.
#### Advantages

- **Simplicity**: Easy to implement and understand.
- **Scalability**: Efficient for large datasets with relatively low computational complexity.

#### Limitations

- **Number of Clusters (K)**: Requires the number of clusters to be specified in advance.
- **Initial Centroids**: Sensitive to the initial placement of centroids, which can lead to different results.
- **Cluster Shape**: Assumes clusters are spherical and equally sized, which may not always be true.

#### Applications

- **Market Segmentation**: Grouping customers based on purchasing behavior.
- **Image Compression**: Reducing the number of colors in an image by clustering pixels.
- **Anomaly Detection**: Identifying outliers in data by their distance from cluster centroids.



K-means clustering is a fundamental and widely used algorithm in unsupervised learning for partitioning datasets into distinct clusters. While it is simple and scalable, careful consideration of the number of clusters and initialization methods is crucial for optimal performance.


# Gaussian mixture models 
Gaussian Mixture Models (GMMs) are probabilistic models used for clustering and density estimation by representing a distribution as a mixture of multiple Gaussian distributions.

### Key Concepts

1. **Gaussian Distribution**: Defined by its mean (μ\muμ) and variance (σ2\sigma^2σ2), describing a normal distribution's bell curve.
2. **Mixture Model**: A combination of multiple distributions, in this case, Gaussians.
3. **Parameters**:
    - **Means (μi\mu_iμi​)**: Centers of the Gaussian components.
    - **Covariances (Σi\Sigma_iΣi​)**: Spread of the Gaussian components.
    - **Mixing Coefficients (πi\pi_iπi​)**: Weights of each Gaussian component in the mixture.

### How GMM Works

1. **Initialization**: Start with initial estimates of parameters, often using K-means.
2. **Expectation-Maximization (EM) Algorithm**:
    - **E-step**: Compute responsibilities (γik\gamma_{ik}γik​), which are the probabilities that each Gaussian component kkk is responsible for each data point xix_ixi​.
    - **M-step**: Update the parameters (μi,Σi,πi\mu_i, \Sigma_i, \pi_iμi​,Σi​,πi​) to maximize the likelihood of the data given the model.

GMMs are widely used for tasks like clustering, image segmentation, and anomaly detection.


# expectation-maximization, 
The Expectation-Maximization (EM) algorithm is an iterative method used to find maximum likelihood estimates of parameters in statistical models, where the model depends on unobserved latent variables. In the context of Gaussian Mixture Models (GMMs), EM is used to estimate the parameters of the mixture model.




# evaluation of clustering - Rand index, mutual information based scores, Fowlkes-Mallows index

Evaluating the quality of clustering is crucial to understanding how well the clustering algorithm has performed. Several metrics are used for this purpose, each with its own strengths and weaknesses. Here, we will discuss three commonly used evaluation metrics: Rand Index, Mutual Information-based scores, and Fowlkes-Mallows Index.

### 1. Rand Index

The Rand Index measures the similarity between two clusterings by considering all pairs of samples and counting pairs that are either in the same cluster in both clusterings or in different clusters in both clusterings.

#### Adjusted Rand Index (ARI):
The Adjusted Rand Index adjusts the Rand Index for the chance grouping of elements. It is defined as:
### 2. Mutual Information-based Scores

Mutual Information (MI) measures the agreement of the two clusterings by quantifying the amount of information obtained about one clustering by knowing the other.
### 3. Fowlkes-Mallows Index (FMI)

The Fowlkes-Mallows Index measures the similarity between two clusterings based on the number of pairs of points that are clustered together in both clusterings.

where:
- \(TP\) (True Positive) is the number of pairs that are in the same cluster in both clusterings.
- \(FP\) (False Positive) is the number of pairs that are in the same cluster in one clustering but not in the other.
- \(FN\) (False Negative) is the number of pairs that are in different clusters in one clustering but not in the other.

### Summary

- **Rand Index**: Measures the similarity of the pairwise agreement between two clusterings.
- **Mutual Information-based Scores**: Measure the amount of information shared between two clusterings, with variations such as NMI and AMI adjusting for chance and normalization.
- **Fowlkes-Mallows Index**: Measures the geometric mean of precision and recall for pairs of points.

These metrics provide different perspectives on the quality of clustering and are often used together to get a comprehensive evaluation.