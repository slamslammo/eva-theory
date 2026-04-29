# eva-agent Theory / Implementation Bridge

This file is intentionally thin.

`eva-theory` is the theory repository. It defines EVA's problem framing, scope conditions, core architectural claims, terminology, and public-facing explanatory materials.

The public companion implementation project is [`eva-agent`](https://github.com/slamslammo/eva-agent). That project is the right place for:

- current implementation status
- source-level design
- roadmap and engineering priorities
- implementation-specific documentation

## What remains in this repository

This repository keeps only the minimal bridge needed between theory and implementation:

- `THEORY/v0.5-integrated.md` — canonical public theory text
- `ARTICLES/02-architectural-contributions.md` — reader-facing explanation of EVA's four main architectural choices
- `VISUALS/five-layer-overview.html` and `VISUALS/signal-flow.html` — public-facing architecture visuals

## How to use this boundary

- Read `eva-theory` when you want the architecture as theory.
- Read [`eva-agent`](https://github.com/slamslammo/eva-agent) when you want implementation status or implementation-specific design.
- If an implementation decision appears to diverge from the theory, inspect the implementation project directly and treat this repository as authoritative for the stated architecture until the theory text is revised.

The purpose of this split is to keep the theory stable and legible without turning this repository into a moving implementation status board.
