# Extreme Learning Machine

> Huang, G. B., Zhu, Q. Y., & Siew, C. K. (**2006**). Extreme learning machine: theory and applications. Neurocomputing, 70(1-3), 489-501.

## 1. Abstract
This paper rigorously proves that the single-hidden layer feedforward network(SHFN) with input weight and biased random assigned and then fixed, which means the only parameter to be learned is the weight of output layer, can approximate any function with infinitely differentiable activation function. 

The straightforward of the application of the above theory is that we can then reduce the number of parameters in the network. Furthermore, in the case of SHFN, the parameters to be learned have analytical expression, which leads to significant training time reduction. 

More importantly, having input weight and bias random assigned doesn't deteriorate the performance of network. Instead, the generalization performance get improved. *However, the comparison happened in 2006, with small datasets and SHFN.*

## 2. Features
- The learning speed of ELM is extremely fast, since the we have analytical solution for the parameters in the case of single-hidden layer feedforward neural net- works (SLFNs).  Training time is hundreds or thousands less than BP algorithm for neural network.
- The analytical solution is attained by **Moore–Penrose generalized inverse**. 
- **Better generalization performance** than the gradient-based learning in most case. 
- The ELM tends to reach the solutions straightforward without trivial issues like local minima, improper learning rate, overfiting and so on. Again, it is due to the existence of analytical solution.
- **Efficiency on the test stage** is quite the same with neural network with the same structure.
- ELM cannot be used in multilayer network at the time (year 2006).
  
## 3. Takeaways
- What is the reason of better generalization performance?

  First, the traditional network cannot be overfitting, otherwise the ELM will be more overfiting and have worse generalization performance. 

  So the possible reasons are

       -   Better convergence? - 
       -   Overcoming underfitting - use larger data set to testify?

- Can we fix some parameters to get a better generalization performance in general case?

- **Moore Penrose Inverse**

  - A matrix $\mathbf{G}$ of order $n\times m$ is the Moore-Penrose generalized inverse of matrix $\mathbf{A}$ of order $m \times n$ if  

    ​	$$\mathbf{AGA=A, GAG=G, (AG)^T=AG, (GA)^T=GA}$$

    the formula for $\mathbf{G}$ is $\mathbf{G = (A^TA)^{-1}A^T}$  if $ \mathbf{A^TA}$ is nonsingular  and $\mathbf{A^T(AA^T)^{-1}}$  if $\mathbf{AA^T}$ is nonsingular. For more information, see [wikipedia.]([https://en.wikipedia.org/wiki/Moore%E2%80%93Penrose_inverse#Definition](https://en.wikipedia.org/wiki/Moore–Penrose_inverse#Definition))

  -  Minimum norm least-squares solution of general linear system is Moore Penrose Inverse

     For an optimization problem $min_{\mathbf{X}}||\mathbf{AX - y}||$, let there exists a matrix $\mathbf{G}$ s.t. $\mathbf{Gy}$ is the minimum norm least-squares solution of a linear system $\mathbf{Ax=y}$, then it is necessary and sufficient that $\mathbf{G}=A^{\dagger}$. This explains why the solution for ELM is exact Moore-Penrose inverse. 



# Variants of Extreme Learning Machine
> Huang, G. Bin, Wang, D. H., & Lan, Y. (**2011**). Extreme learning machines: A survey. International Journal of Machine Learning and Cybernetics, 2(2), 107–122. https://doi.org/10.1007/s13042-011-0019-y



## 1. Random hidden layer feature mapping based ELM

- This variant add an regulation term on the optimization problem, i.e.

  $$Min_{\mathbf{\beta}} ||\mathbf{H\beta - T}||^2 + \lambda||\mathbf{\beta}||^2$$， 

  whose solution is correspondingly $\beta = \mathbf{H^T}(\frac{\mathbf{I}}{\lambda}+\mathbf{HH^T})^{-1}\mathbf{T}$.

- The result is stabler and tends to have better generalization performance. 



## 2. Kernel Based ELM

- Based on the observation of $\beta$, we actually do not need to know mapping $\mathbf{H}$. When it is the case, define kernel $\mathbf{\Omega}_{ELM} = \mathbf{HH^T}:\Omega_{i, j} =  \mathbf{h(x_i)}\mathbf{h(x_j)}=K(\mathbf{x_i, x_j})$.  Then we replace $\mathbf{HH^T}$ in the solution expression to get the solution based on kernel. 	
- The benefit of kernel-based ELM is that it further reduce computation complexity.



## 3. Online sequential ELM(OS-ELM)

- ELM algorithm can learn the training data one-by-one and chunk-by-chunk. Again, due to the explicit solution for $\beta$ and bunch of matrix manipulation. 

- The basic idea of sequence learning.

  - Step 1: calculate initial weight $\beta^{o}$
  - Step 2: calculate new the mapping output of new data
  - Step 3:  The new $\beta^t$ can be expressed by the old ones and some matrix of new data.
  - Step 4: go back to step 2.

- The key is to derive the connection between old $\beta$ and new $\beta$. It is worth to note that we do not have to derive the relationship exact between them, the relationship between their building block also works. 

- The sequential online learning can be used on time series prediction

  

## 4. Pruning ELM

- P-ELM by Rong - A systematic and automated method for ELM classifier network design. The elimination of hidden notes is supported by statistical criteria, such as Chi-square and information gain measures. 

- Optimally-pruned ELM by Miche

  

## 5. Constructive model selection ELM

- Error minimized ELM (EM-ELM) is an error minimization based method in which the number of hidden nodes can grow one-by-one or group-by-group until optimal. 
  - The selection method can be
    - add node one by one
    - random search
- Stepwise forward selection based constructive ELM for regression
- Two-stage ELM for regression



## 6. Interesting Comments

- It seems that ELM performs better than other conventional learning algorithms in applications with higher noise.

  



