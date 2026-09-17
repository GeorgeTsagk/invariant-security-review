# <triage-severity>: Concrete violated behavior

Target: `<repository> @ <full-commit> (<branch-or-tag>)` | Tree: `<tree-hash-or-unavailable>` | Date: `<YYYY-MM-DD>`

- Finding revision override, only if different from Target:
- Reporter-provided severity, scale, and rationale:
- Reporting pass and agent:

## Triage classification

- Severity: T0 / T1 / T2 / T3
- Plain-language tier anchor:
- Mechanical tier calculation:
- Attack Vector: Local / Adjacent / Network
- Exploitability: Low / Med / High
- Impact: Low / Med / High
- Virality: Low / Med / High
- Human override of mechanical tier, if any:
- Severity policy and decision reference:
- Confidence:
- Vulnerability eligibility decision and gate evidence:
- Low-severity exit result:

The triage classification never replaces the reporter-provided severity.

## Code anchors

Use repository-relative paths and one contiguous range per row. The first row
must locate the defect itself. For an omission, cite where the missing behavior
belongs. Name a dependency or external repository explicitly.

| Order | Repository | File | Line start | Line end | What this establishes |
| --- | --- | --- | --- | --- | --- |
| 1 | target | path/to/file | | | Defect location |

## Finding

- Finding status: active / resolved / discarded
- Disposition rationale:
- Subsystem and invariant IDs:
- Originating run:
- Originating and validating passes and agents:
- Catalog commit:
- Deployment and attacker prerequisites:
- Adversary, input authorship, and baseline capability:
- Capability increase caused by the defect:
- Controlled input and complete path:
- Existing controls and why they do not prevent the case:
- Expected behavior:
- Actual behavior and demonstrated impact:
- Harm prevented by fixing this defect alone:
- Root cause and affected entry points:
- Related findings and shared mechanism:

## Proof and limitations

- Proof artifact, command, configuration, and revision:
- What the proof directly establishes:
- What the proof does not establish:
- Real boundary exercised:
- Valid control and test convention:
- Persistent, restart, or external effects:
- Counterevidence, uncertainty, and coverage limits:
- Code snippets, optional:

## Handoff

- Remediation, only if requested:
- Regression evidence, if patched:
- Human review status:
- Disclosure status: local only unless explicitly authorized

## Disposition history

Preserve every status transition. Never erase the original evidence or rating.

| Date | Pass and agent | Previous status | New status | Evidence or human decision |
| --- | --- | --- | --- | --- |
| None | | | active | Initial promotion after reproduction |
