# OpenUAS – Governance

## Transparent, Anti-Capture Project Governance

Status: Draft  
Scope: Project governance, decision-making, and stewardship

---

## Purpose of This Document

This document defines how OpenUAS is governed.

Its goals are to:

- enable sustainable evolution of the project
- prevent capture by individuals, organizations, or interests
- ensure transparency and accountability
- protect the immutable principles of OpenUAS
- allow community participation without chaos

Governance exists to **limit power**, not to concentrate it.

---

## Core Governance Principles

OpenUAS governance is based on the following principles:

1. **Rules over authority**  
   Decisions are constrained by published rules, not personal power.

2. **Transparency by default**  
   Discussions, decisions, and changes must be observable and auditable.

3. **Minimal necessary structure**  
   Governance should be as simple as possible, but no simpler.

4. **Separation of concerns**  
   Specification, implementation, and stewardship are distinct roles.

5. **Anti-capture design**  
   No single actor must be indispensable.

---

## Roles

### Founder

The Founder is the individual who initiated OpenUAS and defined its original
vision and immutable principles.

Responsibilities:

- safeguard the immutable rules
- guide the project during its early phase
- facilitate the initial formation of the community

Limitations:

- the Founder does NOT own OpenUAS
- the Founder does NOT have unilateral control
- the Founder role is temporary by design

The Founder role is expected to phase out as the project matures.

---

### Maintainers

Maintainers are contributors responsible for the day-to-day evolution of the
project.

Responsibilities:

- review and merge contributions
- maintain documentation and specifications
- ensure consistency with the Core Model and Threat Model
- participate in design discussions

Requirements:

- sustained, meaningful contributions
- demonstrated understanding of OpenUAS principles
- adherence to transparent processes

Maintainers do not have absolute authority and act within governance rules.

---

### Stewards (Trust Set)

Stewards form the OpenUAS **Trust Set**.

They are responsible for protecting the long-term integrity of the project.

Responsibilities:

- approve changes that affect security guarantees
- oversee governance changes
- manage the conformance philosophy
- resolve escalated disputes

Properties:

- limited number of members
- geographic and organizational diversity
- rotating membership
- publicly documented membership

No Steward is permanent or irreplaceable.

---

## Decision-Making Process

### Normal Decisions

Most decisions are handled by Maintainers through:

- public discussion
- consensus seeking
- documented rationale

If consensus cannot be reached, Maintainers may proceed with a majority
decision, provided it does not conflict with immutable rules.

---

### Security-Critical Decisions

Decisions that affect:

- security properties
- trust assumptions
- core authentication behavior

require explicit approval from the Stewards.

Such decisions must:

- be documented
- include a security rationale
- include migration or mitigation considerations

---

### Immutable Rules Protection

The Immutable Rules defined in `IMMUTABLE_RULES.md` cannot be overridden.

If a proposed change conflicts with immutable rules:

- the change must be rejected
- or the project must explicitly fork

There is no governance mechanism to bypass immutable rules.

---

## Change and Evolution

### Proposals

Changes are introduced via public proposals:

- issues
- pull requests
- design documents

Each proposal must include:

- motivation
- impact analysis
- compatibility considerations

---

### Deprecation

OpenUAS favors backward compatibility.

When deprecation is unavoidable:

- it must be explicitly documented
- sufficient transition time must be provided
- security must not be weakened during transition

---

## Conflict Resolution

Disagreements are resolved through:

1. discussion
2. mediation by Maintainers
3. escalation to Stewards if necessary

Personal attacks, coercion, or opaque decision-making are unacceptable.

---

## Forking

Forking OpenUAS is permitted and protected.

However:

- only implementations and specifications that conform to OpenUAS rules
  may claim compatibility
- forks that violate immutable rules must not use the OpenUAS name

Compatibility is defined by conformance, not by lineage.

---

## Transparency Requirements

OpenUAS governance requires:

- public repositories
- public issue tracking
- public change history
- public documentation of roles

Private decision-making channels must not be used for governance decisions.

---

## Evolution of Governance

This governance model may evolve.

However:

- changes to governance must not weaken anti-capture properties
- changes must be approved by the Stewards
- changes must be publicly documented

Governance exists to serve OpenUAS, not the reverse.

---

## Summary

OpenUAS governance is designed to be:

- transparent
- minimal
- resilient
- accountable

By limiting authority and enforcing transparency, OpenUAS aims to remain a
public, trustworthy authentication system for the long term.

---
