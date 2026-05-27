#tls #handshake #termination #ssl 
```table-of-contents
```
# RSA TLS Handshake diagram
![[TLS Handshake.excalidraw | 800x800]]

# Terminologies
1. PlAINTEXT: plain text
2. CIPHERTEXT: the plain text after encrypted using secret and public key
3. session key: The key which is created from client & server random number and pre-master secret then encrypted by the server public key
4. Cipher suites: AES-GCM, ...
5. SSL Termination: This is the process of encrypting/decrypting traffic at the intermediary device such as proxy/ load balancer before forwarding the real data to the backend server.
6. mTLS: Both client and server must send their own certificate, and server have to verify the client certificate using the client public key.
7. RSA Key exchange: Client sends the encrypted pre-master key, server use private key to decrypt. The server private key can be hacked and used to re-generate the session key to encrypt messages which are recorded by hacker before.
8. Diffie-Hellman (DH protocol): Not exchange random numbers, they exchange the public keys which are generated from their big random numbers. From that, they can calculate to the pre-master key using Diffie-Hellman algorithm. And the random numbers are existed on RAM only, so the hackers cannot get that to re-gen the pre-master key.
9. Diffie-Hellman (DH protocol) can be break by quantum machine in the future, now we have more algorithms using PQC (post-quantum) for the safety.
10. PFS (Perfect Forward Secrecy): The past sessions cannot be decrypted in the future if the private key got hacked. It's specification of Diffie-Hellman Ephemeral (DHE hoặc ECDHE)

# TLS versions
- The standards of each TLS version has been upgraded to remove weak encrypting/hashing algorithms to ensure the connection safety. 
- At the moment the TLS 1.3 is the strongest version and TLS 1.2 is enough to use for the temporary safety