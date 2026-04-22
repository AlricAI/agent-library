# Setup

> This tutorial explains how to setup and run IBM federated learning from scratch.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Setup

This tutorial explains how to setup and run IBM federated learning from scratch. All commands are assumed to be run from the base directory at the top of this repository.

## Setup IBM federated learning

To run projects in IBM federated learning, you must first create a Python environment to install all the requirements. You can use either Conda or venv:

<details>
<summary>Conda (recommended)</summary>

If you don't have Conda, you can install it [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install).

Once installed, create a new Conda environment. We recommend using Python 3.7, but newer versions may also work. For Mac M1/M2 systems, you must use Python 3.8 or above.

```sh
conda create -n <env_name> python=3.7
```

Activate the newly created Conda environment.

```sh
conda activate <env_name>
```

</details>

<details>
<summary>Venv</summary>

Create a new virtual environment using Python's built-in `venv` module. This will use your system's Python version which may or may not be fully compatible.

```bash
python -m venv venv
```

Activate the newly created virtual environment.

```sh
source venv/bin/activate
```

</details>

After creating and activating the Python environment, install the wheel file to install the IBM federated learning library and all dependencies. This file is located in the `federated-learning-lib` directory of this repo. By default, the wheel file will not install any additional machine learning libraries. You must specify the desired model training backend library in brackets. The following backends are supported:

```sh
# Install with no additional machine learning libraries
pip install "/path/to/federated_learning_lib.whl"
# Install with Scikit-learn backend
pip install "/path/to/federated_learning_lib.whl[sklearn]"
# Install with PyTorch backend
pip install "/path/to/federated_learning_lib.whl[pytorch]"
# Install with Keras (TensorFlow v1) backend
pip install "/path/to/federated_learning_lib.whl[keras]"
# I

*[truncated — see source for full prompt]*