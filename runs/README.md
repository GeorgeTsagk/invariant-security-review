# Review runs

Create one directory per trial or scan using `YYYY-MM-DD-subsystem-shortsha`.

Each run contains:

- `SCAN.md`: immutable manifest and coverage accounting.
- `hypotheses.md`: candidates, counterevidence, and disposition.
- `repro/`: minimized test patches and inputs.
- `logs/`: captured outputs with secrets removed.

Link reproduced findings to their canonical reports under `findings/`. Preserve failed experiments and unresolved paths so later reviewers do not mistake silence for coverage.
