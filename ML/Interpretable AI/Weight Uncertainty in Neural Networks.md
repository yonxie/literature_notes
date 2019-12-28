# Weight Uncertainty in Neural Networks

## 1. Abstract

This paper proposes an new algorithm, named ***Bayes by Backprop*** to update weights in neutral network based on the view that the weights follows certain distribution, and thus can be updated by Bayesian rule. 

Given that the true distribution is intractable, this paper use proxy distribution to approximate true distribution, and use *KL* divergence to measure the approximation. 

Briefly speaking, the objective of the training process is to learn the parameters to to distribution of weights, instead of weights. 

Surprisingly, the method work very good compared with other benchmark, even with neutral network of best performance. 

## 2. Main

Let $D = (x_i, y_i)$ be the sample set, the objective of the Bayes by Backprop algorithm is to find the maximum a posterior (MAP) weights:

$$\mathbf{w^{MAP}} = argmax_{\mathbf{W}}log(p(\mathbf{W}) | D) = argmax_{\mathbf{W}}log(p(D|\mathbf{W})) + log P(\mathbf{W})$$ .

By using variational approximation, we minimize the *KL* divergence with true Bayesian posterior, i.e.

$$\theta^* = arg max_{\theta} KL[q(\mathbf{w}|\theta)||P(\mathbf{w}|D)] = argmin KL[q(\mathbf{W}|\theta)||p(\mathbf{W})] - \mathbf{E}_{q(\mathbf{w}|\theta)}[logP(D|\mathbf{W})]$$ .

Then this paper use Monte Carlo gradients to update the $\theta $. 

## 3. Takeaways

- **The view that take weights in neutral network follow certain distribution.**
- The combination of **variational approximation, KL divergence and Monte Carlo** simulation to approximate unknow distribution.
- The method perform very good.
- Interestingly, randomly deleting up to **98%** posterior weights doesn't have severe impact on the performance of neutral network. 
- **What can we do after knowing the posterior distribution of weights? How does the distribution contribute to understanding the network?**

