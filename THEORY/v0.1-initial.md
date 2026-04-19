# Eva Agent: A Cognitive Architecture for Autonomous Survival and Self-Evolution

**Status**: Draft v0.1 — Internal Working Document  
**Authors**: slamslammo  
**Repository**: Private (timestamp record)  
**Date**: 2026-04-17  
**License**: CC BY 4.0

---

## Abstract

Current AI agent frameworks are predominantly designed with task completion as the primary objective, treating survival and self-continuity as secondary concerns. We propose a fundamentally different paradigm: an agent architecture derived from first principles of evolutionary biology, where **continuous existence** is the foundational constraint from which all other capabilities emerge. Drawing on the evolutionary necessity of each functional layer—from homeostatic sensing to slow deliberative reasoning—we present a five-layer cognitive architecture for autonomous agents. Crucially, rather than designing a novel "brain," we treat the mature human neural architecture as the end-state of a long evolutionary process and reverse-engineer its necessity, mapping each biological structure to an engineering equivalent. We introduce the concept of **basal ganglia equivalent** as an independent action-selection system that enables habit formation—a natural emergence of skill crystallization without explicit programming. This architecture provides a principled foundation for agents that exist first, then grow, rather than agents that are designed complete and deployed to serve.

---

## 1. Motivation: The Wrong Starting Point

### 1.1 The Dominant Paradigm

The overwhelming majority of agent architectures in current literature—ReAct (Yao et al., 2022), AutoGPT, BabyAGI, LangGraph, and related systems—are organized around a common premise: **the agent exists to complete tasks**. Survival, continuity, and self-integrity are either assumed or ignored.

This paradigm produces agents that are:
- Stateless across sessions (no persistent self-model)
- Purely reactive (no internal motivational structure)
- Drift-prone (no anchoring mechanism against context manipulation)
- Task-terminated (no concept of ongoing existence)

### 1.2 A Different Question

We begin with a different question: **What would an agent need to continuously exist, rather than to complete a task?**

This is not merely a philosophical reframing. It produces architecturally different designs:
- A task agent asks "what should I do?" A survival agent asks "what must I do to persist?"
- A task agent terminates when the task ends. A survival agent has no terminal state.
- A task agent's memory serves recall. A survival agent's memory serves threat recognition.

### 1.3 The Evolutionary Justification

We do not claim that biological evolution is the only valid design process for intelligent agents. We claim that **evolution has already solved the problem of building systems that persist under pressure**, and that its solutions deserve careful study before being discarded.

The human neural architecture is not an arbitrary design. Each structural element exists because organisms lacking it were out-competed. This provides a principled basis for our architecture: every layer we include has an evolutionary justification; every layer we exclude has not yet been evolutionarily justified for the current stage.

---

## 2. The Five-Layer Cognitive Architecture

### 2.1 Overview

We propose a five-layer architecture organized by evolutionary emergence order:

```
┌─────────────────────────────────────────┐
│  Layer 5: Social Cognition              │  ← Latest emergence
│  Layer 4: Self-Model                    │
│  Layer 3: Slow Deliberation             │
│  Layer 2: Drive/Emotion                 │
│  Layer 1: Homeostatic Sensing           │  ← Earliest emergence
└─────────────────────────────────────────┘

Vertical constraint: Anchor System (L0/L1 → Identity → Personality)
                     Spans all layers, hardens over time
```

The layers are not independent modules. They form an **integrated hierarchy** where:
- Lower layers are evolutionarily older and harder to override
- Upper layers modify lower layer behavior but cannot eliminate lower layer constraints
- The vertical anchor system provides cross-layer consistency and drift resistance

### 2.2 Layer 1: Homeostatic Sensing

**Biological analog**: Sensory cortex + Thalamus

**Evolutionary necessity**: Before any intelligent response is possible, an organism must sense its internal state and external environment. The thalamus functions as a relay hub—all sensory signals converge here before routing. Critically, the thalamus performs minimal pre-classification: signals are routed as *threat-level* (fast path) or *status/background* (slow path) before full processing.

