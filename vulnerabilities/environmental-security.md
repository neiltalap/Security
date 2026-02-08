# Environmental Security

Not all vulnerabilities are triggered by malicious processing of data. Some occur when an attacker manipulates the software's underlying environment (OS, hardware, network, file system).

## Environmental Attacks
These flaws result from assumptions made about the environment in which the software runs.
- **Manipulation:** An attacker changes the state of the environment (e.g., the file system) to cause the program to behave unexpectedly during interaction with the OS.

## Race Conditions: The /tmp Race
A classic example in UNIX environments where a program uses a public temporary directory (/tmp or /var/tmp) incorrectly.
- **The Attack:** An attacker anticipates the program's use of a temporary file and sets a "trap" by creating a symbolic link in the public directory.
- **The Impact:** The program is tricked into creating or modifying a file elsewhere on the system, often leading to privilege escalation if the program runs with root privileges.

---

## Exceptional Conditions
Vulnerabilities can arise when an attacker causes an unexpected change in a program's normal control flow via external measures.

### Asynchronous Interruptions
- **Signals:** Sending signals (like UNIX `SIGPIPE`) to interrupt a program at a critical moment.
- **Example:** Triggering a `SIGPIPE` by closing a pipe connection during a write operation, potentially causing the application to crash or leave the system in an unstable state (e.g., NFS daemon crashes).

### Resource Exhaustion
- **Denial of Service:** Deliberately consuming global system resources to induce failure conditions at specific points in a program.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
