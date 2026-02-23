# Trust Stack Specification (TS‑Spec) v1.0  
Canonical Technical Specification — Publication Edition

---

## Front Matter

**Title:** Trust Stack Specification (TS‑Spec) v1.0  
**Status:** Draft Specification  
**Version:** v1.0  
**Supersedes:** None (first edition)

**Steward:** SCU Foundation  
**Research Body:** Lattice Research Institute (LRI)

**Canonical Home:** https://latticeprotocol.org/specifications/ts/  
**HTML Edition:** https://latticeprotocol.org/specifications/ts/html/  
**PDF Edition:** https://latticeprotocol.org/specifications/ts/ts-spec-v1.0.pdf  
**GitHub Source:** https://github.com/SCU-Foundation/specifications/tree/main/ts

---

# 0. Preface

## 0.1 Purpose of TS‑Spec

The Trust Stack Specification (TS‑Spec) defines the **technical, implementation‑agnostic structures** that operationalise the Trust Stack Standard (TS v1.0).

Where TS v1.0 defines the *constitutional rules* of identity, provenance, safety, and trust, TS‑Spec v1.0 defines the **canonical technical structures** that implement those rules:

- identity metadata  
- provenance metadata  
- safety metadata  
- trust envelopes  
- trust‑state transitions  
- attestation metadata  
- trust‑level negotiation  
- trust validation rules  

TS‑Spec ensures **interoperability** across all Lattice‑conformant systems.

## 0.2 Scope

TS‑Spec defines:

- identity metadata structures  
- provenance metadata structures  
- safety metadata structures  
- trust envelopes  
- trust‑state machines  
- trust‑level negotiation rules  
- attestation metadata  
- trust validation rules  

TS‑Spec does **not** define:

- semantic primitives (LP Spec governs these)  
- meta‑semantic schemas (LM Spec governs these)  
- graph schemas (LW Spec governs these)  
- identity token structures (LIT Spec governs these)  

## 0.3 Normative Status

This document is **normative**.  
Requirements expressed using **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** follow RFC 2119.

## 0.4 Relationship to TS v1.0

TS‑Spec is the **technical companion** to TS v1.0.

- TS defines *what trust is*  
- TS‑Spec defines *how trust is represented*  

TS‑Spec MUST comply with TS v1.0 and MUST NOT weaken or contradict any TS guarantees.

---

# 1. Trust Metadata Model

## 1.1 Overview

All Lattice‑conformant systems MUST attach **trust metadata** to:

- semantic packets  
- semantic envelopes  
- graph nodes  
- graph edges  
- identity tokens  
- attestation surfaces  

Trust metadata is composed of:

- identity metadata  
- provenance metadata  
- safety metadata  
- trust‑level metadata  
- environment metadata  

---

# 2. Identity Metadata

## 2.1 Purpose

Identity metadata binds trust to explicit identity.

## 2.2 Structure

Identity metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `identity_key` | Primary identity key | YES |
| `identity_type` | Human, agent, device, system | YES |
| `identity_domain` | Domain of identity issuance | YES |
| `identity_version` | Version of identity metadata | YES |
| `identity_provenance` | Provenance of identity issuance | YES |
| `identity_constraints` | Constraints on identity usage | OPTIONAL |

## 2.3 Requirements

Identity metadata MUST:

- be explicit  
- be verifiable  
- be non‑inferential  
- be domain‑bounded  
- be provenance‑anchored  

Identity metadata MUST NOT:

- be inferred  
- be implicit  
- cross identity boundaries without authorization  

---

# 3. Provenance Metadata

## 3.1 Purpose

Provenance metadata records the origin, lineage, and transformation history of content.

## 3.2 Structure

Provenance metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `origin_identity` | Identity of originator | YES |
| `origin_timestamp` | Timestamp of creation | YES |
| `origin_domain` | Domain of origin | YES |
| `transformation_chain` | Ordered list of transformations | YES |
| `provenance_version` | Version of provenance metadata | YES |

## 3.3 Requirements

Provenance metadata MUST:

- be immutable  
- be append‑only  
- be identity‑anchored  
- be domain‑bounded  

Systems MUST reject:

- missing provenance  
- ambiguous provenance  
- inferred provenance  

---

# 4. Safety Metadata

