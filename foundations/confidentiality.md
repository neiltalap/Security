# Confidentiality

Confidentiality ensures that only authorized parties can view data, typically enforced via **Encryption** when data is transmitted over insecure channels.

## Encryption Approaches

### Symmetric (Shared Key)
- **Mechanism:** All parties share the same key.
- **Pros:** Fast and efficient.
- **Cons:** Key management is difficult (how do you share the secret securely?).

### Asymmetric (Public Key)
- **Mechanism:** Each party has a Public/Private key pair. Encrypt with the recipient's Public key; decrypt with the recipient's Private key.
- **Pros:** Solves key distribution; proves sender identity.
- **Cons:** Computationally expensive. usually used only to exchange a temporary symmetric key.

## Ciphers

### Block Ciphers
Encrypt fixed-size blocks of data.
- **ECB (Electronic Code Book):** Encrypts each block independently. **INSECURE** (identical patterns in plaintext appear in ciphertext).
- **CBC (Cipher Block Chaining):** XORs each block with the previous one. **SECURE** (standard for fixed-block encryption).

### Stream Ciphers
Encrypt arbitrarily sized data streams (often used for network sockets).
- **CTR (Counter Mode):** Turns a block cipher into a stream cipher. Efficient and secure (no padding needed).

### Initialization Vectors (IV)
A "dummy" block used to randomize the encryption process.
- **Requirement:** Must be **unique** for every encryption operation with the same key.
- **Vulnerability:** **IV Reuse** is a critical flaw that can allow attackers to decrypt data.

## Key Exchange
Protocols to safely exchange keys over an open network (RSA, Diffie-Hellman, El Gamal).
- **Risk:** Must be authenticated to prevent Man-in-the-Middle (MITM) attacks (e.g., using PKI/Certificates).

## Common Vulnerabilities

### 1. Storing Sensitive Data Unnecessarily
A major design flaw is maintaining sensitive data without a valid requirement.
- **Passwords:** Validating a password does **not** require storing it in clear text. Store a hash instead.
- **Data Minimization:** Designs must properly classify data sensitivity and store only what is absolutely required.

### 2. Lack of Necessary Encryption
Failing to encrypt data traversing hostile environments.
- **Data in Transit:** Clear-text communication over public/untrusted networks (e.g., using TELNET) is a critical vulnerability.
- **Data at Rest:** Sensitive database fields or files on disk should be encrypted to protect against physical theft or unauthorized access.

### 3. Homemade Encryption
The primary cause of confidentiality vulnerabilities. Encryption is mathematically complex; developers often incorrectly implement "simple" logic that is trivially breakable (e.g., Checkpoint FWN/1 replay attack). **Always use established, vetted libraries.**

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
