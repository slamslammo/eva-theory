# CHANGELOG

Version-by-version record of substantive changes in the EVA theoretical framework.

This is not a line-by-line diff. It records the conceptual evolution—what claims were added, strengthened, weakened, or restructured at each version.

---

## Reader-Facing Simplification (2026-05-14)

Repository-level explanatory materials simplified. Theory claims unchanged.

- Root README shortened into a single reading path for technically curious readers rather than separate researcher / engineer / curious-reader tracks
- `ARTICLES/` rewritten as short, visual-first explainers with implementation details kept as boundary notes rather than theory content
- `VISUALS/` simplified to direct SVG diagrams without HTML-as-diagram-source, spec files, or preview PNG dependency
- Legacy HTML visuals and old visual specifications preserved under `archive/visuals-html-2026-05-17/`
- Visual set currently focuses on the two core diagrams: five-layer overview and signal flow

---

## v0.6 — Theoretical Extension (2026-05-08)

**Status**: Current theoretical extension. Extends v0.5 without replacing it.

v0.6 preserves the v0.5 core architecture: Claim A / Claim B, C1-C3 operating conditions, the L1-L3 structural core, the anchor system, drive as contextual broadcast, LLM as Level 3 cultural carrier, and peer-circuit action selection. It adds the theoretical commitments needed once EVA is applied beyond a single narrow runtime field.

### New in v0.6
- **Active persistence**: continuous existence is clarified as preserving future capacity to continue existing, not passively preserving current state. Inaction has cost in environments with metabolic pressure, environmental risk, or expiring opportunity.
- **Persistence target hierarchy**: the framework now distinguishes substrate instance, embodied instance, capability structure, resource and asset system, reproductive structure, group structure, and cultural information as different persistence targets.
- **Capability sources and provenance**: structural invariants, existence-field conditions, designer-given priors, individually acquired capabilities, and inherited priors are separated by origin, modification permission, and identity implications.
- **Structural invariant / operational content distinction**: release authority, anchor boundaries, drive prototypes within a life, and field conditions are structural; LLM advice, retrieved content, candidate content, and learned biases are operational content.
- **Observable stability**: stability is introduced as the external measurement interface for continuous existence, with architecture-neutral metric families and architecture-specific audit.
- **Multi-dimensional outcome**: outcome is treated as a vector evaluated under drive context, with hard constraints separated from soft trade-offs.
- **Extension discipline**: new scenarios default to scenario specification rather than theory expansion. Theory extension requires inexpressibility, internal contradiction, or boundary failure.

### Revisions to how v0.5 should be read
- v0.5 references to continuous existence should be read through the active-persistence interpretation.
- The four-drive list in v0.5 is a field condition, not a universal architectural drive inventory.
- v0.5's skill library should be read as simplified relative to v0.6's provenance distinction.
- "Grow, don't deploy" applies only to content that is permitted to grow; structural invariants and existence-field conditions do not grow within a life.
- LLM positioning in v0.5 is preserved and sharpened: language models provide operational content, not release authority.

### Explicit limits
- Inherited prior mechanisms are positioned theoretically but not implemented.
- Persistence levels 5-7 are theoretical placeholders for future versions.
- Cross-environment transfer, physical embodiment, and multi-agent structural commitments are not resolved by v0.6.

---

## Reader-Facing Content Expansion (2026-04-20)

Repository-level content packaging expanded. Theory claims unchanged.

- Root `README.md` rewritten as a reader-facing entry point with clearer reading paths, repository structure, implementation relationship, and visual navigation
- `ARTICLES/` added as a public-facing companion layer, including a paradigm introduction and an engineering-oriented article
- `VISUALS/` added as a public-facing diagram layer, with static preview assets for repository browsing
- `index.html` added as a repository landing page for the public-facing visuals and their source/spec links
- Cross-navigation between theory, articles, visuals, and implementation correspondence made explicit across the repository

---

## Repository Rename and Naming Note (2026-04-20)

Non-theoretical housekeeping. Theory content unchanged.

- Repository renamed from `agent-cognitive-architecture` to `eva-theory` to consolidate project identity (theory + implementation both under the EVA name)
- Naming note added to `README.md` and `THEORY/v0.5-integrated.md` (Abstract section): clarifies that EVA derives from Hebrew *Chava* (life), reflecting the project's continuous-existence framing, without claiming agents are "alive" in any biological sense
- Cross-references between `eva-theory` and `eva-agent` repositories made explicit

---

## v0.5 Pre-Publication Polish (2026-04-20)

Small precision adjustments before public release. No substantive claims changed.

- "Only coherent solution" strengthened to "most coherent under EVA constraints" throughout drive-as-context discussions (3 locations). Preserves architectural force while narrowing to EVA's specific coordination requirements.
- Section 8.5 on LLM as Level 3 cultural carrier: boundary clarification added, explicitly not denying the role of model architecture or optimization in LLM capability.
- Section 4.3: operational test added for distinguishing existence-centered from task-centered agents (three-condition negative test).
- Section 14 correspondence table: implementation references abstracted for consistency with the pre-release disclosure level in `IMPLEMENTATION/eva-agent-correspondence.md`.

The document is still called v0.5. These are precision refinements within v0.5, not a new version number.

---

## v0.5 — Integrated Stable Version (2026-04-19)

**Status**: Core stable version. v0.6 extends this version without replacing it.

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

**Decided at v0.1, stable through v0.6**:
- Five-layer architecture (not three, not seven)
- Biological evolution as reference system
- Anchor system as vertical cross-layer structure

**Decided at v0.3, stable through v0.6**:
- Scope limited to C1/C2/C3
- Epistemic three-layer grounding (A/B/C)
- L4/L5 included in architecture but with weaker derivation

**Decided at v0.5**:
- No paper split; Claim A and Claim B remain in single document
- LLM positioned as Level 3 cultural carrier; building agent's own memory layer takes engineering priority over stronger LLM integration
- Drive-as-context framed as architectural necessity (not stylistic preference)
- Peer circuit framed as structural requirement (not design choice)

**Decided at v0.6**:
- v0.6 extends v0.5; it does not supersede the v0.5 core architecture
- Continuous existence should be read as active persistence
- New environments default to scenario specification rather than theory extension
- Capability provenance and structural-invariant boundaries must remain explicit

---

## Conventions

- Version numbers increment on substantive theoretical change, not editorial polishing
- All earlier versions are preserved in `THEORY/` — they document the reasoning path, not just the final product
- Substantive rejected alternatives are recorded here, not silently dropped
