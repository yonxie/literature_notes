# On Calibration of Modern Neural Networks

## 1. Abstract

This paper provides a brief review on the approaches of calibrating confidence of prediction. The essence of these methods are dividing the output into several groups and calculate the accuracy of each group, which is take as confidence for future prediction. The variants on the way of dividing and calculation the confidence yield different calibration methods.

This paper also offers the observed conclusion on the relationship between prediction confidence and model structure. 

## 2.  Method of Calibration

- **Histogram Binning**. Divide the output into fixed number of groups, and calculate the accuracy of each group as the calibrate confidence for that group.
- **Isotonic Regression** shares the same idea with Histogram Binning, but goes further on the group division. More specifically, the division is also the parameters to learn. 
- **Bayesian Binning into Quantiles (BBQ)** also views partition and confidence (accuracy) as parameters to learn. However, it believes they follow certain priors and update in Bayesian manner. 
- **Platt Scaling**, on the contrary, functions by finding a mapping between network output to probability, via logistic regression.
- Methods in other vein are also discussed in the paper.

## 3. Takeaways

- To some extent, I don't believe the relationship between prediction confidence and NN output is stationary. How to explain the outputs lying in certain range hit a lower prediction accuracy? 
- **Model capacity is negatively correlated with prediction confidence**, based on the result of this paper.
- Robust NN can be done by punishing overconfident prediction
- Ensemble NN might be the most straightforward way of calibrating uncertainty.
- **Confidence Bayesian NN**.

