## Emergent State Machine (ESM)

The **Emergent State Machine (ESM)** is a turn-based control architecture for governing state mutation in model-assisted systems.

ESM makes the decision boundary explicit by separating:

- **Signals** (measurement)  
- **Interpretation** (evaluation)  
- **Authorization** (authority to mutate state)  

Each interaction is bound into a **Turn**, which records the versions of signal logic, interpretation logic, and authorization policy in effect at that moment. State may only evolve through this structured boundary.

The result is a system where evolution is:

- Reconstructible  
- Versioned  
- Inspectable  
- Governable  

ESM is domain-agnostic. It applies wherever probabilistic interpretation and consequential state mutation must coexist — including AI-assisted systems, digital twins, enterprise workflows, and learning platforms.

For systems that require a deterministic and instrumented mutation boundary, ESM formalizes that layer through a **Controlled Mutation Layer (CML)**.

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

ESM addresses this by enforcing a strict architectural separation between descriptive projection and authoritative mutation.

Behavioral change may occur only through explicit, versioned state transitions mediated by the Controlled Mutation Layer (CML) — never through implicit drift.

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

- *ESM: A Turn-Based Control Architecture (v0.9)*  
  [Download PDF](paper/ESM_Turn_Based_Control_Architecture_v0.9.pdf)

---

## Engineering Specification

Canonical engineering specification:

[spec/esm_spec.md](spec/esm_spec.md)

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

We invite collaboration and discussion.
