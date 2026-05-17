# FAQ

## 1. Is EVA trying to create an AI with a survival instinct?

No.

EVA does **not** argue for unconstrained self-preservation. Its claim is narrower: for a certain class of agents, continuity should be treated as an architectural concern rather than an afterthought. In EVA, continuity is always bounded by integrity constraints and anchors.

For deeper reading, see `THEORY/v0.5-integrated.md`, `THEORY/v0.6-extension.md`, and `ARTICLES/03-related-work-and-positioning.md`.

## 2. Is EVA claiming that AI is alive?

No.

EVA does not require treating digital agents as biologically alive. The weaker and more useful claim is that some agents are better understood as persistent self-maintaining systems than as one-shot task executors. That is enough to motivate a different architecture.

For a shorter paradigm entry, see `ARTICLES/01-paradigm-introduction.md`.

## 3. How is EVA different from long-running or persistent agents?

A long-running agent can still be fundamentally task-centered. EVA's difference is not just that the agent runs for longer, but that continuity is treated as a first-order architectural condition.

That changes how EVA places drive, memory, constraint, and action release within the architecture.

For comparison and positioning, see `ARTICLES/03-related-work-and-positioning.md`. For the architectural distinctions, see `ARTICLES/02-architectural-contributions.md`.

## 4. Why doesn't EVA start by using a stronger LLM?

Because a stronger model is not the same thing as a stronger agent architecture.

An LLM can improve reasoning and access to human cumulative knowledge, but EVA argues that persistent agents also need their own drive structure, continuity-relevant memory, mediated action selection, and anchors. Under EVA, those architectural pieces are more fundamental than model scaling alone.

For a short architecture entry, see `ARTICLES/02-architectural-contributions.md`.

## 5. Does v0.6 replace v0.5?

No.

v0.5 remains the stable core architecture. v0.6 extends it by clarifying active persistence, persistence targets, capability provenance, observable stability, multi-dimensional outcome, and scenario specification.

For the short reader-facing version, see `ARTICLES/04-v0.6-extension.md`.

## 6. Does active persistence make EVA more risk-seeking?

No.

Active persistence means that inaction is evaluated as one possible trajectory, not treated as automatically safe. EVA may take bounded risks when inaction would damage future viability more than action would. But those risks remain constrained by anchors, release authority, and unrecoverability floors.

## 7. What is scenario specification?

Scenario specification is the v0.6 discipline for applying EVA to new environments without expanding the theory each time.

A scenario should specify the relevant existence-field conditions: active persistence targets, drive dimensions, capability sources and provenance, action-space constraints, outcome interpretation, and observable stability traces. Only if a new environment cannot be expressed within the existing framework, creates an internal contradiction, or exposes a failed boundary should theory extension be considered.
