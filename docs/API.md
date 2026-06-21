# API Reference for MLflow & DAGsHub Demo

This document provides concise reference material for the functions and classes used in the demonstration notebook `ml_flow_dagshub.ipynb`.

---

## MLflow Functions

| Function | Description | Typical Use‑Case |
|----------|-------------|------------------|
| `mlflow.start_run()` | Starts a new MLflow run context. | Wrap training code to automatically log parameters, metrics, and artifacts. |
| `mlflow.log_param(key, value)` | Logs a single parameter (e.g., hyper‑parameter). | Record model configuration. |
| `mlflow.log_metric(key, value, step=None)` | Logs a metric value, optionally with a step index. | Track loss/accuracy over epochs. |
| `mlflow.log_artifact(local_path, artifact_path=None)` | Uploads a local file or directory as an artifact. | Save plots, model files, or other outputs. |
| `mlflow.sklearn.log_model(model, artifact_path, registered_model_name=None)` | Saves a scikit‑learn model and optionally registers it. | Persist the trained model in the MLflow Model Registry. |
| `mlflow.register_model(model_uri, name)` | Registers an existing model artifact under a given name. | Create a versioned model entry. |
| `mlflow.transition_model_version_stage(name, version, stage, archive_existing_versions=False)` | Moves a model version to a stage (`None`, `Staging`, `Production`, `Archived`). | Promote a model after validation. |
| `mlflow.pyfunc.load_model(model_uri)` | Loads a model (any supported flavor) as a generic Python function. | Perform inference without re‑training. |

---

## DAGsHub Functions (via `dagshub` package)

| Function | Description | Typical Use‑Case |
|----------|-------------|------------------|
| `dagshub.login()` | Interactive login that stores a personal access token. | Authenticate CLI/SDK with DAGsHub. |
| `dagshub.init(repo_path, **kwargs)` | Initialise a Git repository for DAGsHub tracking. | Prepare a new project folder. |
| `dagshub.mlflow.init(repo, experiment_name=None, **kwargs)` | Convenience wrapper that configures MLflow to sync runs to the specified DAGsHub repo. | Replace manual `mlflow.set_tracking_uri` calls. |
| `dagshub.upload_file(local_path, remote_path)` | Upload a file to the DAGsHub repository (similar to `git push`). | Add custom artifacts not captured by MLflow. |

---

## Example Snippets

```python
import mlflow
import mlflow.sklearn
from dagshub import mlflow as dh_mlflow

# Initialise DAGsHub sync (assumes you are inside a cloned DAGsHub repo)
dh_mlflow.init(repo=".")

with mlflow.start_run() as run:
    # Log parameters
    mlflow.log_param("n_estimators", 100)
    mlflow.log_param("max_depth", 5)

    # Train model
    model = RandomForestRegressor(n_estimators=100, max_depth=5)
    model.fit(X_train, y_train)

    # Log metrics
    preds = model.predict(X_test)
    mse = mean_squared_error(y_test, preds)
    mlflow.log_metric("mse", mse)

    # Log the model and register it
    mlflow.sklearn.log_model(model, "model", registered_model_name="demo-rf")
```

---

## Further Reading

- **MLflow Documentation** – https://mlflow.org/docs/latest/index.html
- **DAGsHub Python SDK** – https://dagshub.com/docs/python-sdk
- **Model Registry Guide** – https://mlflow.org/docs/latest/model-registry.html

---

*This API reference is intentionally lightweight; the demo focuses on a subset of MLflow’s capabilities. For production projects, consult the full MLflow and DAGsHub docs.*
