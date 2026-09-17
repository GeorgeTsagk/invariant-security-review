# Invariant Security Review

A repository skeleton and agent skill for evidence-backed source-code security review. It guides agents from threat modeling and invariant definition through reproduction, prioritization, and durable finding tracking.

This methodology adapts the sequential review architecture described by Mandiant in Google Cloud's [Staying Ahead of Adversarial AI Through Agentic Source Code Review](https://cloud.google.com/blog/topics/threat-intelligence/staying-ahead-of-adversarial-ai-through-agentic-source-code-review/) and vulnerability triage concepts from Lightning Labs' [Severity Taxonomy](https://security.lightning.engineering/severity/). This repository is an independent implementation and is not either organization's product.

## Use

Clone or copy this repository, launch a compatible agent CLI from its root, and describe the target repository and review goal in conversation. `AGENTS.md` provides automatic onboarding for Codex and compatible tools, while `CLAUDE.md` routes Claude-compatible tools to the same instructions. For example:

> Review `/path/to/project`, starting with authentication and transaction processing. Interview me wherever the intended security invariants are unclear.

All review data for a target is written under `scan/<project>/`, a gitignored directory, so the repository itself stays a clean skeleton across targets. See [scan/README.md](scan/README.md) for the layout.

The user does not populate catalog files manually. The agent inspects the target source and available specifications, fills in [PROJECT.md](PROJECT.md), [BASELINE.md](BASELINE.md), and [THREAT_MODEL.md](THREAT_MODEL.md), creates subsystem and protocol invariants under [subsystems](subsystems), and maintains all run and finding records.

Every agent registers a durable pass before analysis. [REVIEW_LOG.md](REVIEW_LOG.md) shows who reviewed what, while detailed records under [passes](passes) capture exact scope, invariant reads and writes, evidence, outputs, and handoff. Existing invariants are discovered through [the subsystem index](subsystems/INDEX.md) and retain per-agent review history across passes.

The agent actively searches every detected invariant for gray areas. When project intent cannot be established from evidence, it asks a concrete scenario question in the session, explains the interpretations and their effect on the test oracle, then records the answer. It presents system invariants first and subsystem or protocol invariants in manageable batches. The user verifies, corrects, rejects, disputes, or defers each invariant.

The agent then stops, ranks all discovered subsystems by review priority, and asks the user to select one or more. The choices always include a separate `Global scan` option. No scan starts until the user selects its scope.

The repository is also an installable skill. Its [SKILL.md](SKILL.md) instructs compatible agents to follow [METHODOLOGY.md](METHODOLOGY.md) and use the included templates.

Keep the catalog separate from production source and from this skeleton. The agent should use isolated source worktrees for experiments, store reproducible evidence under `runs/`, and promote only validated issues into `findings/`.

Findings have a durable lifecycle: active, resolved, or discarded. Closing a
finding never deletes its evidence. The agent preserves its historical priority
and disposition history, verifies fixes dynamically before marking them
resolved, and records the requirement evidence or human decision before marking
them discarded.

Before promotion, the agent tests whether an untrusted actor actually gains a
new capability, whether the defect itself owns the claimed harm, and whether
the trigger is realistic in a supported deployment. Eligible findings score
Impact, Attack Vector, Exploitability, and Cross-victim Amplification
separately. Low-impact cases without practical reach or amplification remain
ordinary product issues rather than inflated security reports.

## Layout

- `scan/`: gitignored, one subdirectory per target holding the populated copies of the catalog files below.
- `PROJECT.md`: purpose, architecture, supported deployments, and trust boundaries.
- `AGENTS.md` and `CLAUDE.md`: automatic agent CLI entrypoints.
- `BASELINE.md`: pinned source and execution environment.
- `THREAT_MODEL.md`: assets, actors, entry points, trust assumptions, and approval state.
- `REVIEW_LOG.md`: repository-wide overview of agent passes and coverage.
- `passes/`: detailed, immutable-identity pass records and handoffs.
- `subsystems/`: system, subsystem, and protocol invariants.
- `interviews/`: unresolved questions and scoped human decisions.
- `runs/`: scan manifests, hypotheses, experiments, and logs.
- `findings/`: canonical priority-sorted findings.
- `references/`: reusable vulnerability eligibility and severity guidance.
- `templates/`: reusable records for each phase.

Define the project's priority levels with
[the priority policy template](templates/PRIORITY_POLICY.md). Maintain both
priority and subsystem views in [the findings index](findings/INDEX.md).
