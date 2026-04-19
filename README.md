# agent-cognitive-architecture

**EVA: An architecture for agents centered on continuous existence**

---

## Project Positioning

Most AI agent architectures are organized around **task completion**. EVA starts from a different premise: for a certain class of agents, **continuous existence is the first-order constraint**, and other capabilities must be understood relative to that constraint.

**This is a theoretical framework paper, not a benchmark-oriented agent design.**

---

## Two Claims

**Claim A (paradigm claim)**: There exists a meaningful class of agents for which the task-centered framing is structurally insufficient. For such agents, the correct starting point is not "what task should the agent complete?" but "what must the agent maintain in order to persist as the same agent over time?"

**Claim B (structural claim)**: Under three operating conditions—survival continuity, environmental non-stationarity, and finite encoding capacity—a layered architecture comprising homeostatic sensing (L1), drive structure (L2), and adaptive deliberation (L3) is a structurally coherent response. Two further layers, self-model (L4) and social cognition (L5), are proposed as downstream extensions under additional pressures, with explicitly weaker derivational strength than L1–L3.

---

## Core Contributions

1. **Drive as context**
   - The drive layer continuously broadcasts contextual state rather than issuing instructions.
   - Reasoning occurs within this state rather than receiving commands from it.

2. **Anchor as structural constraint**
   - Anchors are pre-generative structural restrictions, not post-hoc rules.
   - Candidate actions are generated within an anchor-restricted domain rather than filtered only after generation.

3. **Basal ganglia analog as peer circuit**
   - Action selection and habit formation are architecturally parallel to deliberation rather than a sub-module of reasoning.
   - This preserves default inhibition, separates selection from justification, and supports skill crystallization.

---

## Current Status

- **Theory**: v0.5 stable integrated version
- **Implementation**: `eva-agent` Step 2 complete
- **License**: CC BY 4.0

The current stable manuscript is `THEORY/v0.5-integrated.md`.

---

## Repository Structure

```text
agent-cognitive-architecture/
├── README.md
├── THEORY/
│   ├── v0.1-initial.md
│   ├── v0.2-expanded.md
│   ├── v0.3-scoped.md
│   ├── v0.4-claim-structured.md
│   ├── v0.5-integrated.md
│   └── CHANGELOG.md
├── DISCUSSIONS/
│   └── 01-route-selection.md
├── IMPLEMENTATION/
│   └── eva-agent-correspondence.md
└── LICENSE
```

---

## Reading Guide

- Start with `THEORY/v0.5-integrated.md` for the current stable framework
- See `THEORY/CHANGELOG.md` for substantive theory evolution from v0.1 to v0.5
- See `IMPLEMENTATION/eva-agent-correspondence.md` for the mapping from theory to `eva-agent`

---

## License

This work is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
