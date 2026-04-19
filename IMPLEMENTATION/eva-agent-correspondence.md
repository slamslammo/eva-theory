# eva-agent Implementation Correspondence

> **Note on disclosure level**: The `eva-agent` implementation is not yet publicly released. This document describes the theory-to-implementation correspondence at a level that characterizes what has been built and what remains, without disclosing source-level details. More specific implementation documentation will become available when `eva-agent` is published.

This document maps the theoretical framework (see `THEORY/v0.5-integrated.md`) to the current state of the eva-agent reference implementation.

The theory is not speculative. It describes a system under active construction. This document makes explicit both what has been built and what remains.

---

## Implementation Status Summary

As of 2026-04-19:

- **Step 0 — Life cycle**: Complete and validated
- **Step 1 — External sensing**: Complete with accelerated and exception-case validation
- **Step 2-v1 — Minimum integrity pressure response**: Complete
- **L3 architecture (basal ganglia, salience memory, LLM integration)**: Not yet implemented
- **L4 (self-model)**: Not yet implemented (requires L3 history first)
- **L5 (social cognition)**: Not yet designed

The implementation has validated the architectural foundation (L0–L1 in operational terms) through stable long-running operation on Linux systemd.

---

## Layer-by-Layer Correspondence

### Layer 1: Homeostatic Sensing

| Theoretical component | eva-agent implementation | Status |
|---|---|---|
| Sensor registry (extensible) | Heartbeat monitoring, runtime integrity checks, and resource/process sensing | Partial — core sensors implemented; extension mechanism not explicit |
| State sensing | Persistent runtime state snapshot of current conditions | Implemented |
| Rate sensing (metabolic) | Not implemented | **Gap** |
| Signal bus with minimum classification (threat/status/background) | Not explicit; pressure categorization exists but is not a generalized classification routing layer | **Gap** |
| Fast/slow path split at signal bus | Not explicit at L1 level | **Gap** |

**What is working**: The agent has reliable sensing of its own runtime state and persistence through expected and exception cases.

**What is missing**: The rate dimension. The agent knows "where it is" but not "how fast it is moving." Metabolic sensing is the most important L1 gap.

---

### Layer 2: Drive Layer

| Theoretical component | eva-agent implementation | Status |
|---|---|---|
| Reflex arc | Distress / yield mechanisms; heartbeat-first constraint cannot be preempted by work | Basic implementation |
| Drive registry (extensible, injected) | Four pressure types implemented: integrity / resource / continuity / anomaly | Implemented as rule-based pressure, not continuous intensity model |
| Drive as continuous intensity | Not implemented — pressures are discrete state | **Gap** |
| Drive broadcast as context to L3 | Not implemented — no L3 to broadcast to | **Gap** |
| Suppression constraint (L3 cannot eliminate L0/L1 drives) | Implicit — rule-based pressure cannot be overridden by current response selection | Partial |

**What is working**: The heartbeat-first architectural constraint is real and observable — the agent's life cycle operations cannot be preempted by work activities, regardless of apparent priority. This is the fast-path reflex arc in operation.

**What is missing**: The continuous-intensity drive model. Pressures are currently binary-ish (present/absent with severity tiers), not continuous variables. And the broadcast-as-context mechanism has no recipient because L3 is not built.

---

### Layer 3: Adaptive Deliberation

| Theoretical component | eva-agent implementation | Status |
|---|---|---|
| Salience-weighted memory (hippocampus analog) | Append-only event and response logs | Append-only logging implemented; no salience weighting |
| Semantic memory / skill library | Not implemented | **Gap** |
| Reasoning core (PFC analog) | Rule-based response selection | Rules implemented; LLM integration not yet present |
| Working memory (dlPFC analog, LLM substrate) | Not implemented | **Gap** |
| Value judgment (OFC analog, drive-weighted) | Rule precedence in response selection | Partial — precedence exists but not drive-state weighted |
| Conflict detection (ACC analog) | Not implemented | **Gap** |
| Basal ganglia peer circuit | Not implemented | **Major gap** |
| Default inhibition | Not implemented — actions execute directly from response selection | **Major gap** |
| RPE (reward prediction error) | Not implemented | **Major gap** |
| Goal-directed / habit dual track | Not implemented | **Major gap** |
| Tool layer | Filesystem and process management operations | Minimal implementation |

