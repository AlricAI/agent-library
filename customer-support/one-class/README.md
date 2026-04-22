# One Class

> #### Introduction
One-class Support Vector Machines (SVMs) are a specialized version of SVMs used primarily for anomaly detection, also known as novel

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
### Chapter: One-Class SVM for Anomaly Detection

#### Introduction
One-class Support Vector Machines (SVMs) are a specialized version of SVMs used primarily for anomaly detection, also known as novelty detection. This model learns a decision function for outlier detection: classifying new data as similar or different to the training set. The method is particularly useful in applications where the majority of the data is 'normal' and anomalies are few or not well defined. This chapter delves into the concept, usage, and implementation of one-class SVMs.

#### 1. Understanding One-Class SVM
A one-class SVM works by fitting a decision boundary that encompasses the majority of the normal data points. It attempts to separate all the normal data points from the origin (in feature space) and maximize the distance from this hyperplane to the origin. This results in a model that is sensitive to new data points that are different from the training set, identifying them as anomalies.

##### Key Concept:
- **Nu Parameter**: Represents an upper bound on the fraction of training errors and a lower bound of the fraction of support vectors. It essentially controls the sensitivity of the support vectors and must be set between 0 and 1.

#### 2. Applications of One-Class SVM
- **Fraud Detection**: Identifying unusual transactions.
- **Network Security**: Detecting unusual patterns in network traffic that could indicate a security breach.
- **Machine Condition Monitoring**: Predicting equipment failures by identifying deviations from normal operational patterns.
- **Medical Anomaly Detection**: Identifying rare diseases or abnormal medical test results.

#### 3. Practical Example in Scikit-learn
Here is an example of using a one-class SVM for detecting outliers in a dataset. We'll simulate a dataset where the majority of the data is normal but includes some outliers.

##### Example with Scikit-learn:
```python
import numpy as np
from sklearn.svm import OneClassSVM
import matplotlib.p

*[truncated — see source for full prompt]*