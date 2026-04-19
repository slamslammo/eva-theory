# CHANGELOG

Version-by-version record of substantive changes in the EVA theoretical framework.

This is not a line-by-line diff. It records the conceptual evolution—what claims were added, strengthened, weakened, or restructured at each version.

---

## Repository Rename and Naming Note (2026-04-20)

Non-theoretical housekeeping. Theory content unchanged.

- Repository renamed from `agent-cognitive-architecture` to `eva-theory` to consolidate project identity (theory + implementation both under the EVA name)
- Naming note added to `README.md` and `THEORY/v0.5-integrated.md` (Abstract section): clarifies that EVA derives from Hebrew *Chava* (life), reflecting the project's continuous-existence framing, without claiming agents are "alive" in any biological sense
- Cross-references between `eva-theory` and `eva-agent` repositories made explicit

---

## v0.5 — Integrated Stable Version (2026-04-19)

**Status**: Current stable version. Theoretical framework considered stable; further changes expected to be precision refinements rather than structural modifications.

### Integrates from v0.4 (preserved)
- Claim A (paradigm) / Claim B (structural) explicit separation
- Anchor minimal formalization: `G(s) → A'(s) ⊆ A(s)` — pre-generative domain restriction vs. post-hoc rule filtering
- Epistemic three-layer structure (Level A established / Level B hypothesis / Level C contribution)
- L4/L5 weaker derivational strength explicitly acknowledged
- Unconstrained self-preservation disambiguation (Section 4.5)

### Restored from v0.3 (reversing v0.4 softening)
- **Drive as context** — recovered as "the coherent solution to cross-system coordination in an architecture without a central controller." v0.4 had softened to "historical pressure becomes current bias," which loses the architectural force.
- **LLM as Level 3 cultural carrier** — recovered as independent core engineering judgment with explicit roadmap consequences (Section 8.5 and 15.2). v0.4 had demoted to "can be interpreted as cultural access," losing the engineering priority judgment.
- **Peer circuit structural necessity** — explicit "why not sub-module" argument added (Section 8.6.4), with three structural breakdowns: default inhibition becomes policy not structure; selection and justification collapse; habit formation entangles with reasoning updates.

### New in v0.5
- Section 1.3: explicit decision not to split into separate papers, with rationale against the Claim A/B split strategy
- Section 4.3: disambiguation from related concepts (long-running, persistent, autonomous, artificial life)
- Section 11.7: anchor system positioned as core contribution, not peripheral safety mechanism — "existence-centered design without a robust anchor system is not a safe version of EVA; it is a different and dangerous thing"

### Decisions locked at v0.5
- Two claims remain in single document; no separate paradigm/structural papers
- EVA positioned as "new paradigm for a problem class," not "new architecture for adaptive agents"
- LLM positioned as Level 3 cultural information carrier (not reasoning engine), with engineering priority consequences

---

## v0.4 — ChatGPT-Contributed Structural Refinement (2026-04-19)

**Status**: Intermediate version. Contributed key structural improvements integrated into v0.5, but over-softened some core claims in pursuit of standard academic defensibility.

### Contributions accepted into v0.5
- Claim A / Claim B separation as organizing structure
- Minimal formal distinction between anchor (pre-generative) and rule (post-hoc filter)
- Three-level epistemic structure (Established / Hypothesis / Engineering)
- Explicit weakness acknowledgment for L4/L5 derivation
- Distinction between continuous existence and unconstrained self-preservation

### Contributions rejected or reversed in v0.5
- Softening of "drive as context" claim — reversed; sharp architectural version restored
- Reframing LLM position as auxiliary interpretation — reversed; independent core engineering judgment restored
- Suggestion to split paper into paradigm + structural versions — rejected; combined document retained with explicit rationale (Section 1.3)

### Analysis
v0.4's contribution to structure was substantial and valuable. Its softening of three core claims, while defensible from a publishability standpoint, would have compromised EVA's paradigm identity. v0.5 adopts the structural improvements while restoring the sharp core.

---

## v0.3 — Scoped Version (2026-04-17)

