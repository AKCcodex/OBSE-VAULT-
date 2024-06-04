### MODULE-I (Short Answer Type Questions)

#### 1. Define binomial distribution and provide a real-world application. [CO1]

**Definition**: The binomial distribution is a discrete probability distribution that models the number of successes in a fixed number of independent and identically distributed Bernoulli trials. Each trial results in a success with probability \( p \) and a failure with probability \( 1 - p \).

**Real-World Application**: A real-world example is quality control in manufacturing. If a factory produces light bulbs with a 95% success rate, the binomial distribution can be used to model the probability of finding a certain number of defective bulbs in a sample of 100 bulbs.

#### 2. Explain the difference between Type I and Type II errors [CO2]

**Type I Error**: A Type I error occurs when a true null hypothesis is incorrectly rejected. This is also known as a false positive.

**Type II Error**: A Type II error occurs when a false null hypothesis is not rejected. This is also known as a false negative.

**Difference**: The main difference is that a Type I error relates to rejecting a true null hypothesis, while a Type II error relates to failing to reject a false null hypothesis.

#### 3. Define mean, median, and mode, and explain their differences. [CO1]

**Mean**: The mean is the average of a set of numbers, calculated by dividing the sum of all values by the number of values.

**Median**: The median is the middle value in a sorted list of numbers. If the list has an even number of values, the median is the average of the two middle numbers.

**Mode**: The mode is the value that appears most frequently in a data set.

#### 4. Explain the concept of maximum likelihood estimation and give an example. [CO4]

**Concept**: Maximum Likelihood Estimation (MLE) is a method for estimating the parameters of a statistical model. It finds the parameter values that maximize the likelihood function, which measures how well the model explains the observed data.

**Example**: Suppose we have a set of data points from a normal distribution, and we want to estimate the mean (\(\mu\)) and variance (\(\sigma^2\)). The MLE for \(\mu\) is the sample mean, and the MLE for \(\sigma^2\) is the sample variance.

#### 5. How do visualizations enhance communication and storytelling with data? [CO2]

**Enhancement**: Visualizations translate complex data sets into graphical representations, making it easier to understand and interpret data. They highlight patterns, trends, and outliers, which can enhance storytelling by providing clear and compelling evidence to support arguments. Visualizations can simplify complex information, engage the audience, and improve retention of the presented information.

### MODULE-I (Long Answer Type Questions)

#### A1. Explain about Markov Model. Explain the difference between point estimation and interval estimation [CO1]

**Markov Model**: A Markov Model is a stochastic model used to represent systems that transition from one state to another on a state space. It is characterized by the Markov property, which states that the future state depends only on the present state and not on the sequence of events that preceded it.

**Point Estimation vs. Interval Estimation**:
- **Point Estimation**: Provides a single value as an estimate of a parameter. For example, the sample mean is a point estimate of the population mean.
- **Interval Estimation**: Provides a range of values within which the parameter is expected to lie with a certain level of confidence. For example, a 95% confidence interval for the mean provides a range that has a 95% chance of containing the true mean.

#### A2. Explain the probability density function for continuous random variables. Briefly describe estimation theory. [CO1]

**Probability Density Function (PDF)**: For a continuous random variable, the PDF describes the likelihood of the variable taking on a particular value. The area under the PDF curve between two points gives the probability that the variable falls within that range. The total area under the PDF curve is 1.

**Estimation Theory**: Estimation theory is a branch of statistics that deals with estimating the values of parameters based on measured data. It involves point estimation, interval estimation, and hypothesis testing. Methods include Maximum Likelihood Estimation (MLE) and Bayesian estimation.

#### A3. Explain the concept of probability distribution and provide examples of discrete and continuous probability distributions. Discuss their properties and applications. [CO1]

**Probability Distribution**: A probability distribution describes how the values of a random variable are distributed. It gives the probabilities of different outcomes.

**Discrete Probability Distributions**: 
- **Examples**: Binomial distribution, Poisson distribution.
- **Properties**: The sum of the probabilities of all possible outcomes is 1. The probabilities are non-negative.
- **Applications**: Quality control (binomial), number of events in a fixed interval (Poisson).

**Continuous Probability Distributions**:
- **Examples**: Normal distribution, Exponential distribution.
- **Properties**: The total area under the probability density function (PDF) curve is 1. Probabilities are found using areas under the curve.
- **Applications**: Heights and weights of people (normal), time between events (exponential).

#### A4. Discuss the central limit theorem and its significance in statistics. Explain how the central limit theorem allows for the use of normal distribution-based methods in statistical inference. [CO5]

**Central Limit Theorem (CLT)**: The CLT states that the distribution of the sample mean of a large number of independent, identically distributed random variables approaches a normal distribution, regardless of the original distribution of the variables. 

**Significance**: The CLT is crucial because it allows us to make inferences about population parameters even when the population distribution is not normal, as long as the sample size is sufficiently large.

**Use in Statistical Inference**: Because of the CLT, we can use normal distribution-based methods (such as confidence intervals and hypothesis tests) for the sample mean, facilitating simpler and more robust statistical analysis even when dealing with non-normal population distributions.



