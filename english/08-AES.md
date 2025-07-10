## 8. AES

AES (Advanced Encryption Standard) is a widely used encryption algorithm to protect data. It is a common standard for encrypting HTTP communication asymmetrically, as we saw before in TLS.

However, another of its main uses is encrypting data at rest, known as **encryption at rest**. In this case, AES is used **symmetrically** to protect data whose original content must be recoverable, like names, card numbers, etc. This means they can’t simply be hashed, as with passwords.

### How is AES applied to encrypt data at rest?

1. The server takes sensitive data before storing it.  
2. It uses an AES key to encrypt the data.  
3. It saves the encrypted data in the database.  
4. When it is necessary to access that data, it is decrypted using the same key.

### Considerations

- The AES key must be protected; if leaked, everything encrypted with that key can be decrypted.  
- Nowadays, to increase security, the key is usually stored in specialized external services, like **AWS KMS** or **Azure Key Vault**, to isolate it further.
