# Accountability

Accountability ensures that a system can identify and log user activities. It provides the data essential for forensic analysis and mitigating successful compromises.

## Concepts
- **Accountability:** The ability to trace actions to a specific user.
- **Non-Repudiation:** A guarantee that users cannot deny performing an action (a subset of accountability).

## Common Vulnerabilities

### 1. Failure to Log
The most common issue is simply not logging access to sensitive data. Without logs, there is no audit trail.

### 2. Insecure Log Protection
Logs themselves are high-value targets.
- **Read Access:** Attackers can read logs to deduce user patterns or finding passwords accidentally typed into username fields.
- **Write Access:** Attackers can delete logs to cover their tracks or corrupt them to cause Denial of Service.

### 3. Log Injection
This vulnerability occurs when user-supplied input is written to a log file without sanitization, allowing an attacker to forge log entries.

#### Example Scenario
A log file format: `[Timestamp] [Event]: [User]`

**Normal Entry:**
`2026-02-18 12:00:00 Logon Failure: Bob`

**Attack:**
A user enters their name as: `Bob\n2026-02-18 12:05:00 Logon Success: Greg`

**Resulting Log:**
```text
2026-02-18 12:00:00 Logon Failure: Bob
2026-02-18 12:05:00 Logon Success: Greg
```
The attacker has successfully forged a "Success" entry for another user, potentially framing them or confusing forensic analysis.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
