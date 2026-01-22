# OpenUAS – Threat Model

## Security Assumptions, Guarantees, and Limits

Status: Draft  
Scope: Conceptual / Defensive (non-normative)

---

## Purpose of This Document

This document defines the **threat model** for OpenUAS.

It explicitly describes:

- which threats OpenUAS is designed to mitigate
- which threats are intentionally out of scope
- which assumptions are required for security guarantees to hold

This document exists to:

- prevent false security expectations
- guide correct implementations
- provide a clear basis for security evaluation
- avoid security theater

---

## Security Philosophy

OpenUAS assumes that **humans are the weakest link** in authentication systems.

Therefore, OpenUAS:

- removes reliance on human memory
- removes reliance on user judgment under pressure
- removes reliance on recognizing malicious services

Security is achieved through **structural properties**, not behavioral correctness.

---

## Threat Actors

The following threat actors are considered in scope:

- Remote attackers
- Phishing operators
- Credential stuffing operators
- Malicious service operators
- Database breach attackers
- Network-level attackers
- Passive observers
- Active replay attackers

The following threat actors are considered partially in scope:

- Malware with limited user privileges
- Compromised but non-persistent client environments

---

## Assets to Protect

OpenUAS aims to protect:

- User authentication authority
- Service access control decisions
- User privacy across services
- Authentication integrity
- Resistance to impersonation

OpenUAS does NOT aim to protect:

- user data stored by services
- application-layer authorization logic
- post-authentication session security

---

## In-Scope Threats and Mitigations

### 1. Phishing Attacks

**Threat:**  
Attackers trick users into authenticating on fake or proxied services.

**Mitigation:**

- Authentication proofs are bound to the service identifier
- Proofs cannot be replayed on other services
- No secrets are disclosed by the user

**Result:**  
Phishing attacks are structurally ineffective.

---

### 2. Credential Reuse and Credential Stuffing

**Threat:**  
Attackers reuse credentials obtained from one service to access others.

**Mitigation:**

- No reusable credentials exist
- Per-service cryptographic isolation
- Compromise of one service does not affect others

**Result:**  
Credential stuffing is eliminated.

---

### 3. Service Database Breaches

**Threat:**  
Attackers obtain authentication data from breached services.

**Mitigation:**

- Services store only public verification material
- No shared secrets or password hashes exist

**Result:**  
Database breaches do not enable user impersonation.

---

### 4. Replay Attacks

**Threat:**  
Captured authentication messages are replayed to gain access.

**Mitigation:**

- Fresh challenges per authentication
- Single-use proofs
- Challenge expiration requirements

**Result:**  
Replay attacks are ineffective.

---

### 5. Network Interception (MITM)

**Threat:**  
Attackers intercept or modify authentication traffic.

**Mitigation:**

- Proofs are bound to challenges and service identifiers
- Transport security is assumed (e.g., TLS)
- No reusable secrets are transmitted

**Result:**  
Interception does not grant authentication capability.

---

### 6. Cross-Service Tracking

**Threat:**  
Services correlate user identities across different services.

**Mitigation:**

- Per-service cryptographic material
- No global identifiers
- No shared stable identifiers

**Result:**  
Cross-service correlation is structurally prevented.

---

## Partially Mitigated Threats

### 7. Client-Side Malware (Limited)

**Threat:**  
Malware operating with limited privileges attempts to interfere.

**Mitigation:**

- Non-exportable keys limit exfiltration
- Hardware-backed protection reduces exposure

**Limitations:**

- Malware may initiate authentication while user is present
- Malware may abuse authenticated sessions

**Result:**  
Impact is reduced but not eliminated.

---

## Out-of-Scope Threats

OpenUAS explicitly does NOT defend against:

### 8. Fully Compromised Devices

**Threat:**  
Attackers gain full control of the user’s device.

**Reason:**  
No authentication system can protect users from fully compromised endpoints.

---

### 9. Physical Coercion

**Threat:**  
Users are forced to authenticate under duress.

**Reason:**  
This is a societal and legal problem, not a protocol problem.

---

### 10. Malicious Operating Systems or Hardware

**Threat:**  
The platform itself is malicious or compromised at a deep level.

**Reason:**  
OpenUAS relies on platform guarantees for key protection.

---

### 11. Post-Authentication Attacks

**Threat:**  
Attackers hijack sessions after authentication.

**Reason:**  
Session management is explicitly out of scope.

---

## Assumptions

The following assumptions are required:

- Clients correctly implement non-exportable key protection
- Services correctly verify proofs
- Cryptographic primitives are correctly implemented
- Transport security is present
- Users protect their devices reasonably

Violation of these assumptions weakens guarantees.

---

## Failure Modes and Safe Degradation

OpenUAS is designed to fail safely:

- Authentication fails closed
- No fallback to weaker methods
- Registry unavailability does not block authentication
- Breaches do not cascade across services

---

## Security Guarantees Summary

When assumptions hold, OpenUAS guarantees:

- Phishing resistance
- No credential reuse
- No credential stuffing
- No server-side credential theft
- Strong privacy isolation across services

---

## Non-Guarantees Summary

OpenUAS does NOT guarantee:

- Protection against fully compromised devices
- Anonymity beyond authentication
- Authorization correctness
- Protection against all malware
- Session integrity after authentication

---

## Final Note

OpenUAS does not promise perfect security.

It promises **predictable security**, with explicit limits and no hidden trust
dependencies.

Understanding what OpenUAS does NOT protect is as important as understanding
what it does.

---