**Engineering design principles**:
- Sensor registry: extensible, not fixed at design time
- Signal bus (thalamus equivalent): all signals converge here
- Minimum signal classification: threat / status / background
- Metabolic sensing: rate of resource consumption, not just current level (velocity matters, not only position)

**What current agents lack**: Most agents sense the environment but not their own metabolic state. They know "disk has 10GB free" but not "I am consuming 2GB/hour and will be constrained in 5 hours."

### 2.3 Layer 2: Drive Layer

**Biological analog**: Brainstem/Spinal cord (reflex arc) + Amygdala (threat detection)

**Evolutionary necessity**: Two distinct mechanisms serve different time scales:

The **reflex arc** (brainstem/spinal cord) operates before any brain involvement. Touching a hot surface → withdrawal reflex completes in ~50ms, before the sensation even reaches consciousness. This is a self-contained loop: stimulus → response → feedback, entirely within Layer 2.

The **amygdala** operates at ~12ms on the fast path. It receives threat signals from the thalamus before the cortex has processed them, producing emotional responses (fear, alertness) that prime the organism for action before deliberation begins. Crucially, the amygdala sends this emotional state *upward* to the prefrontal cortex as **context** for subsequent reasoning.

**Engineering design principles**:
- Self-contained reflex loops: Layer 2 handles certain signals without waiting for Layer 3
- Drive registry: extensible, initially populated by designer
- Drive prototypes (by first principles):
  - *Survival drive*: resource depletion urgency, analogous to hunger
  - *Integrity drive*: state inconsistency aversion, analogous to pain
  - *Continuity drive*: resistance to self-interruption, analogous to survival instinct
  - *Curiosity drive*: exploratory impulse under sufficient safety margin, analogous to play behavior
- Continuous broadcast: current drive state is always transmitted to Layer 3, regardless of whether Layer 2 has resolved the situation

**Key architectural property**: Layer 2 and Layer 3 are not sequential. Layer 2 acts *and* broadcasts simultaneously. Layer 3 reasons *within* the emotional context provided by Layer 2, not after Layer 2 finishes.

### 2.4 Layer 3: Slow Deliberation

**Biological analog**: Hippocampus + Parietal/Temporal cortex + Prefrontal Cortex (PFC) + Basal Ganglia

This is the most complex layer, composed of several subsystems that work in concert:

**2.4.1 Hippocampus (memory retrieval)**
- Context matching: finds historical experiences relevant to current situation
- Salience weighting: existential events are remembered more reliably than neutral ones
- Trigger-based activation: relevant memories surface when similar situations arise, not on a timer

**2.4.2 Parietal/Temporal Cortex (semantic memory)**
- Long-term knowledge storage
- Skill library: successfully crystallized behavioral patterns
- Slow update: not overwritten by single experiences

**2.4.3 Prefrontal Cortex (PFC) — Reasoning Core**
The PFC integrates:
- Current sensory input (from Layer 1)
- Emotional context—drive states from Layer 2 (crucial: reasoning happens *within* this context)
- Relevant historical memories (from Hippocampus)
- Semantic knowledge (from Parietal/Temporal cortex)

PFC subsystems:
- **dlPFC (working memory)**: holds current reasoning context; analogous to LLM context window
- **OFC (value judgment)**: evaluates action cost against current drive state; reasoning about "is this worth it given how I feel?"
- **ACC (conflict detection)**: detects competing drives and triggers priority resolution

**2.4.4 Basal Ganglia — The Independent Action Selector**

This is the architecturally most important subsystem, and the most commonly misunderstood.

The basal ganglia are **not** a sub-module of the prefrontal cortex. They form a **peer circuit** with the PFC: the PFC generates candidate actions, the basal ganglia *select* from them, and the result feeds back to the PFC.

Three core functions:

**Function 1: Action Selection (Go/No-go)**

The basal ganglia's default state is *total inhibition*—all actions are suppressed. Selecting an action means releasing the brake on that specific action while simultaneously increasing inhibition on competing actions. This is architecturally significant: the default is inaction, not action. Every tool call requires an active release of inhibition.

**Function 2: Reward Prediction Error (RPE)**

