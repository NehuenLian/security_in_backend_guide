## 2. X.509 Certificate

An X.509 certificate is a credential used to identify an entity (such as a server). Besides ensuring that the server is legitimate, it also serves to encrypt communication and sign data to guarantee its authenticity.

The certificate is issued and signed by an entity called a **Certificate Authority (CA)**, and there are several around the world.

- Physically, a CA is also a server or a set of servers that operate under very strict security policies to issue certificates.

When a client (like a browser) wants to connect to a server, during the **Handshake** process, the server sends its certificate to the client, and the client verifies it.

### How is the certificate verified?

All browsers have a stored list of CAs that they consult to check the legitimacy of the received certificate.

### Verification process within the Handshake (simplified):

1. The client starts with a `ClientHello`.  
2. The server responds with a `ServerHello` and sends its certificate.  
3. The client verifies that the certificate is valid by consulting the stored CAs.  
4. If everything is fine, the Handshake process continues to establish and encrypt the session.

### Cryptographic operation of the X.509 certificate

It is an asymmetric encryption mechanism that works with a public key and a private key.

- The public key is embedded in the X.509 certificate.  
- The private key is kept on the server. This is the asymmetric key pair.

The CA issuing the certificate has its own private key and uses it to sign the certificate. This signature is the result of hashing the certificate data plus the CA’s private key.

The client calculates the hash of the received certificate content and uses the CA’s public key to verify the accompanying digital signature. If the verification succeeds, it means the certificate is valid and was signed by a trusted CA.

### Tip

- Sometimes the server’s certificate is not directly signed by a root CA but by an intermediate CA. In that case, the server also sends the chain of intermediate certificates so the client can build the “chain of trust” up to a known root CA.
