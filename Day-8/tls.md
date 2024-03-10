## TLS Certificates

TLS certificates are used to secure the communication between the Kubernetes components and the communication between the client and the server.

### Symmetric and Asymmetric Encryption

- Symmetric encryption involves the same key for both encryption and decryption.
- Asymmetric encryption involves a pair of keys, a public key for encryption and a private key for decryption.

#### Use cases of Symmetric and Asymmetric Encryption

- If a Client makes a first request to the server, the server will send the public key to the client.
- The client will use the public key to encrypt the symmetric key and send it to the server.
- The server will use the private key to decrypt the symmetric key.
- Then the server and client will use the symmetric key for further communication.
- Thus way the symmetric key is secure. No hackers can get the symmetric key.

### How the Client Verifies the Server

- We already know that the server sends the public key to the client.
- But how the client verifies the server?
- The client verifies the server using the Certificate Authority (CA).


### How Certificate Authority (CA) Works

- The CA is a trusted third party that signs the server's public key.
- CA has its own public key and private key.
- CA signs the server's public key using its private key.
- Then the client uses the CA's public key to verify the server's public key. Normally the CA's public key is already installed in the client's machine.
- The client uses the CA's public key to verify the server's public key.
- If the server's public key is signed by the CA, then the client will trust the server's public key.

### How the Server Verifies the Client

- The server verifies the client using the client's public key. Same as the client verifies the server using the server's public key.
- The client sends the public key to the server.
- The server verifies the client's public key using the CA's public key.
- If the client's public key is signed by the CA, then the server will trust the client's public key.

### Public Key Infrastructure (PKI)

- The combination of the above two processes is called Public Key Infrastructure (PKI).

### Private and Public Keys Format

- Private Keys will end with `.key` extension or `-key.pem` extension.
- Public Keys will end with `.crt` extension or `.pem` extension.

Date of Commit: 10/04/2024