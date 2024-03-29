# RSA
# RSA Encryption Algorithm

RSA (Rivest-Shamir-Adleman) is a widely used asymmetric encryption algorithm for secure communication over an insecure channel. Here are the steps involved in RSA:

## 1. Key Generation:
   - Choose two distinct prime numbers, p and q.
   - Compute n = p * q.
   - Calculate the totient φ(n) = (p - 1) * (q - 1).
   - Choose an integer e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1. This is the public exponent.
   - Compute the private exponent d, such that (d * e) % φ(n) = 1.
   - The public key is (n, e) and the private key is (n, d).

## 2. Encryption:
   - Convert the plaintext message into an integer m, where 0 < m < n.
   - Compute the ciphertext c = m^e mod n.

## 3. Decryption:
   - Given the ciphertext c, compute the plaintext message m = c^d mod n.

RSA relies on the mathematical properties of modular exponentiation and the difficulty of factoring large composite numbers to provide security. It ensures that while the public key can be freely distributed for encryption, only the holder of the corresponding private key can decrypt the message.
