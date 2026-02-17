# Authentication

Authentication is the process of determining who a user (or component) claims to be and validating that claim. It is a primary mechanism for enforcing a security policy by identifying trust boundaries.

## Authentication in the Security Policy
Authentication establishes the identity of a peer (human or software) when initiating communication.

### Centralized vs. Decentralized Authentication
- **Best Practice:** Centralize authentication to ensure that *every* request within a protected domain is validated.
- **Vulnerability (Follow-on Bypass):** Some applications authenticate users only at a "entry" page but fail to enforce it on subsequent pages. This allows persistent interaction without further validation.

---

## Common Design Vulnerabilities

### 1. Lack of Authentication
The most straightforward oversight: failing to require authentication for sensitive information (e.g., exposing corporate accounting data to anyone on the internet). This is often less obvious when dealing with internal, presumably "private" interfaces between peer modules.

### 2. Untrustworthy Credentials
A common mistake where authentication information is presented but the validation is insufficient or the credentials themselves are and easily spoofable. This often occurs when:
- **Client-Side Authentication:** Trusting information sent by a client that an attacker completely controls.
- **Implicit Domain Trust:** Trusting credentials based purely on the reporting of the client system.

#### Examples:
- **SunRPC (`AUTH_UNIX`):** The server trusts the user and group IDs passed by the client without further validation.
- **rexd (Remote Execute Daemon):** Allowed remote users to run programs as regular users (excluding `root`) based purely on client-supplied data.
- **sadmind (Solaris):** A remote root flaw occurred because it treated `AUTH_UNIX` as sufficient validation for running commands on behalf of the client.

---

### 3. Insufficient Validation
Authentication systems can be fundamentally flawed even if they work "correctly" in their intended environment. This often happens in programmatic authentication between systems rather than user-facing login forms.

- **IP-Based Trust:** Many network daemons (`rshd`, `rlogind`, even `sshd`) can be configured to trust a peer based solely on source IP.
    - **Vulnerability:** UDP is trivially spoofed. TCP can be spoofed or hijacked (especially on local networks).
- **One-Way Authentication:** Distributed systems often authenticate only the client or only the server. Attackers can masquerade as the unauthenticated peer to launch attacks.

### 4. Homemade Authentication
Developers often underestimate the complexity of cryptographic protocols and attempt to roll their own.

- **The Fallacy:** "I'll send a challenge, they encrypt it with a shared secret, and I'll verify it."
- **Common Flaws:** Replay attacks, oracle attacks, and weak entropy.

#### Case Study: Checkpoint Firewall-1 (FWN/1)
Thomas Lopatic discovered a vulnerability in the FWN/1 protocol.
- **Protocol:** Peers exchange a random number `R1` and a hash `Hash(R1 + SharedKey)`.
- **The Flaw:** The protocol did not prevent replay. An attacker could simply capture a valid `R1` and `Hash` pair and replay them to the server to authenticate, as the server had no way to know `R1` was "stale."

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
