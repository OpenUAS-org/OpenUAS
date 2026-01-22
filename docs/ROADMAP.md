# OpenUAS – Roadmap

Status: Living document  
Scope: Strategic and architectural progression (non-technical implementation details)

---

## Purpose of This Roadmap

This roadmap defines the **intended evolution path** of OpenUAS.

It is not a promise of timelines, features, or deliverables.
It exists to:

- keep the project focused
- avoid premature implementation
- prevent scope creep
- ensure alignment with OpenUAS immutable principles

OpenUAS prioritizes correctness, ethics, and resilience over speed.

---

## Phase 0 — Foundations (Current)

### Objectives

- Establish the philosophical, ethical, and architectural foundations
- Prevent future capture, drift, or vendorization
- Create a shared mental model before writing code

### Deliverables

- Immutable principles (`IMMUTABLE_RULES.md`)
- Vision document (`OPEN_UAS_VISION.md`)
- Project overview (`README.md`)
- High-level roadmap (this document)

### Exit Criteria

- Principles are stable and publicly defensible
- Vision is clear to external readers
- Project scope is explicitly limited

---

## Phase 1 — Conceptual Architecture

### Objectives

- Translate principles into a shared architectural model
- Define actors, trust boundaries, and responsibilities
- Avoid premature standardization or wire formats

### Focus Areas

- Authentication mental model
- Trust and verification flow
- Client–service interaction
- Optional registry role (non-critical, non-authoritative)
- Failure and recovery scenarios

### Deliverables

- Core model document (conceptual, no protocol syntax)
- Threat model (what OpenUAS defends against and what it does not)
- Glossary and terminology alignment

### Exit Criteria

- Architecture can be explained without diagrams or code
- Threat assumptions are explicit and agreed upon
- No contradictions with immutable rules

---

## Phase 2 — Governance and Trust Model

### Objectives

- Define how OpenUAS evolves without central control
- Prevent single-person or single-organization capture
- Establish long-term sustainability

### Focus Areas

- Governance roles and responsibilities
- Decision-making processes
- Trust set concept (rules, not authorities)
- Transparency and accountability mechanisms
- Forking and compatibility enforcement

### Deliverables

- Governance document (`GOVERNANCE.md`)
- Change and deprecation process
- Trust and conformance philosophy

### Exit Criteria

- Governance is understandable and auditable
- No role is indispensable
- Abuse and stagnation scenarios are addressed

---

## Phase 3 — Minimal Core Specification (v0.x)

### Objectives

- Define the smallest possible interoperable core
- Preserve maximal flexibility for future extensions
- Avoid feature inflation

### Focus Areas

- Authentication primitives
- Proof verification requirements
- Per-service key isolation rules
- Recovery requirements
- Error handling principles

### Deliverables

- Core specification draft (informational)
- Explicit list of non-goals
- Extension mechanism definition

### Exit Criteria

- Core can be implemented independently by multiple parties
- No dependency on specific vendors or platforms
- Specification remains readable and minimal

---

## Phase 4 — Conformance and Verification

### Objectives

- Ensure interoperability without central enforcement
- Replace authority with verifiable behavior

### Focus Areas

- Conformance test philosophy
- Continuous compliance concepts
- Transparency and auditability
- Failure visibility

### Deliverables

- Conformance requirements document
- Initial test vectors (conceptual)
- Transparency log model

### Exit Criteria

- Compatibility is objectively measurable
- Forks are possible but non-interoperable by default
- Trust is derived from observable compliance

---

## Phase 5 — Reference Implementations (Non-Normative)

### Objectives

- Prove feasibility without becoming a de facto monopoly
- Enable experimentation and feedback

### Focus Areas

- Client reference implementation
- Service-side reference implementation
- Clear separation between spec and code

### Deliverables

- At least two independent reference implementations
- Developer documentation
- Security review notes

### Exit Criteria

- Implementations are replaceable
- No implementation becomes mandatory
- Spec remains the source of truth

---

## Phase 6 — Community Expansion

### Objectives

- Grow a healthy, aligned contributor community
- Encourage adoption without compromising principles

### Focus Areas

- Contributor onboarding
- Review and moderation processes
- Community norms and code of conduct

### Deliverables

- Contribution guidelines
- Community governance practices
- Public discussion channels

### Exit Criteria

- Contributions improve quality, not noise
- Disagreements are resolved through process, not power
- Core principles remain intact

---

## Phase 7 — Standardization Path (Optional)

### Objectives

- Explore formal standardization if and only if beneficial
- Preserve OpenUAS principles under external processes

### Focus Areas

- Interaction with standards bodies (e.g., IETF, W3C)
- Risk assessment of formal standardization
- Preservation of governance independence

### Deliverables

- Position papers
- Compatibility analysis
- Formal proposals (if appropriate)

### Exit Criteria

- Standardization does not weaken principles
- Governance safeguards remain enforceable
- OpenUAS remains open and neutral

---

## Guiding Principle

At every phase, OpenUAS must answer one question:

> Does this step increase long-term security, resilience, and public trust
> without concentrating power?

If the answer is not clearly yes, the step should not be taken.

---
