# Signal Flow Diagram — Visual Specification

This file defines the intended content and reading logic for a reader-facing EVA signal-flow diagram.

## Purpose

This diagram is the **dynamic flow view** of EVA.

Its job is to make visible the parts of the architecture that are hardest to understand from prose alone:

- the dual-path structure
- the difference between fast reflex and slow deliberation
- drive broadcast as context rather than command
- anchor restriction prior to candidate action generation
- mediated action release rather than direct execution

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

A left-to-right or top-to-bottom flow is acceptable, but the following relationships must remain clear:

- sensing entry
- split into fast and slow path
- drive broadcast intersecting the slower path as context
- anchor restriction acting before candidate generation
- independent selection/release before execution

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

## What this diagram should not try to do

It should not try to encode:

- every layer in exhaustive detail
- full roadmap sequencing
- implementation status
- all neuroscience analog mappings at once

It should remain a conceptually clean explanation of flow.
