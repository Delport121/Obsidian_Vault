# 1) State Estimation
![[Pasted image 20240611085554.png|450]]
## Dead reckoning
- Calculate current position of the car based on previous position and inputs. 
- There is uncertainty in the outputs and error accumulate over time.
# 2) Probability and Bayes Rule
## Bayes rule
![[Pasted image 20240325095014.png|150]]
![[Pasted image 20240325095043.png|500]]
![[Pasted image 20240611085722.png]]
## Law of total probability
![[Pasted image 20240611091015.png]]
## More evidences -> More conditions
![[Pasted image 20240611090955.png]]
# 3) Recursive Bayes filter
## Hidden Markov Model
![[Pasted image 20240325102332.png|500]]
Markov property: Conditional independence
## 4) Variant of the bayes filter
- Kalman
- Particle
- EKF