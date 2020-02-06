# Targeted Clean-label Poisoning Attack

## Summary

This paper presents a new tactic to implement target attach without access to the training dataset, but with model structure. The idea is to find a trustable base instance and mimic the instance to create a fake instance whose representation (output) is close enough to the instance with target label. The poisoning instance is calculated by solving

$$p = argmax_{\mathbf{x}}||f(x) - f(t)||_{2}^{2} + \beta||x - b||$$.

This paper also discusses the difference between attacking transferring learning and end-to-end learning. Briefly put, attack to transferring learning is easier since the amount of learnable weights are small. The result of the attack will change the decision boundary. In the end-to-end case, the attack changes the representation of shadow layer, but the boundary remains unchanged.

The problem arises in the end-to-end attack. The attacker wants to create poisoning instance that are close to target instance but labeled as base instance. After retraining the model on poisoned data, the model can learn the difference between poisoned instance and target instance, even though they are close. As a result, the higher layer representation, they are not close anymore. To solve the problem, the author adds target instance as watermark on poisoning instance.

## Takeaway

- The idea of mimic instance, but without changing label to attack models
- The difference between shadow layer representation and deeper layer representation. The instances that are inseparate in shadow layer representation can be separate in deeper layer representation provided that their labels are different
- The attack to transferring learning might change the decision boundary since the shadow layer are fixed; the attack to end-to-end model might change the shadow layer representation while keeps decision boundary unchanged. 