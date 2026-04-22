# Setup Crypto

> This tutorial explains how to setup and run IBM federated learning with crypto using fully homomorphic encryption (HE).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Setup with Crypto

This tutorial explains how to setup and run IBM federated learning with crypto using fully homomorphic encryption (HE). All commands are assumed to be run from the base directory at the top of this repository.

**Note:** This will only work on a Linux machine (x86 and IBM Z). Other operating systems and architectures are not supported.

## Setup IBM federated learning with crypto

To run projects in IBM federated learning, you must first create a Python environment to install all the requirements. You can use either Conda or venv:

<details>
<summary>Conda (recommended)</summary>

If you don't have Conda, you can install it [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install).

Once installed, create a new Conda environment. We recommend using Python 3.7, but newer versions may also work.

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

After creating and activating the Python environment, install the wheel file to install the IBM federated learning library and all dependencies. This file is located in the `federated-learning-lib` directory of this repo. By default, the wheel file will not install any additional machine learning or crypto libraries. You must specify `crypto` and the desired model training backend library in brackets. The following backends are supported:

```sh
# Install with crypto and no additional machine learning libraries
pip install "/path/to/federated_learning_lib.whl[crypto]"
# Install with crypto and Scikit-learn backend
pip install "/path/to/federated_learning_lib.whl[crypto,sklearn]"
#

*[truncated — see source for full prompt]*