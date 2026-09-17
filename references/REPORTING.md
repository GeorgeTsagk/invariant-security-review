# Security reporting policy

This policy incorporates reporting guidance supplied by a senior security
engineer. It governs canonical findings and report exports. It improves code
anchoring and triage; it is not a reason to reject an external report or force
its author into a prescribed layout.

## Target baseline

Put the target repository, full commit, optional branch or tag, and report date
once at the top of the report. Add the tree hash when available. If one finding
uses a different revision, state that override in the finding.

Line numbers are meaningful only against the named revision. Resolve and verify
all anchors at that revision before promotion or export.

## Code anchors

Every canonical finding must have at least one code anchor with these fields:

- repository;
- repository-relative file path;
- line start;
- line end;
- a short statement of what the location establishes.

Use one contiguous range per anchor. List anchors in evidentiary order, with the
defect itself first. Cite the missing check, unsafe write, bad allocation, or
other faulty operation before callers and consequences.

For an omission, cite the hand-written map, switch, validator, state machine,
or other location where the missing item or check belongs. An identifier in a
generated file does not replace an anchor to the code that owns the omission.

Never use a bare filename. Paths are relative to the named repository root. If
an anchor belongs to a dependency or another repository, identify that
repository by name and URL or module path. Do not imply that dependency code is
part of the primary target.

## Proof scope

For every test, patch, harness, trace, or other proof, state separately:

- what it directly establishes;
- what it does not establish;
- which boundary it exercises;
- the exact command, configuration, and revision used.

Do not infer dynamic reachability, impact, or severity from a proof that only
shows a missing guard or suspicious local behavior. Code snippets are optional
and must never substitute for repository anchors at the pinned revision.

## Severity provenance

Preserve the reporter-provided severity, scale, and rationale as immutable
provenance. Triage independently under the approved T0 through T3 policy and
store the resulting Severity, Attack Vector, Exploitability, Impact, and
Virality separately. Never overwrite the reporter's rating when triage
disagrees.

For agent-originated findings, the generating agent's provisional rating is the
reporter rating. A validating agent or human records the triage rating.

## Finding boundaries

Keep one independently fixable defect per finding section and canonical file.
Shared root cause, invariant, or attack path does not justify merging defects
that require separate fixes. Merge only duplicate descriptions of the same
defect and same remediation point. Link related findings and explain their
shared mechanism without combining their evidence or severity.

## Report normalization

External reports may use prose, any severity scale, and any layout. Do not
reject or downgrade them for omitting this structure. The reviewing agent owns
normalization: pin the baseline, locate and verify code anchors, preserve the
original rating, and record the structured fields without asking the reporter
to reformat material the agent can resolve from source.

When producing a report, include structured metadata alongside readable prose:
the commit and tree hash at report level, plus repository, file, line start, and
line end for every finding anchor. Structured metadata removes inference but
does not replace the prose mechanism, impact, proof scope, or limitations.
