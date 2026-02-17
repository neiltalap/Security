# Authorization

Authorization is the process of determining **what** a user is permitted to do, after Authentication has established **who** they are.

## Concepts
- **Trust Domains:** Authorization rules are valid within a specific boundary.
- **Access Control:** The framework for enforcing authorization (e.g., DAC, MAC, RBAC).

## Common Vulnerabilities

### 1. Inconsistent Logic (Logic Flaws)
Authorization logic is often complex and prone to "business logic" errors that are hard for automated tools to catch.

#### Case Study: The "Virtual Manager" (Expense Tracker)
**Scenario:** A corporate expense system allows managers to approve their subordinates' expenses.
- **The Feature:** To handle day-to-day changes, the system allows users to designate a "Virtual Manager" who inherits view/approve rights.
- **The Flaw:** The logic failed to prevent a user from selecting *themselves* as their own Virtual Manager.
- **The Exploit:** An employee designates themselves as their own manager, then approves their own fraudulent expenses.

### 2. Missing Checks (Vertical Privilege Escalation)
A common issue in web applications where authorization is enforced in the UI (hiding buttons) but not in the backend handlers.
- **Vulnerability:** A standard user can access administrative functions simply by guessing the URL or crafting a POST request, because the server assumes "if they clicked the button, they must have permission."

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
