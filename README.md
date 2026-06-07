# Piecewise Symbolic Regression (Pc-SR) – Modular Demo

## Description

Piecewise Symbolic Regression (Pc-SR) is a modular framework for building interpretable symbolic regression models through a combination of decision-tree partitioning and symbolic equation discovery. The project uses a two-stage workflow that first partitions data into meaningful regions and then fits symbolic expressions to each region, optionally merging similar regions to produce more compact and interpretable models.

This project is intended for researchers, data scientists, and engineers interested in explainable artificial intelligence (XAI), symbolic regression, and interpretable machine learning.

The software addresses the challenge of accurately modelling complex nonlinear systems while maintaining model transparency. By combining Decision Tree Regression (CART) and symbolic regression, Pc-SR provides human-readable equations that can help users understand system behaviour and generate insights that traditional black-box models often cannot provide.

---

# 1. Project Status

**Status:** In Progress

 Core functionalities for piecewise symbolic regression and post-hoc model merging are implemented and operational.

---

# 2. Technology Stack

### Programming Language

* Python 3.10

### Frameworks and Libraries

* PySR
* Scikit-learn
* SymPy
* Sentence Transformers
* PyTorch
* Joblib
* Matplotlib
* NumPy
* Pandas

### Additional Technologies

* Julia Backend (required by PySR)

### Execution Model

* Standalone Python application
* Modular package structure for reuse and extension

---

# 3. Dependencies

Dependencies should be installed using the project's `requirements.txt` file.

### Core Dependencies

* numpy
* pandas
* scikit-learn
* matplotlib
* sympy
* pysr
* joblib
* sentence-transformers
* torch

### Special Requirements

PySR requires a Julia backend installation.

If PySR is being executed for the first time on a machine, Julia package compilation may occur automatically and can take several minutes.

Refer to the official PySR installation documentation if additional setup is required.

---

# 4. Installation

## Clone the Repository

```bash
git clone <repository-url>
cd <repository-name>
```

## Create and Activate a Virtual Environment

```bash
python -m venv .venv
```

### Windows

```bash
.venv\Scripts\activate
```

### Linux/macOS

```bash
source .venv/bin/activate
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Configure the Dataset

Open:

```text
scripts/run_pipeline.py
```

Update the user settings:

* `DATA_PATH` – path to the CSV dataset
* `TARGET_COL` – target variable name
* `FEATURES` – optional feature subset
* `DROP_COLS` – optional columns to remove
* `OUTDIR` – output directory
* `DO_MERGE` – enable or disable Stage-2 merging

---

# 5. Usage

## Running the Pipeline

### From an IDE

Run:

```text
scripts/run_pipeline.py
```

### From the Terminal

```bash
python scripts/run_pipeline.py
```

Results will be stored in the configured output directory (`outputs/` by default).

## Workflow Overview

### Stage 1: Piecewise Symbolic Regression

1. CART pruning and alpha selection.
2. Per-leaf symbolic regression using PySR.
3. Model selection and diagnostics.
4. Export of trained models and metadata.

### Stage 2 (Optional): Post-hoc Merging

1. Initialize clusters from Stage-1 leaves.
2. Compare symbolic equations using embeddings and structural similarity.
3. Validate candidate merges numerically.
4. Retrain symbolic models for merged clusters.
5. Iterate until convergence.

---

# 6. Architecture Diagrams

Architecture diagrams should be stored under:

```text
docs/diagrams/
```

Recommended diagrams include:

### UML Diagrams

* Class Diagram
* Sequence Diagram
* Component Diagram

### Flowcharts

* Process Flowchart
* Decision Flowchart
* Data Flow Diagram

Suggested files:

```text
docs/diagrams/class-diagram.png
docs/diagrams/sequence-diagram.png
docs/diagrams/component-diagram.png
docs/diagrams/process-flowchart.png
```

*No architecture diagrams are currently included in the repository.*

---

# 7. Known Issues

### PySR Initialization

The first execution may be slow due to Julia package installation and compilation.

### Package Import Errors

If the following error appears:

```text
ModuleNotFoundError: pcsr
```

Ensure that:

* The script is executed from the repository root.
* The project root is configured as the working directory in your IDE.

### Windows Parallelization

Using excessive parallel workers may lead to instability or reduced performance. Moderate values for `n_jobs` are recommended.

---

# 8. License

A LICENSE file must be included before public release.

**License:** To be determined.

Example:

```text
MIT License
```

---

# 9. Documentation and Resources

## Repository Structure

```text
pcsr/
├── __init__.py
├── DTR_ccp_a_prune_SR_stage1.py
└── posthoc_merge.py

scripts/
└── run_pipeline.py

data/
└── synthetic_dataset.csv

outputs/
```

## Academic Reference

If you use this code in academic work, please cite:

> I. Lamprianidou, F. Fernandes, R. J. Bessa, and P. Papadopoulos,
> “Symbolic Explainer of Power System Dynamics,”
> Proceedings of the 24th Power Systems Computation Conference (PSCC),
> Limassol, Cyprus, June 8–12, 2026.

Additional resources, tutorials, API documentation, and demonstration videos may be added in future releases.

---

# 10. Community Standards and Contribution

Before contributing, please review the organisation-wide governance documents:

* Code of Conduct
* Contributing Guidelines
* Reporting Template
* Security Policy

These documents define:

* Expected community behaviour
* Contribution workflows
* Vulnerability disclosure procedures
* Security reporting practices

Contributors are expected to follow these guidelines before submitting pull requests or reporting issues.

---

# 11. Credits and Acknowledgements

### Contributors

* Ifigeneia Lamprianidou – Lead Developer

### Acknowledgements

This work supports research in explainable artificial intelligence, symbolic regression, and power system transient stability. The work was developped within the context of the ENFIELD project.

---

# 12. Contacts

For support, collaboration opportunities, or project-related inquiries:

**Ifigeneia Lamprianidou**

GitHub: https://github.com/ifiglampr

Email: francisco.s.fernandes@inesctec.pt

GitHub issues may also be used for reporting bugs and requesting enhancements if the repository is actively monitored.
