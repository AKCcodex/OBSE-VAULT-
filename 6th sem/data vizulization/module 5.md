Supervised classification methods: K-nearest neighbor, naive Bayes, logistic
regression, decision tree, support vector machine.

Supervised classification methods are used to assign labels to data points based on training data. Here are brief descriptions of some common methods:

### 1. K-Nearest Neighbor (KNN)
KNN classifies a data point based on the labels of the closest \(K\) data points in the feature space. It assigns the most common label among these neighbors to the new data point. It is simple and intuitive but can be computationally expensive for large datasets.

### 2. Naive Bayes
Naive Bayes is a probabilistic classifier based on Bayes' Theorem. It assumes that the features are independent given the class label (hence "naive"). Despite its simplicity and the strong independence assumption, it often performs well, especially for text classification problems.

### 3. Logistic Regression
Logistic regression models the probability that a given data point belongs to a particular class. It uses a logistic function to model the probability and assigns a class label based on a threshold (usually 0.5). It is widely used for binary classification problems and can be extended to multiclass classification.

### 4. Decision Tree
A decision tree classifier splits the data into subsets based on feature values, creating a tree structure where each node represents a feature and each branch represents a decision rule. The leaves represent class labels. It is easy to interpret and visualize but can overfit the training data if not pruned properly.

### 5. Support Vector Machine (SVM)
SVM finds the hyperplane that best separates the classes in the feature space. It maximizes the margin between the classes, which is the distance between the hyperplane and the nearest data points from each class (support vectors). SVMs can handle non-linear classification by using kernel functions to project the data into higher-dimensional spaces. They are effective in high-dimensional spaces but can be memory-intensive.

### Summary
- **K-Nearest Neighbor (KNN)**: Classifies based on the closest neighbors.
- **Naive Bayes**: Uses probability and assumes feature independence.
- **Logistic Regression**: Models class probabilities and uses a logistic function.
- **Decision Tree**: Splits data based on feature values, creating a tree of decisions.
- **Support Vector Machine (SVM)**: Finds the hyperplane that best separates classes and can handle non-linear data with kernels.

These methods offer different strengths and are suitable for various types of classification problems depending on the nature of the data and specific requirements of the task.