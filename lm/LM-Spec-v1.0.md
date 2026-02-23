# Lattice Meta Specification (LM‑Spec) v1.0  
Canonical Technical Specification — Publication Edition

---

## Front Matter

**Title:** Lattice Meta Specification (LM‑Spec) v1.0  
**Status:** Draft Specification  
**Version:** v1.0  
**Supersedes:** None (first edition)

**Steward:** SCU Foundation  
**Research Body:** Lattice Research Institute (LRI)

**Canonical Home:** https://latticeprotocol.org/specifications/lm/  
**HTML Edition:** https://latticeprotocol.org/specifications/lm/html/  
**PDF Edition:** https://latticeprotocol.org/specifications/lm/lm-spec-v1.0.pdf  
**GitHub Source:** https://github.com/SCU-Foundation/specifications/tree/main/lm

---

# 0. Preface

## 0.1 Purpose of LM‑Spec

The Lattice Meta Specification (LM‑Spec) defines the **technical, implementation‑agnostic structures** that operationalise the Lattice Meta Standard (LM v1.0).

Where LM v1.0 defines the *meta‑semantic rules* of contextual meaning, alignment, and cross‑domain coherence, LM‑Spec defines the **canonical metadata structures, contextual envelopes, alignment schemas, and validation rules** that implement those rules in interoperable systems.

LM‑Spec ensures that contextual meaning is:

- explicit  
- deterministic  
- identity‑anchored  
- provenance‑anchored  
- domain‑bounded  
- non‑inferential  
- safe  
- interoperable  

## 0.2 Scope

LM‑Spec defines:

- contextual metadata structures  
- contextual envelope format  
- alignment metadata  
- meta‑semantic boundary metadata  
- contextual validity metadata  
- canonical serialization rules  
- error semantics  

LM‑Spec does **not** define:

- semantic primitives (LP‑Spec governs these)  
- graph schemas (LW‑Spec governs these)  
- identity token structures (LIT‑Spec governs these)  
- trust metadata structures (TS‑Spec governs these)  

## 0.3 Normative Status

This document is **normative**.

## 0.4 Relationship to LM v1.0

LM‑Spec is the **technical companion** to LM v1.0.

- LM defines *what contextual meaning is*  
- LM‑Spec defines *how contextual meaning is represented*  

LM‑Spec MUST comply with LM v1.0 and MUST NOT weaken or contradict any LM guarantees.

---

# 1. Contextual Metadata Model

## 1.1 Overview

All Lattice‑conformant systems MUST attach **contextual metadata** to:

- semantic packets  
- semantic envelopes  
- graph nodes  
- graph edges  
- identity tokens  
- attestation surfaces  

Contextual metadata is composed of:

- contextual frames  
- contextual modifiers  
- alignment anchors  
- contextual provenance  
- contextual constraints  

---

# 2. Contextual Frame Encoding

## 2.1 Purpose

Defines the canonical structure of a contextual frame.

## 2.2 Structure

A contextual frame MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `frame_type` | Type of contextual frame | YES |
| `context_domain` | Domain of contextual meaning | YES |
| `context_scope` | Scope of contextual meaning | YES |
| `identity` | Identity binding (LIT‑Spec) | YES |
| `provenance` | Contextual provenance metadata | YES |
| `modifiers` | List of contextual modifiers | OPTIONAL |
| `constraints` | Contextual constraints | OPTIONAL |

## 2.3 Requirements

Contextual frames MUST:

- be explicit  
- be deterministic  
- be identity‑anchored  
- be provenance‑anchored  
- be domain‑bounded  

Frames MUST NOT:

- imply context not explicitly encoded  
- cross contextual boundaries without authorization  

---

# 3. Contextual Modifiers

## 3.1 Purpose

Modifiers refine or qualify contextual meaning.

## 3.2 Structure

Each modifier MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `modifier_type` | Type of modifier | YES |
| `value` | Modifier value | YES |
| `domain` | Domain of modifier | YES |
| `identity` | Identity binding | YES |
| `provenance` | Provenance metadata | YES |

