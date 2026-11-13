# University Governance Consistency Checker

A Python-based tool for examining university governance documents and identifying potentially inconsistent, conflicting, or structurally related clauses. The project combines a knowledge graph, semantic analysis, and rule-based checks, with a Streamlit interface for exploring results.

> The application and its supporting scripts are currently organized inside the `data/` directory.

## Key Capabilities

- Build and query a governance knowledge graph using RDF.
- Analyze relationships between governance clauses.
- Apply semantic analysis to compare clause meanings and identify potential conflicts.
- Run rule-based and hierarchy-related consistency checks.
- Import governance documents in supported PDF, DOCX, and TXT formats through the application.
- Review analysis results, compare clauses, inspect the knowledge base, and audit the dataset.
- Export analysis artifacts such as graph files and structured reports.

## Technology Stack

- Python
- Streamlit
- RDFLib
- NumPy
- Sentence Transformers and Transformers (optional neural analysis)
- PDF and DOCX document processing

## Repository Structure

```text
University-Governance-Consistency-Checker/
└── data/
    ├── app.py
    ├── build_knowledge_graph.py
    ├── consistency_checker.py
    ├── semantic_analyzer.py
    ├── analyze_governance.py
    ├── governance_clauses.csv
    ├── ground_truth.csv
    ├── requirements.txt
    ├── requirements-neural.txt
    └── README.md
```

The `data/` folder also contains supporting datasets, relationship files, tests, and run scripts.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Ayesha-Javed7155/University-Governance-Consistency-Checker.git
cd University-Governance-Consistency-Checker
```

### 2. Create and activate a virtual environment (recommended)

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

macOS/Linux:

```bash
source .venv/bin/activate
```

### 3. Install the core dependencies

```bash
python -m pip install -r data/requirements.txt
```

For the optional neural-analysis components:

```bash
python -m pip install -r data/requirements-neural.txt
```

### 4. Run the application

From the repository root:

```bash
streamlit run data/app.py
```

Streamlit will print a local URL in the terminal. Open it in your browser.

## Command-Line Workflow

Run these commands from the repository root when you want to use the individual scripts:

```bash
python data/build_knowledge_graph.py
python data/consistency_checker.py
python data/analyze_governance.py
```

The neural option can be enabled where supported by the analysis script:

```bash
python data/analyze_governance.py --neural --threshold 0.45
```

Run the available unit tests with:

```bash
python -m unittest discover -s data -v
```

## Data and Outputs

- `governance_clauses.csv` contains the governance clauses used by the project.
- `ground_truth.csv` supports evaluation.
- Supporting relationship and exception files provide additional structured data.
- Generated outputs may include RDF/Turtle knowledge-graph files and Markdown, CSV, or JSON reports.

Review the existing `data/README.md` for additional implementation and workflow details.

## Scope and Limitations

- Results are decision-support signals and should be reviewed by a qualified human; the tool does not replace legal, academic, or institutional review.
- Semantic similarity or an automated conflict flag does not by itself prove that two clauses are contradictory.
- Analysis quality depends on the completeness, quality, and interpretation of the supplied clauses and reference data.
- The optional neural components require additional packages and may take longer to install.

## Future Improvements

- Add more institution-specific governance datasets and evaluation examples.
- Expand automated tests for document imports and analysis edge cases.
- Add clearer evaluation summaries and reviewer feedback workflows.
- Document benchmark results against the ground-truth dataset.
