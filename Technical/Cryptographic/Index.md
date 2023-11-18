
Cryptographic refers to the practice of secure communication in the presence of third parties. The process involves the use of mathematical algorithms to transform data into a form that is unreadable to unauthorized users.

Cryptographic techniques are used to ensure the confidentiality, integrity, and authenticity of data in electronic communication. This includes securing sensitive information such as personal data, financial transactions, and military intelligence.

There are two main types of cryptographic techniques: symmetric and asymmetric. In symmetric cryptography, the same key is used for both encryption and decryption. Asymmetric cryptography, on the other hand, uses a pair of keys - a public key for encryption and a private key for decryption.

Some of the popular cryptographic algorithms used today include Advanced Encryption Standard (AES), Rivest-Shamir-Adleman (RSA), and Secure Hash Algorithm (SHA).

In addition to electronic communication, cryptography is also used in other areas such as password protection, digital signatures, and blockchain technology.

Overall, the use of cryptographic techniques is essential in maintaining the security and privacy of data in modern communication.

Asymetric crypto
1. Public key
    
    It’s used to encrypt message
2. Private key
    
    It’s used to decrypt message that encrypted by public key
    
    Can create a digital signature for a document or message. The signature verifies the authenticity and integrity of the content, ensuring that it has not been tampered with during transmission.


## HS256 (HMAC SHA-256) vs RS256 (RSA SHA-256)

- HS256 (HMAC SHA-256): This algorithm uses a symmetric key (a shared secret) to both sign and verify the JWT. It relies on the SHA-256 cryptographic hash function to generate the signature.
- RS256 (RSA SHA-256): This algorithm uses asymmetric key pairs (public and private keys) to sign and verify the JWT. It uses the RSA cryptographic algorithm with SHA-256 for the digital signature.

- These algorithms are widely supported and used in various JWT implementations. **HS256** is often used when the JWT is intended for communication between components of the **same system** or **trusted parties with a shared secret**.
- On the other hand, **RS256** is commonly used for scenarios involving communication between **different systems** or when the JWT needs to be **publicly verifiable**.