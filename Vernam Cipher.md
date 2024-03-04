---  
share: "true"  
---  
# Vernam Cipher  
  
- If using a random stream of bits for the key, and never reuse the same key, this is a _one-time pad_.  
- A one-time pad is information-theoretically secure for confidentiality: “even given unlimited computing power and time, an attacker without the key cannot recover plaintext from ciphertext”.  
- Useful in theory! Try to approach its level of security.  
- In practice, we try to have [Computational Security](./Computational%20Security.md), meaning protection against an attacker with fixed resources, unable to brute force keys chosen from a large space.  
- Has no integrity.  
