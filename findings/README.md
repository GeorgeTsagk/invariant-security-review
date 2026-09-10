# Findings

This directory is the canonical store for evidence-backed findings. Run directories contain working hypotheses, test patches, and logs.

## Naming and ordering

Store reports as `P<priority>-<concrete-behavior>.md`. Lower priority numbers sort first. The project must define and approve what each level means for its assets and threat model using [the priority policy template](../templates/PRIORITY_POLICY.md).

Priority follows demonstrated impact and exposure. Confidence is separate. A critical-looking pattern with uncertain reachability is not automatically high priority.

Maintain [INDEX.md](INDEX.md) with views grouped by priority and subsystem. Deduplicate by root cause and invariant, while preserving all affected entry points in the canonical report.

## Promotion gate

A canonical finding requires:

- A justified invariant or normative requirement.
- Realistic attacker prerequisites and reachability.
- A complete source path to a meaningful consequence.
- Counterevidence review.
- Dynamic reproduction with a valid control.
- Exact revisions, configuration, commands, and limitations.
- Human expert review before disclosure.

Unresolved and disproven hypotheses remain in their originating run, not here.

Keep findings private. Do not publish, push, comment, or disclose without explicit authorization.
