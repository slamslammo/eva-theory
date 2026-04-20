# FAQ

## 1. Is EVA trying to create an AI with a survival instinct?

No.

EVA does **not** argue for unconstrained self-preservation. Its claim is narrower: for a certain class of agents, continuity should be treated as an architectural concern rather than an afterthought. In EVA, continuity is always bounded by integrity constraints and anchors.

For deeper reading, see `THEORY/v0.5-integrated.md` and `ARTICLES/03-related-work-and-positioning.md`.

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

For an engineering-oriented entry, see `ARTICLES/02-architectural-contributions.md` and `IMPLEMENTATION/eva-agent-correspondence.md`.

## 5. What is implemented today?

The theory is relatively stable at **v0.5**, but the implementation remains **partial**.

Early implementation work covers lower-layer concerns such as lifecycle continuity, sensing, and minimum integrity-pressure response. Central EVA mechanisms that are not yet fully realized include continuous drive broadcast, salience-weighted memory, mediated action selection, structural anchors, self-model, and social cognition.

For the current implementation map, see `IMPLEMENTATION/eva-agent-correspondence.md`.
