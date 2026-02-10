# Data Protection Frameworks

Key legal frameworks govern how personal data is handled across different regions.

## Regional Frameworks
- **European Union:** The **General Data Protection Regulation (GDPR)** is the primary law.
- **United Kingdom:** Governed by the **Data Protection Act 2018** and the "UK GDPR".
- **Global Context:** **Convention 108** (Council of Europe) aligns with GDPR; GDPR also has extraterritorial effects.
- **United States:** Lacks a single comprehensive law, relying instead on fragmented sector-specific regulations.

## Key GDPR Concepts
- **Personal Data:** Any information relating to an identified or identifiable "data subject" (e.g., name, ID, location data).
- **Special Categories:** Sensitive data requiring extra protection (race, politics, religion, health, biometrics).
- **Key Actors:**
    - **Data Subject:** The individual the data describes.
    - **Data Controller:** Determines the purpose of processing.
    - **Data Processor:** Processes data on behalf of the controller.
    - **Data Protection Authority (DPA):** The regulator (e.g., the ICO in the UK).

## Core Principles of Processing
Data must be processed:
- Fairly, lawfully, and transparently.
- For specific, limited purposes.
- With **Data Minimization** (adequate, relevant, not excessive).
- Accurately and kept no longer than necessary.
- Securely against malice or loss.

## Legal Bases for Processing
Processing is only lawful if it meets one of these:

1.  **Consent:** Clear, affirmative action. Usage is fragile as it can be withdrawn.
2.  **Contract Execution:** Necessary to fulfill a contract with the user (e.g., needing an address to deliver a package, or bank details to pay salary).
3.  **Legal Obligation:** Statutory requirement (e.g., holding tax records, responding to court orders, KYC checks).
4.  **Vital Interests:** To protect someone's life (e.g., sharing medical data with A&E for an unconscious patient).
5.  **Public Interest:** Exercising official authority (e.g., census, police investigation, tax collection).
6.  **Legitimate Interests:** Necessary for legitimate business interests (fraud prevention, network security) provided they don't override the user's rights. Requires a "Balancing Test".

## Data Subject Rights
- Right to be informed (transparency).
- Right of access, rectification, and erasure ("Right to be forgotten").
- Right to restrict or object to processing.
- Right to data portability.

## Security and Enforcement
- **Measures:** Must use "state of the art" and "appropriate" measures (e.g., encryption at rest and in transit).
- **Anonymisation vs. Pseudonymisation:**
    - **Pseudonymisation:** Data is masked but still considered personal data.
    - **Anonymisation:** Data cannot be re-identified; no longer considered personal data.
- **Fines:** Up to 4% of global turnover or €20M. Notable cases: British Airways (£20M), Marriott (£14M).

---

## Practical Application: Corporate Monitoring & Investigations

### Case Study: Internal Investigation
**Scenario:** A company suspects an employee (David) of leaking data and hires an investigator (John) to examine his computer.

**Key Compliance Steps:**
1.  **Lawfulness (Basis):** Usually **Legitimate Interests** (protecting IP) or **Contract** (employment terms). **Consent is NOT valid** due to power imbalance.
2.  **Fairness & Transparency:** Employees must be informed of monitoring via an **Acceptable Use Policy (AUP)** or Privacy Notice. Secret monitoring is high-risk.
3.  **Purpose Limitation:** Investigation must be strictly for the leak, not for other non-related misconduct ("fishing" for bad behavior).
4.  **Data Minimization:** Use keyword searches (e.g., "Project X") rather than reading every email. Avoid personal folders unless necessary.
5.  **Data Retention:** If David is cleared, the forensic data should be destroyed, not kept indefinitely.

### Employee Monitoring Rights
| Area          | Requirement                   | Reality in Security Context                                                                                                           |
| :------------ | :---------------------------- | :------------------------------------------------------------------------------------------------------------------------------------ |
| **Erasure**   | Right to be forgotten         | **Limited.** Security logs are a legal/business necessity; employees usually cannot demand deletion of audit trails.                  |
| **Objection** | Right to object to processing | **Qualified.** Employer can override objection if monitoring is critical for network security.                                        |
| **Privacy**   | Expectations of privacy       | **Balanced.** Workplace privacy is not absolute, but monitoring must be proportional (e.g., no keyloggers unless strictly necessary). |
