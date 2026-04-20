# Five-Layer Overview — Visual Specification

This file defines the intended content and reading logic for a reader-facing EVA architecture overview diagram.

## Purpose

This diagram is the **static structure map** for EVA.

It should help a new reader answer four questions quickly:

1. What are the major layers of EVA?
2. Which parts are the strongest current focus of the theory?
3. How do anchors relate to the layers?
4. Why is the basal ganglia analog shown as a peer circuit rather than inside the reasoning layer?

## Audience

- readers coming from `ARTICLES/01-paradigm-introduction.md`
- readers entering `ARTICLES/02-architectural-contributions.md`
- technically literate visitors who need a structural map before reading the full theory

## Diagram type

A single-page **static architecture overview**.

It should privilege clarity over completeness. It is not meant to visualize every data flow or every subcomponent in detail.

## Required semantic elements

### 1. Five main layers

Show five layers vertically, from lower-level continuity support toward higher-order cognition:

- L1 — Homeostatic sensing
- L2 — Drive layer
- L3 — Adaptive deliberation
- L4 — Self-model
- L5 — Social cognition

## 2. Relative status emphasis

The diagram should visually indicate that:

- L1–L3 are the strongest current theoretical core
- L4–L5 are part of the architecture but have weaker derivational status

This can be done with opacity, annotation, or labeling, but should not imply that L4/L5 are absent.

## 3. Anchor system as cross-layer structure

The anchor system should not appear as a small module inside one layer.

It should be shown as a **cross-layer vertical or spanning constraint structure** that applies across the architecture.

The intended message is:

- anchors are not a peripheral rule box
- anchors are not confined to one module
- anchors constrain multiple layers consistently

## 4. Basal ganglia analog as peer circuit

Within L3, the reasoning core and basal ganglia analog should not be drawn in a parent-child relationship.

They should be shown as distinct but interacting components, with the basal ganglia analog positioned as a **peer circuit** involved in selection and release, not as a small sub-module inside reasoning.

## 5. Tool layer / execution edge

It should be visually clear that environmental action happens only after mediated release.

The exact rendering is flexible, but the diagram should not imply direct execution from reasoning alone.

## Recommended composition

### Top-level layout

- central vertical stack for L1–L5
- anchor bar or anchor spine crossing multiple layers
- L3 drawn with internal separation among:
  - memory-related structure
  - reasoning core
  - basal ganglia peer circuit
- execution/tool edge shown at the output side of L3

### Visual priorities

Emphasize:

- layer distinction
- cross-layer anchors
- L3 internal structural differentiation

De-emphasize:

- implementation naming
- future roadmap
- low-level operational detail

## Labels that should appear

Recommended minimal labels:

- "L1 Homeostatic sensing"
- "L2 Drive layer"
- "L3 Adaptive deliberation"
- "L4 Self-model"
- "L5 Social cognition"
- "Anchor system"
- "Reasoning core"
- "Basal ganglia analog"
- "Default inhibition / selective release"

## Labels to avoid

Avoid:

- source-code names
- roadmap stage names
- implementation-specific file references
- strong claims like "proven" or "complete"

## Caption intent

Suggested caption:

> High-level structural overview of EVA. The architecture is organized around homeostatic sensing, drive structure, and adaptive deliberation as the strongest current core, with anchors acting across layers and action selection mediated by a peer circuit rather than collapsed into reasoning.

## Relation to articles

This diagram pairs best with:

- `ARTICLES/01-paradigm-introduction.md` as an orientation aid
- `ARTICLES/02-architectural-contributions.md` Sections 3–5 as a structural map

## What this diagram should not try to do

It should not attempt to show:

- full signal timing
- fast path vs slow path dynamics in detail
- roadmap / implementation sequence
- exhaustive neuroscience mapping

Those belong in separate visuals or in the theory text.