**Status**: Major theoretical consolidation. First version with fully articulated scope, epistemic layering, and L2→L3 timescale mismatch argument.

### Major additions
- **Operating conditions (C1/C2/C3)**: explicitly states scope of applicability — framework does not apply to static environments, one-shot task systems, or benchmarks with costless reset
- **Three-level theoretical grounding**: separates established science / theoretical hypotheses / engineering contributions; prevents weaker claims from being smuggled into the space of stronger ones
- **L2→L3 timescale mismatch formalization**: "if environmental change outruns inherited encoding rate, a within-lifetime adaptation mechanism becomes advantageous" — the strongest theoretical bridge in the framework
- **Three levels of non-genetic information carriage**: individual memory / social learning / cumulative culture; supported by biological evidence
- **LLM positioning**: first version to position LLMs as Level 3 cultural information carriers rather than reasoning engines
- **Related Work expansion**: Voyager, Agent Economy, RLHF, Constitutional AI, Predictive Processing, Hierarchical Control

### Language shifts from v0.2
- "Necessity" language replaced with "structural coherence under stated conditions"
- "First-principles derivation" claims reduced to match actual evidential basis
- Limitations section expanded to include quantification gaps, uniqueness disclaimer, empirical validation status

### Locked at v0.3
- Scope definition will not expand beyond C1–C3
- Epistemic layering (A/B/C) will remain throughout future versions
- L4/L5 remain in architecture but with acknowledged weaker support

---

## v0.2 — Expanded Coverage (2026-04-17)

**Status**: First substantially complete draft. Expanded initial structure with worked examples and developmental dynamics.

### Major additions
- **Evolutionary progression chapter** (Section 2): traces logical sequence of layer emergence — L1 sensing, L2 drives, L3 deliberation spiral
- **Worked example**: instance validity threat traced through all seven steps from detection to RPE recording
- **Anchor dynamics**: developmental sequence from initialization to personality crystallization; explicit distinction between designer-injected (L0/L1) and emergent (L2+) anchors
- **eva-agent correspondence table**: maps theoretical layers to current implementation components, identifies explicit gaps
- **Basal ganglia insights consolidated**: four key insights about default inhibition, RPE, skill crystallization, and peer circuit nature

### Structure
- "Emotion as reasoning context, not reasoning input" established as core architectural property of L2
- Anchor system positioned as cross-layer vertical constraint
- Developmental phases 0–5 articulated as ordered sequence

---

## v0.1 — Initial Commit (2026-04-17)

**Status**: Foundation. Established theoretical structure that remained stable through all subsequent versions.

### Core structure established
- Five-layer architecture (L1–L5)
- Three core engineering contributions:
  - Evolutionary necessity as design criterion
  - Basal ganglia as independent peer circuit
  - Emotion as reasoning context
- Anchor system as cross-layer constraint
- Distinction between task-centered and existence-centered agents

### Initial positioning
- First articulation of "continuous existence first" paradigm
- Initial critique of task-centered agent frameworks
- Biological reference system introduced as existence proof, not design template

---

## Decisions History

This section records decisions that have remained stable across versions and will not be reopened without substantive new information.

**Decided at v0.1, stable through v0.5**:
- Five-layer architecture (not three, not seven)
- Biological evolution as reference system
- Anchor system as vertical cross-layer structure

**Decided at v0.3, stable through v0.5**:
- Scope limited to C1/C2/C3
- Epistemic three-layer grounding (A/B/C)
- L4/L5 included in architecture but with weaker derivation

**Decided at v0.5**:
- No paper split; Claim A and Claim B remain in single document
- LLM positioned as Level 3 cultural carrier; building agent's own memory layer takes engineering priority over stronger LLM integration
- Drive-as-context framed as architectural necessity (not stylistic preference)
- Peer circuit framed as structural requirement (not design choice)

---

## Conventions

- Version numbers increment on substantive theoretical change, not editorial polishing
- All earlier versions are preserved in `THEORY/` — they document the reasoning path, not just the final product
- Substantive rejected alternatives are recorded here, not silently dropped
