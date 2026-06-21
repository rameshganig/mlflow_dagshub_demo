# MLflow & DAGsHub Demo Project

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Detailed Walk‑through](#detailed-walk-through)
- [API Reference](#api-reference)
- [Testing & Validation](#testing--validation)
- [Contributing](#contributing)
- [License](#license)

---

## Project Overview

This repository provides a **self‑contained demonstration** of how to integrate **MLflow** with **DAGsHub** for end‑to‑end machine‑learning experiment tracking, model versioning, and collaborative sharing.

The core of the demo lives in the Jupyter notebook `ml_flow_dagshub.ipynb`, which walks through the typical workflow:

1. **Initialize an MLflow tracking server** (local or remote on DAGsHub).
2. **Log parameters, metrics, and artifacts** during a training run.
3. **Synchronise the run with a DAGsHub repository** using the `dagshub` Python client.
4. **Register a model** in the MLflow Model Registry.
5. **Load the registered model** for inference.

All steps are reproducible with a single command (`jupyter notebook ml_flow_dagshub.ipynb`) and require only a handful of Python dependencies.

---

## Features

- **Experiment tracking** with MLflow (parameters, metrics, artifacts).
- **Remote sync** to a DAGsHub repository – runs appear in the DAGsHub UI automatically.
- **Model registry** usage – versioned models are stored and can be loaded later.
- **Minimal setup** – only a `requirements.txt` (or pip install) is required.
- **Extensible** – the notebook can be converted to a script for CI pipelines.

---

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/mlflow_dagshub_demo.git
   cd mlflow_dagshub_demo
   ```

2. **Create a virtual environment** (recommended)
   ```bash
   python -m venv .venv
   source .venv/bin/activate   # Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   If the `requirements.txt` file is missing, install the core packages directly:
   ```bash
   pip install mlflow dagshub jupyter
   ```

4. **(Optional) Configure DAGsHub credentials**
   ```bash
   dagshub login
   ```
   Follow the interactive prompt to generate a personal access token.

---

## Quick Start

```bash
# Launch the notebook
jupyter notebook ml_flow_dagshub.ipynb
```

Execute the cells in order. After the final cell you will see:
- An MLflow run listed on your local UI (`http://127.0.0.1:5000`).
- The same run mirrored on DAGsHub (if you logged in).
- A registered model version that can be loaded with `mlflow.pyfunc.load_model`.

---

## Detailed Walk‑through

The notebook is divided into the following sections:

1. **Setup & Imports** – imports, environment variables, and DAGsHub initialisation.
2. **Data Generation** – synthetic dataset creation for a regression task.
3. **Model Definition** – a simple Scikit‑Learn `RandomForestRegressor`.
4. **Training & Logging** – `mlflow.start_run` context, logging of parameters, metrics, and model artifact.
5. **Sync to DAGsHub** – `dagshub.mlflow.init` call that binds the run to the remote repository.
6. **Model Registry** – `mlflow.register_model` and transition to `Staging`/`Production` stages.
7. **Inference** – loading the registered model and making predictions on new data.

Each section contains explanatory markdown cells, so you can read the rationale while you run the code.

---

## API Reference

The public API used in this demo is documented in `docs/API.md`. It includes:
- Functions from the `mlflow` Python package that are relevant for experiment tracking.
- Helper utilities from the `dagshub` package for remote sync.
- Example signatures for custom helper functions (if you extend the notebook).

---

## Testing & Validation

The repository does not ship automated tests yet, but you can manually verify the workflow:
1. Run the notebook and confirm that a new run appears on the local MLflow UI.
2. Check the DAGsHub repository page – the run should be visible under the *Experiments* tab.
3. Ensure the model is listed under *Models* and can be downloaded.

Future work will include a `pytest` suite that programmatically runs the notebook using `nbconvert`.

---

## Contributing

We welcome contributions! Please read the `CONTRIBUTING.md` file for guidelines on:
- Branch naming conventions.
- Code style (PEP‑8 + `black`).
- How to submit a pull request.
- Reporting bugs or requesting features.

---

## License

This project is licensed under the MIT License – see the `LICENSE` file for details.
