## 5. RSA

RSA is an **asymmetric** cryptographic algorithm. Although it can be used to encrypt data, in this context we are interested in its application to **digital signatures**, as an alternative to HMAC for signing tokens.

Its purpose and use is the same as HMAC (signing, verification), but its implementation is different.

RSA solves certain limitations of HMAC:

- HMAC requires all services to share the same key (in microservices). This complicates scalability, and if the key is leaked, anyone can sign valid tokens.

As seen in asymmetric encryption, RSA generates a **public key** and a **private key**, mathematically linked.

### RSA signing process

1. Take the JWT payload and generate its hash.  
2. Encrypt the hash using the private key.  
3. The result is added to the token as the `"signature"` attribute.

Now, anyone with the public key can verify tokens without exposing or needing the private key. But only services with the private key can sign tokens.

### Key points

- What is signed with the private key can only be verified using the public key.  
- Responsibility is divided between signing nodes and verifying nodes. Verifiers cannot sign, and signers cannot verify, following the single responsibility principle.  
- If the JWT payload specifies a signing algorithm different from the one defined on the server, it is automatically rejected and not even attempted to be verified, following the *fail-fast* principle. This helps prevent attacks like *algorithm confusion*.  
- RSA is more secure but consumes more resources and computing power.  
- It doesn’t make much sense to use it in monolithic architectures.
