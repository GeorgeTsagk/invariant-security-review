# Finding severity policy

- Approval status and decision reference:
- Scope and protected assets:
- Source policy: Lightning Labs Severity Taxonomy
- Local interpretations that preserve the tier anchors:
- Severity scale and ordering: T0, T1, T2, T3
- Canonical filename format: `<severity>-<concrete-behavior>.md`, where
  severity is T0, T1, T2, or T3
- Default treatment of unknowns:

## Vulnerability eligibility gates

- In-scope untrusted actors and their baseline capabilities:
- No-adversary and ordinary-operation exclusions:
- Privilege-escalation counterfactual:
- Supported/default deployment requirement:
- Documentation-induced misconfiguration exception:
- Material security consequences:
- Realistic resource and denial-of-service thresholds:
- Duplicate and already-fixed policy:
- Low-severity exit rule: exit when Impact is Low, Virality is Low, and either
  Exploitability is Low or both Attack Vector and Exploitability are no higher
  than Med

## Scoring dimensions

- Impact definitions for Low / Med / High:
- Attack Vector definitions for Local / Adjacent / Network:
- Exploitability definitions for Low / Med / High:
- Virality definitions for Low / Med / High:
- Persistence and recovery boundaries:
- Affected-population denominator:
- Causal attribution rule:

## Tier anchors and arithmetic

- T0 anchor: viral fund loss
- T1 anchor: targeted fund loss or invalidated liveness
- T2 anchor: viral denial of service or fund loss with a rare trigger
- T3 anchor: reachable, non-viral, operator-recoverable denial of service
- Impact = High rule: start at T1; promote to T0 when Attack Vector,
  Exploitability, and Virality are each at least Med; never demote
- Impact = Med rule: start at T1; promote to T0 when Attack Vector,
  Exploitability, and Virality are all High; demote to T2 when Exploitability
  is Low or both Attack Vector and Virality are Low
- Impact = Low rule: start at T3; promote to T2 when Virality is High; promote
  to T1 when Attack Vector, Exploitability, and Virality are all High; otherwise
  apply the low-severity exit; the T1 condition takes precedence over T2
- Treatment when arithmetic conflicts with the anchor: re-check the actor,
  trigger, attributable harm, and dimension scores before considering override
- Tier override authority: the human security owner may move the mechanical
  result by one tier when the rubric clearly fails the case, with a recorded
  rationale

## Tier-specific project interpretation

- Label and meaning:
- Demonstrated impact:
- Required reachability:
- Attacker prerequisites:
- Scale or affected population:
- Persistence and recovery:
- Qualifying examples:
- Exclusions and lower-tier examples:

## Rating rules

- How multiple impacts combine:
- How deployment profiles affect severity:
- How environmental controls affect severity:
- How actor capability and delegated scope affect eligibility:
- How separate defects on one causal chain divide impact and exploitability:
- How reusable techniques differ from automatic propagation:
- Reassessment triggers:

Confidence records evidence quality and remains separate from severity.
