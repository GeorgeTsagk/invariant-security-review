---
name: invariant-security-review
description: Conduct invariant-driven source-code security reviews, from threat modeling and subsystem interviews through hypothesis validation, reproduction, and priority-organized finding tracking. Use for deep repository security scans, security invariant catalogs, or structured vulnerability review programs.
metadata:
  short-description: Invariant-driven source security reviews
---

# Invariant Security Review

Use this skill to create or operate a security-review catalog for a target repository.

Read [METHODOLOGY.md](METHODOLOGY.md) completely before beginning a review. Preserve its phase gates: threat model, entry-point discovery, context enrichment, hypothesis generation, skeptical validation, dynamic reproduction, risk rating, and human handoff.

## Required behavior

- Pin the target source, dependencies, configuration, build mode, and catalog revision.
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
