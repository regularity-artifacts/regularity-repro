# Artifact Notes for Anonymous Review

## Purpose

This repository accompanies an anonymous submission on regularity geometry, local obstruction modules, RPD/RSD descriptors, and homological trimming of filtered flag complexes.

The code is intended to reproduce:

1. the trimming experiments reported in the main experimental section;
2. the preliminary synthetic RSD structural-descriptor experiment reported in the appendix.

## What is included

- C++ implementation of the trimming procedure.
- Python drivers for synthetic trimming experiments.
- Python script for the RSD structural-descriptor experiment.
- Smoke-test scripts.
- Small reference outputs.

## What is not included

- Author-identifying metadata.
- Personal machine paths.
- Large generated output folders.
- Paper source files.
- Nonessential exploratory notebooks or logs.

## Suggested reviewer workflow

```bash
pip install -r requirements.txt
bash scripts/run_trimming_smoke.sh
bash scripts/run_rsd_structure.sh
```

For a longer run:

```bash
bash scripts/run_trimming_paper.sh
```

## Expected outputs

The scripts generate CSV summaries under `results/`. The exact runtime depends on compiler, hardware, and Python/Matplotlib versions.

## Version

Anonymous submission artifact, initial reproducibility release.
