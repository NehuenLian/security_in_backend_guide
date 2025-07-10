## 3. Tokens and Digital Signatures

### What is a token?

A token is a data object that contains information and acts as an identifier.

They are issued by the server and included in requests (for example, in the header) so the server can verify if the token was issued by itself and, therefore, if the request is legitimate. One of the most common tokens is the **JWT (JSON Web Token)**.

A JWT has three parts, encoded in Base64 format:

1. Header  
2. Payload  
3. Signature

### How is a JWT signed?

When a server issues a JWT, the flow is as follows:

1. The server receives the data.  
2. It creates the token. The issued token will be linked to that user and will be used to identify them.  
3. The server signs the token.  
4. The server sends the token to the client.  
5. The client stores the token (for example, in `localStorage`) and includes it in subsequent requests.  
6. Each time the server receives a request with the token, it verifies the signature and validity.

### How is a token signed?

Signing tokens uses signature algorithms, the most common are:

- **HMAC (symmetric)**  
- **RSA (asymmetric)**  

Both are used depending on the case.
