# Justification-Based Reliability in Machine Learning

> label: ML Interpretability; Prediction Confidence

## 1. Abstract

- This paper proposes a model agnostic method for trained model to calibrate the prediction confidence, based on Justification-based Reliability from epistemology. The confidence is derived by classifying the prediction into different confidence region based on the predictions of input's neighbors. High confidence means the neighbors of input leads to the same category as the input.  
- The parameters for this method is the radius of neighborhood or the number of closest instances to be considered. The objective of parameter learning is to maximize the coverage of high confidence region, instead of accuracy. The optimization for ParameterSelection function can be accomplished with grid search or by using [Bayesian optimization (BO)](https://en.wikipedia.org/wiki/Bayesian_optimization). 
- The experiment shows that the proposed method outperforms benchmark, threshold softmax model, by large margin when samples are overlapping and suffer large noises. 


## 2. Features
- Support construction can be conducted in hidden layers as well. 
- The support construction is derived from comparing input and output of **each layer**, instead of input and ultimate output.

- Parameters for support construction is **Endogenetic**,  i.e., learned during training. 
- Justification-Based Reliability system is built and learned on a trained model. 
- Similar Method:  Threshold Softmax Function
- Support different distances 


## 3. Limitation

- Searching for neighbors is computationally expensive when the dimension goes high. Potential solution: Locality-sensitive hashing. 
- The closeness of semantic distance between points and the mathematically-convenient $l_2$-norm distance metric is **unavailable** in input and early layers. **The influence of different distance???**
- This method requires the sample is dense in the space, otherwise you cannot find neighbors in most case. Curse of dimensionality requires huge sample size. 


## 4. Insight and Inspiration
- Neighbor as the building block for confidence
- Category confidence V.S. Numerical confidence
- Neighborhood radius shift between different layers. 
  