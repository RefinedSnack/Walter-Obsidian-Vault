---  
share: "true"  
---  
# Block Cipher  
  
Takes blocks of items and encodes   
Modes are required to prevent frequency analysis  
  
Modes help us to relate those modes to each other  
  
### ECB Mode  
  
- Electronic Code Book  
- Not recommended due to its weaknesses  
![Pasted image 20240119130604.png](./assets/Pasted%20image%2020240119130604.png)  
  
### CBC mode  
  
- Cipher Block Chaining  
- blocks are chained together  
- uses an Initialization Vector to make sure each message is unique, should be random  
- encryption must be done sequentially by block  
- message must be padded to a multiple of the block size  
  
![Pasted image 20240119130551.png](./assets/Pasted%20image%2020240119130551.png)  
  
### CTR mode  
  
- Counter  
- uses a non-repeating counter  
- nonce is an initialization vector  
- for a given AES key, do not re-use the same nonce  
- the counter is encrypted and then XORed with the plaintext to produce ciphertext  
- turns a block cipher into a stream cipher, since each bit of the plaintext is individually XORed with the encrypted counter  
- encryption and decryption can be done in parallel  
  
![Pasted image 20240119130707.png](./assets/Pasted%20image%2020240119130707.png)