## 3.3 Requirements

Modifiers MUST:

- be explicit  
- be deterministic  
- be non‑inferential  

---

# 4. Alignment Metadata

## 4.1 Purpose

Defines how meaning is aligned across domains, contexts, and semantic structures.

## 4.2 Structure

Alignment metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `alignment_type` | Type of alignment | YES |
| `source_context` | Source contextual frame | YES |
| `target_context` | Target contextual frame | YES |
| `alignment_basis` | Basis for alignment | YES |
| `identity` | Identity binding | YES |
| `provenance` | Provenance metadata | YES |

## 4.3 Requirements

Alignment MUST:

- be explicit  
- be deterministic  
- be identity‑anchored  
- be provenance‑anchored  

Systems MUST reject:

- inferred alignment  
- ambiguous alignment  
- unauthorized cross‑domain alignment  

---

# 5. Contextual Envelope Encoding

## 5.1 Purpose

Defines how contextual meaning is grouped into coherent units.

## 5.2 Envelope Types

LM‑Spec MUST support:

- `contextual_frame_envelope`  
- `alignment_envelope`  
- `contextual_assertion_envelope`  
- `contextual_constraint_envelope`  

## 5.3 Envelope Structure

Each envelope MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `type` | Envelope type | YES |
| `frames` | List of contextual frames | YES |
| `alignment` | Alignment metadata | OPTIONAL |
| `identity` | Identity binding | YES |
| `provenance` | Provenance metadata | YES |

---

# 6. Meta‑Semantic Boundary Metadata

## 6.1 Purpose

Defines the limits of contextual inference and cross‑domain meaning.

## 6.2 Boundary Types

LM‑Spec MUST encode:

- contextual boundaries  
- domain boundaries  
- identity boundaries  
- semantic scope boundaries  

## 6.3 Boundary Structure

| Field | Description | Required |
|-------|-------------|----------|
| `context_domain` | Domain boundary | YES |
| `context_scope` | Scope boundary | YES |
| `identity_boundary` | Identity boundary | YES |
| `semantic_scope` | Semantic scope | YES |

---

# 7. Contextual Validity Metadata

## 7.1 Purpose

Defines rules for validating contextual meaning.

## 7.2 Structure

Validity metadata MUST include:

| Field | Description | Required |
|-------|-------------|----------|
| `structural_validity` | Structural correctness | YES |
| `contextual_validity` | Contextual correctness | YES |
| `alignment_validity` | Alignment correctness | OPTIONAL |
| `provenance_validity` | Provenance correctness | YES |
| `identity_validity` | Identity correctness | YES |
| `version` | Validity metadata version | YES |

## 7.3 Requirements

Systems MUST reject:

- ambiguous context  
- inferred context  
- cross‑domain context  
- identity‑implicit context  
- unsafe context  

---

# 8. Canonical Serialization

## 8.1 Purpose

Defines the canonical encoding format.

## 8.2 Requirements

Serialization MUST:

- be deterministic  
- be reversible  
- be lossless  
- be implementation‑agnostic  

Canonical ordering MUST be:

1. contextual frames  
2. modifiers  
3. alignment metadata  
4. boundaries  
5. validity  
6. identity  
7. provenance  
8. version  

---

# 9. Error Semantics

## 9.1 Purpose

Defines how invalid contextual meaning is reported.

## 9.2 Error Types

LM‑Spec MUST define:

- structural errors  
- contextual errors  
- alignment errors  
- boundary errors  
- identity errors  
- provenance errors  

Each error MUST include:

- error type  
- error reason  
- error provenance  
- error identity  
- error timestamp  

---

# 10. Conformance

A system conforms to LM‑Spec v1.0 if and only if:

- it implements all structures defined in Sections 1–9  
- it complies with LM v1.0  
- it complies with LP‑Spec v1.0  
- it complies with TS‑Spec v1.0  
- it exposes sufficient metadata to verify contextual correctness  

---

# Lattice Meta Specification (LM‑Spec) v1.0 — COMPLETE
