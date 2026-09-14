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

## Pass registration and prior work

Before target analysis, register this agent pass:

1. Choose a stable pass ID and agent name. Use runtime identity when available; otherwise use a unique local label. Record provider, model, CLI, and session ID only when known. Never invent identity metadata.
2. Create `passes/<pass-id>.md` from the pass template with status `in progress` and add it to `REVIEW_LOG.md`.
3. Enumerate files and invariant IDs under `subsystems/`, then reconcile them with `subsystems/INDEX.md`. The index is a discovery aid, not the sole authority. Repair missing or stale index entries. Read relevant invariant files, `interviews/VERIFICATION.md`, applicable decisions, prior passes, runs, and findings before proposing new invariants or repeating analysis.
4. Treat existing invariants as persistent review state. Update them in place when they describe the same property. Preserve stable IDs, prior wording, decisions, and review history. Record conflicts instead of silently replacing prior conclusions.
5. For every invariant substantively examined, add one review-history row for this pass showing the agent name and actions such as read, created, modified, challenged, or validated. Add the history table if an older record lacks one. Update `subsystems/INDEX.md` after invariant changes.
6. Keep the pass file current at phase boundaries. Before stopping, update its status, exact coverage, artifacts changed, unresolved work, and handoff, then synchronize its row in `REVIEW_LOG.md`.

An inventory listing alone is not a substantive read. Agent identity is provenance, not authentication. Never claim that a prior pass reviewed code or semantics beyond its recorded coverage.

## Conversational onboarding

1. Infer the review goal, target repository, and requested scope from the session.
2. Inspect source, history, documentation, configuration, dependency metadata, and available specifications.
3. Populate missing project context and update stale context in `PROJECT.md`, `BASELINE.md`, and `THREAT_MODEL.md`. Preserve prior sourced decisions. Mark unavailable facts as unknown instead of inventing them.
4. Reuse and reassess existing invariant records before deriving missing system, subsystem, or protocol invariants. Classify each as clear, gray, conflicting, or unknown.
5. Present the system invariants first in short, readable language. Then present subsystem and protocol invariants in manageable batches.
6. Require the user to verify, correct, reject, dispute, or defer every proposed invariant. Maintain the result in `interviews/VERIFICATION.md`.
7. For every gray, conflicting, or unknown invariant, ask a concrete scenario question that distinguishes the plausible meanings. Record each answer in `interviews/DECISIONS.md` and update affected records.
8. Present the resulting threat model and verified invariant scope.
9. Rank the discovered subsystems by review priority using protected-asset impact, attacker reachability, trust boundaries, privilege, state complexity, recovery risk, code churn, and unresolved uncertainty. Explain each rank briefly. Review priority is not finding severity.
10. Stop and ask the user which subsystems to scan. Use a multi-select control when available, or a numbered checklist that accepts multiple choices. Include a recommended selection and a distinct `Global scan` option covering every in-scope subsystem.
11. Wait for the user's selection. Record it in the scan manifest and analyze only the selected scope. Choosing `Global scan` supersedes individual choices.

Ask for information incrementally. Do not present blank templates or a bulk questionnaire. Continue evidence collection that does not depend on an unanswered question. Do not replace invariant review with a generic yes-or-no approval question.

Completing onboarding, threat-model approval, or invariant verification never authorizes a system-wide scan. Do not begin broad entry-point tracing, hypothesis generation, or dynamic experiments until the user passes the subsystem-selection gate.

## Required behavior

- Pin the target source, dependencies, configuration, build mode, and catalog revision.
- Create and update the catalog files on the user's behalf throughout the review.
- Register every agent pass and make its identity, scope, invariant reads, invariant writes, and disposition discoverable from `REVIEW_LOG.md`.
- Define system, subsystem, and protocol invariants before treating implementation behavior as correct.
- Investigate specifications and code before asking the user. Actively search each invariant for vague, undefined, disputed, conflicting, or materially unclear semantics. Record answers as scoped decisions, not universal assumptions.
- Track requirement status separately from enforcement status.
- Trace attacker-controlled input through the complete implementation path to a meaningful consequence.
- Keep hypotheses separate from findings. Seek counterevidence before reproduction.
- Promote a hypothesis only after a meaningful dynamic reproduction with a valid control.
- Organize findings by subsystem and invariant, deduplicate by root cause, and sort canonical reports by project-defined priority.
- Keep severity and confidence separate. Preserve unresolved and disproven hypotheses.
- Require explicit subsystem selection for each new scan. Never infer `Global scan` from a general request to review the repository.
- Preserve prior invariant work. Never overwrite, renumber, or regenerate an existing invariant without first reading its history and applicable decisions.
- Do not publish findings, push changes, or contact third parties without explicit user authorization.

Use files in [templates](templates) when creating catalog entries. Read only the templates needed for the current phase.

## Human decisions

Ask one concrete distinguishing question at a time when practical. Show the conflicting interpretations, an example, and how the answer changes the test oracle. Continue independent work while unrelated questions remain open.

Treat terms such as valid, current, owned, trusted, final, available, authorized, live, canonical, and synchronized as suspect until their scope and temporal meaning are clear. Probe boundary conditions involving retries, partial completion, concurrency, restart, rollback, reorganization, stale state, delegation, and cross-subsystem ownership. Also probe differences between local state and remote claims, producer guarantees and consumer assumptions, and specification intent and existing implementation behavior.

Before a broad scan, present the synthesized threat model and every selected invariant for human review. Record an explicit status for each invariant: verified, corrected, rejected, disputed, or deferred. A blanket approval is insufficient while any selected invariant has an unasked gray area. Existing explicit feedback satisfies this gate only for the exact invariant IDs and scope it addressed.

Do not silently choose the most likely interpretation. If different reasonable interpretations produce different valid or adversarial test outcomes, ask the user and preserve the uncertainty until answered.

## Scan-scope selection

After invariant verification, reach a stopping point. Present every in-scope subsystem with its stable name, short responsibility, review-priority rank, concise rationale, and applicable system-invariant IDs. Recommend the highest-value starting scope without hiding lower-ranked options.

Ask for a multi-selection. Always include `Global scan` as a separate option, but never preselect or imply it. If the interface cannot render a multi-select control, ask the user to reply with one or more subsystem numbers or `Global scan`. Do not substitute a yes-or-no confirmation.

Start a run only after the user selects the scope. If the user selects several subsystems, preserve their priority order unless the user specifies another order. Return to this gate before expanding the run to an unselected subsystem.

## Completion

A review run is complete only when every selected invariant and entry point is accounted for as analyzed, exercised, disproven, unresolved, out of scope, or not examined. An agent pass is complete only when its pass record, overview row, and touched invariant histories are current. Absence of findings is never proof of correctness.
