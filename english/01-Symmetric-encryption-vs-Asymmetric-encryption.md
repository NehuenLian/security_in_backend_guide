## Symmetric vs Asymmetric Encryption

There are several types of encryption, but symmetric and asymmetric are the most commonly used in the context of the web. Remembering that encryption uses a key to encrypt and decrypt, we have:

### Symmetric Encryption

Symmetric encryption involves using a single key to both encrypt and decrypt information. All messages encrypted with this key require the same key to be decrypted.

In architectures like microservices, this is referred to as a **“shared symmetric key”**, since all microservices need the key to communicate, encrypt, and decrypt messages. In contrast, in monolithic architectures or with a single server, the server handles encryption and decryption without needing to share the key, because there are no other actors that require it.

This concept is often misunderstood, as symmetric encryption is frequently introduced using microservice examples.

### Asymmetric Encryption

Asymmetric encryption involves two keys instead of one: a public key and a private key.

**How are these keys generated?**  
They are generated from certain mathematical parameters, depending on the chosen encryption algorithm. Both keys are generated together when the algorithm is applied. They are mathematically linked and follow this dynamic:

- The private key is kept secret.  
- The public key can be shared with any node/microservice.

The key idea of asymmetric encryption is that the public key can only be used to encrypt information, but it cannot decrypt it. Only the entity with the private key can decrypt the data.
