# Cryptography

## What is cryptography?
Cryptography is the practice and study of techniques for secure communication in the presence of third parties or adversaries. It involves creating mathematical algorithms for encrypting and decrypting data to ensure confidentiality, integrity, and authenticity. Cryptography is used in various applications such as securing communication channels, protecting sensitive information, authenticating users, and verifying the integrity of data.

## Symmetric Key Algorithms
Symmetric key algorithms, also known as secret key algorithms, are cryptographic techniques that use the same key for both encryption and decryption of data. In these algorithms, the sender and receiver must share the same secret key to communicate securely. Symmetric key algorithms are typically faster and more efficient than asymmetric key algorithms but require a secure method for key distribution.

Examples of symmetric key algorithms include:

1. Advanced Encryption Standard (AES)
2. Data Encryption Standard (DES)
3. Triple DES (3DES)
4. Blowfish
5. Twofish

These algorithms are widely used in various applications such as data encryption, secure communication protocols, and disk encryption.

![image](https://github.com/Rohail30/Blockchain/assets/96627590/cfaf671f-0019-44bd-850f-908ea566e0c2)

#### In symmetric key cryptography, there are two main types of encryption algorithms: block ciphers and stream ciphers.

1. **Block Ciphers:**
   - Block ciphers encrypt data in fixed-size blocks, typically 64 or 128 bits in length.
   - They operate on blocks of plaintext and produce blocks of ciphertext of the same size.
   - Block ciphers use a key to perform encryption and decryption, and the same key is used for both operations.
   - Examples of block ciphers include AES (Advanced Encryption Standard), DES (Data Encryption Standard), and 3DES (Triple DES).

2. **Stream Ciphers:**
   - Stream ciphers encrypt data one bit or byte at a time, typically by XOR-ing the plaintext with a keystream generated from the key.
   - They are often used for real-time communication or situations where data arrives continuously.
   - Stream ciphers are generally faster than block ciphers for encrypting data on a bit-by-bit basis.
   - Examples of stream ciphers include RC4 (Rivest Cipher 4) and A5/1 used in GSM mobile phone networks.

Both block ciphers and stream ciphers have their advantages and disadvantages, and the choice between them depends on the specific requirements of the application and the desired level of security.

## Asymmetric Key Algorithms
Asymmetric key algorithms, also known as public-key cryptography, are cryptographic techniques that use two different keys for encryption and decryption: a public key and a private key. Each key performs a unique function:

1. **Public Key:**
   - The public key is widely distributed and used for encryption by anyone who wants to send a message to the owner of the corresponding private key.
   - Messages encrypted with the public key can only be decrypted by the corresponding private key.

2. **Private Key:**
   - The private key is kept secret and known only to the owner.
   - It is used for decrypting messages that were encrypted with the corresponding public key.
   - Private keys are never shared or distributed.

Asymmetric key algorithms provide several advantages, including secure key exchange, digital signatures, and secure communication over insecure channels. They are commonly used in various cryptographic applications such as secure email, digital signatures, and SSL/TLS for securing web communication. Use of asymmetric systems enhances the security of communication however; it consumes CPU resources heavily. 

Examples of asymmetric key algorithms include:

1. RSA (Rivest-Shamir-Adleman)
2. Diffie-Hellman key exchange
3. Elliptic Curve Cryptography (ECC)
4. Digital Signature Algorithm (DSA)
5. ElGamal Encryption

These algorithms play a crucial role in modern cryptography and are fundamental to ensuring secure communication and data protection in digital environments.

![image](https://github.com/Rohail30/Blockchain/assets/96627590/7e141632-d2a5-4fff-ac37-3320cc727a56)

## Cryptographic Hash Functions
Cryptographic hash functions are mathematical algorithms that take an input (or 'message') and produce a fixed-size string of characters, known as a hash value or digest. These functions are designed to be fast to compute and irreversible, meaning it's computationally infeasible to reverse-engineer the original input from the hash value.

## Digital Signatures
A digital signature is a cryptographic technique used to authenticate the sender of a digital message or document and ensure its integrity. It provides a way for the recipient to verify that the message was indeed sent by the claimed sender and has not been altered during transmission.

Here's how digital signatures work:

**Signing:** The sender generates a digital signature by applying a cryptographic algorithm to the message or document they want to send. This algorithm uses the sender's private key to create a unique digital fingerprint, known as the signature.

**Verification:** The recipient of the message uses the sender's public key (which is freely available) to verify the digital signature. The recipient applies the same cryptographic algorithm to the received message and compares the resulting signature with the one provided by the sender.

**Authentication:** If the digital signature matches the calculated signature, and the sender's public key successfully decrypts the signature, the recipient can be confident that the message was indeed sent by the claimed sender and has not been altered in any way during transmission. This process ensures the authenticity and integrity of the message.

![image](https://github.com/Rohail30/Blockchain/assets/96627590/212670ef-5aa9-4743-8c64-95e1ce1d3f78)

Key characteristics of digital signatures include:

**Authentication:** They provide proof of the identity of the sender.
**Integrity:** They ensure that the message has not been tampered with or altered during transmission.
**Non-repudiation:** The sender cannot later deny sending the message, as their private key is used to create the signature.
**Security:** Digital signatures rely on the strength of cryptographic algorithms and the secrecy of private keys to prevent forgery and unauthorized access.

Digital signatures are widely used in various applications, including electronic transactions, email communication, digital contracts, legal documents, and blockchain technology. They provide a secure and reliable way to verify the authenticity and integrity of digital messages and documents in the digital world.

## Modern Encryption
Each encryption algorithm has advantages and convenient therefore Modern Encryption associates both symmetric and asymmetric techniques. Modern algorithm uses a session key (temporarily key) to encrypt information with symmetric cryptography. Next, the session key encrypted with the public key of the recipient. To unencrypt information, first the recipient unencrypts the session key with his private key and unencrypt information with the session key.

![image](https://github.com/Rohail30/Blockchain/assets/96627590/57a17e49-371c-4180-8547-63e994134af6)

On the sender side, following actions performed:
1. A temporarily key called session key (Ks) generated;
2. Information encrypted with session key (Ks);
3. (Ks) Encrypted with the public key (Kpu) of the recipient. This key called Kse;
4. Kse added to the encrypted information file. This file sent to the recipient.
   
On the recipient side, the below action performed:
1.	The encrypted information and Kse are separated;
2.	The Kse key is unencrypt with the private key (Kpr) of the recipient and becomes the Ks;
3.	The document is unencrypted with Ks.

## Encryption and Digital Signature Operation

![image](https://github.com/Rohail30/Blockchain/assets/96627590/2af0a3c0-9afe-440e-878a-028b935000d6)

When the signature and encryption used together, the signing process done first. Following steps performed:
1. A digest is created from the initial information;
2. This thumbprint is encrypted with the private key (Kprg);
3. The thumbprint is added to the initial information (in the same file);
4. A temporarily session key is generated (Ks) It will be used to encrypt initial information;
5. The session key is encrypted (Kse) with the public key of the rececipient (Kpub);
6. Kse added to encrypted information file. So this file is contains the encrypted information, the Kse and the signature.
   
When the recipient receives the file from the issuer, it begins by unencrypt file and next to verify the signature:
1. The recipient extract the Kse from the received file. This key is unencrypt with the private key (Kprb) to obtain session key (Ks);
2. Ks is used to unencrypt information;
3. Next recipient extract the encrypted thumbprint;
4. The public key (Kpug) is used to unencrypt the thumbprint;
5. In the same time, the recipient creates a digest from the previously unencrypted information;
6. To finish, the recipient compares the unencrypted thumbprint with the digest generated from unencrypted information. If they match, the signature verified.


