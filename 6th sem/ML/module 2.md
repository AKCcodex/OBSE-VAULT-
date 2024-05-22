Feature Selection Techniques
Filter Methods- Information gain, Chi-Square test, Correlation and coefficient.
Wrapper methods- Recursive feature elimination, Genetic Algorithm. Embedded
method- Decision trees
~~Principal Component Analysis (PCA)~~

Feature Selection Techniques
Feature selection is a process that chooses a subset of features from the original features so that the feature space is optimally reduced according to a certain criterion.
 Feature selection is a critical step in the feature construction process. In text categorization problems, some words simply do not appear very often.\
 1. To reduce the dimensionality of feature space.

2. To speed up a learning algorithm.

3. To improve the predictive accuracy of a classification algorithm.

4. To improve the comprehensibility of the learning results.


Some popular techniques of feature selection in machine learning are:

- Filter methods
- Wrapper methods
- Embedded methods

**Filter Methods**

These methods are generally used while doing the pre-processing step. These methods select features from the dataset irrespective of the use of any machine learning
- **Information Gain –** It is defined as the amount of information provided by the feature for identifying the target value and measures reduction in the entropy values. Information gain of each attribute is calculated considering the target values for feature selection.
- **Chi-square test —** Chi-square method (X2) is generally used to test the relationship between categorical variables. It compares the observed values from different attributes of the dataset to its expected value.
- - **Correlation Coefficient –** Pearson’s Correlation Coefficient is a measure of quantifying the association between the two continuous variables and the direction of the relationship with its values ranging from _-1 to 1_.
**Wrapper methods:**

Wrapper methods, also referred to as greedy algorithms train the algorithm by using a subset of features in an iterative manner. Based on the conclusions made from training in prior to the model, addition and removal of features takes place. Stopping criteria for selecting the best subset are usually pre-defined by the person training the model such as when the performance of the model decreases or a specific number of features has been achieved.
**Embedded methods:**

In embedded methods, the feature selection algorithm is blended as part of the learning algorithm, thus having its own built-in feature selection methods. Embedded methods encounter the drawbacks of filter and wrapper methods and merge their advantages. These methods are faster like those of filter methods and more accurate than the filter methods and take into consideration a combination of features as well.

A decision tree is a popular and intuitive model used in machine learning and statistics for classification and regression tasks. It represents decisions and their possible consequences, including chance event outcomes, resource costs, and utility. Here is a breakdown of the key concepts and components:

### Key Concepts

1. **Nodes:**
    
    - **Root Node:** The topmost node in a decision tree, representing the entire dataset, which is split into subsets.
    - **Internal Nodes:** These represent the features of the dataset that are used to split the data.
    - **Leaf Nodes (Terminal Nodes):** The final nodes that predict the outcome or target variable.
2. **Edges (Branches):** These connect the nodes and represent the decision rules or conditions for splitting the data.
    
3. **Splitting:** The process of dividing a node into two or more sub-nodes based on certain conditions. The goal is to create homogeneous sub-nodes to the extent possible.
    
4. **Pruning:** The technique of removing parts of the tree that do not provide additional power to classify instances, to reduce complexity and prevent overfitting.
    

### How Decision Trees Work

1. **Select the Best Feature:** At each node, the best feature to split on is selected based on a certain criterion (e.g., Gini impurity, Information gain for classification tasks, or Mean squared error for regression tasks).
    
2. **Split the Data:** The data is divided into subsets based on the selected feature and its threshold.
    
3. **Repeat the Process:** The splitting process is recursively repeated for each subset, creating branches, until one of the stopping criteria is met (e.g., maximum depth of the tree, minimum number of samples per leaf).
    

### Advantages

- **Easy to Understand and Interpret:** The structure of decision trees makes them simple to understand and interpret.
- **Little Data Preparation Required:** Decision trees require minimal data preprocessing.
- **Handles Both Numerical and Categorical Data:** They can manage different types of data with ease.

### Disadvantages

- **Overfitting:** Decision trees are prone to overfitting, especially with complex trees.
- **Bias in Favor of Features with More Levels:** Features with more categories might dominate the splits.
- **Unstable:** Small variations in the data might result in completely different trees.

**Principal Component Analysis 
is a dimensional reduction technique used to simplify datasets while preserving important information. It does this by transforming the original variables into a new set of variables, called principal components, which are linear combinations of the original variables. These principal components are ordered by the amount of variance they explain, with the first component explaining the most variance in the data and subsequent components explaining less and less.

principal components should be orthogonal because both should be independent should not depend on one another.

Here's a simple example of how PCA works:

Let's say we have a dataset with two variables: height (in inches) and weight (in pounds) of a group of individuals. We want to reduce the dimensionality of this dataset using PCA.

1. **Data Collection**: We collect data on the height and weight of, let's say, 100 individuals.
    
2. **Data Preprocessing**: Before applying PCA, it's essential to standardize the data (subtract the mean and divide by the standard deviation) since PCA is sensitive to the scale of the variables.
    
3. **Compute the Covariance Matrix**: Next, we compute the covariance matrix of the standardized data. The covariance matrix gives us information about the relationships between the variables.
    
4. **Compute Eigenvectors and Eigenvalues**: We then compute the eigenvectors and eigenvalues of the covariance matrix. The eigenvectors represent the directions (or components) of maximum variance in the data, while the eigenvalues represent the magnitude of variance along these directions.
    
5. **Select Principal Components**: We select the top k eigenvectors (principal components) based on the corresponding eigenvalues. These are the directions that capture the most variance in the data. Typically, we sort the eigenvalues in descending order and select the top k eigenvectors.
    
6. **Transform the Data**: Finally, we project the original data onto the new feature space formed by the selected principal components.