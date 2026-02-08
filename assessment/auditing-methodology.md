## Security Testing Methods

### Black Box Testing
Evaluating a system by manipulating only its exposed interfaces.
- **Process:** Generating specially crafted inputs (abnormally large fields, invalid requests) to trigger crashes or exposed data.
- **Fuzz-Testing:** Automated black box testing.
    - **"Dumb" Fuzzers:** Generic, protocol-unaware tools.
    - **"Intelligent" Fuzzers:** Protocol-aware tools that understand expected data structures.
- **Advantage:** Quick results, automated.
- **Disadvantage:** Low code coverage; missed internal logic/code paths that automated tools can't trigger.

### Code Auditing vs. Black Box Testing
Code auditing involves analyzing code constructs intelligently to detect paths a tool might miss. Combining both provides maximum results in identifying vulnerabilities.

---

## Auditing and the Development Life Cycle (SDLC)
The cost of fixing vulnerabilities varies based on when they are identified.

### SDLC Phases
1. **Feasibility Study:** Identifying project needs and technical/financial viability.
2. **Requirements Definition:** Establishing project goals and study of requirements.
3. **Design:** Designing the technical solution to achieve requirements.
4. **Implementation:** Developing the application code.
5. **Integration and Testing:** Quality assurance to catch bugs and ensure basic functionality.
6. **Operation and Maintenance:** Deployment, user feedback, and updates.

Auditing can be performed at any stage, but earlier detection (Design/Implementation) is significantly cheaper and more efficient.

---

## Code-Auditing Situations

| Situation                  | Description                             | Advantage                                                      |
| :------------------------- | :-------------------------------------- | :------------------------------------------------------------- |
| **In-house (Prerelease)**  | Auditing during development.            | Saves money/embarrassment by fixing flaws before market.       |
| **In-house (Postrelease)** | Auditing after release.                 | Find and fix flaws before malicious discovery.                 |
| **Third-party Range**      | Comparison of competing products.       | Objective info for consumers to select secure products.        |
| **Third-party Eval**       | Independent audit for a client.         | Understand relative security before deployment.                |
| **Preliminary Eval**       | Review before a product goes to market. | Helps venture capitalists or vendors ensure viability/quality. |
| **Independent Research**   | Audit by security firms independently.  | Develop protective measures for scanners; industry watchdog.   |

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
