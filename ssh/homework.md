1. Secure Shell (SSH) is a widely used protocol for securely accessing remote servers over an unsecured network and It is a combination of cryptographic techniques.

2. Asymmetric Cryptography in SSH Authentication

SSH uses asymmetric cryptography during the authentication phase.

Concept

Asymmetric cryptography uses a pair of keys:

A public key (shared with servers)
A private key (kept securely on the client machine)

These two keys are mathematically related but cannot be derived from each other.

How SSH uses it
The user generates an SSH key pair locally.

The public key is copied to the server and stored in:

~/.ssh/authorized_keys
When a connection is initiated:
The server sends a challenge
The client proves ownership of the private key by responding correctly
The server verifies this using the stored public key
Key Security Insight
The private key never leaves the client device
Even if the public key is exposed, it cannot be used to log in
This method eliminates password-based attacks such as brute force and credential stuffing
3. Symmetric Cryptography in SSH Session Security

After authentication is completed, SSH switches to symmetric cryptography for the rest of the session.

Concept

Symmetric cryptography uses a single shared secret key for both encryption and decryption.

How SSH uses it
After successful authentication, client and server negotiate a session key
This session key is used to encrypt all communication during the session
Both directions (client → server and server → client) use the same key
Common Algorithms
AES (Advanced Encryption Standard)
ChaCha20-Poly1305 (modern and high-performance encryption)
Why SSH switches to symmetric encryption
Asymmetric encryption is computationally slow
Symmetric encryption is much faster and suitable for continuous data exchange
Each SSH session uses a temporary key, improving security through key rotation
4. Practical Implementation: Securing Web Infrastructure Lab Servers
Objective

To secure the following servers:

web-01
web-02
lb-01

by:

Enabling SSH key-based authentication
Disabling password authentication (pass123 or any password login)