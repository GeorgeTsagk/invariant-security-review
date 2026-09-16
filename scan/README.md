# Scan data

All target-specific review state lives here and is ignored by git. The rest of the repository is the reusable skeleton: methodology, skill, agent entrypoints, and templates. Never write target data at the repository root.

## Layout

```
scan/
  <project>/               one directory per target repository, slug of its name
    PROJECT.md
    BASELINE.md
    THREAT_MODEL.md
    REVIEW_LOG.md
    passes/
    runs/
    subsystems/
    interviews/
    findings/
```

Initialize `scan/<project>/` by copying the blank catalog files from the repository root: `PROJECT.md`, `BASELINE.md`, `THREAT_MODEL.md`, `REVIEW_LOG.md`, and the `passes/`, `runs/`, `subsystems/`, `interviews/`, and `findings/` directories. Templates stay at `templates/` in the repository root and are referenced from there.

Reuse an existing `scan/<project>/` directory when the target is already present. Do not create a second directory for the same target. If the project directory should be versioned, initialize its own git repository inside it or point it at a private remote. This repository never tracks it.
