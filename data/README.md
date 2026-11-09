# University Governance Document Consistency Checker

This project analyzes university governance clauses using an RDF knowledge
graph, sentence embeddings, natural language inference (NLI), symbolic rules,
governance hierarchy checks, and explainable outputs.

`governance_clauses.csv` is the single source of truth.

## Features

- Imports PDF, DOCX, and TXT governance documents.
- Extracts candidate clauses containing governance language.
- Stores clauses and inferred governance tiers in RDF.
- Generates Sentence-BERT embeddings with `all-MiniLM-L6-v2`.
- Computes cosine similarity to retrieve related clauses.
- Uses `nli-deberta-v3-small` for entailment, contradiction, and neutral labels.
- Detects explicit exceptions, redundancies, numeric conflicts, and hierarchy violations.
- Produces human-readable explanations.
- Provides a Streamlit user interface and downloadable results.

The system can also run offline in symbolic mode when neural models are not
available.

## Quick Start

Double-click:

```text
run_app.bat
```

The browser interface contains:

1. Dashboard
2. Full knowledge-base analysis
3. Two-clause comparison
4. PDF, DOCX, and TXT import
5. Dataset audit

## Command Line

Build the base RDF graph:

```powershell
python build_knowledge_graph.py
```

Run structural checks:

```powershell
python consistency_checker.py
```

Run fast offline relationship analysis:

```powershell
python analyze_governance.py
```

Run Sentence-BERT and NLI analysis:

```powershell
python analyze_governance.py --neural --threshold 0.45
```

Run all offline tasks by double-clicking `run_project.bat`.

## Outputs

- `cust_knowledge_graph.ttl`: clause and governance knowledge graph
- `analyzed_knowledge_graph.ttl`: graph enriched with analysis relationships
- `consistency_report.md`: structural data audit
- `relationship_report.csv`: classified clause pairs
- `relationship_report.json`: machine-readable pair analysis

## Installation

Core:

```powershell
python -m pip install -r requirements.txt
```

Neural models and DOCX:

```powershell
python -m pip install -r requirements-neural.txt
```

Model weights are cached locally after their first download. The application
then loads them in offline mode.

## Dataset

The main CSV includes the required minimum:

- at least 20 regulations;
- at least 5 policies;
- 5 procedures; and
- 5 exceptions.

It also includes clearly marked examples for contradiction, entailment, and
redundancy demonstrations.

## Tests

```powershell
python -m unittest -v
```

The tests verify RDF construction, structural validity, document segmentation,
and all required relationship classes.
