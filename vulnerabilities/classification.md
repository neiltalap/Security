# Vulnerability Classification

A vulnerability class is a mental device for conceptualizing software flaws. There isn't a single, clean taxonomy; vulnerabilities often overlap.

## 1. Design Vulnerabilities
Flaws in high-level software architecture, requirements, base interfaces, and key algorithms.
- **Nature:** The software does exactly what it was designed to do, but it was designed insecurely.
- **Example:** The TELNET protocol relying on unencrypted communication is a design flaw.
- **SDLC Phases:** Typically originates in Phases 1, 2, and 3 (Feasibility, Requirements, Design).

## 2. Implementation Vulnerabilities
Low-level technical flaws in the actual construction (coding) of the software.
- **Nature:** The code carries out its intended operation in an insecure manner, often due to technical nuances of the platform or language.
- **Examples:** Buffer overflows, SQL injection, format string attacks.
- **SDLC Phases:** Typically occurs in Phase 4 (Implementation) and carries over into Phase 5 (Integration and Testing).

## 3. Operational Vulnerabilities
Issues rooted in how the software interacts with its environment rather than its source code.
- **Nature:** Flaws arise from deployment, configuration, and administrative practices.
- **Examples:**
    - Unsafe configuration of supporting components (Web servers).
    - Unsound management practices (e.g., using TELNET for administrative updates).
    - Attacks on users (Social engineering, theft).
- **SDLC Phases:** Primarily occurs in Phase 6 (Operation and Maintenance).

---

## Gray Areas
The distinctions between these classes are often blurred:
- An implementation flaw might be interpreted as a design failure to anticipate an environmental concern.
- Low-level pieces (functions/classes) are "designed" by programmers during implementation.
- Unsafe deployment might be considered a failure of the application's implementation to handle environmental risks.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
