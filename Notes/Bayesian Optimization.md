
# Bayesian Regression

>Applying bayesian rule to the regression problem.  With a presumed prior distribution for each parameter and then use data to update the believe on those distributions and thus get posterior distribution. 

For more information, see the book [An Introduction to Bayesian Thinking](https://statswithr.github.io/book/introduction-to-bayesian-regression.html).


## 1.1 Comments
-  Since bayesian regression generates posterior distribution for each parameter, one then is able to use different point estimation approach to infer parameter value. 
-  **Credible confidence interval** is possible with posterior distribution.
-  **Outlier detection**. After inferring stage, one is able to get the sample distribution with posterior believe. Such distribution can be used in outlier detection. For example, define the sample beyond a multiple of standard deviation as outlier. 
-  Bayesian regression is equivalent to OLS with **non-informative prior**. 
-  **Computation Efficiency**. The result of comparison between computation efficiency of bayesian regression and OLS is unknown. But I suppose bayesian approach is more computationally expensive. 
- Two approaches for **posterior prediction** : First, use parameters from point estimation. Second, use posterior distribution to take parameter uncertainty into account. It is done by using marginal distribution and then marginalize parameter out.    

# Bayesian Process

A Gaussian process is a random process where any point $\mathbf{X}\in\mathbb{R}$ is assigned a random value $f(\mathbf{X})$ and where the joint distribution of a finite number if these r.v.s $p(f(X_1, ..., f(X_N)))$ is itself Gaussian:
$$p(\mathbf{f|X}) \sim N(\mathbf{f|\mu, K})$$,
where $\mu$ is the vector of mean function, $K_{i,j}=k(X_i, X_j)$, positive definite kernel function or covariance function. For more discussion on kernel function in machine learning, see Chapter 6 in *Pattern Recognition and Machine Learning*. 

Thus, a Gaussian process is a distribution over functions whose shape is defined by $\mathbf{K}$. If points $\mathbf{x_i}$ and $\mathbf{x_j}$ are considered to be similar by the kernel the function values are these points, $f(\mathbf{x_i})$ and $f\mathbf{x_j}$ can be expected to be similar too. 




# Bayesian Optimization
