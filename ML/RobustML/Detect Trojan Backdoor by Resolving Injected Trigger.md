# Detect Trojan Backdoor by Reversing Injected Trigger

> 1. Neural Cleanse: Identifying and mitigating backdoor attacks in Neutral Networks
>
> 2. TABOR: A highly accurate approach to inspecting and restoring trojan backdoor in AI system

## Summary

This paper proposes a new scheme of detecting backdoor attack by solving a non-convex optimization problem. The objective function is

$$argmin_{trigger}  L(f(x_{trigger}), y_{target})$$.

Correspondingly, by maximizing the objective function, the solver is aimed to resolve the injected trigger, if it does exist. The procedure is summarized as follows.

- Step1: For a given label, treat it as a potential attack target, the find a trigger that misclassifies all samples into this target.
- Step2: Repeat step 1 for each label.
- Step3: Run outlier detection algorithm on those triggers, to detect if any trigger is significantly different than the others.

The difference here between triggers can vary. In paper 1, it’s size. The authors argue that the smaller a resolved trigger is, the more likely it is a true trigger. The intuition behind such argument is that the reverse engineering of trigger can be very bad, especially when there is no triggers at all. 

A few methods also proposed to mitigate the attack:

- Filter for detecting adversarial input. The intuition is based on the fact that infected instances cause higher activation. The author use it as filter. 
- Patching DNN via Neuron Pruning. Rank the difference of activation between clean data and adversarial data. Remove the units associated large difference. 
- Patching DNN via unlearning. Create instances with trigger but right label, and use then to train the trained model. 

Such defense scheme is resilient to different types of attack:

- Complex trigger
- Larger triggers
- Multiple infected labels with separate trigger
- Single infected label with multiple trigger
- Source-label-specific backdoor.

Of course, several constraint can be integrated into the optimization problem. In paper 2, the authors use sparsity and smoothness as additional constraint to get a smooth and compact resolved trigger. The authors observe that the the above defense scheme is futile when the triggers have different size, shape and location. The reasoning here is that when triggers come with such difference, the optimization problem  may encounter more non-interest triggers. **More constraints can be utilized to separate different type of triggers**.  

Besides, the author also consider misclassification as source of penalty. 

The method of question requires access to data set but not model details. The mitigating method may require access to the model. 

## Takeaways

- The most important intuition behind these two papers is that they believe instances with trigger are more vulnerable, and **the trigger always associated with target label, it becomes the dominant factor for the classification result**. That is reason why reverse algorithm works.

- The idea of using reversing features as defense method.

- Different type of attack mitigating technique.

- We can transform optimization problem in a optimization problem into constraints.

  

