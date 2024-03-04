---  
share: "true"  
---  
# Hybrid Encryption  
![Pasted image 20240119132912.png](./assets/Pasted%20image%2020240119132912.png)  
- Each party creates a separate _key pair_, (public key, private key).  
- If Alice knows Bob’s public key, she can encrypt a message using his public key (eB) and only Bob can decrypt the message using his private key (dB).  
    - c = EeB(m)  
    - m = DdB(c)  
- Bob _must_ keep his private key secret, otherwise anybody could decrypt his messages.  
- Standard public key cryptography algorithm is called RSA — provides computational security  
- Typically use padding with RSA to turn a deterministic encryption into one that incorporates some randomness. A common standard is PKCS#1 v2.  
