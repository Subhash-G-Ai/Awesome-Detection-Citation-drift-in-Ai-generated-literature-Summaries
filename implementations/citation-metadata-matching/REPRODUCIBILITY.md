# Reproducibility Guide

## Project

**Title:** Exact vs. Fuzzy Metadata Matching for Citation Record Recovery Under Controlled Corruption

**Research area:** Detection of citation drift in AI-generated literature summaries.

## 1. Research objective

This project compares three approaches for recovering bibliographic records from potentially corrupted citations:

- M1: Strict exact matching.
- M2: Title-only fuzzy matching.
- M3: Weighted multi-field fuzzy matching.

The experiment evaluates classification reliability, candidate retrieval performance, and the trade-off between false acceptance and false rejection.

## 2. Dataset

The experiment uses the CiteCheck citation corruption dataset.

- Total citation records: 982
- Valid records: 356
- Minor hallucinations: 300
- Major hallucinations: 326
- Candidate catalogue: 978 unique original records
- Development records: 639
- Test records: 343
- Random seed: 42

The experiment uses collection-grouped splitting to prevent records from the same collection appearing in both development and test partitions.

The original citation and ground-truth labels are used for evaluation. Matching methods receive the corrupted citation as their input.

Dataset source:
https://github.com/FirstPrinciplesLabs/citecheck

Dataset schema:
https://github.com/FirstPrinciplesLabs/citecheck/blob/main/dataset/SCHEMA.md

## 3. Experimental methods

### M1: Strict exact matching

Compares normalized title, author, and publication year fields. A candidate is accepted when all required fields match exactly.

### M2: Title-only fuzzy matching

Uses normalized title similarity to rank candidate records. An acceptance threshold controls whether a candidate is accepted.

### M3: Weighted multi-field fuzzy matching

Combines title, author, publication year, and identifier similarity. The weights and missing-field treatment must match the executed implementation. Refer to the final verified method description in the research paper.

## 4. Evaluation

The project uses classification and retrieval metrics.

Classification:
- Macro-F1
- Precision and recall
- False acceptance of corrupted citations
- False rejection of valid citations

Retrieval:
- Hit@1
- Hit@5
- Mean Reciprocal Rank (MRR)

Additional analysis:
- Threshold sensitivity
- Label-wise performance
- Error analysis

## 5. Recorded environment

The reported experimental environment was:

| Component | Version |
|---|---|
| Python | 3.13.18 |
| NumPy | 2.1.3 |
| SciPy | 1.18.1 |
| scikit-learn | 1.6.1 |
| Pandas | 2.2.3 |
| Matplotlib | 3.10.0 |
| Requests | 2.32.3 |

RapidFuzz was used for fuzzy string similarity. Its exact executed version should be taken from the project's installed environment or dependency lock information.

## 6. Project structure

The project archive contains:

- `src/`: reusable matching implementation
- `scripts/`: experiment and environment scripts
- `notebooks/`: research and implementation notebook
- `configs/`: experiment configuration
- `data/`: dataset instructions
- `results/`: experiment outputs
- `paper/`: LaTeX and bibliography files
- `docs/`: research and experiment documentation

## 7. Expected experiment outputs

The results directory contains:

- `predictions.csv`
- `error_analysis.csv`
- `metrics.json`
- `run_metadata.json`
- `splits.json`
- `threshold_sensitivity.csv`
- `label_breakdown.csv`
- `threshold_sensitivity.png`

These files provide the predictions, metrics, split information, metadata, error analysis, and threshold analysis.

## 8. Re-running the experiment

1. Download the project ZIP from the GitHub repository and extract it.
2. Open the extracted project directory.
3. Create a Python environment compatible with the documented dependencies.
4. Install the packages listed in `requirements.txt`.
5. Obtain the CiteCheck dataset from its official repository.
6. Follow the project's configuration and notebook instructions to prepare the dataset.
7. Run the environment verification script.
8. Run the experiment entry point.
9. Compare the generated outputs with the supplied results.

The exact dataset placement, configuration path, and command-line arguments must follow the actual project scripts. Do not assume that a command works until it has been tested.

## 9. Reproducibility limitations

- Results are based on a single collection-grouped split.
- The candidate catalogue is fixed and includes records from held-out test collections.
- The experiment uses controlled citation corruption.
- Parser behavior is limited by the citation formats it supports.
- Threshold sensitivity analysis must be interpreted in light of the documented threshold-selection procedure.
- Bibliographic metadata matching does not establish whether a source supports a generated research claim.

## 10. Verification record

Before submission, verify:

- [ ] The actual code matches the method descriptions in the paper.
- [ ] Dataset hash and split information match the recorded experiment.
- [ ] Package versions match the executed environment.
- [ ] The documented commands run successfully.
- [ ] The regenerated metrics agree with the submitted results.
- [ ] The paper's tables and plots agree with the final result files.

Only mark these checks complete after personally running them.
