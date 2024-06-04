1. Define machine learning.

    Machine learning is a subset of artificial intelligence (AI) that focuses on the development of algorithms and statistical models that enable computers to progressively improve their performance on a specific task through experience, without being explicitly programmed. In other words, it is the process of teaching computers to learn from data patterns and make predictions or decisions without human intervention. Machine learning algorithms learn from labeled or unlabeled data, allowing them to find hidden insights or patterns within the data and make predictions or decisions based on that information. The main goal of machine learning is to enable computers to learn automatically from data and improve their performance over time as more data becomes available.

2. How supervised learning different from unsupervised learning techniques?

    **Supervised Learning**: Uses labeled data to train algorithms to predict outputs based on inputs. Examples include classification and regression tasks.
-    **Unsupervised Learning**: Works with unlabeled data to find patterns or       structures within it. Examples include clustering and dimensionality reduction tasks.
- - **Supervised Learning Example**: Suppose you're building a spam email filter. You have a dataset of emails labeled as either "spam" or "not spam," along with the email content as features. Using this labeled data, you can train a supervised learning algorithm, such as a Naive Bayes classifier or a Support Vector Machine, to learn patterns in the email content and predict whether new, unseen emails are spam or not.
    
- **Unsupervised Learning Example**: Let's say you're a retailer analyzing customer purchase data. You have a dataset containing information about customer purchases, such as the items purchased and the amount spent, but without any labels. Using unsupervised learning techniques like k-means clustering, you can identify groups of customers who exhibit similar purchasing behavior. This can help you tailor marketing campaigns or product recommendations to different customer segments without needing predefined categories.


3. What is Gradient descent? How does gradient descent works.
      




4. Difference between overfitting & underfitting?

   - **Overfitting**: Think of overfitting as memorizing the training data rather than learning from it. It's like a student who memorizes answers without understanding the concepts. They perform well on the exact questions they've seen before (training data), but struggle when faced with new questions (unseen data).
    
- **Underfitting**: On the other hand, underfitting is like not studying enough. The model fails to grasp the patterns in the data, akin to a student who hasn't studied enough to answer any questions effectively. They perform poorly on both the questions they've seen before (training data) and new questions (unseen data).

5. What techniques use to reduce underfitting?

   **Increase Model Complexity**: Use more complex models or increase the number of parameters/layers.
- **Feature Engineering**: Add more informative features or remove irrelevant ones.
- **Reduce Regularization**: Decrease the strength of regularization or remove it.
- **Increase Training Data**: Gather more data or augment existing data.
- **Cross-validation**: Ensure evaluation metrics are sensitive enough.
- **Ensemble Methods**: Combine multiple models for better performance.

6. What techniques use to reduce overfitting?

- **Regularization**: Apply L1/L2 regularization to penalize large parameter values.
- **Cross-validation**: Use k-fold cross-validation to assess model performance.
- **Early Stopping**: Stop training when performance on a validation set starts to degrade.
- **Simpler Models**: Use simpler architectures or fewer features.
- **Dropout**: Randomly deactivate neurons during training in neural networks.
- **Data Augmentation**: Increase training data diversity with transformations.
- **Ensemble Methods**: Combine multiple models to reduce variance.

7. Short notes on Regularization.
     - Purpose: Prevents overfitting by penalizing complex models.
- Techniques: L1 (Lasso), L2 (Ridge), Elastic Net.
- Strength: Controlled by hyperparameter, balances fit and simplicity.
- Implementation: Penalty term added to loss function during training.
- Effects: Improves generalization by reducing variance.
- Considerations: Choose technique based on data and model characteristics.

8. Describe the various application on machine learning 
     - **Healthcare**: Disease diagnosis, drug discovery, medical image analysis.
- **Finance**: Fraud detection, credit risk assessment, algorithmic trading.
- **E-commerce**: Product recommendation, customer churn prediction, dynamic pricing.
- **Automotive**: Autonomous vehicles, predictive maintenance, traffic optimization.
- **Manufacturing**: Quality control, predictive maintenance, supply chain optimization.
- **Marketing**: Customer segmentation, sentiment analysis, ad optimization.
- **NLP**: Language translation, chatbots, sentiment analysis.
- **Recommendation Systems**: Content recommendation, collaborative filtering.
- **Energy**: Demand forecasting, predictive maintenance, renewable energy.
- **Agriculture**: Crop yield prediction, pest detection, precision agriculture.

9. How does Machine Learning Work?
       
In short, machine learning works by training algorithms on data to learn patterns and make predictions or decisions without explicit programming. It involves collecting and preprocessing data, training the model, evaluating its performance, deploying it for use, and monitoring its performance for updates as needed.

10. What is probability distribution? What is difference between a combination and a permutation?
       
In machine learning:

1. ==**Probability Distribution**:==
    
    - ==It represents the likelihood of outcomes in data.==
    - ==Used for uncertainty modeling and in various algorithms.==
    - ==Examples include Gaussian, Bernoulli, and multinomial distributions.==
2. **Combination vs. Permutation**:
    
    - **Combination**: Used for feature subsets without considering order.
    - **Permutation**: Considers order, useful in sequence tasks or optimization.

In essence, probability distributions model data uncertainty, while combinations and permutations are used in feature engineering and optimization tasks.