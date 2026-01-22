# OpenUAS

## Open Source Universal Authentication System

OpenUAS is an open, vendor-neutral authentication system designed to replace
password-based login with a secure, phishing-resistant, and human-friendly
alternative.

It is not a product.
It is not a platform.
It is a public digital infrastructure.

---

## The Problem

Passwords dominate the internet despite being fundamentally broken.

They are:

- reused across services
- easily phished
- leaked in large-scale breaches
- incompatible with human behavior

At the same time, identity is increasingly centralized under a small number of
large providers, creating systemic risks, power concentration, and single points
of failure.

OpenUAS exists to solve this problem at its root.

---

## What OpenUAS Provides

OpenUAS defines a universal authentication protocol that is:

- **Phishing-resistant by design**
- **Passwordless and secret-free**
- **Privacy-preserving (no cross-service tracking)**
- **Usable by non-technical users**
- **Compatible with web and native applications**
- **Independent from centralized identity providers**
- **Open-source and publicly auditable**

Authentication is based on cryptographic proof of possession, not on knowledge
of secrets.

---

## What OpenUAS Does NOT Do

OpenUAS is intentionally limited in scope.

It does NOT:

- manage user identities or personal data
- provide authorization or access control
- act as a login provider or intermediary
- require proprietary platforms or services
- replace existing applications or protocols

OpenUAS focuses exclusively on authentication.

---

## Design Principles

OpenUAS is built on a small set of immutable principles:

- No shared secrets (no passwords, no reusable OTPs)
- Phishing resistance by default
- User-controlled, non-exportable cryptographic roots
- Per-service cryptographic isolation
- Minimal core, explicit extensions
- Secure recovery as a first-class requirement
- Transparency over authority
- Forking allowed, compatibility earned
- Governance designed to prevent capture

These principles are defined in detail in
[`docs/IMMUTABLE_RULES.md`](./docs/IMMUTABLE_RULES.md).

---

## Architecture Overview (Conceptual)

At a high level, OpenUAS works as follows:

1. The user authenticates locally using a secure, non-exportable cryptographic
   root (hardware-backed when available).
2. For each service, unique cryptographic material is generated or derived.
3. Authentication is performed via challenge–response proofs bound to the
   service identifier.
4. No shared secrets are transmitted or stored.
5. Servers verify proofs using public keys only.

Optional registry components may be used for discovery, anchoring, or
transparency, but are not required for authentication.

---

## Governance Model

OpenUAS is governed by rules, not by owners.

- The specification is open and public
- Multiple independent implementations are encouraged
- Compatibility is defined by conformance tests
- No single individual or organization controls the system
- Governance roles are limited, transparent, and rotatable

See [`docs/OPEN_UAS_VISION.md`](./docs/OPEN_UAS_VISION.md) for the full vision and
philosophy.

---

## Project Status

OpenUAS is in an **early design phase**.

Current focus:

- defining immutable principles
- establishing governance foundations
- designing a minimal, robust core protocol

No production-ready implementation exists yet.

---

## Who Is This For?

OpenUAS is for:

- developers and security engineers
- researchers and protocol designers
- organizations seeking strong authentication without vendor lock-in
- anyone interested in improving global digital security

---

## How to Contribute

OpenUAS welcomes contributions aligned with its principles.

At this stage, the most valuable contributions are:

- design reviews
- threat modeling
- governance feedback
- protocol critique

Code contributions will be invited once the core design stabilizes.

---

## License

OpenUAS specifications and reference materials are released under an open
license. Specific licensing details will be defined as the project matures.

---

## Final Note

OpenUAS aims to make strong authentication universal, invisible, and boring.

Its success will not be measured by market share, but by a future where
passwords are no longer necessary.

---

# Documentation Index

## Overview

- [Immutable Principles](./docs/IMMUTABLE_PRINCIPLES.md)
- [Vision](./docs/OPEN_UAS_VISION.md)
- [Core Model](./docs/CORE_MODEL.md)
- [Threat Model](./docs/THREAT_MODEL.md)
