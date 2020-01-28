# How To Backdoor Federated Learning

## 1. Summary

The contribution of this paper is based on the fact that the backdoor attack schemes proposed for single-machine learning don't work for federated learning. The reason lies on the feature that the detrimental impact caused by single or a group of participants will be **averaged out by the aggregator**.  

To bypass the averaging effect of federated learning and conduct backdoor attack effectively, this paper proposes a new scheme based on the characteristic of FL. Under the assumption that the attacker completely knows the its target model $X$, i.e., 

$$X = G^t + \frac{\alpha}{n} \sum_{i =1}^{m}(L^{t+1} - G^t)$$

the attacker reports the following model to survive the averaging, 

$$L^{t+1}_{m} = \frac{n}{\alpha} X - (\frac{n}{\alpha} - 1)G^t - \sum_{i=1}^{m-1}(L_i^{t+1} - G^t) \approx \frac{n}{\alpha}(X-G^t)+G^t $$,

which is the solution of the above equation. 

The intuition behind this formula is that the attacker needs to scale up its report model to survive. Such  scale-up can be detected by defense schemes, so more adjustments that aims to evade defense are discussed. 

## 2. Takeaways

- The the success odd of backdoor attack relies on the both the population of **trigger and target label.** Large population of target label and small trigger have higher odd.
- The backdoor learning in FL is different single-machine model, the defense are also supposed to be different. **How??**
- The key issue in backdoor in FL is **how to survive the averaging**, and probably **how to survive the defense**.
- Methods evades federate learning defense:
  - Constraint-and-scale. Test the model with anomaly detection loss
  - Train-and-scale. consider magnitudes of model weights.