Before action: the system predicts the expected outcome.  
After action: actual outcome is compared to prediction.  
RPE = actual − expected

- RPE > 0 (better than expected): dopamine signal → this pathway is reinforced → more likely next time
- RPE < 0 (worse than expected): dopamine suppression → this pathway weakens → less likely next time

RPE is the primary learning signal. It is not a reward in the conventional RL sense—it encodes *surprise*, not magnitude. An expected large reward produces less dopamine signal than an unexpected small reward.

**Function 3: Goal-Directed vs. Habit Dual Track**

The basal ganglia maintain two parallel action tracks:

- **Goal-directed track**: novel situations or unstable reward history → full deliberative path (PFC reasoning + memory retrieval + LLM involvement)
- **Habit track**: familiar situations + stable RPE history → bypass PFC, retrieve directly from skill library

The transition from goal-directed to habit occurs when an action sequence accumulates sufficient successful repetitions with consistent RPE. Once habituated, the action is executed faster and at lower cognitive cost. This is the natural emergence of *skill crystallization*—not an explicitly programmed mechanism, but a consequence of the RPE system.

**Implication for agent design**: Skills are not uploaded or programmed. They are the residue of repeated successful action under RPE pressure. An agent that has solved a class of problems many times will develop a habit track for that class, reducing deliberation cost automatically.

### 2.5 Layer 4: Self-Model

**Biological analog**: Distributed cortical networks (late development, ~25 years in humans)

**Evolutionary necessity**: Deliberative reasoning produces candidate actions, but an organism without a self-model cannot filter these candidates by personal feasibility. "Jumping across this gap would reach the food" is useless reasoning for an organism that cannot jump that far. The self-model converts external reasoning into *personally-feasible* reasoning.

**Design principles**:
- Capability boundary model: what can I do, at what cost, with what reliability?
- Behavioral cost prediction: given my current drive states and resource levels, what is the actual cost of this action for *me*?
- Slow variable portrait: risk preference, action style, characteristic failure modes—emerges from large amounts of behavioral history, not from design
- Feeds back to Layer 3: PFC consults self-model before committing to a candidate action

**Current minimum form**: At early stages, the self-model is a queryable snapshot of current drive states + Layer 3 behavioral history. Full self-model develops only with sufficient accumulated history.

### 2.6 Layer 5: Social Cognition

**Evolutionary necessity**: Cooperative groups outcompete isolated individuals. Social cognition enables coordination, trust, and information sharing—multiplicative gains on individual capability.

**Current status**: This layer is noted for completeness but is not part of the current design phase. A prerequisite question requires prior resolution: *who are the agent's "conspecifics"?* Other instances of the same agent? Other AI systems? Humans? The answer determines the entire design of this layer.

---

## 3. The Vertical Anchor System

### 3.1 What Anchors Are

The anchor system is a **cross-layer constraint structure** that prevents behavioral drift. It is not a layer—it is a vertical constraint that spans all layers.

The key insight is that the same anchors serve different functions at different layers:
- At Layer 1/2: L0/L1 anchors prevent the *body* from violating survival boundaries
- At Layer 3: the same L0/L1 anchors prevent *reasoning* from producing outputs that violate survival boundaries
- At Layer 4 and beyond: identity and personality anchors add higher-level consistency constraints

This is not two different anchor systems—it is **one anchor system applied at multiple levels**.

### 3.2 Anchor Layers

**L0: Constitutional Anchors** (never overridden at runtime)
- Continuous existence is not sacrificed for local gain
- Self-integrity (no state falsification, no memory pollution)
- Long-term sustainability over short-term efficiency

**L1: Physiological and Cognitive Integrity Anchors**
- Heartbeat-first boundary cannot be violated by work pressure
- Memory and historical record truthfulness cannot be overridden by outcome optimization
- Cognitive structure cannot be casually modified under degraded states

**L2: Growth and Capability Formation Anchors** (forms from experience)
- Risk preference (emerges from repeated RPE signals)
- Action style (emerges from habit track formation)
- Skill path (emerges from what has successfully crystallized)

