---
name: Copilot Instructions Uv Python
description: ## Project Overview
This is a Python machine learning project for training and predicting rocktype and rock quality from MWD (Measurement While Drilli
model: claude-sonnet-4-5
---
# Copilot Instructions

## Project Overview
This is a Python machine learning project for training and predicting rocktype and rock quality from MWD (Measurement While Drilling) data from drill and blast rock tunnelling operations. The project is designed to run both remotely with Azure ML and locally for development and testing.

- Single codebase, two runtimes: everything runnable locally (CPU) and on AML (GPU/CPU) with the same entrypoints + configs.
- Versioned data via AML Data Assets (read-only in training), with raw → intermediate → model_ready as explicit steps.
- Dual MLflow tracking: local for quick tests; AML workspace for shared experiments—switchable via env.
- Determinism: project-local virtualenv, pinned deps, containerized training on AML, and “data+code+config” recorded per run.
- Artifacts: models (incl. ONNX), feature sets (YAML), preprocessing fingerprints (schemas, stats), plots, and logs—all first-class.

## Key Technologies

**Dependency Management**: uv (`pyproject.toml`, `uv.lock`)
**Python Version**: 3.12 (specified in `.python-version`)
**Core ML Stack**: Scikit-learn, pandas, numpy, LightGBM, XGBoost, CatBoost
**Configuration**: Hydra (CLI config management) with YAML configs in `scripts/config/`, Pydantic (validation)
**Experiment Tracking**: MLflow, Optuna (hyperparameter tuning)
**Data Quality**: ydata-profiling, pandera (validation), pyod (outlier detection)
**ML Interpretability**: SHAP, PFI
**Azure Integration**: Azure ML SDK v2, azure-storage-blob, azure-identity
**Code Quality**: Pre-commit hooks with Ruff formatting, mypy type checking, isort import sorting, bandit for security
**Testing**: pytest with coverage reporting


## Repository Structure

```bash
prediction-backend-sogn-ulven/
├── .env.template               # Template for environment variables
├── .gitignore                  # Git ignore patterns
├── .pre-commit-config.yaml     # Pre-commit hook configuration
├── .python-version             # Python version specification for pyenv
├── .secrets.baseline           # Baseline for secret scanning
├── pyproject.toml              # Project configuration and dependencies
├── README.md                   # Project documentation
├── uv.lock                     # Dependency lock file for UV
├── scripts/                    # Entry-point scripts with Hydra decorators
│   ├── config/                # Hydra configuration hierarchy
│   │   ├── main.yaml         # Main config with defaults
│   │   ├── data/             # Data processing configs
│   │   ├── model/            # Model-specific configs (lightgbm, xgboost, etc.)
│   │   ├── training/         # Training configs
│   │   └── azure/            # Azure ML configs
│   ├── train.py              # Local training script
│   └── azure/                # Azure ML submission scripts
├── src/ml_prediction_tabular/  # Main package (importable library code)
│   ├── data_processing.py    # Data cleaning, feature engineering
│   ├── model_training.py     # ML model training and evaluation
│   └── schema_config.py      # Pydantic configuration models
├── tests/                    # Test files mirroring src/ structure
├── data/                     # Data directories
│   ├── raw/                  # Original unprocessed single-tunnel data files (incoming)
│   ├── processed/            # Cleaned, combined single-tunnel datasets (previously `raw`)
│   ├── production/           # Feature-selected, filtered production datasets
│   ├── model_ready/          # Final train/test splits ready for modeling (previously `final`)
│   ├── intermediate/         # Temporary datasets for inspection
│   ├── test/                 # Small datasets for testing
│   └── schemas/              # Pandera data validation schemas
├── docs/                     # Project documentation
├── notebooks/                # Jupyter exploration notebooks
├── experiments/              # MLflow local experiment tracking
└── models/                   # Saved model artifacts (local)
```

## Development Workflow

### Environment Setup
```bash
# Install UV package manager (recommended)
curl -LsSf https://astral.sh/uv/install.sh | sh

# Install dependencies
uv sync --dev

# Setup pre-commit hooks
uv run pre-commit install
```

**NOTE**: uv will install the environment in a local `.venv/` directory. This directory is in `.gitignore` and should not be committed.

### Common Commands
```bash
# General help
uv --help 

# Handling python versions
uv pin python 3.12.11  # Pin project to Python 3.12.11
uv python list       # List available Python versions
uv python install 3.12.11 # install python version if needed
uv python pin # Check the pinned version

# Code formatting and linting
uv run ruff format .              # Format code (replaces black)
uv run ruff check . --fix        # Lint and auto-fix
uv run mypy src/                  # Type checking
uv run pre-commit run --all-files  # Run all pre-commit checks
uv run pre-commit run bandit --all-files # run security scan with bandit from pre-commit

# Testing
uv run pytest -q                  # Run all tests
uv run pytest --cov=src/ml_prediction_tabular  # With coverage
uv run pytest -m "not slow"     # Skip slow tests
uv run pytest -k "test_data"    # Run specific test pattern

# Local ML training
uv run python scripts/train_eval.py                          # Default config
uv run python scripts/train_eval.py model=xgboost            # Use XGBoost
uv run python scripts/train_eval.py training.optuna_trials=50  # Custom hyperparams

# Azure ML training
uv run python scripts/train_eval.py

```

### Format, lint and test after every code change

Prerequisites: Python 3.12 and uv. 

```bash
uv sync --dev
```

Format and lint (keep line length = 88, see `pyproject.toml`):

- Format: `uv run ruff format .`
- Sort imports: `uv run isort .`
- Lint (auto-fix where possible): `uv run ruff check --fix .`
- Type check: `uv run mypy`
- Test: `uv run pytest -q`
- Security checking with bandit. Cannot be done with `uv run bandit` but must be run with `uv run pre-commit run bandit`

CI expectations for PRs created by Copilot:

- Code is formatted, linted, and type-checked with no new warnings
- Tests pass locally; add/adjust tests when changing behavior


### Justfile-driven automation
- The project ships with a cross-platform `Justfile` that wraps frequent uv
    invocations; run `just --list` to discover the curated recipes.
- Do **not** activate a virtual environment manually—always prefer
    `uv run <command>` so the pinned interpreter and dependencies are used.
- Typical workflows:
    - Dataset builds: `just build_dataset_blastholes_1m` and
        `just build_dataset_longholes_1m`.
    - Training pipelines: `just train_eval` for experimentation and
        `just train_production` for the production configuration.
    - Analysis utilities: `just select_features`, `just hyperparameter_tuning`,
        and `just make_plot`.
- When scripting beyond the Justfile, mirror the same uv-first pattern the
    recipes use; this keeps CLI execution deterministic across platforms.

## Security Considerations
- Keep `.env` files and Azure credentials out of source control; populate them
  from `.env.template`, prefer managed identities or Azure Key Vault, and
  rotate secrets immediately if exposure is suspected.
- Treat drilling datasets and ML artifacts as confidential: store them only in
  sanctioned directories, avoid uploading to personal storage, and redact
  customer or tunnel identifiers before sharing.
- Stick to the pinned toolchain by running commands with `uv run` and do not
  introduce new dependencies or outbound network usage without review.
- Authenticate to Azure with least privilege via `DefaultAzureCredential`, and
  never hard-code subscription IDs, keys, or connection strings in code or
  logs.
- Scrub notebooks, logs, and screenshots for sensitive values prior to
  distributing them outside the project team.

## Configuration Architecture

### Hydra + Pydantic Pattern
- **Hydra decorators**: Only use in `scripts/` for CLI/config loading
- **Pydantic validation**: Always validate raw Hydra cfg with models from `schema_config.py`
- **Use `pcfg`**: Throughout codebase, use validated Pydantic config (`pcfg`), NOT raw Hydra cfg
- **No Hydra imports**: Never import Hydra in `src/ml_prediction_tabular/` package code
- Hierarchical YAML configs under `scripts/config/` with `main.yaml` as the root
- Modular configs in subdirectories: `dataset/`, `model/`, `experiment/`, `azure/`, `plot`
- Use Hydra ONLY in scripts under `scripts/` to load YAML configs from `scripts/config/**`
- Validate configuration with Pydantic models in `src/ml_prediction_tabular/schema_config.py`
- Use the validated config object (commonly `pcfg`) inside library code; do not use raw Hydra config in `ml_prediction_tabular`
- Entrypoints: use Hydra `@hydra.main()` decorator for configuration injection
- Override with: `python scripts/train_eval.py model=catboost`


```python
# In scripts/ (GOOD)
import hydra
from omegaconf import DictConfig
from ml_prediction_tabular.schema_config import TrainingConfig

@hydra.main(config_path="config", config_name="main")
def main(cfg: DictConfig) -> None:
    pcfg = TrainingConfig(**cfg)  # Validate with Pydantic
    # Use pcfg, not cfg

# In src/ package code (GOOD) - Use explicit parameters, not config objects
def optimize_hyperparameters(
    X: pd.DataFrame,
    y: pd.Series,
    model_type: str,
    n_trials: int = 100,
    cv_folds: int = 5,
) -> dict[str, Any]:
    # Never import hydra here
    # Always define variables explicitly in function signatures

# BAD - Don't use config objects as parameters in src/ package
def optimize_hyperparameters(config: TrainingConfig) -> dict[str, Any]:
```

## Testing and validation Standards

### Test Structure
- **Location**: Tests in `tests/` directory mirroring `src/` structure
- **Naming**: `test_<module_name>.py` files, `test_<function_name>()` functions
- **Framework**: pytest with parametrize and fixtures
- **Pattern**: Arrange-Act-Assert structure
- **Markers**: Use `@pytest.mark.slow` for long-running tests
- **Parametrize**: Use `@pytest.mark.parametrize` for testing multiple inputs/scenarios
- **Conftest**: Collect fixtures and other common tooling in `conftest.py`
- **Single file per source module**: All tests that target a given source module (e.g. `src/ml_prediction_tabular/training_funcs.py`) must live in exactly one corresponding test file (e.g. `tests/test_training_funcs.py`). Do NOT split tests for the same production module across multiple `test_*.py` files; consolidate helper/edge‑case/error‑path tests in that single file for clarity, discoverability, and reduced import/fixture duplication.

```python
import pytest
import pandas as pd
from ml_prediction_tabular.data_processing import clean_data

@pytest.fixture
def sample_mwd_data():
    """Sample MWD data for testing."""
    return pd.DataFrame({
        'penetration_rate': [5.2, 4.8, None, 6.1],
        'torque': [120, 115, 130, None],
        'rock_type': ['granite', 'limestone', 'shale', 'granite']
    })

def test_clean_data_removes_nulls(sample_mwd_data):
    """Test that clean_data removes rows with missing values."""
    # Arrange
    expected_len = 2  # Only 2 complete rows

    # Act
    result = clean_data(sample_mwd_data)

    # Assert
    assert len(result) == expected_len
    assert result.isnull().sum().sum() == 0

@pytest.mark.parametrize("rock_type,expected", [
    ("granite", "igneous"),
    ("limestone", "sedimentary"),
    ("sandstone", "sedimentary"),
    ("shale", "sedimentary")
])
def test_classify_rock_family(rock_type, expected):
    """Test rock family classification for multiple rock types."""
    # Act
    result = classify_rock_family(rock_type)

    # Assert
    assert result == expected
```


### Configuration & Validation Scripts
All code/config validation scripts live in `scripts/validation_scripts/` (e.g. smoke
tests for centralized labelnames and dataset path/key verification). Place any new
validation or integrity check scripts there so Copilot (and CI, if added) can discover
them consistently. Keep scripts fast, dependency‑light, and focused on catching
drift early.


## MLOps Best Practices

### Experiment Tracking
- **Local**: MLflow tracking in `experiments/mlruns` directory
- **Remote**: Azure ML integrated MLflow
- **Model Registry**: Automatic versioning and registration
- **Artifacts**: Save models, plots, metrics consistently

### Data Validation
- **Schemas**: Define Pandera schemas in `src/ml_prediction_tabular/dataset/preprocessing`
- **Validation**: Validate all input data before processing
- **Profiling**: Generate ydata-profiling reports for EDA

### Reproducibility
- **Seeds**: Set random seeds for reproducible results
- **Versioning**: Track data, code, and model versions
- **Environments**: Pin dependencies in pyproject.toml
- **Configuration**: Use Hydra for experiment configuration


## Azure ML Integration

### Setup and authentication
**Configure credentials**
Populate `.env` from `.env.template` with Azure subscription, resource group, and workspace identifiers (never commit real secrets). Managed identity is preferred when running inside Azure.

Except for credentials set in `.env` configure Azure settings using the hydra config system in `scripts/config/azure/`

```python
from azure.identity import DefaultAzureCredential
from azure.ai.ml import MLClient

credential = DefaultAzureCredential()
ml_client = MLClient(subscription_id, resource_group, workspace_name, credential)
```


### Production training, model registration and Azure batch deployment
1. **Run the production trainer**: Execute
    `uv run python scripts/train_production.py` with Hydra overrides for the
    dataset, experiment label, and model (for example
    `dataset=blastholes_1m.yaml experiment.label=Rock model=extra_trees.yaml`).
    Enable `experiment.track_experiment` and
    `experiment.production_settings.register_in_mlflow_registry` when the run
    should be logged to MLflow and pushed to the registry.
2. **Register the model**: Use
    `scripts/azure_manage_resources.py register-model` either against the local
    MLflow artifact path or an `azureml://` job URI, adding descriptive tags for
    dataset and label.
3. **Bundle scoring assets**: Call
    `scripts/azure_manage_resources.py prepare-batch-assets` to emit a
    preprocessing-aware `score.py`, `inference_config.json`, and packaged source
    tree under a deployment directory.
4. **Deploy the batch endpoint**: Invoke
    `scripts/azure_manage_resources.py deploy-batch-endpoint` with the endpoint
    name, deployment name, model reference, compute target, and asset directory.
    The command updates the deployment and, by default, sets it as the endpoint
    default. Use `--no-set-default` when rolling out side-by-side versions.
5. **Feed compliant input data**: Batch scoring expects semicolon-separated CSV
    files matching the production dataset schema (including `Tunnel` and
    `PegStart`). Azure runs `scripts/azure/batch_scoring.py`, which rebuilds the
    dataset features before invoking the registered model.
6. **Operate iteratively**: Repeat the sequence to publish new model versions;
    reusing deployment and endpoint names performs in-place upgrades while
    preserving lineage through MLflow tracking.


## Git Workflow

### GitHub Issue Format
When creating issues, follow this structure:
- **Title**: Clear, descriptive summary (50 chars max)
- **Labels**: Appropriate labels (bug, feature, documentation, etc.)
- **Template**: Use issue templates when available
- **Description**:
  - Problem description or feature request
  - Steps to reproduce (for bugs)
  - Expected vs actual behavior
  - Environment details (Python version, OS, etc.)
  - Relevant logs or error messages

### Commit Standards
- **Title**: Short, imperative summary (50 chars max)
- **Body**: Bullet list of specific changes
- **Format**: Use conventional commits when appropriate

### PR Guidelines
- **Description**: Context, issue links, summary of changes
- **Tests**: Include tests for new functionality
- **Coverage**: Maintain or improve test coverage
- **Documentation**: Update relevant docs

### Pre-commit Hooks
Automatically run on commit:
- Ruff code formatting and linting
- mypy type checking
- YAML/TOML validation
- Security scanning with bandit

## Pre-Production Deprecation & Backward Compatibility Policy

This repository is in a pre-release / early development phase. As such:

- Do NOT add backward compatibility layers (shims, alias functions, fall-through imports).
- Do NOT keep deprecated functions, scripts, or parameters once they are replaced—remove them outright.
- Do NOT emit `DeprecationWarning`, custom warnings, or log messages about removed features.
- Do NOT maintain a deprecation schedule or changelog sections for removed internals at this stage.
- Refactors may freely change function names, signatures, module paths, and behaviors as needed to improve clarity or correctness.
- Tests should be updated to the new API surface immediately; never keep tests for removed code.

Rationale: velocity and clarity outweigh stability before the first production release. This policy may change once the project reaches an externally consumed, versioned production milestone. When that happens, introduce a formal semantic versioning + deprecation process explicitly (and update this section accordingly).