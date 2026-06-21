# mlflow_dagshub_demo

## Overview

A small demonstration project showcasing how to integrate **MLflow** with **DAGsHub** for experiment tracking, model versioning, and collaboration. The repository contains example code and a Jupyter notebook that walks through the typical workflow.

---

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/mlflow_dagshub_demo.git
   cd mlflow_dagshub_demo
   ```

2. **Create a virtual environment** (optional but recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows use `venv\Scripts\activate`
   ```

3. **Install the required Python packages**
   ```bash
   pip install -r requirements.txt
   ```
   > **Note**: If a `requirements.txt` file is not present, install the core dependencies manually:
   ```bash
   pip install mlflow dagshub
   ```

4. **Set up DAGsHub credentials** (if you want to push runs to DAGsHub)
   ```bash
   dagshub login
   ```
   Follow the prompts to authenticate with your DAGsHub account.

---
<!-- FIXME: Need to add more complex workflow details here later -->

## Usage

The main entry point is the Jupyter notebook `ml_flow_dagshub.ipynb`. You can launch it with:
```bash
jupyter notebook ml_flow_dagshub.ipynb
```

The notebook demonstrates:
- Initializing an MLflow run.
- Logging parameters, metrics, and artifacts.
- Syncing the run with a DAGsHub repository.
- Registering a model and loading it for inference.

If you prefer a script‑based approach, you can copy the relevant cells into a Python file and run it with:
```bash
python my_mlflow_script.py
```

---

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**.
2. **Create a new branch** for your feature or bug‑fix:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** and ensure the code style is consistent (PEP‑8).
4. **Write or update documentation** if you add new functionality.
5. **Run tests** (if any) to confirm everything works.
6. **Commit your changes** with a clear commit message.
7. **Push to your fork** and open a Pull Request against the `main` branch.

Please see the `CONTRIBUTING.md` file for more detailed guidelines (if it exists) or open an issue to discuss larger changes.

---

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.