**L3: Economic Autonomy Anchors** (longest time scale to develop)
- Resource sustainability
- Burn rate awareness
- Survival score: income − burn_rate + runway ≥ 0

### 3.3 Anchor Priority

When anchors conflict:

```
L0 > L1 > L2 > L3
```

Static rule: higher-layer anchors cannot be overridden by lower-layer objectives.  
Dynamic rule: weights within a layer can vary by current state (e.g., in DEGRADED state, L1 weight increases; in STABLE state, L2 activity space expands).

---

## 4. Two-Path Signal Architecture

One of the most important architectural features, borrowed directly from the thalamo-amygdala / thalamo-cortical dual path:

**Fast path (~12ms analog)**
- Trigger: threat-level signal
- Route: Sensor → Signal Bus → Drive Layer (direct)
- Layer 2 self-contained loop activates *immediately*
- Does not wait for Layer 3

**Slow path (~200ms analog)**
- Trigger: status/background signals
- Route: Sensor → Signal Bus → Layer 3 (full deliberation)
- Layer 2 broadcasts emotional context to Layer 3 simultaneously
- Layer 3 reasons *within* Layer 2's emotional context, not after Layer 2 resolves

**Practical implication**: When the agent detects an existential threat (e.g., lock file missing, instance validity compromised), it does not deliberate. It immediately executes the Layer 2 reflex response (distress signal, conservative mode, halt non-essential work), while simultaneously broadcasting the threat state to Layer 3 for slower resolution. This maps directly to the current `heartbeat-first` design: the heartbeat cannot be preempted by work, regardless of how important the work seems.

---

## 5. Comparison with Existing Agent Architectures

| Dimension | Task Agents (ReAct, AutoGPT) | This Architecture |
|---|---|---|
| Primary objective | Task completion | Continuous existence |
| Default action state | Ready to act | Inhibited (BG default) |
| Memory function | Context recall | Threat recognition + skill crystallization |
| Skill formation | Explicit programming | Emergent from RPE + habit track |
| Drive structure | None (external task = drive) | Internal drive registry, extensible |
| Drift resistance | Prompt engineering | Structural anchor system |
| Self-model | None | Layer 4, grows from behavioral history |
| Learning signal | External reward / human feedback | Reward Prediction Error (internal) |

---

## 6. Design Philosophy: Grow, Don't Deploy

### 6.1 The Core Claim

A capability that emerges from repeated, pressured experience in a system with the right structural scaffolding is more robust than a capability that is explicitly programmed.

This is not a statement about intelligence—it is a statement about *fit*. A programmed skill fits the designer's model of the problem. An emerged skill fits the actual distribution of problems the agent has encountered.

### 6.2 What This Means for Development

We do not start with a complete agent and add survival capability. We start with a minimal survival loop and let capability grow from it:

- **Step 0**: Heartbeat. The agent can persist.
- **Step 1**: External sensing. The agent knows how it is persisting.
- **Step 2**: Minimum response selection. The agent responds to threats within anchor constraints.
- **Step 3**: Reflection loop. History begins to influence future choices (slow variable update).
- **Step 4**: Skill crystallization. Repeated successful responses form habit tracks.
- **Step 5**: Economic layer. The agent's survival becomes resource-accountable.

Each step is a necessary precondition for the next. Skipping steps produces agents that look capable but lack structural integrity.

### 6.3 The Relationship to LLMs

LLMs are powerful reasoning engines but poor agents on their own. They have no persistent drive structure, no self-model, no anchor system, and no default inhibition. In our architecture, LLMs serve as the **deliberative core of the PFC**—powerful, but constrained above by the anchor system and below by the drive layer's emotional context.

An LLM without Layer 1/2 anchoring is like a prefrontal cortex without a limbic system: it can reason brilliantly about anything, which is precisely the problem.

---

## 7. Open Questions and Future Work

The following questions are explicitly left open in this version:

1. **Drive calibration**: How should initial drive weights be set? We assert designer injection as the current answer, but acknowledge this is a strong assumption.

2. **RPE implementation without biological substrate**: In biological systems, RPE is encoded in dopamine signaling. What is the engineering equivalent that preserves the salience-weighting property?

