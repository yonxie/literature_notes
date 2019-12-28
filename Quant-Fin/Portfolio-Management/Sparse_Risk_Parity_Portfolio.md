# Sparse Risk Parity Portfolio

## 1. Motivation

Risk parity method tends to assign non-zero but small weight to assets, which attenuates portfolio returns significantly in the case of transaction cost. So the more sparse optimization is called to build a more concentrated portfolio while keep the advantage of diversity. 

## 2. Abstract

This paper proposes a new form of regulation item for sparse portfolio: $l_0$ norm of weight. However, $l_0 $ norm is not convex, which causes it intractable to solve the optimization. Correspondingly, this paper also proposes a flexible successive convex optimization algorithm solve the difficulty emerged in the presence of $l_0 $ norm. 

The main way of doing that is to use differentiable function to approximate the discrete $l_0 $function.  As the name suggests, the algorithm is kind of iterative optimization solver. In order to integrate the risk parity optimization into the framework, this paper also uses a method to make the risk parity objective convex.

The algorithm is flexible, and can be used in many portfolio optimization problem.

Sparse Risk Parity Portfolio achieve higher return and lower volatility compared with a bunch of benchmarks.

## 3. Takeaways

- The optimization with $l_0$ norm can be intractable. 
- Easy to understand that, w.r.t. the effect of sparsity: $l_0 > l_1 > l_2$. 
- Use continuous function to approximate discrete component in the objective function.
- Optimization problem with non-convex function can be intractable. 
- Pay attention to the role of iterative algorithm in solving optimization problem. Especially when the parameters to be found are more than one. Recall that the dynamic programming algorithm of finding optimal state and optimal policy.  

