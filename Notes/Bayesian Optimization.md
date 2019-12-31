
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

> Frazier, Peter I. "A tutorial on Bayesian Pptimization." *arXiv preprint arXiv:1807.02811* (2018).

## 1. Overview

Bayesian Optimization (BayesOpt) is used to find the **global** optimum of a function which is expensive to be evaluated many times.  A few assumptions are important to formulation and solution.

- The most successful application of BayesOpt is typically when dimension $< 20$. 
- "Expensive to evaluate" also means we typically **cannot observe the first and second-order derivatives** of the objective function.
- The feasible set is simple, in which it is easy to evaluate membership.

A typical BayesOpt algorithm involve two primary components: A model for statistical inference of the objective function, and acquisition function for deciding where to to sample:

---

**BayesOpt Algorithm**: Evaluate reminder N sample

Evaluate $f$ by Gaussian Process based on a prior and observed samples.

**While **$n<N$ **do**

​		$x_n = max_x \text(Acquision Function)$ based on current posterior dis. of $f$.

​		Observe $y_n = f(x_n)$.

​		Increment $n$

**end while**  

Return a solution: either the point evaluated with the largest f(x), or the point with the largest posterior mean

-----

## 2. Acquisition Function

Informally speaking, as the name suggests, an Acquisition function is use to ''acquire'' the next point to sample. Given the nature of randomness of objective function, the next sample can be attained in many way, each of which is based on its own philosophy.

### 2.1 Expected Improvement

$f(x_{n+1})$, where $x_{n+1}$ is the next sample, can be explicitly expressed by Normal distribution. Besides, we already know the current observation where $f$ attains its optimum. As such, we define 

$$EI(x) := E_n[[f(x) - f(x^*_n)]^+]$$,

which is the expected improvement of $f$ over $x$ compared with current optimum. The Expected Improvement Method is to maximize the expected improvement. Fortunately, it is mathematically tractable and computationally inexpensive. 

### 2.2 Knowledge Gradient

It is easy to see that the solution of optimization associated with expected improvement is always one point that has been previously observed.  However, when the evaluation has noise, the observation might involve with uncertainty.  In order to overcome such shortcoming, we work on expectation of  $f$, instead of single sample of $f$. Define KG acquisition function as

$$KG_n(x) := E_n[\mu^*_{n+1} - \mu_n^* | x_{n+1}=x]$$,

where the $\mu^*_{n+1}$ is the maximum of the expectation of posterior of $f$ at $x'$ . The expectation comes since we need to **update the posterior after observing  $f(x_{n+1})$**, but it is a random variable.  The Knowledge Gradient Method is to maximize the Knowledge-gradient function. 

One way to estimate KG acquisition function is simulation.  The simulating part is to observe $y_{n+1}$. Then we update posterior function based on the new observation. The last step is to get the $\mu^*_{n+1}$ and calculate the difference w.r.t. $\mu^*_n$. Averaging differences leads to $KG_n(x)$.

Then what remains is to find the point where KG function hits optimum. ==Evaluate KG function at the whole domain of $x$, to argmax $x$????==

- KG method provides substantially performance improvement in problem with noise. 

### 2.3 Entropy Search and Predictive Entropy Search

Entropy Search, different from the above methods, seeks the point to evaluate that causes the largest decrease in differential entropy.  Recall that smaller differential entropy indicates less uncertainty, the ES method seeks points that reduces uncertainty of optimum most. 

We now assume $x_*$  is global optimum of $f$.  Define Entropy-search acquisition function as

$$ES_n(x) = H(P_n(x^*)) - E_{f(x)}[H(P_n(x^*|f(x)))]$$.

The ES method is to find the point that maximizes the ES acquisition function.

It is worth to emphasize that the computation of ES function is challenging, which is why we use alternative approach PES to compute the above expression. See more in the reference paper. 

### 2.4 Multi-Step Optimal Acquisition Functions

By construction, the EI, KG, ES, and PES acquisition functions are optimal when N = n+1, in the
sense of maximizing the expected reward under the posterior. However, they are no longer obviously optimal when N > n+1.

In principle, it is possible to compute a multi-step optimal acquisition function that would maximize expected reward for general N. That is the main idea behind Multi-Step Optimal Acquisition Functions. 

The methods and applications of Multi-Step Optimal Acquisition Functions is highly related to **reinforcement learning**.



# Exotic Bayesian Optimization

Exotic Bayesian Optimization problem are ones with certain assumptions violated. Some selected prominent examples are listed below. 

- **Noisy Evaluation** problem emerges when the posterior of $f$ is integrated with noise. Informally speaking, one can simply apply the above acquisition functions to the noise posterior of $f$ , nevertheless EI may present conceptual challenge, i.e., its evaluation is based on single point and thus the improvement is for $f + \varepsilon$, instead of $f$. 
- **Parallel Evaluation** 
- **Constraints** type of EBO means one enforces sort of constraints on feasible set, and thus the assumption of simple set is violated.  It is worth to emphasize that the challenge associated with constraints comes from that it might be very harder to evaluate the membership. So the challenges emerges only when the constraints is expensive to evaluate. 
- **Multi-Fidelity and Multi-Information Source Evaluations** appears when one combines the optimization from different sources and each of them provides partial information.
- **Random Environmental Conditions and Multi-Task Bayesian Optimization** is similar with the above one.  The information, or the environment, where to seek optimum is itself a random variable, thus, the optimization objective is to maximize the expectation of target objective $f$ over different environment. **It is of great importance in application**.

EBOs are more in line with the tasks we encounter in real word. to Modify and to develop methods that are suitable such modification is very important. 



