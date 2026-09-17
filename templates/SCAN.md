# Review run

## Manifest

- Date and run ID:
- Participating pass IDs and agent names:
- Source repository, full commit, branch or tag, and tree hash:
- Catalog commit:
- Toolchain, dependencies, and replacements:
- Build tags and binary provenance:
- Deployment configuration and storage backends:
- Subsystems, invariant IDs, and entry-point IDs:
- Invariant verification ledger and remaining gray areas:
- Threat-model approval and decision reference:
- Ranked subsystem options shown to the user:
- User-selected subsystems and order:
- Global scan selected: yes / no
- Selection date and session reference:
- Explicitly unselected subsystems:
- Trusted services and attacker capabilities:
- Vulnerability eligibility and severity policy reference:
- Open requirements and decision references:
- Time or resource budget, if assigned:

## Coverage

Account for every selected invariant and entry point. Record controlled fields, concrete paths, validation gates, persistence, consumers, exceptions, and unexamined branches.

## Hypotheses

Link candidates in `hypotheses.md`. Keep generated, disproven, rejected, unresolved, and promoted outcomes distinct.

## Experiments

Record patches, exact commands, expected and actual outcomes, seeds, valid
controls, logs, persistent effects, and environment limitations. For every
proof, state what it establishes, what it does not establish, and which boundary
it exercises.

## Final disposition

List reproduced security findings, product defects rejected by the vulnerability gates, disproven and rejected candidates, unresolved questions, out-of-scope paths, and paths not examined. Absence of findings is not proof of correctness.
