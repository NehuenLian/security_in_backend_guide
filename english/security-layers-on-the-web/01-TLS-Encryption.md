## Security Layers

Below, I will explain the different security layers from bottom to top, to show how security is built at different levels.

### 1. TLS Encryption

TLS is a cryptographic protocol that operates below the application layer (see OSI model). Its function is to encrypt communications between the client and the server, converting HTTP requests into HTTPS so that the content cannot be easily read or altered.

TLS also works with asymmetric keys: a public key sent to the client, and a private key kept on the server. The public key encrypts the packets sent to the server, and the server uses its private key to decrypt the incoming messages.

TLS is established by validating a secure connection between the client and the server; this process is called the **Handshake**, which will not be deeply covered in this guide.

Within the handshake, there are several steps when establishing the TLS protocol. These steps involve a rather complex key exchange, so I will try to explain it below as clearly as possible.

Once the encryption method to be used for the packets is configured (this is done automatically by the server when negotiating the handshake parameters with the client).

Knowing that the server has both keys (public and private):

1. The client initiates the connection to the server (for example, by entering a site with `https://`).  
2. The server sends its public key to the client.  
3. The client generates a new key, this time a temporary symmetric AES key.  
4. Then, the client encrypts that symmetric key with the server's public key and sends it to the server.  
5. The server uses its private key to decrypt the symmetric key sent by the client.

After this process, the connection is encrypted to securely send requests and receive information.

TLS might seem complex internally, but this happens automatically; developers rarely have to worry about it, as it is handled without manual intervention.

### Relevant Tips

- If decryption fails, it means the key did not come from a legitimate client.  
- If encryption succeeds, it is accepted and from now on all packets will travel encrypted.  
- This entire process happens within the handshake.  
- The security comes from the fact that only the server has the private key to decrypt.
