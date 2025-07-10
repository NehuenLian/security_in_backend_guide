## 8. Conclusion on Security Layers

On the web, there are at least four main security layers that work together to protect data and communications:

1. **X.509 Certificate:** Identifies and legitimizes the server through a chain of trust signed by a Certificate Authority (CA).  
2. **TLS Encryption (HTTPS):** Protects communication between client and server using asymmetric encryption for secure key exchange and symmetric encryption for data transmission.  
3. **Token Signing (HMAC, RSA):** Ensures the integrity and authenticity of tokens used to validate requests and sessions.  
4. **Password Hashing (with SALT) and Encryption at Rest:** Protects stored user credentials and sensitive data to prevent unauthorized access.

### Common Methodology to Validate Legitimacy

- In **symmetric encryption**, strings or signatures are recalculated using the same shared secret key.  
- In **asymmetric encryption**, signatures are recalculated using the public key, without exposing the private key.
