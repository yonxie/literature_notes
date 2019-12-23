# Extreme Machine Learning
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
-  What is the reason of better generalization performance?

First, the traditional network cannot be overfitting, otherwise the ELM will be more overfiting and have worse generalization performance. 

So the possible reasons are

       -   Better convergence? - 
       -   Overcoming underfitting - use larger data set to testify?
  


-  Can we fix some parameters to get a better generalization performance in general case?

