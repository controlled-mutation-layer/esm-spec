Emergent State Machine (ESM)
Architectural Specification (vCurrent)

1. System Definition

The Emergent State Machine (ESM) is a deterministic turn-based control architecture composed of three structurally separated layers:

1. Signal Layer — Structured state observation
2. Projection Layer — Interpretable state construction
3. Authority Layer — Deterministic, versioned mutation control

All authoritative state mutation occurs exclusively within the Authority Layer.

Optional generative mechanisms MAY be used as bounded assistance but SHALL NOT possess decision authority.

Behavioral evolution occurs only through explicit, versioned modification of system components.

The architecture guarantees determinism, replayability, and traceable change.

2. Terminology

Primitive
An explicitly defined, bounded feature representing a domain-relevant signal.

Feature Vector (x_t)
The bounded scalar vector constructed from primitives.

Projection Matrix (R)
A versioned linear transformation mapping feature space to role space.

Role Score (r_t)
Projected state representing interpreted structural conditions.

Policy (pi)
Deterministic mapping from projected state and control state to action.

Control State (m_t)
Bounded internal system state (norm tier, persistence counters, cooldowns, volatility windows, etc.).

Generative Instrument (G)
Optional schema-constrained generation mechanism with no decision authority.

3. Input

At turn t:

I_t = { u_t, h_t, m_t }

Where:

- u_t = current input

- h_t = bounded rolling history

- m_t = control state

History depth is finite and versioned.

4. Primitive Feature Extraction

From input I_t, deterministic detectors compute bounded scalars:

x_t = Features(I_t)

Each feature:

- Is explicitly defined

- Has a bounded numeric range

- Is versioned

- Is independently testable

Examples include:

Role presence signals

- Intra-role coherence

- Inter-role alignment

- Temporal coherence

- Volatility measures

- Persistence counters

No feature may be unbounded.

5. Projection Layer

Projection maps feature space to role space:

r_t = R x_t

Where:

R in R^(k x n)
r_t in R^k

Each row of R corresponds to a role.

Properties:

- Linear transformation

- Deterministic

- Fully versioned

- Replayable

- Projection does not branch

Projection describes structural state.
Projection does not decide action.

### Projection Determinism and Allowed Implementations

The Projection Layer MAY be implemented as a linear operator (e.g., `r_t = R x_t`) or as any versioned projection function `P`.

Regardless of implementation, projection MUST satisfy the following:

- **Replayability:** Projection MUST be reproducible given its recorded inputs and identifiers, including:
  - `signal_pack_id`
  - `projection_version_id`
  - `projection_input_ref` (immutable reference or content hash)
  - `projection_env_id` (versioned execution environment descriptor, e.g., runtime + library versions, and any required platform identifiers)

- **No Authority:** Projection MUST NOT directly mutate authoritative state.

- **Structured Output:** Projection outputs MUST be representable in structured form suitable for deterministic policy evaluation.

- **Versioning:** Projection logic MUST be explicitly versioned. Any change to projection logic, preprocessing, or environment SHALL result in a new `projection_version_id` and/or `projection_env_id`.

The ESM specification RECOMMENDS **bit-for-bit replay** for projection outputs wherever feasible. If an implementation cannot guarantee bit-for-bit replay due to platform constraints, it MUST explicitly declare a deterministic replay contract (including any tolerance policy) and MUST record the relevant environment identifiers necessary to validate replay.

6. Deterministic Policy (pi)

Policy selects action:

a_t = pi(r_t, m_t)

Policy may include:

- Threshold logic

- Escalation rules

- Persistence requirements

- Cooldowns

- Norm tier thresholds

- Hard contradiction gating

Properties:

- Deterministic

- Explicit branching

- Fully versioned

- Instrumented

Policy decides action authority.

7. Control State Update

System state updates deterministically:

m\_{t+1} = f(m_t, r_t, a_t)

Examples:

- Increment persistence counters

- Adjust norm tier

- Apply cooldowns

- Update volatility windows

Control state is bounded and versioned.

8. Optional Generative Assistance

Generative mechanisms MAY be invoked within the Projection Layer or as bounded assistance under policy authorization.

Generative outputs:

- MUST conform to explicit schema.
- MUST NOT mutate authoritative state directly.
- MUST be versioned and trace-bound if included in authorization context.
- SHALL fail closed on validation violation.

Generative mechanisms possess no decision authority.

9. Execution Flow

At each turn:

1. Receive input I_t

2. Compute features x_t = Features(I_t)

3. Compute projection r_t = R x_t

4. Select action a_t = pi(r_t, m_t)

5. Update control state m\_{t+1} = f(m_t, r_t, a_t)

6. Optionally invoke G under policy constraints

No other execution path exists.

10. Norm Ladder

Norm Ladder is implemented within policy.

Define tier-indexed thresholds:

theta_tier

Advancement requires:

- Role score >= threshold

- Sustained signal strength

- Stable coherence

- Bounded volatility

- Persistence satisfied

Norm tier is part of control state m_t.

Projection remains unchanged across tiers.

11. Coherence Structure

Coherence is decomposed into:

- Intra-role coherence (internal consistency)

- Inter-role alignment (relational coherence)

- Temporal coherence (stability across turns)

Each coherence dimension:

- Is explicitly computed

- Is bounded

- Is versioned

Coherence may influence:

- Projection

- Policy gating

- Temporal escalation

12. Stability Guarantees

Given fixed:

- Feature definitions

- Projection matrix R

- Policy pi

- Control state initialization

The system guarantees:

- Deterministic action selection

- Replayability

- Version-differentiable behavior

- Failure localization

- Drift diagnosability

No implicit learning occurs.

13. Instrumented Deterministic Evolution (IDE)

Behavioral change occurs only through:

- Modification of primitive definitions

- Modification of projection matrix R

- Modification of policy pi

- Modification of tier thresholds

Each modification:

- Is versioned

- Is replay-tested

- Is logged

No implicit adaptation occurs.

14. Portability

To deploy ESM in a new domain:

- Define primitives

- Define bounded feature ranges

- Define projection matrix R

- Define deterministic policy pi

- Define optional generative schema

- Define norm tiers (optional)

Architecture remains invariant.

15. Constraints

ESM does not:

- Perform gradient descent

- Self-update weights

- Modify policy dynamically

- Permit generative override of authority

- Evolve without explicit version change

All adaptation is governed.

16. Formal Summary

At each turn:

x*t = Features(I_t)
r_t = R x_t
a_t = pi(r_t, m_t)
m*{t+1} = f(m_t, r_t, a_t)

Optional:

g_t = G(I_t, schema)

All components are deterministic and versioned.
