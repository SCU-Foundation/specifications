# Lattice Identity Token Specification (LIT‑Spec) v1.0  
Canonical Technical Specification — Publication Edition

---

## Front Matter

**Title:** Lattice Identity Token Specification (LIT‑Spec) v1.0  
**Status:** Draft Specification  
**Version:** v1.0  
**Supersedes:** None (first edition)

**Steward:** SCU Foundation  
**Research Body:** Lattice Research Institute (LRI)

**Canonical Home:** https://latticeprotocol.org/specifications/lit/  
**HTML Edition:** https://latticeprotocol.org/specifications/lit/html/  
**PDF Edition:** https://latticeprotocol.org/specifications/lit/lit-spec-v1.0.pdf  
**GitHub Source:** https://github.com/SCU-Foundation/specifications/tree/main/lit

---

# 0. Preface

## 0.1 Purpose of LIT‑Spec

The Lattice Identity Token Specification (LIT‑Spec) defines the **technical, implementation‑agnostic structures** that operationalise the Lattice Identity Token Standard (LIT v1.0).

Where LIT v1.0 defines the *constitutional rules* of identity, provenance, attestation, boundaries, and revocation, LIT‑Spec defines the **canonical token format, identity metadata structures, attestation schemas, revocation metadata, and validation rules** that implement those rules in interoperable systems.

LIT‑Spec ensures that identity is:

- explicit  
- deterministic  
- non‑inferential  
- provenance‑anchored  
- domain‑bounded  
- safe  
- interoperable  

## 0.2 Scope

LIT‑Spec defines:

- identity token format  
- identity metadata structures  
- identity provenance metadata  
- identity constraints  
- attestation metadata  
- revocation metadata  
- identity boundary metadata  
- identity validity metadata  
- canonical serialization rules  
- identity error semantics  

LIT‑Spec does **not** define:

- semantic primitives (LP‑Spec governs these)  
- contextual metadata (LM‑Spec governs these)  
- graph schemas (LW‑Spec governs these)  
- trust metadata structures (TS‑Spec governs these)  

## 0.3 Normative Status

This document is **normative**.

## 0.4 Relationship to LIT v1.0

LIT‑Spec is the **technical companion** to LIT v1.0.

- LIT defines *what identity is*  
- LIT‑Spec defines *how identity is represented*  

LIT‑Spec MUST comply with LIT v1.0 and MUST NOT weaken or contradict any LIT guarantees.

---

# 1. Identity Token Format

## 1.1 Overview

A **Lattice Identity Token (LIT)** is the canonical container for identity metadata.

All identity tokens MUST include:

- identity metadata  
- identity provenance  
- identity constraints  
- attestation metadata  
- revocation metadata  
- identity boundaries  
- identity validity metadata  
- version metadata  

## 1.2 Token Structure

A LIT MUST contain the following top‑level fields:

| Field | Description | Required |
|-------|-------------|----------|
| `identity` | Identity metadata | YES |
| `provenance` | Identity provenance metadata | YES |
| `constraints` | Identity constraints | OPTIONAL |
| `attestation` | Attestation metadata | YES |
| `revocation` | Revocation metadata | OPTIONAL |
| `boundaries` | Identity boundary metadata | YES |
| `validity` | Identity validity metadata | YES |
| `version` | LIT‑Spec version | YES |

---

# 2. Identity Metadata

## 2.1 Purpose

Defines the canonical identity attributes.

## 2.2 Structure

Identity metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `identity_key` | Primary identity key | YES |
| `identity_type` | Human, agent, device, system | YES |
| `identity_domain` | Domain of identity issuance | YES |
| `identity_version` | Version of identity metadata | YES |
| `identity_label` | Human‑readable label | OPTIONAL |
| `identity_constraints` | Constraints on identity usage | OPTIONAL |

## 2.3 Requirements

Identity metadata MUST:

- be explicit  
- be deterministic  
- be non‑inferential  
- be domain‑bounded  
- be provenance‑anchored  

Identity metadata MUST NOT:

- be inferred  
- be implicit  
- cross identity boundaries without authorization  

---

# 3. Identity Provenance Metadata

## 3.1 Purpose

Defines the origin and lineage of identity.

## 3.2 Structure

