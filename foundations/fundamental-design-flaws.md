# Fundamental Design Flaws

Fundamental design flaws are vulnerabilities that arise from the architectural design of a system rather than implementation bugs. They are often the result of misapplying core design principles (like coupling or cohesion) or failing to anticipate how a design will behave in a different context (e.g., single-user vs. multi-user).

## Characteristics
- **Conceptual Level:** They affect the system's logic and rules, not just a single line of code.
- **Hard to Fix:** Addressing them often requires re-architecting significant portions of the system, not just applying a patch.
- **Context Dependent:** A design might be secure in one context (e.g., isolated desktop) but vulnerable in another (e.g., connected network).

---

## Case Study: Exploiting Strong Coupling (The "Shatter" Attack)

This vulnerability is a classic example of **Strong Coupling** leading to a privilege escalation attack. It highlights how a design choice—the Windows messaging system—became a flaw when the operating environment changed.

### The Context
- **Original Design:** Early Windows (95/98) was designed for single users. Trust boundaries between applications on the same desktop were unnecessary because the user "owned" everything.
- **The Mechanism:** Windows applications communicate via a **messaging system**. Each desktop has a single message queue.
- **The Feature:** The API allows *any* process on a desktop to send messages to *any other* window on the same desktop, regardless of the process's privilege level.

### The Flaw
When Windows moved to a multi-user architecture (NT/2000/XP), it retained this messaging system for backward compatibility. This created a **Strong Coupling** between different trust domains:
1.  **Low-Privilege Process:** A user application (or malware) running with standard permissions.
2.  **High-Privilege Process:** A system service (e.g., Antivirus console) running as `SYSTEM` but displaying a window on the interactive desktop.

Because of the shared message queue, the low-privilege process could "drive" the high-privilege process.

### The Attack Vector (Shatter)
The "Shatter" class of vulnerabilities (popularized by Chris Paget) exploited this by using the `WM_TIMER` message.

1.  **Injection:** The attacker sends a `WM_SETTEXT` (or similar) message to the target window to inject malicious bytecode into the target's memory space (e.g., into a text box buffer).
2.  **Trigger:** The attacker calls `SetTimer()` to send a `WM_TIMER` message to the target window.
3.  **Execution:** The `WM_TIMER` message includes a **callback function pointer**. The attacker points this to the malicious code they just injected.
4.  **Escalation:** The high-privilege service processes the message, jumps to the callback address, and executes the attacker's code with `SYSTEM` privileges.

### The Lesson
- **Trust Boundaries:** Communication across a desktop is a potential attack vector.
- **Evolution:** A design that is "correct" for a single-user OS can become fatally flawed in a multi-user OS.
- **Coupling:** The message queue tightly coupled processes that should have been isolated, allowing one to manipulate the execution flow of the other.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
