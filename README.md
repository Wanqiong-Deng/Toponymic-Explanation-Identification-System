# Toponymic-Explanation-Identification-System

A hybrid NLP system for extracting and classifying toponymic explanations from Classical Chinese texts, combining rule-based logic, large language models, and retrieval-augmented inspection.

---

## Overview

This project implements an end-to-end pipeline for identifying **toponymic explanations**—passages that explain why a place is named in a certain way—from historical Chinese texts.

The system focuses on:
- high-precision extraction,
- explainable decision logic,
- and scalable batch processing.

Although the case study is Classical Chinese geographical records, the architecture is applicable to other **low-resource, rule-sensitive information extraction tasks**.

---

## Key Features

- Hybrid rule-based + LLM classification
- Mandatory evidence span extraction
- Explicit handling of cross-entry narration
- Resume-safe batch processing for large corpora
- Post-hoc pattern mining and quantitative analysis
- RAG-based semantic retrieval for inspection (non-decisional)

---

## Classification Schema

Each placename record is classified into one of three categories:

- **STRONG** — the author directly explains the naming reason using causal or definitional language  
- **WEAK** — a naming explanation is present but attributed to cited sources  
- **NONE** — descriptive geographic or administrative information without naming logic

This is a **logic-oriented classification task**, not topic or sentiment classification.

---

## System Pipeline

The overall workflow is shown below.

【Insert Technical Pipeline Diagram Here】

1. HTML text normalization and cleanup  
2. Placename detection and context aggregation  
3. Naming target resolution across entries  
4. Hybrid classification (regex-first, LLM fallback)  
5. Statistical analysis and visualization

Each stage produces structured outputs that can be inspected independently.

---

## Code Structure

【Insert Code Structure Diagram Here】

### Core Modules

- `transport_to_txt.py`  
  Cleans HTML-based historical texts into normalized UTF-8 plain text.

- `extract_placename_records.py`  
  Identifies placename entries using suffix constraints and structural heuristics, then aggregates multi-line contexts.

- `resolve_naming_target.py`  
  Corrects misalignment caused by cross-entry narration through contextual back-reference.

- `extract_explanatory_sentence.py`  
  Implements the hybrid decision engine:
  - high-precision regex rules for canonical patterns  
  - LLM-based semantic classification for ambiguous cases  
  - evidence span extraction and checkpoint-based resume

---

### Analysis & Evaluation

- `analyze_results.py`  
  Generates distribution statistics and publication-ready visualizations.

- `deep_data_mining.py`  
  Performs rule-guided post-hoc mining to decompose STRONG / WEAK / NONE classes into interpretable subtypes and produces consolidated analytical figures.

- `manual_evaluation.py`  
  Evaluates classification accuracy against human-annotated samples.

---

### Retrieval-Augmented Inspection

- `RAG.py`  
  Enables semantic retrieval over extracted records for debugging and exploratory analysis.  
  *Note: this module does not participate in classification decisions.*

---

## Outputs

- Full classification results with evidence spans (`CSV`)
- Category-specific exports
- Statistical summaries and figures
- Reproducible intermediate artifacts

Large generated files are excluded from version control and can be reproduced via the pipeline.

---

## Design Considerations

- Interpretability-first hybrid architecture  
- Deterministic rules with probabilistic fallback  
- Explicit error analysis and failure awareness  
- Clear separation between decision logic and inspection tools  

---
