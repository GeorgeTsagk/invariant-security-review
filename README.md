# Invariant Security Review

A repository skeleton and agent skill for evidence-backed source-code security review. It guides agents from threat modeling and invariant definition through reproduction, prioritization, and durable finding tracking.

This methodology adapts the sequential review architecture described by Mandiant in Google Cloud's [Staying Ahead of Adversarial AI Through Agentic Source Code Review](https://cloud.google.com/blog/topics/threat-intelligence/staying-ahead-of-adversarial-ai-through-agentic-source-code-review/). This repository is an independent implementation and is not a Google or Mandiant product.

## Use

Clone or copy this repository, launch a compatible agent CLI from its root, and describe the target repository and review goal in conversation. `AGENTS.md` provides automatic onboarding for Codex and compatible tools, while `CLAUDE.md` routes Claude-compatible tools to the same instructions. For example:

> Review `/path/to/project`, starting with authentication and transaction processing. Interview me wherever the intended security invariants are unclear.

The user does not populate catalog files manually. The agent inspects the target source and available specifications, fills in [PROJECT.md](PROJECT.md), [BASELINE.md](BASELINE.md), and [THREAT_MODEL.md](THREAT_MODEL.md), creates subsystem and protocol invariants under [subsystems](subsystems), and maintains all run and finding records.

The agent actively searches every detected invariant for gray areas. When project intent cannot be established from evidence, it asks a concrete scenario question in the session, explains the interpretations and their effect on the test oracle, then records the answer. It presents system invariants first and subsystem or protocol invariants in manageable batches. The user verifies, corrects, rejects, disputes, or defers each invariant.

The agent then stops, ranks all discovered subsystems by review priority, and asks the user to select one or more. The choices always include a separate `Global scan` option. No scan starts until the user selects its scope.

The repository is also an installable skill. Its [SKILL.md](SKILL.md) instructs compatible agents to follow [METHODOLOGY.md](METHODOLOGY.md) and use the included templates.

Keep the catalog separate from production source. The agent should use isolated source worktrees for experiments, store reproducible evidence under `runs/`, and promote only validated issues into `findings/`.

## Layout

- `PROJECT.md`: purpose, architecture, supported deployments, and trust boundaries.
- `AGENTS.md` and `CLAUDE.md`: automatic agent CLI entrypoints.
- `BASELINE.md`: pinned source and execution environment.
- `THREAT_MODEL.md`: assets, actors, entry points, trust assumptions, and approval state.
- `subsystems/`: system, subsystem, and protocol invariants.
- `interviews/`: unresolved questions and scoped human decisions.
- `runs/`: scan manifests, hypotheses, experiments, and logs.
- `findings/`: canonical priority-sorted findings.
- `templates/`: reusable records for each phase.

Define the project's priority levels with
[the priority policy template](templates/PRIORITY_POLICY.md). Maintain both
priority and subsystem views in [the findings index](findings/INDEX.md).