Identity provenance MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `issuer_identity` | Identity of issuer | YES |
| `issuer_domain` | Domain of issuer | YES |
| `issuance_timestamp` | Timestamp of issuance | YES |
| `issuance_basis` | Basis for issuance | YES |
| `transformation_chain` | Ordered list of identity transformations | YES |
| `provenance_version` | Version of provenance metadata | YES |

## 3.3 Requirements

Identity provenance MUST:

- be immutable  
- be append‑only  
- be identity‑anchored  
- be domain‑bounded  

Systems MUST reject:

- missing provenance  
- ambiguous provenance  
- inferred provenance  

---

# 4. Identity Constraints

## 4.1 Purpose

Defines limits on identity usage.

## 4.2 Structure

Identity constraints MAY include:

| Field | Description |
|-------|-------------|
| `usage_scope` | Allowed usage scope |
| `domain_restrictions` | Domain restrictions |
| `temporal_constraints` | Time‑based constraints |
| `delegation_rules` | Delegation constraints |

## 4.3 Requirements

Constraints MUST:

- be explicit  
- be deterministic  
- be non‑inferential  

---

# 5. Attestation Metadata

## 5.1 Purpose

Defines how identity is verified.

## 5.2 Structure

Attestation metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `attester_identity` | Identity of attester | YES |
| `attestation_basis` | Basis for attestation | YES |
| `attestation_timestamp` | Timestamp of attestation | YES |
| `attestation_provenance` | Provenance of attestation | YES |
| `attestation_version` | Version of attestation metadata | YES |

## 5.3 Requirements

Attestation MUST:

- be explicit  
- be deterministic  
- be identity‑anchored  
- be provenance‑anchored  

Systems MUST reject:

- inferred attestation  
- ambiguous attestation  
- unauthorized attestation  

---

# 6. Revocation Metadata

## 6.1 Purpose

Defines how identity is revoked.

## 6.2 Structure

Revocation metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `revocation_status` | Active, inactive | YES |
| `revocation_reason` | Reason for revocation | YES |
| `revocation_timestamp` | Timestamp of revocation | YES |
| `revocation_authority` | Identity of revoking authority | YES |
| `revocation_provenance` | Provenance of revocation | YES |

## 6.3 Requirements

Revocation MUST:

- be explicit  
- be deterministic  
- be identity‑anchored  
- be provenance‑anchored  

---

# 7. Identity Boundary Metadata

## 7.1 Purpose

Defines the limits of identity inference and cross‑domain identity.

## 7.2 Structure

Boundary metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `identity_domain` | Domain boundary | YES |
| `identity_scope` | Scope boundary | YES |
| `delegation_boundary` | Delegation boundary | OPTIONAL |
| `cross_domain_rules` | Cross‑domain identity rules | OPTIONAL |

---

# 8. Identity Validity Metadata

## 8.1 Purpose

Defines rules for validating identity correctness.

## 8.2 Structure

Validity metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `structural_validity` | Structural correctness | YES |
| `provenance_validity` | Provenance correctness | YES |
| `attestation_validity` | Attestation correctness | YES |
| `revocation_validity` | Revocation correctness | YES |
| `identity_validity` | Identity correctness | YES |
| `version` | Validity metadata version | YES |

---

# 9. Canonical Serialization

## 9.1 Purpose

Defines the canonical encoding format.

## 9.2 Requirements

Serialization MUST:

- be deterministic  
- be reversible  
- be lossless  
- be implementation‑agnostic  

Canonical ordering MUST be:

1. identity  
2. provenance  
3. constraints  
4. attestation  
5. revocation  
6. boundaries  
7. validity  
8. version  

---

# 10. Identity Error Semantics

## 10.1 Purpose

Defines how invalid identity is reported.

## 10.2 Error Types

LIT‑Spec MUST define:

- structural errors  
- provenance errors  
- attestation errors  
- revocation errors  
- boundary errors  
- identity errors  

Each error MUST include:

- error type  
- error reason  
- error provenance  
- error identity  
- error timestamp  

---

# 11. Conformance

A system conforms to LIT‑Spec v1.0 if and only if:

- it implements all structures defined in Sections 1–10  
- it complies with LIT v1.0  
- it complies with TS‑Spec v1.0  
- it exposes sufficient metadata to verify identity correctness  

---

# Lattice Identity Token Specification (LIT‑Spec) v1.0 — COMPLETE
