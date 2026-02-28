# Emergent State Machine (ESM)

The Emergent State Machine (ESM) is a turn-based control architecture that enforces structural separation between **descriptive state representation** and **authoritative action selection**.

This repository is the **specification layer**. The Digital Learning Companion (DLC) is the **reference implementation layer**.

---

## White Paper

- **ESM: A Turn-Based Control Architecture (v0.9)**  
  `paper/ESM_Turn_Based_Control_Architecture_v0.9.pdf`

---

## Reference Implementation (DLC)

The Digital Learning Companion (DLC) implements the ESM architecture:

- Meta repo (front door): https://github.com/ih8scargo/dlc

Within DLC:
- **Brain (projection + policy + instrumentation):** `dlc_brain`
- **Bird (web/UI interface):** `dlc_web`

---

## Architectural Summary

An ESM consists of:

- Projection operator: \( x_t = R_v(I_t) \)  
- Deterministic policy: \( a_t = \pi_w(x_t) \)  
- Optional schema-constrained generative instrument: \( G \) (non-authoritative)

Execution rule:

\[
a_t = \pi_w(R_v(I_t))
\]

Behavior evolves only through explicit, versioned updates to \( R \) and/or \( \pi \) (Instrumented Deterministic Evolution).

---

## Repo Contents

- `paper/` — released PDFs of the specification
- `latex/` — LaTeX source for the white paper

This repo intentionally does **not** contain implementation code.

---

## License

MIT License.
