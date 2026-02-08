# Data Flow and Input

The majority of software vulnerabilities result from unexpected behaviors triggered by a program's response to malicious data.

## Key Concepts

### Malicious Data Entry
- **Direct Input:** Data comes directly from an attacker via interfaces like command-line arguments or Web requests.
- **Circuitous Routes:** Data might pass through multiple components, survives being stored in databases, and be modified before triggering an exploit.

### Data Tracing
The process of tracing data from its entry point (interface) to its final use is central to both design and implementation reviews.
- **Goal:** Identify where user-malleable data enters and how it travels through the system.
- **Complexity:** In real-world systems, data flow is often fragmented and traverses dozens of components, including third-party frameworks.

### Fragmented Data Flow
Complex systems often develop organically, leading to data flows that delve in and out of various components. Tracing this "end-to-end" is critical for evaluating security threats.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
