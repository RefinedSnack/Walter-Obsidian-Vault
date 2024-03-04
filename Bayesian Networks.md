---  
share: "true"  
---  
# Bayesian Networks  
  
(1a) The probability that John calls, Mary does not call, the Alarm goes off, that a burglary is occurring, and that no earthquake is occurring.  
  
$P(j,\lnot m,a,b,\lnot e)$  
$P(j|\lnot m,a,b,\lnot e) \times P(\lnot m,a,b,\lnot e)$  
$P(j|\lnot m,a,b,\lnot e) \times P(\lnot m|a,b,\lnot e) \times P(a,b,\lnot e)$  
$P(j|a) \times P(\lnot m|a) \times P(a,b,\lnot e)$  
$P(j|a) \times P(\lnot m|a) \times P(a|b,\lnot e) \times P(b,\lnot e)$  
$P(j|a) \times P(\lnot m|a) \times P(a|b,\lnot e) \times P(b | \lnot e) \times P(\lnot e)$  
$P(j|a) \times P(\lnot m|a) \times P(a|b,\lnot e) \times P(b) \times P(\lnot e)$  
$0.90 \times (1-0.70) \times 0.94 \times 0.001 \times (1-0.002)$  
$0.90 \times 0.30 \times 0.94 \times 0.001 \times 0.998$  
$\approx 0.0002532924$  
  
  
(1b) The probability that John and Mary both call given that a burglary is going on and that no earthquake is happening.  
A is unknown  
$P(j,m|b, \lnot e, a)$  
$\sum_{x=\{a,\lnot a\}} P(j,m|b,\lnot e, x) \times P(x | b, \lnot e)$  
$\sum_{x=\{a,\lnot a\}} P(j|x) \times P(m|x) \times P(x | b, \lnot e)$  
$P(j|a) \times P(m|a) \times P(a | b, \lnot e) + P(j|\lnot a) \times P(m|\lnot a) \times P(\lnot a | b, \lnot e)$  
$0.90 \times 0.70 \times 0.94 + 0.05 \times 0.01 \times (1-0.94)$  
$0.90 \times 0.70 \times 0.94 + 0.05 \times 0.01 \times 0.06$  
$0.5922 + 0.00003$  
$\approx 0.59223$  
  
  
(1c)The probability that an alarm is not on given that an earthquake is happening and no burglary is happening.  
$P(\lnot a | e, \lnot b)$  
$(1 - 0.29)$  
$\approx 0.71$  
  
  
![IMG20240220134357.jpg](./assets/IMG20240220134357.jpg)