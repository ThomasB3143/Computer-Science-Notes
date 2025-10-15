Section: [[Cyber Security (Root)]]
# Data Transformation

## Encoding

>[!cite] Definition
>Transforming data from one format to another. Fully **reversible** and **public**
## Hashing

>[!cite] Definition
>Transforming data into a (often) smaller, **fixed** size

a hash $H$ is a function that maps **messages** $m$ to their **hashed** equivalent $h$. A **one-way** scheme cannot compute $m$ from $h$, and a **collision resistant** scheme states that $H(m_1)=H(m_2)\iff m_1=m_2$
## Encryption

>[!cite] Definition
>Transforming data using a **secret** key

Keys are used to **decrypt** and **encrypt** messages. A scheme is **valid** if encrypting and decrypting results in the original message, and is **secure** if a message can only be decrypted with the decryption key
# Public Key Cryptography

1. Recipient (R) computes decryption and encryption keys
2. R sends the encryption key over public domain
3. Sender (S) uses the key to encrypt their message
4. S sends the encrypted message over public domain
5. R retrieves and decrypts the message

Relies on being unable to deduce the decryption key from the encryption key