---  
share: "true"  
---  
# Bayesian reasoning  
  
  
### Part 1  
1. **Prior Probability (P(C))**: 0.003  
  
2. **Likelihood (P(Pos|C) and P(Pos|~C))**: This is the probability of a positive test result given whether the person has colorectal cancer (C) or not (~C)  
   - P(Pos|C) = 50% = 0.50  
   - P(Pos|~C) = 3% = 0.03  
  
3. **Observation Given**: Positive hemoccult test  
  
Prior Probability ($P(C)$): 0.003  
likelihoods:  
  - $P(Pos|C)$: 0.50  
  - $P(Pos|~C)$: 0.03  
  
$P(Pos)$:  
  $P(Pos) = P(Pos|C) \times P(C) + P(Pos|~C) \times P(~C)$  
  $P(Pos) = (0.50 \times 0.003) + (0.03 \times (1 - 0.003))$  
  $P(Pos) = 0.0015 + (0.03 \times 0.997)$  
  $P(Pos) = 0.0015 + 0.02991$  
  $P(Pos) ≈ 0.03141$  
  
Posterior probability:  
  $P(C|Pos) = \frac{P(Pos|C) \times P(C)}{P(Pos)}$  
  $P(C|Pos) = \frac{0.50 \times 0.003}{0.03141}$  
  $P(C|Pos) ≈ \frac{0.0015}{0.03141}$  
  $P(C|Pos) ≈ 0.0477$  
  
Finally, the probability of not having colorectal cancer given a positive test:  
  $P(~C|Pos) = 1 - P(C|Pos)$  
  $P(~C|Pos) = 1 - 0.0477$  
  $P(~C|Pos) ≈ 0.9523$  
  
  
So, the probability that the person actually has colorectal cancer given a positive hemoccult test is approximately 0.0477, and the probability that the person does not have colorectal cancer is approximately 0.9523.  
  
  
### Part 2  
  
#### Q1  
1. **Total Population**: 10,000 people  
2. **People with Colorectal Cancer (CRC)**: 30 out of 10,000  
3. **People with Positive Hemoccult Test given CRC (True Positive)**: 15 out of 30  
4. **People without CRC (Non-CRC)**: 10,000 - 30 = 9,970 people  
5. **People with Positive Hemoccult Test given Non-CRC (False Positive)**: 3% of 9,970, which is approximately 299 people  
  
Number of True Positives=15  
  
#### Q2  
  
I think it is much easier to do the second approach, it is simpler and more concrete  
  
#### Q3  
  
I would explain it as such: "You are in a group of about 300 people. In that group many of them received a positive but do not actually have cancer. You have approximately a 5% chance of having cancer. It is low and we can increase certainty by performing other tests."  
  
