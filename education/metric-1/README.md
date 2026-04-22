# Metric

> **Scikit-learn's metric module** provides a rich set of functions for evaluating the performance of machine learning models.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## Scikit-learn's Metric Package: A Comprehensive Overview

**Scikit-learn's metric module** provides a rich set of functions for evaluating the performance of machine learning models. It offers a variety of metrics for different types of problems, including classification, regression, clustering, and multi-label tasks.

### Key Metrics and Functionalities:

#### Classification Metrics:
* **Accuracy:** Overall correctness of predictions.
* **Precision:** Proportion of positive predictions that were actually correct.
* **Recall:** Proportion of actual positives that were correctly predicted.
* **F1-score:** Harmonic mean of precision and recall.
* **Confusion Matrix:** A table showing the number of correct and incorrect predictions.
* **ROC Curve and AUC:** Visualize and quantify the classifier's ability to distinguish between classes.
* **Log Loss:** Measures the performance of a probabilistic classification model.

#### Regression Metrics:
* **Mean Squared Error (MSE):** Measures the average squared difference between predicted and actual values.
* **Mean Absolute Error (MAE):** Measures the average absolute difference between predicted and actual values.
* **R^2 (Coefficient of Determination):** Represents the proportion of variance in the dependent variable explained by the model.
* **Mean Squared Log Error (MSLE):** Suitable for targets with exponential growth.

#### Clustering Metrics:
* **Homogeneity:** Measures the extent to which clusters contain only members of a single class.
* **Completeness:** Measures the extent to which all members of a given class are assigned to the same cluster.
* **V-measure:** Harmonic mean of homogeneity and completeness.
* **Adjusted Rand Index:** Measures the similarity between two clusterings.
* **Silhouette Coefficient:** Evaluates the quality of clustering by measuring how similar a data point is to its own cluster compared to other clusters.

#### Other Metrics:
* **Distance metrics:** Euclidean, Manhattan, cosine, etc.
* *

*[truncated — see source for full prompt]*