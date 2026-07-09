# Regularity Reproducibility Package

This repository contains anonymized code and scripts for reproducing the computational experiments reported in the accompanying anonymous submission.

The package has two components:

1. **Homological trimming experiments**  
   A C++ implementation of the trimming routine, with Python drivers for the synthetic experiments.

2. **RSD structural-descriptor experiment**  
   A standalone Python experiment illustrating how Regularity Slack Diagram (RSD) summaries can act as structural descriptors of filtered flag complexes.

## Repository layout

```text
.
├── include/                     # C++ headers
├── src/                         # C++ implementation
├── python/                      # Python experiment drivers
├── scripts/                     # Convenience scripts
├── vendor/                      # Compressed third-party minimal headers, if used
├── reference/                   # Small reference outputs
├── results/                     # Generated outputs, created by scripts
├── Makefile
├── CMakeLists.txt
├── requirements.txt
└── README.md
```

Depending on the uploaded version of the repository, the minimal third-party headers may be stored as:

```text
vendor/third_party_minimal.zip
```

The setup script unpacks them automatically when needed.

## Requirements

The C++ code requires a compiler with C++17 support.

The Python scripts require:

```bash
python >= 3.9
numpy
pandas
matplotlib
```

Install Python dependencies with:

```bash
pip install -r requirements.txt
```

## Quick start

Run the trimming smoke test:

```bash
bash scripts/run_trimming_smoke.sh
```

Run the RSD structural-descriptor experiment:

```bash
bash scripts/run_rsd_structure.sh
```

The generated outputs are written under:

```text
results/
```

## Full trimming experiment suite

To reproduce the larger trimming experiment suite, run:

```bash
bash scripts/run_trimming_paper.sh
```

This produces CSV summaries under `results/trimming/`.

## RSD structural-descriptor experiment

The RSD experiment can also be run directly:

```bash
python python/rsd_synthetic_descriptor_experiment.py --out-dir results/rsd_structure
```

The script generates synthetic edge-filtered flag complexes from three families:

- clique-rich
- cycle-rich
- sparse-random

For each family, it computes graph-level RSD summaries such as:

- fraction of regular edges
- median RSD margin
- high-percentile RSD margin
- fraction of finite right walls
- fraction of right endpoint blockers caused by \(H_1\)

The output includes raw graph-level summaries, aggregate tables, and simple classification summaries.

## Cleaning generated files

To remove generated outputs and build products:

```bash
bash scripts/clean_outputs.sh
```

## Notes on anonymity

This repository is prepared for anonymous review. It should not contain author names, affiliations, personal paths, or personal Git history. If cloning or modifying locally before upload, please check:

```bash
grep -RniE "author|name|affiliation|/Users|spritam|Siddharth|Pritam|CMI|Chennai|iitkgp" .
```

## License

This artifact is provided for anonymous review and reproducibility. A permanent license may be added in the non-anonymous archival version.
