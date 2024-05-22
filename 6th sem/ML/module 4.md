Classification
Binary vs Multiclass Classification, 
1. **Number of Classes:**
    
    - **Binary Classification:** Two classes (e.g., positive vs. negative).
    - **Multiclass Classification:** More than two classes (e.g., class 0, class 1, class 2, etc.).
2. **Complexity:**
    
    - **Binary Classification:** Generally simpler to implement and understand.
    - **Multiclass Classification:** More complex due to the need to distinguish between multiple classes.
3. **Algorithms and Techniques:**
    
    - **Binary Classification:** Many standard algorithms directly support binary classification.
    - **Multiclass Classification:** Often requires adaptations of binary classification algorithms (e.g., OvR, OvO).
4. **Evaluation:**
    
    - **Binary Classification:** Evaluation metrics are straightforward with a single set of true/false positives/negatives.
    - **Multiclass Classification:** Evaluation needs to consider metrics for each class and aggregate them (e.g., macro/micro averaging).
5. **Model Training:**
    
    - **Binary Classification:** Single model to distinguish between two classes.
    - **Multiclass Classification:** Either a single model with an output unit for each class or multiple models (e.g., one for each binary pair in OvO).

K Nearest Neighbor (kNN), 

  
K-Nearest Neighbor (kNN) is a simple, instance-based learning algorithm used for both classification and regression tasks in machine learning. Here's an in-depth look at kNN:

### Key Concepts

1. **Instance-Based Learning:** kNN is a type of lazy learning where the algorithm does not explicitly learn a model but instead stores instances of the training data. Predictions are made based on the stored instances.
    
2. **Distance Metrics:** To determine the "nearest" neighbors, kNN relies on a distance metric. Common distance metrics include:
    
    - **Euclidean Distance:** The straight-line distance between two points in Euclidean space.
    - **Manhattan Distance:** The sum of the absolute differences of their coordinates.
    - **Minkowski Distance:** A generalization of Euclidean and Manhattan distances.
3. **k Value:** The number of nearest neighbors to consider. This parameter greatly affects the performance of the algorithm.
    
    - **Small k:** Can lead to a model that captures noise (overfitting).
    - **Large k:** Can lead to a model that is too smooth (underfitting).

### How kNN Works

1. **Choose the Number of Neighbors (k):** Select an integer k, which is the number of nearest neighbors to consider.
2. **Calculate Distance:** For a given test instance, calculate the distance between this instance and all instances in the training set.
3. **Identify Nearest Neighbors:** Sort the distances and identify the k closest training instances.
4. **Vote for Classification:** For classification, the majority class among the k nearest neighbors is chosen.
5. **Average for Regression:** For regression, the average of the target values of the k nearest neighbors is calculated.

### Steps of kNN Algorithm

1. **Data Collection:** Gather the dataset with features and target values.
2. **Data Preprocessing:** Normalize or standardize the data if necessary to ensure fair distance calculations.
3. **Implement kNN:**
    - For each instance in the test set:
        1. Compute the distance between the test instance and all training instances.
        2. Sort the distances in ascending order.
        3. Select the first k entries from the sorted list.
        4. Determine the most frequent class (classification) or average the target values (regression) of the selected k entries.
        5. Assign the class or predicted value to the test instance.

### Advantages

- **Simple to Understand and Implement:** Easy to grasp conceptually and requires no model training phase.
- **Non-Parametric:** Makes no underlying assumptions about the data distribution.
- **Versatile:** Can be used for both classification and regression problems.

### Disadvantages

- **Computationally Intensive:** For large datasets, the distance calculation can be slow, especially as the dimensionality increases.
- **Memory Intensive:** Requires storing the entire training dataset.
- **Curse of Dimensionality:** As the number of features increases, the distance metrics become less reliable, leading to poorer performance.





**Conditional Probability,**
Conditional probability is the probability of an event occurring given that another event has already occurred. It is a fundamental concept in probability theory and statistics, used to refine predictions based on additional information.
![[Pasted image 20240518005826.png]]
Bayes Theorem.
![[Pasted image 20240518010544.png]]
Naive Bayes Classifier.
![[Pasted image 20240518023741.png]]

Naive Bayes Variants: 
Bernoulli Naive Bayes(binary),
Multinomial Naive Bayes,(multidimensional data)
Gaussian Naive Bayes. (probability distribution function)
![[Pasted image 20240518025316.png]]


Support Vector Machine (SVM),
hyperplane - line between two data cluster 
margin - distance between  one cluster to hyperplane + distance between hyperplane to other 
![[Pasted image 20240518030132.png]]

