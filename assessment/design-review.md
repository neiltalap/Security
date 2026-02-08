# Design Review

Design review is a critical component of the security assessment process, bridging the gap between formal development methodologies and code auditing.

## Perspectives on Design Review
- **Formal Developers:** Often receptive; maps closely to **formal development methodologies** (mathematical formal methods like specifications and proofs).
- **Code Auditors:** Often view it as an "ivory-tower" distraction from the "real work" of digging into code.
- **Reality:** It has value for both. It identifies architectural flaws and prioritizes components for implementation review.

## Benefits
- **Architecture Analysis:** Identifies high-level design flaws (vulnerabilities in the architecture itself).
- **Prioritization:** Helps auditors focus their deep-dive efforts on the most critical or risky components.
- **Efficiency:** Makes the entire review process more effective by ensuring the best return on time invested.

## Design Review in the SDLC
Design review is primarily associated with **Phase 3 (Design)** of the Systems Development Life Cycle (SDLC). 
- It occurs after the **Feasibility Study** (Phase 1) and **Requirements Definition** (Phase 2), but before the **Implementation** (Phase 4).
- Its goal is to catch structural flaws before they are "baked into" the code, which is significantly more cost-effective than fixing them later.

## Formally Defined Systems
For "great systems" that are **formally defined**, design review takes on a mathematical dimension. 
- In these cases, the review process includes analyzing the formal specifications and proofs to ensure the architectural model is sound and satisfies the security properties required by the policy.

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
