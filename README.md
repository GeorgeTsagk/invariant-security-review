# Invariant Security Review

A repository skeleton and agent skill for evidence-backed source-code security review. It guides agents from threat modeling and invariant definition through reproduction, prioritization, and durable finding tracking.

This methodology adapts the sequential review architecture described by Mandiant in Google Cloud's [Staying Ahead of Adversarial AI Through Agentic Source Code Review](https://cloud.google.com/blog/topics/threat-intelligence/staying-ahead-of-adversarial-ai-through-agentic-source-code-review/). This repository is an independent implementation and is not a Google or Mandiant product.

## Use

Clone or copy this repository as the security catalog for a target project. Fill in [PROJECT.md](PROJECT.md), [BASELINE.md](BASELINE.md), and [THREAT_MODEL.md](THREAT_MODEL.md), then define subsystem invariants under [subsystems](subsystems).

The repository is also an installable skill. Its [SKILL.md](SKILL.md) instructs compatible agents to follow [METHODOLOGY.md](METHODOLOGY.md) and use the included templates.

Keep the catalog separate from production source. Use isolated source worktrees for experiments. Store reproducible evidence under `runs/`, and promote only validated issues into `findings/`.

## Layout

- `PROJECT.md`: purpose, architecture, supported deployments, and trust boundaries.
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
