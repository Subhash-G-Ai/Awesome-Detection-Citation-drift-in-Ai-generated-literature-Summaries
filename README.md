# Awesome Citation Drift Detection in AI-Generated Literature

A curated, verified academic repository for tracking, auditing, and detecting citation drift, reference hallucinations, and semantic misattribution in AI-generated scholarly summaries.

## Contents
- [Topic Overview](#topic-overview)
- [AI-Assisted Research Paper](#ai-assisted-research-paper)
- [Citation Integrity Audit](#citation-integrity-audit)
- [Curated Research Papers](#curated-research-papers)
- [Tools and Libraries](#tools-and-libraries)

---

## Topic Overview

The integration of Large Language Models (LLMs) into scholarly literature workflows has significantly transformed academic discovery and research synthesis. While generative AI excels at summarizing complex technical domains, it introduces a critical threat to scientific integrity known as **citation drift**. 

Citation drift represents the progressive degradation of fidelity between an AI-generated claim, the target citation's metadata, and the underlying primary source text. Unlike basic factual hallucinations where models generate entirely fake entities, citation drift manifests in subtle, highly plausible structural forms:
1. **Structural Fabrication**: Completely inventing publication metadata (titles, DOIs, or author lists).
2. **Metadata Corruption**: Synthesizing real papers with mutated years, volume numbers, or omitted authors.
3. **Semantic Misattribution**: Accurately citing genuine, highly relevant papers whose full text fails to logically support or entail the generated claim.

As generative tools become embedded in scientific research, undetected citation drift risks polluting academic knowledge bases and deepening the reproducibility crisis. Mitigating this challenge requires multi-stage verification frameworks that combine automated database lookups (e.g., Crossref, OpenAlex), fuzzy metadata string matching, and Natural Language Inference (NLI) cross-encoders for full-text semantic support auditing.

---

## AI-Assisted Research Paper

* **Paper Title**: Detection of Citation Drift in AI-Generated Literature Summaries
* **Authors**: Gorrela Subhash
* **Abstract**: Large Language Models are increasingly integrated into research synthesis workflows, but their adoption is compromised by citation drift. This paper establishes a formal taxonomy of citation distortions (structural fabrication, metadata corruption, and semantic misattribution) and proposes a hybrid detection pipeline combining multi-source scholarly retrieval, string edit distance matching, and NLI-based semantic entailment checks.
* **Repository Link**: [View Full AI-Assisted Research Paper PDF](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/paper/Ai_assisted_reserach_paper.pdf)

---

## Citation Integrity Audit

* **Audit Summary**: Systematic citation audit conducted on the references generated within the primary research paper. A sample of 6 citations was evaluated across pre-verification plausibility, publication authenticity, bibliographic metadata correctness, persistent identifier resolution, and claim-citation entailment.
* **Authenticity Score**: **83.33 / 100**
* **Prediction Accuracy**: **83.33 %**
* **Key Finding**: While most generated references resolved to real preprints, structural metadata errors (such as missing author lists) and subtle context shifts between generated claims and source texts were detected.
* **Repository Link**: [View Complete Citation Audit PDF](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/citation-audit/citation_integrity_audit.pdf)

---

## Curated Research Papers

This repository includes a curated collection of verified scholarly literature organized by research focus. All entry metadata, DOIs, and arXiv identifiers have been verified.

* **Complete Literature Catalog**: [View Full List in references/references.md](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/references/references.md)

### Verified Research Paper Files

- **Paper 1**: [research 1.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%201.pdf)
- **Paper 2**: [research 2.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%202.pdf)
- **Paper 3**: [research 3.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%203.pdf)
- **Paper 4**: [reserach 4.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/reserach%204.pdf)
- **Paper 5**: [research 5.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%205.pdf)
- **Paper 6**: [research 6.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%206.pdf)
- **Paper 7**: [research 7.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%207.pdf)
- **Paper 8**: [reserach 8.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/reserach%208.pdf)
- **Paper 9**: [research 9.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%209.pdf)
- **Paper 10**: [research 10.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%2010.pdf)
- **Paper 11**: [research 11.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%2011.pdf)
- **Paper 12**: [research 12.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%2012.pdf)
- **Paper 13**: [research 13.pdf](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/Curated%20reserach%20papers/research%2013.pdf)

---

## Tools and Libraries

Generative AI platforms used for research drafting alongside external verification databases used during reference auditing.

* **Detailed Tools Catalog**: [View Full List in tools/tools.md](https://github.com/Gorrela-Subhash/awesome-citation-drift-detection/blob/main/tools/tools.md)

### Generative AI Tools
- **Gemini AI**: Primary generative AI tool used to draft the paper (*Gemini 3.6 Flash*).
  * **Link**: [https://gemini.google.com](https://gemini.google.com)
- **ChatGPT**: Secondary generative AI tool used for prompt testing and paper structuring.
  * **Link**: [https://chatgpt.com](https://chatgpt.com)

### Verification Databases
- **Crossref REST API**: Official registry used to check persistent Digital Object Identifier (DOI) records and metadata.
  * **Link**: [https://www.crossref.org](https://www.crossref.org)
- **arXiv Search**: Open repository used to verify preprint identifiers, titles, and publication dates.
  * **Link**: [https://arxiv.org](https://arxiv.org)
