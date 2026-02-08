# Security Policies

## Definition
A **Security Policy** defines the security of a system as a list of what is allowed and what is forbidden for a system composed of software, users, and resources. In practice, a policy is often the user community's consensus on reasonable behavior.

## Policy Types

### 1. Formal Specifications
- **Description:** Mathematical constraints verifiable against program code.
- **Application:** Highly controlled, sensitive environments (e.g., life support, traffic lights).
- **Caveat:** Often prohibitively expensive or unwieldy for most applications.

### 2. Formal Documentation
- **Description:** Written documents with specific clauses and requirements.
- **Sources:** Development process docs, site security policies, OS/Database policies.
- **Example:** "Credit card info must never be disclosed to a third party without encryption."

### 3. Informal Expectations
- **Description:** Ambiguous collection of people's expectations of "reasonable" behavior.
- **Status:** The most common form of security policy in practice.

---

## Code Access Security (CAS)
CAS provides mechanism for validating packages at load time and runtime (e.g., JVM, .NET CLR).
- **Validation:** Bytecode integrity, software originator, access restrictions (sandboxing).
- **Caveats:**
    - Complexity: Most developers don't fully understand it, so it's rarely leveraged correctly.
    - Security Dependencies: CAS security depends on the underlying components (VMs have had escape vulnerabilities).

## Policy Violations
A violation of a software system's security occurs when the system's security policy is violated.

### Example
- **Policy:** "Unauthenticated users are forbidden from using the calendar service on the staging machine."
- **Violation:** A flaw that allows an unauthenticated user to access that specific service.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh), Matt Bishop (Computer Security: Art and Science)*
