# OpenUAS – Core Model

## Conceptual Architecture (Non-Normative)

Status: Draft  
Scope: Conceptual / Architectural (no protocol syntax, no wire format)

---

## Purpose of This Document

This document defines the **conceptual core model** of OpenUAS.

It explains _how OpenUAS works_ at a mental and architectural level, without
specifying APIs, message formats, or cryptographic algorithms.

Its goal is to ensure:

- shared understanding
- design coherence
- alignment with immutable principles
- correct future specifications

This document is intentionally implementation-agnostic.

---

## Fundamental Design Premise

OpenUAS is based on a single premise:

> Authentication must not depend on secrets that can be copied, reused,
> or willingly disclosed by users.

Therefore:

- knowledge-based authentication is excluded
- shared secrets are excluded
- delegated trust is minimized

Authentication becomes a **cryptographic proof of possession**, not an assertion
of identity mediated by a third party.

---

## Actors

### User

A human being attempting to access a service.

The user is **not required** to understand cryptography, security, or protocols.
The only expected action is a local, familiar gesture (e.g. biometric unlock,
PIN, device confirmation).

---

### Client

The software environment acting on behalf of the user.

Examples:

- Web browser
- Native application
- Operating system authentication agent

The Client:

- manages cryptographic operations
- enforces non-exportability of private keys (when supported)
- interacts with services using OpenUAS flows

The Client is trusted only to the extent of its local execution environment.

---

### Relying Party (Service)

A service that requires user authentication.

Examples:

- Websites
- APIs
- Native services

The Service:

- does not store secrets
- does not authenticate users on behalf of others
- verifies cryptographic proofs locally
- makes no assumptions about user identity beyond proof validity

---

### Optional Registry

A non-authoritative, non-critical component.

The Registry:

- never participates in authentication
- never stores private keys
- never makes access decisions

It may provide:

- discovery information
- public commitments
- transparency logs
- revocation signals

Authentication MUST function correctly without registry availability.

---

## Trust Boundaries

OpenUAS explicitly defines trust boundaries:

- The **Client** is trusted to protect private key material locally
- The **Service** is trusted only to verify proofs correctly
- The **Registry** is not trusted and must be verifiable

No component is trusted with universal authority.

---

## Cryptographic Roots

### User Root

Each user possesses a **root cryptographic capability**, referred to as the
User Root.

Properties:

- generated locally
- non-exportable
- never transmitted
- never escrowed
- bound to the user’s device or hardware environment

The User Root is the source of all authentication authority for that user.

---

### Per-Service Keys

For each Service, the Client derives or generates unique cryptographic material.

Properties:

- unique per Service
- unlinkable across Services
- independent compromise domains

This ensures:

- privacy preservation
- breach containment
- prevention of cross-service correlation

---

## Authentication Model

### High-Level Flow

1. The Service issues a fresh challenge.
2. The Client produces a cryptographic proof using the per-Service key.
3. The Service verifies the proof using stored public information.
4. If valid, authentication succeeds.

No secrets are exchanged.
No reusable credentials exist.

---

### Proof Characteristics

All authentication proofs MUST be:

- bound to the Service identifier
- bound to a fresh challenge
- valid for a single authentication event
- non-replayable

Proofs MUST NOT be transferable across Services.

---

## User Experience Model

From the user’s perspective:

- No passwords are created or remembered
- No security decisions are required
- Authentication feels local and familiar
- Failure modes are understandable

Security is structural, not behavioral.

---

## Recovery Model

Loss of a single device MUST NOT imply loss of access.

Recovery is handled through:

- additional registered devices
- offline recovery material
- assisted recovery processes

Recovery mechanisms:

- MUST NOT introduce shared secrets
- MUST NOT weaken baseline security
- MUST be usable by non-technical users

---

## Failure Model

OpenUAS explicitly accepts that failures occur.

Designed failure cases include:

- service database breach
- phishing attempts
- replay attacks
- partial infrastructure outages

OpenUAS degrades safely:

- compromised Services do not affect others
- unavailable Registries do not block authentication
- Clients never disclose reusable secrets

---

## Non-Goals

The OpenUAS core model intentionally does NOT address:

- authorization and role management
- identity verification or KYC
- device trust scoring
- fraud detection
- policy enforcement
- session management details

These concerns belong outside the core.

---

## Design Invariants

The following invariants MUST hold for all compliant implementations:

- No shared secrets
- No central authentication authority
- No silent correlation across Services
- No mandatory online dependency
- No vendor-specific dependency

If an implementation violates these invariants, it is not OpenUAS-compliant.

---

## Relationship to Specifications

This document precedes and constrains all future specifications.

Any protocol, API, or extension:

- MUST be derivable from this model
- MUST NOT contradict its assumptions
- MUST preserve its invariants

Specifications refine this model; they do not redefine it.

---

## Summary

OpenUAS replaces fragile authentication assumptions with structural guarantees.

It shifts trust from:

- memory to possession
- authority to verification
- secrecy to transparency

This core model defines the minimal, stable foundation upon which all future
OpenUAS work must be built.

---
