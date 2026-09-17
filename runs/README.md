# Review runs

Create one directory per trial or scan using `YYYY-MM-DD-subsystem-shortsha`.

Each run contains:

- `SCAN.md`: immutable manifest and coverage accounting.
- `hypotheses.md`: candidates, counterevidence, and disposition.
- `repro/`: minimized test patches and inputs, with statements of what each
  proof establishes, does not establish, and exercises.
- `logs/`: captured outputs with secrets removed.

Every run links its participating agent pass records. A pass may contribute to several runs, and a run may include several agents. The pass records show individual responsibility; the run manifest shows combined scan coverage.

Link reproduced findings to their canonical reports under `findings/`. Preserve failed experiments and unresolved paths so later reviewers do not mistake silence for coverage.
