# Signal Flow Diagram — Visual Specification

This file defines the intended content and reading logic for a reader-facing EVA signal-flow diagram.

## Diagram type

A **layered signal-flow overlay** on the five-layer architecture.

The diagram shares its architectural skeleton with the five-layer overview, but overlays signal flow: fast reflex path through L1–L2, slow deliberative path through L1–L2–L3, drive broadcast from L2 into L3, anchor restriction acting at candidate generation, mediated release inside L3's peer circuit, and execution only after release.

It is designed to be read alongside the five-layer overview rather than as an independent flow chart.

## Audience

- readers of `ARTICLES/02-architectural-contributions.md`
- technically literate readers who understand system flow better from diagrams than from layered decomposition

## Core message

The diagram should make one point unmistakable:

> EVA is not a single serial pipeline. It is a coordinated architecture with parallel paths, contextual broadcast, structural restriction, and mediated release.

## Required semantic elements

### 1. Input signal entry

Show signals entering from sensing / environment into the architecture.

The diagram should visually distinguish at least two broad classes:

- urgent / threat-level input
- non-urgent / status/background input

The exact naming can follow the theory language, but the distinction must be visually obvious.

### 2. Fast path

Show a direct path from sensing toward reflexive response handling.

The fast path should convey:

- immediate response
- no dependence on full deliberation
- priority under threat

This path should not be drawn as if it replaces L3 entirely; it should coexist with the slower path.

### 3. Slow path

Show a separate path from sensing into adaptive deliberation.

This path should convey:

- candidate generation
- evaluation under current drive context
- slower but richer processing

## 4. Drive broadcast as environment/context

This is the most important non-obvious visual element.

Drive should **not** be drawn as a command arrow that tells reasoning what action to take.

Instead, it should be represented as a broadcast or surrounding field affecting the deliberative process. Acceptable strategies include:

- a surrounding shaded band
- distributed arrows into multiple subcomponents
- a contextual overlay around the deliberation zone

The intended message is:

- drive modulates cognition
- drive does not function as a central command dispatcher

## 5. Anchor restriction before candidate generation

The diagram should show that anchors act **before or at the boundary of candidate generation**, not only after action is already proposed.

This should be visible as a restriction on candidate-space entry, not merely as a final filter box near execution.

## 6. Peer-circuit action selection

The diagram should show a distinct selection/release stage that is not identical to reasoning.

It should visually communicate:

- reasoning produces candidates
- a separate selection circuit mediates release
- default inhibition holds until release occurs

## 7. Execution edge

Show that environmental action or tool execution happens only after mediated release.

This is important because the architecture should not read like:

sensing → reasoning → action

It should read more like:

sensing → candidate generation under context and constraint → mediated selection → action

## Suggested composition

### Main layout

Top-to-bottom layout, L5 at top through L1 at bottom, matching the direction of `five-layer-overview.html`.

The layered skeleton should be visually recognizable as the same architecture shown in the five-layer overview. Signal flow is overlaid on that skeleton rather than replacing it.

The following relationships must remain clear:

- L1 sensing entry at the bottom of the layer stack
- split into fast reflex path (L1 → L2 → execution) and slow deliberative path (L1 → L2 → L3 → mediated release → execution)
- drive broadcast from L2 into L3's candidate generation, rendered differently from command-style arrows to convey contextual influence rather than instruction
- anchor spine on the left, consistent with the five-layer overview, with visible restriction at L3's candidate generation
- independent selection/release inside L3 before execution

### Visual priority hierarchy

Most emphasized:

1. fast vs slow path distinction
2. drive broadcast as context
3. mediated release

Secondarily emphasized:

- anchor placement
- feedback / learning loop

## Optional element: learning feedback

If the composition allows, include a feedback loop from action outcome back toward the selection system, labeled at a high level as reward-prediction update or learning signal.

This should remain secondary. The main educational purpose of the diagram is flow, not learning theory.

## Labels that should appear

Recommended labels include:

- "Sensing"
- "Fast path"
- "Slow path"
- "Drive broadcast"
- "Anchor restriction"
- "Candidate generation"
- "Selection / release"
- "Default inhibition"
- "Execution"
- "urgent signal"
- "reflex response"
- "pre-generative restriction"
- "contextual broadcast, not command"
- "default inhibition released"

## Labels to avoid

Avoid:

- code-level names
- implementation-specific file names
- roadmap references
- over-detailed neuroscience labels unless they simplify rather than complicate

## Caption intent

Suggested caption:

> Signal-flow view of EVA. Threats can trigger a fast reflex path while deliberation proceeds in parallel on a slower path. Drive acts as a contextual broadcast rather than a command stream, anchors restrict candidate generation structurally, and execution occurs only after mediated release.

## Relation to articles

This diagram pairs most directly with:

- `ARTICLES/02-architectural-contributions.md` Sections 3–5 and 7

It can also serve as a more intuitive companion for parts of `THEORY/v0.5-integrated.md` Section 12.

This diagram also pairs directly with `VISUALS/five-layer-overview.html` — the two visuals share the same architectural skeleton. The five-layer overview provides the static structural map; the signal-flow view adds dynamic flow on top of that same structure. Readers are encouraged to read them together.

## What this diagram should not try to do

It should not try to encode:

- every layer in exhaustive detail
- full roadmap sequencing
- implementation status
- all neuroscience analog mappings at once

It should remain a conceptually clean explanation of flow.
