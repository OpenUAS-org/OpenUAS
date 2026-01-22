# OpenUAS – Registry Model

## Optional Transparency and Discovery Component

Status: Draft  
Scope: Registry design, constraints, and anti-capture guarantees (pre-spec, non-normative)

---

## Purpose of This Document

This document defines the **OpenUAS Registry Model**.

The Registry is an **optional component** of the OpenUAS ecosystem.
It exists to improve transparency, auditability, and interoperability,
without becoming a point of control, authority, or authentication.

The Registry MUST NOT:

- authenticate users
- authorize access
- act as an identity provider
- become a mandatory dependency

Authentication MUST remain fully functional without any Registry.

---

## Core Principles

The Registry Model is governed by the following principles:

1. **Optionality**  
   The Registry MUST NOT be required for authentication.

2. **Non-Authority**  
   The Registry MUST NOT make trust decisions on behalf of Clients or Services.

3. **Transparency over Control**  
   The Registry exists to publish information, not to enforce behavior.

4. **Verifiability**  
   All Registry data MUST be publicly verifiable.

5. **Anti-Capture**  
   No single Registry instance MUST be able to dominate the ecosystem.

---

## Registry Responsibilities

The Registry MAY provide the following functions:

- publication of public parameters
- discovery of OpenUAS-capable services
- publication of conformance statements
- transparency logs
- publication of revocation signals

The Registry MUST NOT exceed these responsibilities.

---

## What the Registry Is NOT

The Registry is NOT:

- a login service
- an authentication intermediary
- a user database
- a credential store
- an authorization engine
- a policy enforcement point

Any Registry behaving as such is non-compliant.

---

## Data Characteristics

All data published in a Registry MUST be:

- public
- append-only where possible
- cryptographically verifiable
- non-sensitive
- safe to mirror

Registries MUST NOT store:

- private keys
- shared secrets
- user-identifying information

---

## Transparency Logs

Registries MAY implement **transparency logs**.

Transparency logs:

- are append-only
- are publicly auditable
- allow independent verification
- detect equivocation or manipulation

Examples of logged data:

- service public keys
- conformance claims
- registry statements

---

## Conformance Publication

Registries MAY publish **conformance assertions**.

Conformance assertions:

- declare which OpenUAS documents a service claims to implement
- reference specific versions
- are informational, not authoritative

Clients and Services MUST verify conformance independently.

---

## Revocation Signals

Registries MAY publish revocation signals.

Revocation signals:

- indicate that a key or service should no longer be trusted
- are advisory only
- MUST be cryptographically signed
- MUST include reason and timestamp

Clients and Services decide how to interpret revocation signals.

---

## Discovery Function (Optional)

Registries MAY assist in service discovery.

Discovery information MAY include:

- service endpoints
- supported OpenUAS versions
- public parameters

Discovery MUST NOT:

- imply trust
- imply endorsement
- replace verification

---

## Multiple Registries

The OpenUAS ecosystem supports **multiple independent Registries**.

Properties:

- no global Registry
- no canonical Registry
- Registries may mirror each other
- Clients may consult none, one, or many Registries

Diversity of Registries is a security feature.

---

## Client Interaction Model

Clients interacting with Registries MUST:

- treat Registry data as untrusted input
- verify cryptographic signatures
- tolerate Registry unavailability
- continue operating without Registry access

Registries MUST NOT be a single point of failure.

---

## Anti-Capture Safeguards

To prevent capture, the Registry Model enforces:

- optional participation
- no exclusive control
- no mandatory endorsement
- verifiable behavior over reputation

Any attempt to centralize trust in a Registry violates OpenUAS principles.

---

## Failure and Degradation

If a Registry becomes unavailable or compromised:

- authentication MUST continue
- Clients MAY ignore the Registry
- no security downgrade occurs

Registry failure MUST NOT cascade.

---

## Relationship to Governance

Registry behavior is constrained by:

- Immutable Rules
- Governance Model
- Conformance philosophy

Registries are participants, not governors.

---

## Forbidden Registry Designs

The following Registry designs are explicitly forbidden:

- mandatory Registry dependency
- Registry-issued authentication tokens
- user identity tracking
- silent trust enforcement
- proprietary Registry protocols

---

## Summary

The OpenUAS Registry is a **supporting component**, not a control plane.

It improves:

- transparency
- interoperability
- observability

while preserving:

- decentralization
- user sovereignty
- system resilience

A Registry that becomes authoritative is no longer compatible with OpenUAS.

---
