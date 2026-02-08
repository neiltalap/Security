# Software Design Fundamentals

Understanding the core design elements is crucial for identifying security vulnerabilities.

## Algorithms and Data Structures
The choice of algorithms impacts security, particularly regarding **performance**.
- **Performance Attacks:** Algorithms with poor worst-case performance (e.g., searching a linked list) can be targeted by attackers using specially crafted inputs to cause Denial of Service (DoS).

## Problem Domain Logic (Business Logic)
The rules and processes for the main tasks the software carries out.
- **Security Expectations:** Business logic defines who can do what (e.g., banking transfer limits).
- **Logic Flaws:** Oversights in these rules (e.g., draining a main account to bypass a monthly transfer limit on a secondary account) are common vulnerabilities.

## Abstraction and Decomposition
- **Abstraction:** Reducing complexity by isolating important elements and removing details. In security, this helps model processes and trust boundaries.
- **Decomposition:** Breaking down the abstraction.
    - **Top-Down (Specialization):** Breaking a system into smaller parts (Application -> Module -> Function).
    - **Bottom-Up (Generalization):** Identifying similarities to create higher-level abstractions.


## Core Principles of Software Design
These principles apply to every software design and are critical starting points for assessing security.

### 1. Accuracy
Accuracy refers to how effectively design abstractions meet the associated requirements.
- **Implication:** Discrepancies between design and implementation force developers to make undocumented assumptions, creating fertile ground for vulnerabilities.

### 2. Clarity
A good design provides clean, self-evident abstractions and is well-documented.
- **Implication:** Overly complex or poorly documented designs are difficult to understand, leading to inaccurate implementations and security bugs.

### 3. Loose Coupling
Coupling refers to the level of communication and dependency between modules.
- **Implication:** Strongly coupled modules often place a high degree of trust in each other and fail to perform data validation, especially across trust boundaries.

### 4. Strong Cohesion
Cohesion refers to a module's internal consistency (handling a related set of activities).
- **Implication:** Weak cohesion (mixing multiple trust domains within a single module) often leads to vulnerabilities similar to strong coupling issues.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
