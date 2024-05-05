# RSA (Rivest-Shamir-Adleman)
## RSA Encryption Algorithm

RSA (Rivest-Shamir-Adleman) is a widely used asymmetric encryption algorithm for secure communication over an insecure channel. Here are the steps involved in RSA:

### 1. Key Generation:
   - Choose two distinct prime numbers, p and q.
   - Compute n = p * q.
   - Calculate the totient φ(n) = (p - 1) * (q - 1).
   - Choose an integer e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1. This is the public exponent.
   - Compute the private exponent d, such that (d * e) % φ(n) = 1.
   - The public key is (n, e) and the private key is (n, d).

### 2. Encryption:
   - Convert the plaintext message into an integer m, where 0 < m < n.
   - Compute the ciphertext c = m^e mod n.

### 3. Decryption:
   - Given the ciphertext c, compute the plaintext message m = c^d mod n.

RSA relies on the mathematical properties of modular exponentiation and the difficulty of factoring large composite numbers to provide security. It ensures that while the public key can be freely distributed for encryption, only the holder of the corresponding private key can decrypt the message.

## RSA Example with p = 3 and q = 5
```plaintext
Given:
- p = 3
- q = 5

1. Key Generation:
   - Compute n = p * q = 3 * 5 = 15.
   - Calculate φ(n) = (p - 1) * (q - 1) = (3 - 1) * (5 - 1) = 2 * 4 = 8.
   - Choose a public exponent e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1. Let's choose e = 3.
   - Compute the private exponent d, such that (d * e) % φ(n) = 1. In this case, d = 3, as (3 * 3) % 8 = 1.
   - Public key (n, e) = (15, 3)
   - Private key (n, d) = (15, 3)

2. Encryption:
   - Suppose we want to encrypt the plaintext message m = 10.
   - Compute the ciphertext c = m^e mod n = 10^3 mod 15 = 1000 mod 15 = 10.

3. Decryption:
   - Given the ciphertext c = 10, compute the plaintext message m = c^d mod n = 10^3 mod 15 = 1000 mod 15 = 10.
```
So, the original plaintext message (m = 10) is successfully encrypted to ciphertext (c = 10) and decrypted back to the original plaintext message (m = 10) using RSA encryption and decryption with p = 3 and q = 5.


