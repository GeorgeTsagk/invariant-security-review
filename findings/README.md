# Findings

This directory is the canonical store for evidence-backed findings. Run directories contain working hypotheses, test patches, and logs.

## Naming and ordering

Store reports as `<severity>-<concrete-behavior>.md`, where severity is `T0`,
`T1`, `T2`, or `T3`. T0 sorts first. Define and approve any project-specific
interpretation using [the severity policy template](../templates/SEVERITY_POLICY.md),
without changing the tier anchors.

Severity follows the plain-language tier anchor and the four taxonomy
dimensions. Confidence is separate. Uncertain reachability does not by itself
justify a more severe tier.

Before triage, apply [the vulnerability eligibility and severity gates](../references/VULNERABILITY_TRIAGE.md).

Maintain [INDEX.md](INDEX.md) with views grouped by severity and subsystem. Deduplicate by root cause and invariant, while preserving all affected entry points in the canonical report.

## Finding lifecycle

Every canonical report has one status:

- `active`: reproduced and still considered a security issue.
- `resolved`: a remediation is verified at a named source revision with a
  regression test or equivalent dynamic evidence.
- `discarded`: later evidence or an authorized human requirement decision
  establishes that the behavior is expected, out of scope, duplicated, or not
  a security violation.

Never delete or rewrite the original evidence when status changes. Add a dated
disposition-history row with the pass, agent, prior status, new status, and
basis. Retain the historical severity and stable report link. Exclude resolved
and discarded records from active severity and subsystem tables, then list them
in the index's resolved and discarded section. A later decision can reopen a
record as active with another history row.

Do not mark a finding resolved from a patch description or code inspection
alone. Exercise the original reproduction against the patched revision and
record both the revision and regression result. Do not mark a finding discarded
merely because remediation is undesirable. Record the requirement evidence or
human decision that invalidates the security oracle.

## Promotion gate

A canonical finding requires:

- A justified invariant or normative requirement.
- A named untrusted actor who gains a capability they did not already possess.
- Harm attributable to this defect rather than ordinary operation, operator
  choice, or another prerequisite defect.
- Realistic attacker prerequisites and reachability.
- A complete source path to a meaningful consequence.
- Counterevidence review.
- Dynamic reproduction with a valid control.
- Exact revisions, configuration, commands, and limitations.
- Severity, Attack Vector, Exploitability, Impact, and Virality fields
  under the approved project policy.
- Human expert review before disclosure.

Unresolved and disproven hypotheses remain in their originating run, not here.
Actionable behaviors that fail the security gates remain ordinary product
issues and are not promoted into the canonical security index.

Keep findings private. Do not publish, push, comment, or disclose without explicit authorization.
