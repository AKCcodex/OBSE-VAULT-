regression is a statistical method that helps us understand and predict the relationship between variable
describes how one variable (dependent variable) changes as another variable (independent variable ) changes
==dependent variable== we are trying to predict or explain (Y)
independent variable that are used to predict or explain the changes in the dependent variable(X)
for ex= predicting salary based on ==years of experience==, predicting exam score based on ==study hours== , predicting resale price based on ==vehicle age==.

==Curse of
Dimensionality, Managing Missing Features, Managing Categorical Data.==
Confusion Matrix

![[Pasted image 20240516131146.png]]
  

The Curse of Dimensionality refers to the various challenges and complications that arise when analyzing and organizing data in high-dimensional spaces (often hundreds or thousands of dimensions).
dimensionality badha rahe ho and model ka output ka certain point tak he acha hoga jada kar do ge tho model bekar hote chala jaye ga

Managing missing features 

-  removing the record
- create Sub-record
- automatic strategy
     1. mean
     2. median
     3. mode

managing categorical data
![[Pasted image 20240516135939.png]]


LINEAR REGRESSION
equation of linear regression Y=mx+b
Y= represents dependent variable
C = represents independent variable
M is the slope of the line 
b = is the intercept(the value of Y when Xis 0)

outliers **an observation that lies an abnormal distance from other values in a random sample from a population**.

EX
project pizza prices
step1. Data Collection
step2. calculation
step3. prediction
step4. visualisation
![[Pasted image 20240510215846.png]]



LOGISTIC REGRESSION (CLASSES)
ex email , disease
supervised classification model
dependent variable is categorical and binary(0 or 1)
we use sigmoid function

| linear regression                                                        | logistic regression                                                                                                                                    |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| the dependent variable ( the variable you want to predict) is continuous | supervised classification model dependent variable is categorical and binary (0 and 1), making it suitable for calculation the probability or an event |
| equation y=mx+b                                                          | sigmoid function                                                                                                                                       |
| we predict the value by an integer numaber                               | we predict the value by 1 or 0                                                                                                                         |


- **Polynomial Regression** is a regression algorithm that models the relationship between a dependent(y) and independent variable(x) as nth degree polynomial. The Polynomial Regression equation is given below:
- linear model on non linear data

y= b0+b1x1+ b2x12+ b2x13+...... bnx1n
![[Pasted image 20240511014719.png]]
**Ridge regression** is a statistical regularisation technique. It corrects for overfitting on training data in machine learning models.
Ridge regression, also known as Tikhonov regularization, is a technique used to improve the performance of regression models when there are highly correlated independent variables (multicollinearity). It adds a penalty to the size of the coefficients to prevent them from becoming too large, which helps in stabilizing the model.

### Key Points

1. **Multicollinearity**: When independent variables are highly correlated, it can cause issues in regression analysis. Ridge regression helps to address this problem.
    
2. **Penalty Term**: Ridge regression modifies the least squares objective function by adding a penalty term. This term is the sum of the squares of the coefficients, multiplied by a parameter 𝜆λ (lambda). The objective function becomes:
    
3. **Parameter 𝜆λ**: The parameter 𝜆λ controls the strength of the penalty. When 𝜆=0λ=0, ridge regression is the same as ordinary least squares (OLS) regression. As 𝜆λ increases, the penalty on the coefficients increases, leading to smaller coefficients.
    
4. **Bias-Variance Trade-off**: Ridge regression introduces some bias but reduces variance, which can improve the model’s performance on new data.

**Lasso regression** is a regularization technique that applies a penalty to prevent [overfitting](https://www.ibm.com/topics/overfitting) and enhance the accuracy of statistical models.
elastic net regresssion
  
Lasso regression, short for Least Absolute Shrinkage and Selection Operator, is a type of linear regression that performs both variable selection and regularization. It is used to enhance the prediction accuracy and interpretability of the statistical model it produces.

### Key Concepts

1. **Variable Selection**: Lasso regression can shrink some coefficients to zero, effectively selecting a simpler model that retains only the most significant predictors.
    
2. **Regularization**: Like ridge regression, lasso regression adds a penalty to the objective function to prevent overfitting. The key difference is that lasso uses the L1 norm (sum of absolute values of coefficients) rather than the L2 norm (sum of squared values of coefficients) used in ridge regression.
    
3. **Objective Function**: The objective function for lasso regression is:
    
    Minimize ∑𝑖=1𝑛(𝑦𝑖−𝑦^𝑖)2+𝜆∑𝑗=1𝑝∣𝛽𝑗∣Minimize i=1∑n​(yi​−y^​i​)2+λj=1∑p​∣βj​∣
    
    Here, 𝜆λ is the tuning parameter that controls the strength of the penalty.
    
4. **Shrinkage**: The L1 penalty can shrink some coefficients to exactly zero, leading to a sparse model that includes only the most influential predictors.
    

### Advantages of Lasso Regression

- **Feature Selection**: Automatically selects the most important features, which can make the model simpler and easier to interpret.
- **Handles Multicollinearity**: Helps in dealing with correlated predictors by shrinking coefficients.
- **Improves Prediction Accuracy**: Regularization can reduce overfitting, improving the model’s performance on new data.

### Disadvantages of Lasso Regression

- **Bias Introduction**: Adds bias to the model estimates, although this can be offset by reduced variance.
- **Model Interpretation**: The choice of 𝜆λ is crucial, and selecting it requires careful cross-validation.


Elastic Net regression is a regularized regression method that combines the properties of both Ridge regression and Lasso regression. It aims to improve model performance by balancing the limitations of each method. Elastic Net is particularly useful when dealing with highly correlated predictors and when you want to perform feature selection.

### Key Concepts

1. **Combination of L1 and L2 Penalties**: Elastic Net regression adds both the L1 penalty (used in Lasso regression) and the L2 penalty (used in Ridge regression) to the objective function. This combination allows for both coefficient shrinkage and variable selection.
    
2. **Objective Function**: The objective function for Elastic Net regression is:
    
    Minimize ∑𝑖=1𝑛(𝑦𝑖−𝑦^𝑖)2+𝜆1∑𝑗=1𝑝∣𝛽𝑗∣+𝜆2∑𝑗=1𝑝𝛽𝑗2Minimize i=1∑n​(yi​−y^​i​)2+λ1​j=1∑p​∣βj​∣+λ2​j=1∑p​βj2​
    
    Here, 𝜆1λ1​ controls the L1 penalty (Lasso), and 𝜆2λ2​ controls the L2 penalty (Ridge).
    
3. **Hyperparameters**: Elastic Net has two hyperparameters:
    
    - 𝛼α: The mixing parameter between Ridge and Lasso. When 𝛼=0α=0, Elastic Net is equivalent to Ridge regression; when 𝛼=1α=1, it is equivalent to Lasso regression.
    - 𝜆λ: The overall regularization strength.

### Advantages of Elastic Net

- **Handles Multicollinearity**: Like Ridge regression, it can handle correlated predictors effectively.
- **Feature Selection**: Like Lasso regression, it can perform variable selection, shrinking some coefficients to zero.
- **Flexibility**: By adjusting 𝛼α and 𝜆λ, it provides a balance between Ridge and Lasso, offering flexibility based on the specific needs of the dataset.

### Disadvantages of Elastic Net

- **Complexity**: Involves tuning two hyperparameters (𝛼α and 𝜆λ), which can be computationally intensive.
- **Bias Introduction**: Similar to Ridge and Lasso, it introduces bias in exchange for lower variance.