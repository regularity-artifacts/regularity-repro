# Reproducibility Instructions

This file gives the shortest path for reviewers to reproduce the reported computations.

## 1. Install dependencies

```bash
pip install -r requirements.txt
```

A C++17 compiler is required for the trimming executable.

## 2. Run smoke tests

```bash
bash scripts/run_trimming_smoke.sh
bash scripts/run_rsd_structure.sh
```

Expected behavior:

- the C++ trimming executable builds successfully;
- internal C++ trim-engine tests pass;
- the trimming smoke profile produces CSV outputs;
- the RSD structural-descriptor script produces CSV summaries under `results/rsd_structure/`.

## 3. Run the larger trimming suite

```bash
bash scripts/run_trimming_paper.sh
```

This regenerates the trimming experiment outputs under:

```text
results/trimming/
```

The main CSV outputs include raw job-level outputs and summary tables.

## 4. Run the RSD structural-descriptor experiment directly

```bash
python python/rsd_synthetic_descriptor_experiment.py --out-dir results/rsd_structure
```

Optional flags:

```bash
python python/rsd_synthetic_descriptor_experiment.py --num-seeds 20 --p 2 --out-dir results/rsd_structure
python python/rsd_synthetic_descriptor_experiment.py --no-plots --out-dir results/rsd_structure
```

## 5. Clean and rerun

```bash
bash scripts/clean_outputs.sh
bash scripts/run_trimming_smoke.sh
bash scripts/run_rsd_structure.sh
```

## Output locations

```text
results/trimming/
results/rsd_structure/
```

## Troubleshooting

If the build fails because third-party headers are missing, run:

```bash
bash scripts/setup_vendor.sh
```

If the RSD script fails with a Matplotlib keyword error involving `tick_labels`, update to the patched script or use a Matplotlib version supporting either `labels` or `tick_labels`. The current script is intended to support both.