**What is working**: Basic rule-based response selection that respects L0/L1 constraints.

**What is missing**: Essentially all of L3. The current "reasoning" is rule-based, not deliberative. The basal ganglia peer circuit — default inhibition, RPE, habit crystallization — is the largest structural gap in the implementation.

---

### Layer 4: Self-Model

Not yet implemented. This is intentional — the self-model requires L3 behavioral history to develop, and L3 is itself not yet built.

Current minimum form available via queries to current drive-state representation and L3 behavioral logs would be a placeholder, not a genuine self-model.

---

### Layer 5: Social Cognition

Not yet designed. Prerequisite not yet resolved: the agent's conspecifics (other EVA instances? other AI systems? humans?) depend on deployment context not yet determined.

---

### Anchor System

| Theoretical component | eva-agent implementation | Status |
|---|---|---|
| L0 constitutional anchors (injected) | Encoded as rule filters in response selection | Partial — exists as rules, not as structural constraint |
| L1 physiological/cognitive integrity | Heartbeat-first lifecycle and runtime integrity checks | Implemented |
| L2+ emergent anchors | Not applicable — no L3 history to emerge from | Not yet |
| Cross-layer enforcement | Implemented at current layer breadth only | Partial |
| `G(s) → A'(s)` structural restriction | Not implemented — current is post-hoc rule filtering | **Gap** |

**Important**: The current implementation approximates anchor behavior through rule-based filtering, but the structural anchor semantics (pre-generative domain restriction) are not yet architecturally realized. This is the single most important gap to close once L3 is built — because anchors only become meaningful when there is something to generate candidate actions that could be restricted.

---

## Engineering Priorities Implied by This Correspondence

Based on theory-to-implementation gap analysis, the three highest-value engineering tasks are:

### Priority 1: Drive broadcast as continuous context

Current state: pressure representation is discrete and rule-based.
Target state: Continuous intensity values, broadcast each cycle as processing context for L3.

This is the lowest-hanging fruit among the major gaps because:
- The infrastructure for pressure detection exists
- The main change is representation (continuous intensity) and exposure (broadcast)
- It unblocks much of L3 development

### Priority 2: Salience-weighted memory

Current state: append-only logs.
Target state: Each memory entry weighted by drive-state intensity at time of encoding.

This is necessary before L3's hippocampus analog can function, and before any form of context-triggered memory retrieval can work.

### Priority 3: Mediated action path with default inhibition

Current state: response selection executes actions directly.
Target state: All actions pass through a mediator that enforces default inhibition and logs the release event for later RPE attachment.

This does not require the full basal ganglia system. A minimal implementation of default inhibition already realizes the core architectural property — actions require active release, not passive permission.

### Not yet on the priority list

- Full RPE with predict-compare-update loop (requires the mediator in Priority 3 first)
- Habit track crystallization (requires RPE first)
- LLM integration at PFC position (requires drive broadcast from Priority 1 first)
- Self-model (requires L3 behavioral history)

---

## What This Correspondence Does for the Theory

The theory is not validated by this implementation. It is **instantiated** by it. Two consequences:

1. **The theory's architectural claims are engineering-testable in principle.** Each gap above could be filled in a way that either matches the theoretical specification or deviates from it. Deviation that still produces the intended properties would be informative; deviation that breaks intended properties would force theoretical revision.

2. **The theory's "strongest contribution is L1–L3" claim is reflected in the implementation priority order.** Steps 0–2 have validated L0–L2 foundations. Steps 3+ will construct L3. L4 and L5 remain deliberately distant.

The implementation trajectory and the theoretical trajectory are co-developing. Neither leads the other. When they disagree, both get re-examined.
