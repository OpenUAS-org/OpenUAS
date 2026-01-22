# OpenUAS – Technical Design

## Pre-Specification Technical Architecture

Status: Draft  
Scope: Technical design and architectural guidance (pre-RFC, non-normative)

---

## Purpose of This Document

This document describes **how OpenUAS should be implemented at a technical level**,
while deliberately stopping short of defining a formal protocol specification.

Its goals are to:

- translate the Core Model into implementable concepts
- guide independent implementations toward consistent behavior
- highlight mandatory vs optional components
- make security-critical choices explicit
- prevent unsafe or incompatible designs

This document is **not** a final specification.
It is a bridge between architecture and RFC-level definition.

---

## Design Constraints (Non-Negotiable)

All OpenUAS implementations MUST respect the following constraints:

- No shared secrets
- No password-based or OTP-based fallback
- No central authentication authority
- No global user identifier
- No cross-service key reuse
- No silent weakening of security for usability

Any design that violates these constraints is **non-compliant by definition**.

---

## System Components

### Client

The Client is the software component acting on behalf of the user.

Examples:

- Web browser
- Native application
- Operating system authentication agent

Technical responsibilities:

- generate and store cryptographic key material
- enforce non-exportability of private keys when supported
- perform cryptographic proofs
- bind authentication operations to the correct service context
- present a simple, local user interaction

The Client MUST NOT:

- expose private keys
- transmit reusable credentials
- make trust decisions on behalf of the Service

---

### Relying Party (Service)

The Relying Party is the service requiring authentication.

Technical responsibilities:

- generate fresh authentication challenges
- store only public verification material
- verify cryptographic proofs
- bind authentication to its own service identifier

The Service MUST NOT:

- store secrets usable for impersonation
- rely on third-party authentication providers
- correlate users across services

---

### Optional Registry

The Registry is an optional, non-authoritative component.

Possible roles:

- discovery of public parameters
- publication of public commitments
- transparency logs
- revocation signals

The Registry MUST:

- be fully verifiable
- never participate in authentication
- never hold private keys
- be ignorable without breaking authentication

---

## Cryptographic Foundations

### Key Types

OpenUAS uses **asymmetric cryptography exclusively**.

At a minimum, implementations require:

- a private key capable of signing or proving possession
- a corresponding public key for verification

Specific algorithms are intentionally unspecified at this stage.

---

### User Root Key

Each Client maintains a **User Root Key**.

Properties:

- generated locally
- non-exportable where supported
- never transmitted
- never escrowed
- bound to the local device or secure environment

The User Root Key represents the highest level of authority for the user.

---

### Per-Service Derived Keys

For each Service, the Client derives or generates a **service-specific key**.

Requirements:

- unique per Service
- cryptographically unlinkable across Services
- derivation must not allow recovery of the User Root Key
- compromise of one derived key must not affect others

Derivation MAY be:

- hierarchical
- deterministic
- or independent generation

The exact method is left to the specification phase.

---

## Service Identification and Binding

Each Service is identified by a **stable service identifier**.

Examples:

- web origin (scheme + host + port)
- application identifier
- cryptographic service ID

Authentication proofs MUST be bound to this identifier.

This prevents:

- phishing
- replay across services
- credential forwarding attacks

---

## Authentication Flow (Conceptual)

### Registration Phase

1. The Client identifies the Service.
2. The Client generates or derives a per-Service key pair.
3. The Client sends the public verification material to the Service.
4. The Service stores the public key and associates it with an internal account.

No secrets are exchanged.

---

### Authentication Phase

1. The Service generates a fresh, unpredictable challenge.
2. The Service sends the challenge to the Client.
3. The Client produces a cryptographic proof bound to:
   - the challenge
   - the Service identifier
4. The Client sends the proof to the Service.
5. The Service verifies the proof.
6. Authentication succeeds or fails.

Proofs are:

- single-use
- non-replayable
- service-bound

---

## User Interaction Model

User interaction MUST be:

- local
- minimal
- familiar

Examples:

- biometric confirmation
- device unlock
- explicit approval gesture

The user MUST NOT:

- type passwords
- copy codes
- make security decisions

User interaction exists only to authorize key usage, not to authenticate remotely.

---

## Multi-Device Support

OpenUAS supports multiple devices per user.

Approaches MAY include:

- independent User Root Keys per device
- controlled device registration
- device-to-device authorization flows

Requirements:

- no shared secrets
- no central authority required
- compromise of one device does not compromise others

---

## Recovery Design (High-Level)

Recovery is mandatory but must not weaken security.

Allowed recovery mechanisms MAY include:

- pre-registered secondary devices
- offline recovery material stored securely
- assisted recovery with explicit user presence

Recovery MUST NOT:

- rely on shared secrets
- reintroduce passwords or OTPs
- silently bypass security guarantees

Recovery flows MUST be explicit and auditable.

---

## Failure Handling

Implementations MUST fail safely.

Examples:

- authentication fails closed
- no automatic fallback to weaker methods
- partial outages do not expose credentials

Failure must not leak reusable authentication material.

---

## Forbidden Designs

The following designs are explicitly forbidden:

- password-based fallback
- SMS or email OTP authentication
- reusable API keys as user credentials
- global user identifiers
- silent downgrade of security
- mandatory central login services

---

## Relationship to Future Specifications

This document constrains all future OpenUAS specifications.

Any formal protocol or API:

- MUST be derivable from this design
- MUST preserve its guarantees
- MUST not contradict its constraints

Specification work refines this design; it does not replace it.

---

## Summary

This technical design defines **how OpenUAS should be built**, without locking the
project into premature protocol details.

It ensures:

- consistent implementations
- strong security properties
- long-term evolvability
- alignment with OpenUAS principles

This document is the foundation upon which formal specifications will be written.

---
