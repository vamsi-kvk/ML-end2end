# ML-end2end House Price Prediction with MLOps

This project demonstrates an end-to-end machine learning pipeline for house price prediction using MLOps practices with ZenML.

## Prerequisites

- Python 3.6 or higher
- [ZenML](https://docs.zenml.io/getting-started/installation)
- [MLflow](https://www.mlflow.org/)

## Installation and Setup

### Step 1: Install ZenML

Follow the instructions on the [ZenML installation guide](https://docs.zenml.io/getting-started/installation).

### Step 2: Create a Virtual Environment

Once you have downloaded the source code, create a virtual environment. You can follow this [YouTube guide](https://youtu.be/GZbeL5AcTgw?si=uj7B8-10kbyEytKo) to create a virtual environment.

### Step 3: Activate Virtual Environment

Activate your virtual environment and then run the following command to install the required packages:

```bash
pip install -r requirements.txt
```

## Step 4: Install ZenML Integrations

If you are running the `run_deployment.py` script, you will need to install some integrations using ZenML:

```bash
zenml integration install mlflow -y
```


## Step 5: Configure ZenML Stack
The project can only be executed with a ZenML stack that includes an MLflow experiment tracker and model deployer as components. Configure a new stack with these components as follows:

# Install MLflow integration
```bash
zenml integration install mlflow -y
```

# Register MLflow experiment tracker
```bash
zenml experiment-tracker register mlflow_tracker --flavor=mlflow
```
# Register MLflow model deployer
```bash
zenml model-deployer register mlflow --flavor=mlflow
```
# Register and set the stack
```bash
zenml stack register local-mlflow-stack -a default -o default -d mlflow -e mlflow_tracker --set
```