# OpenUAS – Immutable Base Rules

## Open Source Universal Authentication System

Version: 1.0  
Status: Immutable  
Scope: Ethical, Architectural, and Governance Foundations

---

## 0. Purpose

OpenUAS exists to improve global digital security by providing a universal,
phishing-resistant, privacy-preserving authentication system that does not rely
on centralized identity providers or user-managed secrets.

These rules define the non-negotiable foundations of OpenUAS.
Any system, fork, or implementation that violates these rules MUST NOT claim
compatibility with OpenUAS.

---

## 1. No Shared Secrets

OpenUAS MUST NOT rely on shared secrets.

This includes, but is not limited to:

- passwords
- reusable OTPs
- security questions
- static API keys

Authentication MUST be based on cryptographic proof of possession, never on
knowledge of a secret.

---

## 2. Phishing Resistance by Design

OpenUAS MUST be phishing-resistant by default.

Any compliant authentication flow MUST:

- be bound to the service origin or identifier
- prevent credential replay across services
- prevent credential capture via fake or proxied services

Security MUST NOT depend on the user's ability to detect phishing.

---

## 3. No Central Identity Provider

OpenUAS MUST NOT require a central identity provider.

No entity (company, foundation, individual, or state) may:

- authenticate users on behalf of services
- act as a mandatory login intermediary
- gain the ability to impersonate users

Trust MUST be established through cryptographic verification, not delegation.

---

## 4. User-Controlled, Non-Exportable Roots

User authentication MUST originate from user-controlled cryptographic roots.

These roots MUST:

- be generated locally
- be non-exportable
- never be transmitted or escrowed
- remain under the user's exclusive control

Hardware-backed protection SHOULD be used whenever available, but MUST remain
invisible to the user experience.

---

## 5. Per-Service Cryptographic Isolation

OpenUAS MUST prevent cross-service correlation.

This requires:

- unique cryptographic material per service
- no global user identifiers
- no stable identifiers shared across services

Compromise of one service MUST NOT weaken the security or privacy of others.

---

## 6. Minimal Core, Explicit Extensions

The OpenUAS core MUST remain minimal.

The core SHALL include only:

- authentication primitives
- proof verification
- mandatory security properties

All additional features (policy, device posture, recovery enhancements,
attestations) MUST be implemented as explicit, optional extensions.

---

## 7. Recovery Is Mandatory, Not Optional

OpenUAS MUST support secure recovery.

Every compliant implementation MUST provide at least one recovery mechanism that:

- does not rely on shared secrets
- does not reduce baseline security
- is understandable by non-technical users

Loss of a device MUST NOT imply permanent loss of identity.

---

## 8. Transparency Over Authority

OpenUAS governance MUST rely on transparency, not authority.

This includes:

- public specifications
- open-source implementations
- auditable conformance tests
- public change history
- observable compliance

Trust MUST be derived from verifiable behavior, not reputation or branding.

---

## 9. Forking Is Allowed; Compatibility Is Earned

Forking OpenUAS is explicitly permitted.

However:

- compatibility with OpenUAS requires strict conformance
- incompatible forks MUST NOT claim OpenUAS compatibility
- interoperability is defined by tests, not declarations

Freedom to fork MUST NOT compromise ecosystem integrity.

---

## 10. No Vendor Lock-In

OpenUAS MUST NOT depend on:

- proprietary platforms
- mandatory commercial services
- closed components required for compatibility

Multiple independent implementations MUST be possible at all times.

---

## 11. Governance Must Prevent Capture

OpenUAS governance MUST be structured to prevent capture by:

- a single individual
- a single organization
- a single government
- a single economic interest

Roles, powers, and responsibilities MUST be limited, transparent, and rotatable.

---

## 12. Evolution Without Betrayal

OpenUAS MUST be able to evolve without betraying its principles.

This requires:

- backward compatibility where feasible
- explicit deprecation processes
- conservative changes to security-critical behavior

Convenience MUST NEVER override foundational security or privacy guarantees.

---

## 13. Ethics Over Adoption Metrics

Adoption is important, but never at the cost of principles.

OpenUAS MUST NOT:

- weaken security for growth
- trade privacy for convenience
- introduce control points for popularity

OpenUAS exists to improve the world, not to dominate it.

---

## 14. Immutability Clause

These rules are immutable.

They MAY be clarified for precision,
but MUST NOT be weakened, removed, or overridden.

Any version of OpenUAS that violates these rules is, by definition,
not OpenUAS.

---
