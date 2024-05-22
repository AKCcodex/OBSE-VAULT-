## ****Underfitting in Machine Learning****

A [statistical model](https://www.geeksforgeeks.org/difference-between-statistical-model-and-machine-learning/) or a machine learning algorithm is said to have underfitting when a model is too simple to capture data complexities. It represents the inability of the model to learn the training data effectively result in poor performance both on the training and testing data. In simple terms, an underfit model’s are inaccurate, especially when applied to new, unseen examples. It mainly happens when we uses very simple model with overly simplified assumptions. To address underfitting problem of the model, we need to use more complex models, with enhanced feature representation, and less regularization.

### ****Reasons for**** ****Underfitting****

1. The model is too simple, So it may be not capable to represent the complexities in the data.
2. The input features which is used to train the model is not the adequate representations of underlying factors influencing the target variable.
3. The size of the training dataset used is not enough.
4. Excessive regularization are used to prevent the overfitting, which constraint the model to capture the data well.
5. Features are not scaled.

### ****Techniques to Reduce Underfitting****

1. Increase model complexity.
2. Increase the number of features, performing [feature engineering](https://www.geeksforgeeks.org/what-is-feature-engineering/).
3. Remove noise from the data.
4. Increase the number of [epochs](https://www.geeksforgeeks.org/epoch-in-machine-learning/) or increase the duration of training to get better results.

## ****Overfitting in Machine Learning****

A [statistical model](https://www.geeksforgeeks.org/difference-between-statistical-model-and-machine-learning/) is said to be overfitted when the model does not make accurate predictions on testing data. When a model gets trained with so much data, it starts learning from the noise and inaccurate data entries in our data set. And when testing with test data results in High variance. Then the model does not categorize the data correctly, because of too many details and noise. The causes of overfitting are the non-parametric and non-linear methods because these types of machine learning algorithms have more freedom in building the model based on the dataset and therefore they can really build unrealistic models. A solution to avoid overfitting is using a linear algorithm if we have linear data or using the parameters like the maximal depth if we are using decision trees. 

In a nutshell, [Overfitting](https://www.geeksforgeeks.org/underfitting-and-overfitting-in-machine-learning/) is a problem where the evaluation of machine learning algorithms on training data is different from unseen data.

### Reasons for Overfitting:

1.  High variance and low bias.
2. The model is too complex.
3. The size of the training data.

### ****Techniques to Reduce Overfitting****

1. Improving the quality of training data reduces overfitting by focusing on meaningful patterns, mitigate the risk of fitting the noise or irrelevant features.
2. Increase the training data can improve the model’s ability to generalize to unseen data and reduce the likelihood of overfitting.
3. Reduce model complexity.
4. [Early stopping](https://www.geeksforgeeks.org/regularization-by-early-stopping/) during the training phase (have an eye over the loss over the training period as soon as loss begins to increase stop training).
5. [Ridge Regularization](https://www.geeksforgeeks.org/lasso-vs-ridge-vs-elastic-net-ml/) and [Lasso Regularization](https://www.geeksforgeeks.org/implementation-of-lasso-regression-from-scratch-using-python/).
6. Use [dropout](https://www.geeksforgeeks.org/dropout-in-neural-networks/) for [neural networks](https://www.geeksforgeeks.org/neural-networks-a-beginners-guide/) to tackle overfitting.

| Features     | Training Data                                                                                                                             | Testing Data                                                                                                                                                          |     |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| Purpose      | The machine-learning model is trained using training data. The more training data a model has, the more accurate predictions it can make. | Testing data is used to evaluate the model’s performance.                                                                                                             |     |
| Exposure     | By using the training data, the model can gain knowledge and become more accurate in its predictions.                                     | Until evaluation, the testing data is not exposed to the model. This guarantees that the model cannot learn the testing data by heart and produce flawless forecasts. |     |
| Distribution | This training data distribution should be similar to the distribution of actual data that the model will use.                             | The distribution of the testing data and the data from the real world differs greatly.                                                                                |     |
| Use          | To stop overfitting, training data is utilized.                                                                                           | By making predictions on the testing data and comparing them to the actual labels, the performance of the model is assessed.                                          |     |
| Size         | Typically larger                                                                                                                          | Typically smaller                                                                                                                                                     |     |
![[Pasted image 20240516115404.png]]