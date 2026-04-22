---
name: Python.Instructions
description: Python coding conventions and guidelines
model: claude-sonnet-4-5
---
# Python Coding Conventions

## Python Instructions

- Write clear and concise comments for each function.
- Ensure functions have descriptive names and include type hints.
- Provide docstrings following PEP 257 conventions.
- Break down complex functions into smaller, more manageable functions.
- Use Python 3.11+ features and type annotations everywhere
- Prefer PEP 604 unions for optionals (use `T | None` instead of `Optional[T]`); mypy supports this and it keeps annotations concise and consistent

## General Instructions

- Always prioritize readability and clarity.
- For algorithm-related code, include explanations of the approach used.
- Write code with good maintainability practices, including comments on why certain design decisions were made.
- Handle edge cases and write clear exception handling.
- For libraries or external dependencies, mention their usage and purpose in comments.
- Use consistent naming conventions and follow language-specific best practices.
- Write concise, efficient, and idiomatic code that is also easily understandable.
- Single Responsibility Principle: Each function/class has one clear purpose
- DRY: Don't Repeat Yourself - extract common logic

## Code Style and Formatting

- Follow the **PEP 8** style guide for Python.
- Maintain proper indentation (use 4 spaces for each level of indentation).
- Ensure lines do not exceed 88 characters.
- Place function and class docstrings immediately after the `def` or `class` keyword.
- Use blank lines to separate functions, classes, and code blocks where appropriate.
- Strings via f-strings, not `.format()` or `%`
- prefer `match/case` over long `if/elif` chains when appropriate
- Imports at top of file: Never place imports inside functions or deep within code blocks. All imports must be at module top-level to keep dependencies explicit, avoid repeated import overhead, and satisfy linters/type-checkers. The only narrow exceptions are:
  - Optional, heavy dependencies used solely in guarded or plugin-like code paths, with an inline comment explaining why the import is deferred.
  - Try/except ImportError guards for optional extras, again with an explanatory comment and a clear fallback.
- Private methods: Prefix with underscore `_helper_function()`
- Constants: Use `ALL_CAPS` for constants
- Line length: 88 characters max (Black default)
- Docstrings: Google style docstrings

## Library decisions
- Use `numpy.typing.NDArray` for array types when relevant
- Prefer: `pathlib` over `os`, `httpx` over `requests`, `pytest` over `unittest`, Hydra v1.3+, Azure ML SDK v2
- Matplotlib: use the OO style (`ax.plot(...)`), not `plt.plot(...)`
- Prefer `pathlib.Path` over string paths
- For machine learning usecases prefer `hydra` decorator for cli control over `argparse`
- For other scripts and project use `Typer`for CLI control over `argparse`. Only use `argparse` if zero-dependencies are important.

## Testing

- Always include test cases for critical paths of the application.
- Account for common edge cases like empty inputs, invalid data types, and large datasets.
- Include comments for edge cases and the expected behavior in those cases.
- Write unit tests for functions and document them with docstrings explaining the test cases.


### Test Structure

- Location: Tests in `tests/` directory mirroring `src/` structure
- Naming: `test_<module_name>.py` files, `test_<function_name>()` functions
- Framework: pytest with parametrize and fixtures
- Pattern: Arrange-Act-Assert structure
- Markers: Use `@pytest.mark.slow` for long-running tests
- Parametrize: Use `@pytest.mark.parametrize` for testing multiple inputs/scenarios
- Conftest: Collect fixtures and other common tooling in `conftest.py`


### Example of proper test structure

```python
import pytest
import pandas as pd
from ml_prediction_tabular.data_processing import clean_data

# place this in conftest.py
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



## Example of Proper Documentation

```python
import math

def calculate_area(radius: float) -> float:
    """
    Calculate the area of a circle given the radius.

    Parameters:
    radius (float): The radius of the circle.

    Returns:
    float: The area of the circle, calculated as π * radius^2.
    """
    return math.pi * radius ** 2
```

## Example of proper type annotation

```python
from pathlib import Path

import pandas as pd

def process_mwd_data(
    data_path: Path,
    target_col: str = "rock_type",
    features: list[str] | None = None
) -> tuple[pd.DataFrame, pd.Series]:
    """Process MWD drilling data for ML training.

    Args:
        data_path: Path to raw data file
        target_col: Target column name
        features: Feature columns to use (if None, use all numeric)

    Returns:
        Tuple of (features_df, target_series)
    """
    pass
```

## Example of proper use of Hydra for CLI control in machine learning projects

```yaml
# scripts/config/main.yaml
# Short Hydra-compatible main config used by scripts/
defaults:
  - dataset: default_dataset.yaml
  - model: lightgbm.yaml
  - training: default_training.yaml

experiment:
  mlflow_tracking_uri: "file://${hydra:runtime.cwd}/experiments/mlruns"
  run_name: "local_run"
```
```yaml
# scripts/config/dataset/default_dataset.yaml
data_path: "data/model_ready/train.parquet"
target_col: "rock_type"
features: null  # null -> use automatic feature selection
```
```yaml
# scripts/config/dataset/lightgbv.yaml
type: "lightgbm"
params:
  learning_rate: 0.05
  num_leaves: 31
  n_estimators: 100
```
```yaml
# scripts/config/dataset/default_training.yaml
seed: 42
n_trials: 50
cv_folds: 5
early_stopping_rounds: 50
```

```python
# src/schema_config.py

from pathlib import Path
from typing import Any

from pydantic import BaseModel

class Dataset(BaseModel):
    """Dataset configuration used by data loading/preprocessing."""

    data_path: Path
    target_col: str
    features: list[str] | None = None


class Model(BaseModel):
    """Model configuration used by training code."""

    type: str
    params: dict[str, Any] = Field(default_factory=dict)


class TrainingParams(BaseModel):
    """Training/optimization configuration."""

    seed: int = 42
    n_trials: int = 50
    cv_folds: int = 5
    early_stopping_rounds: int = 50


class TrainingConfig(BaseModel):
    """Root config schema validated from Hydra DictConfig."""

    dataset: Dataset
    model: Model
    training: TrainingParams
```


```python
import hydra
from omegaconf import DictConfig
from src.schema_config import TrainingConfig # pydantic validation schema for config

@hydra.main(config_path="config", config_name="main")
def main(cfg: DictConfig) -> None:
    pcfg = TrainingConfig(**cfg)  # Validate with Pydantic
    # Use pcfg, not cfg

```