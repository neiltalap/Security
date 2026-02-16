# Trust and Assumptions

Vulnerabilities often arise when designers and developers make unfounded assumptions or extend misplaced trust to system components or external entities.

## Trust Relationships
Different components in a system place varying degrees of trust in each other.
- **Transitive Trust:** If System A trusts Component B, and Component B trusts Network C, then System A indirectly trusts Network C.
    - *Example (Solaris):* Attackers exploited `rpc.statd` (public interface) to send commands to `automountd` (loopback only) because both ran as root and trusted each other transitively. (See [Fundamental Design Flaws](./foundations/fundamental-design-flaws.md) for details).
- **Misplaced Trust:** Assumptions that a trusted component is impervious to interference. If this trust is misplaced, the entire system can fall like dominos.

## Unfounded Assumptions
Developers can make incorrect assumptions about:
- **Incoming Data:** Validity, length, and format (e.g., assuming a street address won't be 5,000 characters).
- **Environment:** Potential hostility of the network or file system.
- **API/Language Nuances:** Behavior and security properties of specific API calls.
- **Attacker Capabilities:** Underestimating the difficulty for an attacker to reach an interface or reverse-engineer a protocol.

## Interface Security
Vulnerabilities occur when developers assume only trusted peers can use an interface.
- **Proprietary Protocols:** Assuming a custom/complex protocol is "secure" because it's hard to reach. In reality, many attackers enjoy reverse-engineering such protocols.
- **Misconfiguration:** Using reliable OS interfaces but configuring them incorrectly.


## Trust Relationships and Boundaries
Every communication between multiple parties involves some degree of trust.

### Examples of Boundaries
- **Simple (Single-user OS):** In systems like Windows 98, there are no trust boundaries between interactive users. The boundary is physical (who can access the machine).
- **Multiuser OS:** In Windows XP/UNIX, a boundary exists between users (confidentiality/integrity) and between users and administrators (integrity/configuration).

### Absolute Authority
Every system eventually relies on an absolute trusted authority responsible for the system's state (e.g., `root` in UNIX, `Administrator` in Windows). Even with granular controls, one entity must assume final responsibility.

## Complex Trust Relationships
Connecting to a network introduces separate domains for local users, remote users, and those with network access but no account. Firewalls and gateways add further layers of separation.

## Chain of Trust (Transitive Trust)
Implicit trust: If A trusts B, and B trusts C, then A implicitly trusts C.
- **Example (SSL/CA):** You trust a local database of signatures, which trusts a CA, which trusts another CA, which finally signs a website's certificate.
- **Risk:** The integrity of the entire transaction is only as strong as the weakest link in the chain. Compromise of a single valid CA allows an attacker to impersonate any site.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
