# OpenUAS – Recovery Model

## Secure Account Recovery Without Shared Secrets

Status: Draft  
Scope: Recovery design and failure handling (pre-spec, non-normative)

---

## Purpose of This Document

This document defines the **recovery model** for OpenUAS.

Recovery is one of the most critical and dangerous aspects of any authentication
system. Poorly designed recovery mechanisms routinely nullify otherwise strong
security guarantees.

The goal of this document is to define recovery mechanisms that:

- preserve OpenUAS security guarantees
- avoid shared secrets and weak fallbacks
- remain usable by non-technical users
- make trade-offs explicit and auditable

Recovery MUST be considered part of the security model, not an afterthought.

---

## Core Recovery Principles

All OpenUAS recovery mechanisms MUST comply with the following principles:

1. **No shared secrets**  
   Recovery MUST NOT rely on passwords, security questions, or static codes.

2. **No silent privilege escalation**  
   Recovery MUST NOT silently bypass normal authentication guarantees.

3. **Explicit user intent**  
   Recovery MUST require explicit, conscious user action.

4. **Defense in depth**  
   Recovery SHOULD require multiple independent factors.

5. **Recoverability without central authority**  
   Recovery MUST NOT require a global identity provider.

---

## Threats Addressed by Recovery Design

The recovery model addresses:

- loss or destruction of a primary device
- device theft without user cooperation
- partial compromise scenarios
- long-term account continuity

The recovery model does NOT attempt to defend against:

- fully compromised user environments
- physical coercion
- malicious platform vendors

---

## Recovery Scenarios

### Scenario 1: Loss of Primary Device

The user loses access to their primary authentication device due to:

- hardware failure
- loss
- accidental destruction

Recovery must allow the user to regain access without weakening security.

---

### Scenario 2: Device Theft

An attacker gains physical possession of a device without user consent.

Recovery must:

- prevent attacker-initiated recovery
- allow the legitimate user to re-establish access
- support revocation of the stolen device

---

### Scenario 3: Multi-Device Environments

The user owns multiple devices capable of OpenUAS authentication.

Recovery should leverage existing trusted devices to minimize friction.

---

## Recovery Mechanisms

OpenUAS allows multiple recovery mechanisms.
At least one MUST be supported by compliant implementations.

---

### 1. Pre-Registered Secondary Devices (Recommended)

#### Description

The user registers multiple devices in advance.
Any registered device can be used to recover access if another is lost.

#### Properties

- no shared secrets
- cryptographically strong
- user-controlled
- low friction

#### Recovery Flow (Conceptual)

1. User initiates recovery from a remaining trusted device.
2. Client authenticates normally using that device.
3. User authorizes recovery operation locally.
4. Lost device is revoked.
5. New device may be registered.

This is the **preferred recovery mechanism**.

---

### 2. Offline Recovery Material

#### Description

The user generates offline recovery material during enrollment.

Examples:

- recovery key pairs
- sealed recovery tokens
- printed or securely stored artifacts

#### Properties

- usable without online dependencies
- resistant to remote compromise
- higher user responsibility

#### Requirements

Offline recovery material MUST:

- be generated locally
- be unique per user
- never be transmitted unless recovery is invoked
- require explicit user action

Offline recovery material MUST NOT be:

- short codes
- passwords
- easily guessable values

---

### 3. Assisted Recovery (Optional)

#### Description

Assisted recovery involves a trusted recovery service or process.

This MAY include:

- identity verification steps
- time-delayed recovery approval
- multi-party authorization

#### Constraints

Assisted recovery:

- MUST NOT act as an authentication provider
- MUST NOT gain impersonation capability
- MUST NOT introduce a global authority

Assisted recovery SHOULD:

- be slow by design
- be auditable
- require strong user presence

---

## Recovery Authorization Requirements

All recovery operations MUST require:

- explicit user intent
- local authorization on at least one trusted element
- clear user-visible confirmation

Recovery MUST NOT be:

- automatic
- background
- triggered remotely without user interaction

---

## Device Revocation

Recovery flows MUST support device revocation.

Revocation properties:

- explicit
- auditable
- irreversible without recovery

Revocation prevents:

- stolen device reuse
- silent persistence of compromised devices

---

## Recovery Rate Limiting

To reduce abuse:

- recovery attempts SHOULD be rate-limited
- recovery MAY include time delays
- repeated failures SHOULD trigger alerts

Rate limiting MUST NOT rely on shared secrets.

---

## Failure Handling

If recovery fails:

- access remains denied
- no fallback to weaker mechanisms occurs
- users are informed of next steps

Permanent loss is preferable to silent compromise.

---

## Forbidden Recovery Designs

The following recovery designs are explicitly forbidden:

- email-based recovery links
- SMS-based recovery codes
- security questions
- customer support password resets
- single-factor recovery

These mechanisms undermine OpenUAS guarantees.

---

## User Experience Considerations

Recovery flows MUST:

- be explainable in simple language
- make consequences explicit
- avoid panic-driven decisions
- encourage preparation (e.g. registering secondary devices)

Usability is part of security.

---

## Relationship to Authentication Flow

Recovery operations:

- are distinct from normal authentication
- MUST NOT reuse authentication proofs
- MUST be clearly separated in implementation

Recovery restores the ability to authenticate; it does not authenticate itself.

---

## Summary

This recovery model provides a secure path to regain access
without sacrificing OpenUAS core guarantees.

It balances:

- security
- usability
- decentralization
- transparency

A recovery mechanism that weakens authentication is not recovery;
it is a vulnerability.

---
