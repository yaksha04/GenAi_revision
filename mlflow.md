What is MLflow?

MLflow is an open-source platform used to manage the complete machine learning lifecycle.

It helps with:

Experiment tracking
Model versioning
Model packaging
Deployment
Reproducibility
Collaboration

Think of it as:

“Git + DevOps + deployment system for ML models.”

Why MLflow Was Created

In real ML projects, chaos happens quickly.

Example:

You trained:

50 models
different hyperparameters
different datasets
different accuracies

After 2 weeks:
You forget:

which model was best
which parameters worked
which dataset version used
which code generated result

This becomes nightmare in companies.

MLflow solves this.

Real-World Problem Example

Suppose you train:

Model A → Accuracy 82%
Model B → Accuracy 89%
Model C → Accuracy 91%

After a month:
Manager asks:

“Which configuration gave 91%?”

Without MLflow:
💀 “Sir… I forgot.”

With MLflow:
Everything tracked automatically.

Main Components of MLflow

MLflow has 4 major components:

1. Tracking
2. Projects
3. Models
4. Model Registry
1. MLflow Tracking

MOST IMPORTANT PART.

Used to track:

experiments
metrics
parameters
artifacts
What Gets Tracked?
Parameters

Example:

learning_rate = 0.01
epochs = 20
batch_size = 32
Metrics

Example:

accuracy = 91%
loss = 0.12
precision = 0.88
Artifacts

Files generated during training:

models
graphs
plots
datasets
logs
Example Workflow
import mlflow

with mlflow.start_run():

    mlflow.log_param("learning_rate", 0.01)

    mlflow.log_metric("accuracy", 0.91)

    mlflow.log_artifact("model.pkl")

This logs everything.

MLflow UI

You can launch UI:

mlflow ui

Then browser opens:

http://localhost:5000

You can compare experiments visually.

2. MLflow Projects

Used for packaging ML code in reproducible format.

Makes projects portable.

Contains:

code
dependencies
entry points
Why Needed?

Because:

“Works on my machine” problem exists in ML too.

MLflow Projects standardize execution.

Example Structure
project/
 ├── train.py
 ├── MLproject
 ├── conda.yaml
MLproject File

Defines:

entry points
commands
environments

Example:

name: churn_prediction

entry_points:
  main:
    command: "python train.py"
3. MLflow Models

Standard packaging format for ML models.

Supports:

Scikit-learn
TensorFlow
PyTorch
XGBoost
LightGBM
many more
Why Important?

Different frameworks save differently.

Example:

PyTorch → .pt
TensorFlow → SavedModel
sklearn → .pkl

MLflow standardizes deployment.

Model Flavors

MLflow stores models with “flavors”.

Example:

model/
 ├── MLmodel
 ├── conda.yaml
 ├── model.pkl
Saving Model

Example:

mlflow.sklearn.log_model(model, "model")
Loading Model
loaded_model = mlflow.pyfunc.load_model(model_uri)
4. Model Registry

VERY IMPORTANT for MLOps.

Registry manages:

model versions
staging
production deployment
approvals
Example Lifecycle
Version 1 → Staging
Version 2 → Testing
Version 3 → Production
Why Registry Matters

Imagine:

multiple data scientists
many models
production systems

Need centralized management.

MLflow Registry provides that.

Stages in Registry
None

Initial state.

Staging

Testing phase.

Production

Live serving.

Archived

Old model.

MLflow Architecture
ML Code
   ↓
MLflow Tracking Server
   ↓
Backend Store + Artifact Store
Backend Store

Stores:

metrics
parameters
experiment metadata

Usually:

MySQL
PostgreSQL
SQLite
Artifact Store

Stores:

model files
plots
datasets

Usually:

S3
Azure Blob
GCS
local storage
Tracking Server

Central server handling experiments.

Command:

mlflow server \
--backend-store-uri sqlite:///mlflow.db \
--default-artifact-root ./artifacts
MLflow in MLOps

MLflow is HUGE in:

MLOps
AI infrastructure
LLMOps

Because ML systems need:

reproducibility
deployment
monitoring
versioning
MLflow vs Traditional Software

Traditional DevOps tracks:

code versions

ML systems must track:

data versions
model versions
hyperparameters
metrics
experiments

Much harder.

MLflow + Docker

Very common.

ML App
   ↓
Docker
   ↓
MLflow
   ↓
Deployment
MLflow + Kubernetes

Used for:

scalable training
model serving
pipelines

Companies deploy MLflow on:

Kubernetes
ECS
cloud VMs
MLflow + CI/CD

Common MLOps pipeline:

GitHub
  ↓
Jenkins/GitHub Actions
  ↓
Train Model
  ↓
Log to MLflow
  ↓
Register Model
  ↓
Deploy

This is basically:

DevOps for ML.
MLflow vs OpenTelemetry

You asked both, so important difference:

Feature	OpenTelemetry	MLflow
Domain	Observability	MLOps
Purpose	Monitor systems	Manage ML lifecycle
Tracks	Logs, metrics, traces	Experiments, models
Used by	DevOps/SRE	ML Engineers/MLOps
Focus	Infrastructure health	ML model management
MLflow vs Kubeflow

Kubeflow is much bigger and more complex.

MLflow	Kubeflow
Easier	Harder
Experiment tracking	Full ML platform
Lightweight	Kubernetes-heavy
Beginner-friendly	Enterprise-heavy

For beginners:
👉 MLflow first.

MLflow vs DVC

DVC mainly focuses on:

data versioning
pipeline reproducibility

MLflow focuses on:

experiment tracking
model lifecycle

Many companies use both together.
