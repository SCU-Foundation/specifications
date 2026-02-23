# Lattice Specifications

The Lattice Protocol specifications define the **technical, implementation‑agnostic structures** that operationalise the Lattice Standards.  
Where the standards define the constitutional rules of identity, semantics, trust, context, and graph structure, the specifications define the **concrete technical formats** that ensure interoperability across agents, devices, runtimes, and vendors.

Specifications describe **how** the rules of the standards are implemented in practice.

---

## Purpose of the Specifications

The specifications provide:

- canonical packet formats  
- semantic and meta‑semantic schemas  
- graph schemas and node/edge definitions  
- identity token structures and attestation metadata  
- domain‑agnostic, transport‑agnostic encoding rules  
- validation and error semantics  
- interoperability guarantees  

Specifications do **not** describe implementations.  
They define the **structures that all compliant implementations MUST support**.

---

## Available Specifications

The following specifications are published under this directory:

### **TS Specification — Trust Stack**
Defines trust metadata, trust envelopes, trust‑state machines, attestation metadata, and provenance structures.

### **LP Specification — Lattice Protocol**
Defines semantic packet formats, primitive encoding, semantic envelopes, boundary metadata, and semantic validity.

### **LM Specification — Lattice Meta**
Defines contextual metadata, contextual frames, alignment metadata, contextual envelopes, and meta‑semantic validity.

### **LW Specification — Lattice Web**
Defines graph schemas, node and edge encoding, graph envelopes, graph‑level boundaries, and graph‑level validity.

### **LIT Specification — Lattice Identity Token**
Defines identity token format, identity metadata, identity provenance, attestation metadata, revocation metadata, and identity validity.

---

## Governance

All specifications are stewarded by the **SCU Foundation**, which maintains canonical versions, ensures interoperability, and governs long‑term evolution.

Semantic, contextual, identity, and graph‑level research — along with standards‑adjacent proposals — are conducted by the **Lattice Research Institute (LRI)**.

All changes MUST follow the SCU Foundation Change‑Management Charter (CMC) and Update‑Sequence Charter (USC).

---

## Directory Structure

Each specification is published in its own subdirectory:

```
/specifications/
  ts/
  lp/
  lm/
  lw/
  lit/
```

Each subdirectory contains:

- `<SPEC>-Spec-v1.0.md` — Full canonical specification  
- `README.md` — Overview and canonical links  
- `STATUS.md` — Status and version metadata  
- `CHANGELOG.md` — Version history  
- `VERSION` — Machine‑readable version file  
- `LICENSE` — CC BY 4.0 license

---

## Alignment with Standards

Specifications MUST comply with:

- **TS v1.0** — Trust, identity, safety, provenance  
- **LP v1.0** — Semantic primitives and semantic validity  
- **LM v1.0** — Meta‑semantic structures and contextual meaning  
- **LW v1.0** — Graph structures and metadata  
- **LIT v1.0** — Identity tokens and attestation primitives

Specifications operationalise the standards but do not replace them.

---

This directory forms the **technical backbone** of the Lattice ecosystem.