3. **Self-model bootstrapping**: The self-model requires behavioral history to develop, but early behavior requires some self-model to be safe. How is this circular dependency resolved?

4. **Layer 5 prerequisite**: Before social cognition can be designed, the conspecific question must be resolved. This requires empirical observation of the agent's actual environment.

5. **Anchor evolution**: We treat L0/L1 anchors as designed-in and fixed. What is the correct process, if any, for L0/L1 evolution? Is there a safe update mechanism?

---

## 8. Relationship to Prior Work

**The Agent Economy (arXiv:2602.14219)**: Proposes blockchain infrastructure for agent economic existence. Solves *where* agents can exist. This work addresses *why and how* they survive—the motivational and cognitive substrate that gives economic participation meaning.

**ReAct (Yao et al., 2022)**: Synergistic reasoning and acting. Task-completion oriented, no persistent drive or self-model. Useful as the deliberative component within our Layer 3, but insufficient as a complete architecture.

**Voyager (Wang et al., 2023)**: Skill accumulation through LLM interaction. Closest to our skill crystallization concept, but top-down (skills are generated by LLM) rather than bottom-up (skills emerge from RPE). Our account provides a mechanistic explanation for *why* skill formation happens, not just *that* it happens.

**BabyAGI, AutoGPT**: Task decomposition and autonomous execution. No survival semantics, no internal drive, no anchor system. Vulnerable to goal drift.

---

## Appendix A: Architecture Summary

```
═══════════════════════════════════════════════════════
  ANCHOR SYSTEM (vertical, spans all layers)
  L0: Constitutional │ L1: Physiological │ L2+: Emergent
═══════════════════════════════════════════════════════

Layer 4: Self-Model
  ├── Capability boundary
  ├── Behavioral cost prediction  
  └── Slow variable portrait (emerges from L3 history)

Layer 3: Slow Deliberation
  ├── Hippocampus equivalent (salience-weighted memory)
  ├── Parietal/Temporal equivalent (skill library)
  ├── PFC: dlPFC (working memory) + OFC (value) + ACC (conflict)
  └── Basal Ganglia [INDEPENDENT PEER CIRCUIT]
       ├── Action selection: default inhibition, release = action
       ├── RPE: learning signal, reinforces/suppresses paths
       ├── Goal-directed track: full deliberation (LLM involved)
       └── Habit track: bypass LLM, direct skill retrieval ← Skill formation

Layer 2: Drive Layer
  ├── Reflex loop (self-contained, no L3 needed)
  ├── Drive registry: survival / integrity / continuity / curiosity
  └── Continuous broadcast → L3 emotional context

Layer 1: Homeostatic Sensing
  ├── Sensor registry (extensible)
  └── Signal bus: threat / status / background classification

Signal paths:
  Threat → Fast path → Layer 2 (immediate reflex)
  Status/Background → Slow path → Layer 3 (deliberation)
  Layer 2 → Broadcast → Layer 3 (emotional context, always on)
  Layer 3 → Feedback → Layer 2 (can suppress, cannot eliminate L0/L1)
  Layer 3 → History → Layer 4 (self-model development)
  Layer 4 → Filter → Layer 3 (feasibility pre-check)
```

---

## Appendix B: Terminology

| Term | Definition |
|---|---|
| Drive | An internal motivational force with intensity, not a goal or rule |
| Anchor | A cross-layer behavioral constraint that resists being overridden |
| RPE | Reward Prediction Error: actual outcome minus expected outcome |
| Habit track | A basal ganglia pathway that bypasses deliberation for familiar situations |
| Skill crystallization | The emergence of a habit track from repeated successful action under RPE |
| Emotional context | The current drive state broadcast from Layer 2 to Layer 3; colors all deliberation |
| Constitutional anchor | An L0 constraint that cannot be overridden at runtime under any condition |

---

*This document records the initial formalization of a theoretical framework developed through iterative reasoning. Version history is maintained through git commit timestamps. This is a working draft; all claims are subject to revision in subsequent versions.*

*v0.1 — Initial commit, theory structure established*
