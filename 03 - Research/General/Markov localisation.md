Markov localisation is the straight forward application of the Bayes filter to the localisation problem. It addresses the global localisation problem , the position tracking problem and the kidnapped robot problem in static environments. Which of these three issues it solves depends on how the filter is initialised.

The EKF and UKF falls under this type of localisation. Both version uses features and landmarks as a basis for localisation. (It uses feature-based maps)
## Extended Kalman filter
### Estimating correspondences
In practice it is rarely possible that landmark correspondences can be determined with absolute certainty. There most implementation determine the identity of a landmark during localisation.

The most simple implementation of the is the [[Maximum likelihood correspondence]] in which one first determine the most likely value of the correspondence variable. This technique is brittle however h when there are many equally hypotheses for the correspondence variable
# Practical considerations
