# AI Agent Security

AI agents are autonomous systems powered by LLMs that can reason, plan, and execute actions. Their autonomy introduces unique attack surfaces beyond standard prompt injection.

## Key Risks
- **Prompt Injection (Direct/Indirect):** Hijacking agent control via user input or external data (emails, websites).
- **Tool Abuse:** Exploiting overly permissive tools to access unauthorized resources or execute dangerous commands.
- **Data Exfiltration:** Leaking sensitive data through tool calls or logs.
- **Memory Poisoning:** Injecting malicious data into long-term memory to influence future interactions.
- **Goal Hijacking:** Subtly manipulating the agent's objectives.
- **Denial of Wallet (DoW):** Causing excessive compute/API costs via unbounded loops.

## Best Practices & Patterns

### 1. Tool Security (Least Privilege)
**Never** give an agent unrestricted shell or file access.
- **Scope Permissions:** Read-only vs. Write. Specific directories only.
- **Middleware:** Intercept tool calls for validation.

```python
# Bad: Unrestricted
tools = [{"name": "execute_command", "allowed_commands": "*"}]

# Good: Scoped & Allowlisted
tools = [{
    "name": "file_reader",
    "allowed_paths": ["/app/reports/*"],
    "blocked_patterns": ["*.env", "*.key"]
}]
```

### 2. Human-in-the-Loop (HITL)
Require explicit approval for high-risk actions (e.g., financial transfers, file deletions, external emails).
- **Risk Mapping:** Classify tools by risk level (Low, Medium, High, Critical).
- **Preview:** Show the user exactly what the agent plans to do *before* execution.

### 3. Memory & Context Security
Treat memory as an untrusted input source.
- **Validation:** Sanitize data *before* storing it.
- **Isolation:** Segregate memory by user/session.
- **Integrity:** Use checksums to detect tampering.

```python
# Secure Memory Pattern
def add_memory(self, content):
    if self._contains_sensitive_data(content):
        content = self._redact(content)
    content = self._sanitize_injection(content)
    # Store with checksum
```

### 4. Output Validation & Guardrails
Validate agent outputs to prevent data leakage and insecure tool calls.
- **Schema Validation:** Use structured outputs (JSON schemas) to enforce format.
- **PII Filtering:** Redact sensitive data (API keys, PII) from responses.
- **Exfiltration Detection:** Block responses containing encoded data or mostly URLs.

### 5. Multi-Agent Security
- **Trust Boundaries:** Differentiate between internal (trusted) and external (untrusted) agents.
- **Circuit Breakers:** Prevent cascading failures if one agent goes rogue or loops.
- **Signed Messages:** Sign inter-agent communications to prevent spoofing.

---
*Source: OWASP LLM Top 10, NIST AI RMF*
