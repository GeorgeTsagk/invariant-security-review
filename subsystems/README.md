# Invariant catalog

Create one file per coherent system, subsystem, or protocol review unit. Assign stable IDs such as `AU-001` or `PROTO-003`; do not recycle retired IDs.

Each file should record its boundary, entry points, consumers, cross-subsystem obligations, requirement decisions, enforcement evidence, and coverage gaps. Use [the subsystem template](../templates/SUBSYSTEM.md) and [the invariant template](../templates/INVARIANT.md).

An invariant is an intended security property, not a claim that the implementation enforces it. Interview the user when material semantics remain vague, undefined, conflicting, or unclear after reviewing code and specifications.
