# Open invariant questions

Keep only material unresolved decisions. Investigate code and specifications before asking.

For each question record:

- Stable question ID and status.
- Affected invariant IDs.
- Concrete ambiguity and evidence.
- Plausible interpretations.
- One distinguishing example.
- How the answer changes the test oracle.
- Date asked and current owner.

Search explicitly for gray areas involving:

- Ambiguous security terms and authority boundaries.
- Time, lifecycle, finality, retry, rollback, and reorganization.
- Partial success, cancellation, crash, and recovery.
- Local state versus remote or cached claims.
- Producer guarantees versus consumer assumptions.
- Legitimate exceptions and partially verified data.
- Specification intent versus behavior encoded by current tests.

Do not close a gray area with a generic approval question. Ask for the expected outcome of a distinguishing scenario.
