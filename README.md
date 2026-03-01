
# Emergent State Machine (ESM)

The Emergent State Machine (ESM) is a turn-based control architecture pattern within the broader **Controlled Mutation Layer (CML)** framework.

ESM formalizes structural separation between:

- Descriptive state representation  
- Deterministic, versioned authority  
- Optional schema-constrained generative instrumentation  

It is designed for engineers building systems where probabilistic interpretation and consequential action must coexist — without sacrificing auditability, replayability, or policy control.

---

## Why This Exists

Modern AI systems frequently entangle:

- Interpretation  
- Decision authority  
- Generative output  

This entanglement makes systems difficult to:

- Audit  
- Reproduce  
- Version safely  
- Govern at scale  

Controlled Mutation Layer (CML) is an architectural response to that pain.

ESM is a concrete realization of CML principles.

It enforces that behavioral change occurs only through explicit, versioned mutation of authoritative policy layers — never through implicit drift.

---

## Scope of This Repository

This repository contains the **normative specification** of the ESM pattern:

- Formal execution model  
- Required invariants  
- Clarification and ambiguity handling rules  
- Versioning guarantees  
- Instrumented Deterministic Evolution (IDE)  

It does not contain application code.

---

## White Paper

<<<<<<< HEAD
## White Paper

- *ESM: A Turn-Based Control Architecture (v0.9)*  
  [Download PDF](paper/ESM Turn Based Control Architecture v0.9.pdf)
=======
- *ESM: A Turn-Based Control Architecture (v0.9)*  
  `paper/ESM_Turn_Based_Control_Architecture_v0.9.pdf`
>>>>>>> 206a52d (chore: remove Windows Zone.Identifier artifact)

---

## Engineering Specification

Canonical engineering specification:

<<<<<<< HEAD
[spec/esm_spec.md](spec/esm_spec.md)
=======
`spec/esm_spec.md`
>>>>>>> 206a52d (chore: remove Windows Zone.Identifier artifact)

An implementation must satisfy this specification to be considered ESM-compliant.

---

## Reference Implementation

The Digital Learning Companion (DLC) is one implementation of the ESM pattern:

https://github.com/ih8scargo/dlc

Additional implementations are welcome.

---

## Join the Conversation

If you are building systems that require:

- Deterministic authority boundaries  
- Explicit policy control  
- Structured ambiguity handling  
- Safe, versioned evolution  

We invite collaboration, critique, and experimentation.

CML is an architectural direction — not a closed product.

---

## License

MIT License.
