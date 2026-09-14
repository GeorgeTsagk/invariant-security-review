# Invariant catalog

Enumerate existing files and invariant IDs, then reconcile them with [the invariant index](INDEX.md) before proposing new records. The index is a discovery aid, not the sole authority. Create one file per coherent system, subsystem, or protocol review unit. Assign stable IDs such as `AU-001` or `PROTO-003`; do not recycle retired IDs.

Each file should record its boundary, entry points, consumers, cross-subsystem obligations, ambiguity classification, human verification, requirement decisions, enforcement evidence, and coverage gaps. Use [the subsystem template](../templates/SUBSYSTEM.md) and [the invariant template](../templates/INVARIANT.md).

An invariant is an intended security property, not a claim that the implementation enforces it. Actively search for gray areas after reviewing code and specifications, interview the user with distinguishing scenarios, and record verification in [the invariant ledger](../interviews/VERIFICATION.md).

Existing invariants persist across agents. Update the same record for the same property, preserve its history and decisions, and append the current pass and agent to its review-history table after substantive reading or writing. Keep `INDEX.md` synchronized.
