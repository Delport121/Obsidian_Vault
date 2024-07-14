#State_estimation #Bayes_rule #Lectures
# 1) State Estimation
![[Pasted image 20240611085554.png|450]]
## Dead reckoning
- Calculate current position of the car based on previous position and inputs. 
- There is uncertainty in the outputs and error accumulate over time.
# 2) Probability and Bayes Rule
## Bayes rule
![[Pasted image 20240612111149.png]]
Consider a standard Venn Diagram. Conditional probability allows us to write the following:
$$ P(A|B) = \frac{P(BnA)}{P(B)} $$
$$ P(B|A) = \frac{P(BnA)}{P(A)} $$

Bayes' Theorem can then be expressed as by combining the above two equations: $$ P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)} $$ where: 
- \(P(A|B)\) is the probability of \(A\) given \(B\). 
- \(P(B|A)\) is the probability of \(B\) given \(A\). 
- \(P(A)\) is the probability of \(A\). 
- \(P(B)\) is the probability of \(B\).

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
The term Markov property refers to the memoryless property of a stochastic process, which means that its future evolution is independent of its history
## Bayes Filter
![[Pasted image 20240611214143.png]]
![[Pasted image 20240611214223.png]]
### Practical issues 
![[Pasted image 20240611214255.png]]
## Variants of the bayes filter
- Kalman
- Particle
	- Monte Carlo/Particle localization
- EKF