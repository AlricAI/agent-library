# Model Selection

> #### Introduction
Model selection and hyperparameter tuning are critical steps in building effective machine learning models, including Support Vector

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Model Selection and Hyperparameter Tuning Using Grid Search and Random Search

#### Introduction
Model selection and hyperparameter tuning are critical steps in building effective machine learning models, including Support Vector Machines (SVMs). Techniques like Grid Search and Random Search allow for systematic exploration of model parameter spaces, helping to identify the most effective combinations of parameters for optimal performance. This chapter explores these two popular methods, providing insights and examples using Python’s Scikit-learn library.

#### 1. Understanding Hyperparameters in SVMs
SVMs have several key hyperparameters that influence their training and performance:
- **C (Regularization parameter)**: Balances the trade-off between achieving a low error on the training data and minimizing the model complexity.
- **Kernel type**: Determines the type of hyperplane used to separate the data.
- **Gamma (Kernel coefficient for ‘rbf’, ‘poly’ and ‘sigmoid’)**: Defines how far the influence of a single training example reaches.
- **Degree (for polynomial kernel)**: The degree of the polynomial kernel function.

#### 2. Grid Search
Grid Search is an exhaustive searching through a manually specified subset of the hyperparameter space of the learning algorithm. A grid search algorithm must be guided by some performance metric, typically measured by cross-validation on the training set.

##### Example with Scikit-learn:
```python
from sklearn.model_selection import GridSearchCV
from sklearn.svm import SVC
from sklearn.datasets import load_iris
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline

# Load data
data = load_iris()
X, y = data.data, data.target

# Create a pipeline with a scaler and an SVM
pipe = Pipeline([
    ('scaler', StandardScaler()),
    ('svm', SVC())
])

# Define the parameter grid
param_grid = {
    'svm__C': [0.1, 1, 10, 100],
    'svm__gamma': [0.001, 0.01, 0.1, 1],
    'svm__kernel': ['rbf', 'poly',

*[truncated — see source for full prompt]*