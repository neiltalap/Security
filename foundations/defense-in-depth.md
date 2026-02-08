# Defense in Depth

Defense in depth is the concept of layering protections so that the compromise of one aspect of a system is mitigated by other controls.

## Layered Protections
- **Low Privilege Accounts:** Running services and daemons with minimal necessary permissions.
- **Isolation:** Separating different functions to different hardware or logical containers.
- **Environment Hardening:** Using chroot jails, sandboxing, and containers.
- **Memory Protections:** Implementing stack and heap guards to prevent exploitation.
- **Network Segmentation:** Using DMZs and firewalls to isolate critical assets.

## Impact on Auditing
Layered defenses are a key factor in prioritizing components for review:
- **Low Priority:** Intranet-facing components running with low privileges inside a hardened environment.
- **High Priority:** Internet-facing components that must run as root (or with high privileges).

---
*Source: The Art of Software Security Assessment (Dowd, McDonald, Schuh)*
