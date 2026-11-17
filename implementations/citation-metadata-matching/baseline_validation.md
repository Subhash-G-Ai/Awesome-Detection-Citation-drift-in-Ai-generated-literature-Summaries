# Baseline Validation and Experimental Evidence Report

## 1. Project information

**Project:** Exact vs. Fuzzy Metadata Matching for Citation Record Recovery Under Controlled Corruption

**Research question:** How do strict exact matching, title-only fuzzy matching, and weighted multi-field fuzzy matching compare in recovering citation records under controlled corruption?

**Experimental pathway:** Controlled comparative study.

## 2. Dataset validation

The CiteCheck dataset contains 982 citation records.

| Label | Records |
|---|---:|
| Valid | 356 |
| Minor hallucination | 300 |
| Major hallucination | 326 |
| Total | 982 |

The candidate catalogue contains 978 unique original records.

The experiment uses a collection-grouped split:

| Partition | Records |
|---|---:|
| Development | 639 |
| Test | 343 |
| Total | 982 |

Random seed: 42.

The split is intended to keep source collections separate between development and test partitions.

## 3. Baseline methods

### M1 — Strict exact matching

Uses normalized title, author, and publication year equality.

### M2 — Title-only fuzzy matching

Uses fuzzy title similarity to rank candidates and applies an acceptance threshold.

### M3 — Weighted multi-field fuzzy matching

Uses title, author, publication year, and identifier similarity. The precise scoring and missing-field behavior must match the executed implementation and the final paper.

## 4. Experimental environment

The recorded environment:

- Python 3.13.18
- NumPy 2.1.3
- SciPy 1.18.1
- scikit-learn 1.6.1
- Pandas 2.2.3
- Matplotlib 3.10.0
- Requests 2.32.3

The experiment uses RapidFuzz for fuzzy string similarity. Record its exact version from the executed environment.

## 5. Reported experimental results

The implementation paper reports the following test results:

| Method | Macro-F1 | Hit@1 | Hit@5 |
|---|---:|---:|---:|
| M1 — Exact | 1.000 | 0.359 | 0.359 |
| M2 — Title fuzzy | 0.903 | 0.703 | 0.752 |
| M3 — Weighted fuzzy | 0.931 | 0.682 | 0.700 |

The paper also reports:

- M2 accepted 32 corrupted records.
- M3 accepted zero corrupted records.
- M3 incorrectly rejected 21 valid records.

These values must be cross-checked against the final `metrics.json`, `predictions.csv`, and paper tables before submission.

## 6. Interpretation

M1 achieved perfect classification on the reported test set. This result is strongly influenced by the relationship between citation text identity and the dataset labels. It should not be interpreted as proof that exact matching is universally superior.

M2 obtained the highest retrieval performance among the three methods but accepted more corrupted citations.

M3 was more conservative in accepting corrupted records but rejected some valid records.

The methods therefore exhibit different trade-offs between retrieval performance and classification reliability.

## 7. Protocol deviations and validity threats

The original planning documents proposed an external Crossref candidate-retrieval approach. The executed project used a fixed candidate catalogue instead. This is a protocol deviation and should be disclosed.

The experiment also has the following limitations:

- Fixed candidate catalogue rather than an unseen external catalogue.
- Candidate records include records from held-out test collections.
- A single collection-grouped split.
- Heuristic weighted similarity.
- Controlled corruption rather than arbitrary real-world citation errors.
- Limited citation parser coverage.
- Threshold exploration must be described accurately, including any inspection of test results before the final analysis.

## 8. Code-to-paper verification

The saved paper describes normalization of weighted scores over observed metadata components.

Before final submission, inspect the executed M3 implementation and confirm that:

1. The weights are the same as those stated in the paper.
2. Missing components are handled as described.
3. Identifier conflicts are handled as described.
4. The threshold rule matches the implementation.

If the code and paper disagree, correct the paper to match the code that generated the submitted results.

## 9. Validation status

| Check | Status |
|---|---|
| Dataset loaded and evaluated | Reported completed |
| Environment verification | Reported completed |
| Collection-grouped split | Reported completed |
| Three methods evaluated | Reported completed |
| Predictions and metrics saved | Reported completed |
| Threshold analysis | Reported completed |
| Independent full rerun from a clean environment | Not yet independently confirmed |
| Code-to-paper method consistency | Requires final confirmation |

## 10. Conclusion

The experiment provides a controlled comparison of exact and fuzzy bibliographic metadata matching approaches. The results demonstrate a trade-off between retrieval effectiveness and conservative acceptance of corrupted citations.

The conclusions apply to the evaluated dataset, fixed catalogue, parser, and split. They should not be generalized to arbitrary bibliographic databases or semantic claim verification.
