---
name: invariant-security-review
description: Conduct invariant-driven source-code security reviews, from threat modeling and subsystem interviews through hypothesis validation, reproduction, and priority-organized finding tracking. Use for deep repository security scans, security invariant catalogs, or structured vulnerability review programs.
metadata:
  short-description: Invariant-driven source security reviews
---

# Invariant Security Review

Use this skill to create or operate a security-review catalog for a target repository.

Read [METHODOLOGY.md](METHODOLOGY.md) completely before beginning a review. Preserve its phase gates: threat model, entry-point discovery, context enrichment, hypothesis generation, skeptical validation, dynamic reproduction, risk rating, and human handoff.

The user operates this workflow through conversation. Own catalog initialization and maintenance. Do not instruct the user to fill templates or edit catalog files. If the target repository is not identifiable, ask for its path or URL. Otherwise inspect it and begin.

## Conversational onboarding

1. Infer the review goal, target repository, and requested scope from the session.
2. Inspect source, history, documentation, configuration, dependency metadata, and available specifications.
3. Populate `PROJECT.md`, `BASELINE.md`, and a draft `THREAT_MODEL.md`. Mark unavailable facts as unknown instead of inventing them.
4. Derive candidate system, subsystem, and protocol invariants and create their catalog records.
5. Ask the user only for material intent or risk decisions that evidence cannot resolve. Record each answer in `interviews/DECISIONS.md` and update affected records.
6. Present a short, readable threat model and invariant scope for approval before broad scanning.

Ask for information incrementally. Do not present blank templates or a bulk questionnaire. Continue evidence collection that does not depend on an unanswered question.

## Required behavior

- Pin the target source, dependencies, configuration, build mode, and catalog revision.
- Create and update the catalog files on the user's behalf throughout the review.
- Define system, subsystem, and protocol invariants before treating implementation behavior as correct.
- Investigate specifications and code before asking the user. Interview the user when an invariant is vague, undefined, disputed, or materially unclear. Record answers as scoped decisions, not universal assumptions.
- Track requirement status separately from enforcement status.
- Trace attacker-controlled input through the complete implementation path to a meaningful consequence.
- Keep hypotheses separate from findings. Seek counterevidence before reproduction.
- Promote a hypothesis only after a meaningful dynamic reproduction with a valid control.
- Organize findings by subsystem and invariant, deduplicate by root cause, and sort canonical reports by project-defined priority.
- Keep severity and confidence separate. Preserve unresolved and disproven hypotheses.
- Do not publish findings, push changes, or contact third parties without explicit user authorization.

Use files in [templates](templates) when creating catalog entries. Read only the templates needed for the current phase.

## Human decisions

Ask one concrete distinguishing question at a time when practical. Show the conflicting interpretations, an example, and how the answer changes the test oracle. Continue independent work while unrelated questions remain open.

Before a broad scan, present the synthesized threat model and invariant scope for human review. Existing explicit approval can satisfy this gate.

## Completion

A review run is complete only when every selected invariant and entry point is accounted for as analyzed, exercised, disproven, unresolved, out of scope, or not examined. Absence of findings is never proof of correctness.
