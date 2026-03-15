## Emergent State Machine: A Deterministic Architecture for Situational Reasoning in Complex Systems

## Papers

## Latest Paper Release

**Emergent State Machine: A Turn-Based Control Architecture — v1.1.0**

A revised version of the formal architecture paper has been released.

Version 1.1.0 introduces a clearer mathematical framing of the Emergent State Machine (ESM) as a turn-based control architecture. The revision improves conceptual clarity while preserving the original formal structure.

Key Updates

Turn formalization
The architecture is now explicitly defined around the concept of a Turn — a bounded reasoning frame containing observations, signals, state construction, projection, and policy evaluation.

Clearer state construction model
Signals derived during a turn are formally organized into a state vector, providing an interpretable representation of the system’s current situation.

Improved projection framing
Projection is clarified as a transformation of the state vector into policy-relevant coordinates, aligning the architecture with state-space formulations in control theory.

Instrumented Deterministic Evolution (IDE)
The paper now introduces a formal section defining IDE, the mechanism by which ESM systems evolve through explicit versioned changes to detectors, projection logic, and policy artifacts.

Expanded theoretical grounding
The Related Work section situates the architecture within traditions including:

control theory and state-space modeling

dynamical systems

situation awareness research

software architectural separation

AI interpretability and governance

Scope of the Paper

This paper focuses on the mathematical architecture of the Emergent State Machine.
Operational governance topics (policy modularity, generative assistance constraints, etc.) are addressed in the broader ESM specification.

Location

The updated paper is available in: [PDF](papers/esm-architecture/esm_architecture_v1.1.0.pdf)

**Emergent State Machine: A Turn-Based Control Architecture — v1.0.0**

This release updates the architecture paper to align with the ESM specification v1.0.0.

Major clarifications include:

- explicit separation of **Signal**, **Projection**, and **Authority** layers
- introduction of **primitive detectors** and **signals** as the measurement interface
- formalization of **control state** within the policy decision boundary
- clarification of the **authority boundary** separating interpretation from action
- expanded definition of **Instrumented Deterministic Evolution (IDE)**

The paper now reflects the current architectural model used in the ESM specification.

- 📄 [PDF](papers/esm-architecture/Emergent_State_Machine__Control_Architecture_v1.0.0.pdf)

## Designing the Digital Learning Companion

Design narrative describing how the Emergent State Machine architecture emerged.

- 📄 [PDF](papers/dlc-design-narrative/Designing_the_Digital_Learning_Companion_v0.9.0.pdf)

## Emergent State Machine (ESM)

The **Emergent State Machine (ESM)** is a turn-based control architecture for governing state mutation in model-assisted systems.

ESM makes the decision boundary explicit by separating:

- **Signals** - measurement
- **Interpretation** - evaluation
- **Authorization** - authority to mutate state

Each interaction is bound into a **Turn**, which records the versions of signal logic, interpretation logic, and authorization policy in effect at that moment. State may only evolve through this structured boundary.

The result is a system where evolution is:

- Reconstructible
- Versioned
- Inspectable
- Governable

ESM is domain-agnostic. It applies wherever probabilistic interpretation and consequential state mutation must coexist — including AI-assisted systems, digital twins, enterprise workflows, and learning platforms.

For systems that require a deterministic and instrumented mutation boundary, the ESM architecture can be implemented using a **[Controlled Mutation Layer (CML)](https://github.com/controlled-mutation-layer)**.

### ESM Turn Structure

````
### ESM Turn Structure

<<<<<<< HEAD
```text
Input (u_t)
    │
    ▼
[ Signal Layer ]
  Measurement
    │
    ▼
[ Projection Layer ]
  Interpretation
    │
    ▼
==============================
 Authoritative Mutation Boundary
 (often implemented via CML)
==============================
    │
    ▼
[ Authority Layer ]
  Policy Decision
    │
    ▼
State Mutation (m_t → m_{t+1})
````

=======
Input (u*t)
│
▼
┌───────────────┐
│ Signal Layer │
│ Measurement │
└───────────────┘
│
▼
┌─────────────────┐
│ Projection Layer │
│ Interpretation │
└─────────────────┘
│
▼
┌─────────────────┐
│ Authority Layer │
│ Policy Decision │
└─────────────────┘
│
▼
State Mutation (m*{t+1})

> > > > > > > c8b92b4 (Add DLC design narrative preprint v0.9.0)
> > > > > > > Each **Turn** records the versions of:

- signal detectors
- projection logic
- policy rules

This makes every state transition **replayable, inspectable, and governable**.

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

Behavioral change may occur only through explicit, versioned state transitions at the authoritative mutation boundary — never through implicit drift.

In many implementations, this boundary is enforced through a Controlled Mutation Layer (CML).

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

- _ESM: A Turn-Based Control Architecture (v0.9)_  
  [Download PDF](papers/esm-architecture/Emergent_State_Machine__Control_Architecture_v1.0.0.pdf)

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

## Specification

The canonical Emergent State Machine architecture specification is located at:

- [`spec/esm_spec.md`](spec/esm_spec.md)

Current version: **v1.0.0**

---

## Release History

### v1.0.0 — First Public Release

First public release of the Emergent State Machine (ESM) architectural specification.

This release clarifies:

- the separation of Signal, Projection, and Authority layers
- primitive detectors, signals, and feature vectors
- deterministic policy as the exclusive mutation authority
- the placement of probabilistic interpretation within the Projection Layer
- hierarchical composition of nested ESMs
- norm ladders as staged operational or learning progressions

See:

- [`spec/esm_spec.md`](spec/esm_spec.md)
- [GitHub Release: v1.0.0](../../releases/tag/v1.0.0)

### v0.9.1 — Late Pre-Release Draft

Late pre-release draft of the Emergent State Machine architectural specification.

This version is retained as a historical reference point immediately prior to the first stable public release.

Contents at this tag included:

- draft specification at `spec/esm_spec.md`
- accompanying draft paper and LaTeX sources

See:

- [GitHub Release: v0.9.1](../../releases/tag/v0.9.1)

---

## Citation

If you reference the Emergent State Machine architecture in research or technical work, please cite:

**Emergent State Machine (ESM) Architectural Specification v1.0.0**  
Emergent State Machine Project  
[https://github.com/emergent-state-machine/esm-spec](https://github.com/emergent-state-machine/esm-spec)

---

### Designing the Digital Learning Companion

_A Narrative of Discovery and the Emergence of the Emergent State Machine_

This paper presents a design narrative describing how the Emergent State Machine (ESM) architecture was discovered during the development of an AI-assisted tutoring system called the **Digital Learning Companion (DLC)**.

Through iterative experimentation with a conversational AI partner, the project gradually revealed a structural pattern governing how learner interactions could be evaluated and how system state could evolve through discrete, observable turns.

[Designing the Digital Learning Companion (PDF)](papers/dlc-design-narrative/Designing_the_Digital_Learning_Companion_v0.9.pdf)
[LaTeX source](papers/dlc-design-narrative/)

---

## Join the Conversation

If you are building systems that require:

- Deterministic authority boundaries
- Explicit policy control
- Structured ambiguity handling
- Safe, versioned evolution

We invite collaboration and discussion.
