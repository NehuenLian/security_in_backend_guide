## 7. HMAC

HMAC is a signing algorithm, from the acronym **Hash-based Message Authentication Code**, which uses a secret or shared key (depending on whether the architecture is monolithic or microservices).

It consists of “extracting” parts of the token and performing a series of steps and calculations to add a signature to that token.

### Steps to sign a token with HMAC

1. Take the header and payload, and concatenate them to get a resulting string.  
2. Append the secret key to that resulting string.  
3. Apply a hash function to the result (string + secret key), which will be the token’s signature.  
4. This signature (hash) is added to the token as the `"signature"` attribute value.

Once the token is signed, the server can verify if that token is legitimate when it receives it.

### How does the server verify a token signed with HMAC?

When the server receives a previously signed JWT, it must verify it before approving the request.

The server recalculates the token’s signature by performing the same procedure it used to sign it initially.

If the resulting signature matches the JWT’s signature, it means that token was signed by that server and is therefore legitimate.

---

### Clarification about the “shared key”

In HMAC it is called a “shared key” but this is not always the case.

- In a **microservices** architecture, all microservices must share that key, since all need to validate JWTs and recalculate signatures.  
- In **monolithic** architectures, the key is not shared with anyone; only the single available server has it and uses it to validate received tokens.

This concept follows the same principle as symmetric encryption.