## 4.1 Purpose

Safety metadata encodes safety‑critical information required by TS v1.0.

## 4.2 Structure

Safety metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `safety_level` | Safety classification | YES |
| `safety_constraints` | Safety rules applied | YES |
| `safety_provenance` | Provenance of safety evaluation | YES |
| `safety_timestamp` | Timestamp of safety evaluation | YES |
| `safety_version` | Version of safety metadata | YES |

## 4.3 Requirements

Safety metadata MUST:

- be explicit  
- be deterministic  
- be non‑inferential  
- comply with TS safety rules  

Systems MUST reject:

- missing safety metadata  
- ambiguous safety metadata  
- inferred safety metadata  

---

# 5. Trust Envelope

## 5.1 Purpose

The trust envelope is the **canonical container** for trust metadata.

## 5.2 Structure

A trust envelope MUST contain:

- identity metadata  
- provenance metadata  
- safety metadata  
- trust‑level metadata  
- environment metadata  

## 5.3 Envelope Rules

Trust envelopes MUST:

- be explicit  
- be deterministic  
- be non‑inferential  
- be identity‑anchored  
- be provenance‑anchored  

Trust envelopes MUST NOT:

- imply trust not explicitly encoded  
- cross trust boundaries without authorization  

---

# 6. Trust‑Level Metadata

## 6.1 Purpose

Defines the trust level of content.

## 6.2 Structure

Trust‑level metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `trust_level` | Trust classification | YES |
| `trust_basis` | Basis for trust level | YES |
| `trust_provenance` | Provenance of trust evaluation | YES |
| `trust_timestamp` | Timestamp of trust evaluation | YES |
| `trust_version` | Version of trust metadata | YES |

## 6.3 Requirements

Trust‑level metadata MUST:

- be explicit  
- be deterministic  
- be non‑inferential  
- comply with TS trust rules  

---

# 7. Trust‑State Machine

## 7.1 Purpose

Defines how trust transitions between states.

## 7.2 States

TS‑Spec defines the following trust states:

- **Untrusted**  
- **Partially Trusted**  
- **Trusted**  
- **Revoked**  
- **Invalid**  

## 7.3 Transitions

Transitions MUST:

- be explicit  
- be deterministic  
- be logged  
- be identity‑anchored  
- be provenance‑anchored  

Systems MUST reject:

- inferred transitions  
- ambiguous transitions  
- unauthorized transitions  

---

# 8. Trust‑Level Negotiation

## 8.1 Purpose

Defines how systems negotiate trust levels.

## 8.2 Requirements

Systems MUST:

- negotiate trust explicitly  
- negotiate trust deterministically  
- anchor negotiation to identity  
- anchor negotiation to provenance  

Systems MUST NOT:

- infer trust  
- assume trust  
- weaken trust guarantees  

---

# 9. Attestation Metadata

## 9.1 Purpose

Defines metadata required for attestation.

## 9.2 Structure

Attestation metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `attestation_identity` | Identity of attester | YES |
| `attestation_basis` | Basis for attestation | YES |
| `attestation_timestamp` | Timestamp of attestation | YES |
| `attestation_provenance` | Provenance of attestation | YES |
| `attestation_version` | Version of attestation metadata | YES |

---

# 10. Conformance

## 10.1 Conformance Requirements

A system conforms to TS‑Spec v1.0 if and only if:

- it implements all metadata structures defined in Sections 2–9  
- it complies with TS v1.0  
- it exposes sufficient metadata to verify trust correctness  

## 10.2 Non‑Conformance

Systems that:

- partially implement TS‑Spec  
- weaken TS guarantees  
- omit required metadata  

**MUST NOT** claim TS‑Spec conformance.

---

# Appendix A — Glossary (Non‑Normative)

**Trust Envelope**  
Canonical container for trust metadata.

**Trust‑State Machine**  
Defines trust transitions.

**Attestation Metadata**  
Metadata describing trust verification.

---

# Appendix B — Versioning & Registry (Non‑Normative)

- TS‑Spec v1.0 is registered in the SCU Foundation Specifications Registry.  
- Future versions MUST document changes and compatibility guarantees.  
- Implementations SHOULD track TS‑Spec version and conformance level.

---

# TS Specification v1.0 — COMPLETE
