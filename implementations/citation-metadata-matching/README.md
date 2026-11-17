# Exact vs. Fuzzy Metadata Matching for Citation Record Recovery

**Status:** Research implementation scaffold. Run the notebook to generate actual evidence before reporting results.

## Research scope

This project studies a *closed-catalogue bibliographic record-recovery task*: given a possibly corrupted citation string, rank a catalogue of reference records and determine whether the citation metadata is consistent with a catalogue record.

It compares:
- **M1 — Exact-field matching:** exact normalized title, author string and year.
- **M2 — Title-only fuzzy matching:** RapidFuzz title similarity.
- **M3 — Weighted multi-field fuzzy matching:** title 0.60, authors 0.25, year 0.10, arXiv identifier 0.05.

The weights are pre-registered heuristics for this course experiment, not established optimal weights. A development split selects the classification threshold for M2/M3. The test split is held out by `collection_id`.

## Dataset

The benchmark is obtained from the public CiteCheck repository:
- Dataset: https://github.com/FirstPrinciplesLabs/citecheck/blob/main/dataset/corruption_metadata.json
- Schema: https://github.com/FirstPrinciplesLabs/citecheck/blob/main/dataset/SCHEMA.md
- Repository: https://github.com/FirstPrinciplesLabs/citecheck
- Companion paper: https://aclanthology.org/2026.groundlm-1.58/

The schema documents 42 collections and 982 citations with labels `valid`, `hallucinated_minor`, and `hallucinated_major`. The detector input is `corrupted_citation`; `original_citation`, labels, severity and change descriptions are evaluation metadata only.

**Important protocol boundary:** this implementation builds a reference catalogue from the dataset's `original_citation` records and uses the paired original only for evaluation. This is a closed-catalogue recovery experiment, not open-world citation verification, semantic claim-support checking, or proof that a source supports a claim. The full gold catalogue is available to the retrieval methods as a reference database; labels and paired target IDs are not passed into scoring functions.

## Quick start — Google Colab

1. Upload `notebooks/Prompt08_to_18_Research_Pipeline.ipynb` to Colab.
2. Run cells from top to bottom.
3. The notebook downloads the public dataset and installs pinned dependencies.
4. Inspect the printed schema and environment diagnostics.
5. Run the experiment cell. It writes split, predictions, metrics, plots and logs under `results/`.
6. Download the `results/` folder and retain the raw outputs for the paper.

## Local commands

```bash
python -m pip install -r requirements.txt
python scripts/run_experiment.py --data data/corruption_metadata.json --out results
```

If the dataset is not already present, the script downloads it from the official repository URL.

## Main outputs (created only after a genuine run)

- `results/environment.json`
- `results/splits.json`
- `results/predictions.csv`
- `results/metrics.json`
- `results/threshold_sensitivity.csv`
- `results/threshold_sensitivity.png`
- `results/error_analysis.csv`
- `results/run_metadata.json`

No result numbers are prefilled. Empty result files in the repository are placeholders only.

## Reproducibility and integrity

- Random seed: 42.
- Group split: `collection_id` is the grouping unit; no collection may occur in both development and test sets.
- Thresholds are tuned only on the development partition.
- The test partition is evaluated once after protocol decisions are frozen.
- All methods receive the same query records and candidate catalogue.
- The script checks that query IDs and target catalogue IDs align.
- A successful run does not, by itself, prove the method is scientifically correct. Inspect `docs/VALIDATION_CHECKLIST.md`.
- Record any changed settings in `docs/PROTOCOL_CHANGELOG.md`.
- Do not commit API keys, private data or restricted files.

## Repository structure

```text
.
├── README.md
├── requirements.txt
├── configs/experiment.json
├── data/README.md
├── notebooks/Prompt08_to_18_Research_Pipeline.ipynb
├── src/matching.py
├── scripts/run_experiment.py
├── results/                 # genuine outputs after execution
├── paper/main.tex
├── paper/references.bib
├── docs/research_decisions.md
├── docs/experiment_protocol.md
├── docs/VALIDATION_CHECKLIST.md
├── docs/PROTOCOL_CHANGELOG.md
└── docs/ai_assistance_log.md
```

## Citation

Khajavi, K., Sadeghi, S., Adhikari, R., & Tessier, A. (2026). *CITECHECK: Retrieval-Grounded Detection of LLM Citation Hallucinations in Scientific Text*. Proceedings of the 1st Workshop on Grounding Language Models: Learning Faithfully and Efficiently, 779–795. https://aclanthology.org/2026.groundlm-1.58/

## License

Project scaffold: MIT. The benchmark is described as MIT-licensed in the source repository's dataset schema; verify the exact repository revision and retain its license notice when redistributing.