Non-Linear Support Vector Machine (SVM) And Kernel Function.

  
Non-linear Support Vector Machines (SVM) are a type of SVM used for classifying data that cannot be separated by a straight line. Here’s a simpler explanation:

### Key Concepts

1. **Non-Linear Separation**: When data points cannot be separated by a straight line (or a hyperplane in higher dimensions), a non-linear SVM is used. This means the decision boundary between different classes is curved or more complex.
    
2. **Kernel Trick**: To handle non-linear data, non-linear SVM uses a method called the kernel trick. Kernels are functions that transform the data into a higher-dimensional space where it becomes easier to separate with a straight line. This transformation is done without explicitly calculating the coordinates in the higher-dimensional space.
    

### Common Kernel Functions

- **Polynomial Kernel**: Creates curved boundaries based on polynomial functions.
- **Radial Basis Function (RBF) Kernel**: Uses the distance between data points to create flexible decision boundaries.
- **Sigmoid Kernel**: Similar to activation functions in neural networks, used less commonly.



Decision Tree Algorithm, 

A Decision Tree is a supervised machine learning algorithm used for classification and regression tasks. It models decisions and their possible consequences, including outcomes, resource costs, and utility. It consists of nodes that form a tree-like structure, where each internal node represents a test on an attribute, each branch represents the outcome of the test, and each leaf node represents a class label or regression outcome.

### Key Concepts

1. **Root Node**: The topmost node in a decision tree, representing the entire dataset. This node is split into two or more homogeneous sets.
2. **Decision Node**: A node that splits into branches based on certain conditions.
3. **Leaf/Terminal Node**: The end node that contains the final output or decision.
4. **Splitting**: The process of dividing a node into two or more sub-nodes.
5. **Pruning**: The process of removing parts of the tree to prevent overfitting and improve generalization.

### How Decision Trees Work

1. **Selecting the Best Feature**: At each step, the algorithm selects the feature that best separates the data according to some criteria (e.g., Gini impurity, entropy, information gain).
2. **Splitting**: Based on the selected feature, the data is split into subsets. This process is repeated recursively for each subset.
3. **Stopping Criteria**: The recursion stops when a stopping criterion is met, such as when all data points in a node belong to the same class, or when a maximum depth is reached.
### Advantages of Decision Trees

- **Easy to Understand**: The model's logic is easy to understand and interpret.
- **No Scaling Required**: Works with both numerical and categorical data without the need for scaling.
- **Handles Missing Values**: Can handle datasets with missing values well.

### Disadvantages of Decision Trees

- **Prone to Overfitting**: Can create complex trees that do not generalize well to unseen data.
- **Unstable**: Small changes in the data can lead to significantly different tree structures.
- **Bias**: Can be biased towards attributes with more levels or categories.


Random Forest (RF), ROC Curve.

Random Forest (RF) is an ensemble learning method used for classification and regression tasks. It builds multiple decision trees and merges them together to get a more accurate and stable prediction. The key idea is to create a 'forest' of random trees, each trained on a random subset of the data, and use their collective decision to improve predictive performance and control overfitting.

### Key Concepts

1. **Bagging (Bootstrap Aggregating)**:
    
    - **Process**: Random Forest uses bagging to create multiple subsets of the original dataset by sampling with replacement.
    - **Purpose**: This helps in reducing variance and overfitting by averaging the predictions of multiple decision trees.
2. **Random Feature Selection**:
    
    - **Process**: Each tree in the forest considers a random subset of features when splitting nodes.
    - **Purpose**: This introduces further randomness, making the trees less correlated and improving the model's robustness.
3. **Ensemble Prediction**:
    
    - **Process**: For classification, the final output is the mode (majority vote) of the predictions from all trees. For regression, it is the average of all predictions.
    - **Purpose**: Aggregating the results of multiple trees enhances predictive accuracy.

### Advantages of Random Forest

- **Accuracy**: Often more accurate than individual decision trees due to reduced overfitting.
- **Robustness**: Handles large datasets with higher dimensionality and does not require extensive data preprocessing.
- **Feature Importance**: Provides insights into the importance of features in making predictions.
- **Versatility**: Can be used for both classification and regression tasks.

### Disadvantages of Random Forest

- **Complexity**: More complex and computationally intensive than individual decision trees.
- **Interpretability**: Harder to interpret the final model compared to a single decision tree.


The **Receiver Operating Characteristic (ROC**) curve is a graphical representation used to evaluate the performance of a binary classification model. It plots the True Positive Rate (TPR) against the False Positive Rate (FPR) at various threshold settings. The ROC curve is a useful tool for visualizing and comparing the diagnostic ability of classifiers.