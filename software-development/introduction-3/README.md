# Introduction

> Machine learning is a branch of artificial intelligence that focuses on developing algorithms that allow computers to learn from and make predictions or decisions based on data.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
### 1. Introduction to Machine Learning and SVMs

Machine learning is a branch of artificial intelligence that focuses on developing algorithms that allow computers to learn from and make predictions or decisions based on data. Supervised learning, one of the key categories of machine learning, involves training a model on a labeled dataset, where the correct output is known, to predict outcomes for unseen data.

Support Vector Machines (SVMs) are a vital tool in the supervised learning arsenal. Originally developed in the 1960s and later refined in the 1990s, SVMs have been extensively used due to their powerful ability to handle high-dimensional data and perform classification tasks effectively.

### 2. Theoretical Background of SVMs

The core idea behind SVMs is to find a hyperplane that best divides a dataset into classes. In two-dimensional space, this hyperplane can be thought of as a line dividing a plane in two parts where each class lays on either side.

#### 2.1 Linear SVMs
In its simplest form, the SVM algorithm attempts to find the optimal separating hyperplane which maximizes the margin between two classes. The data points nearest to the hyperplane are the support vectors, which are the critical elements of the training set because the position and orientation of the hyperplane depend directly on them.

Mathematically, if \((x_1, y_1), (x_2, y_2), ..., (x_n, y_n)\) represent the training examples, where \(x_i\) is a feature vector and \(y_i\) is the class label (typically +1 or -1), the goal is to solve the following optimization problem:
\[ \min_{\mathbf{w}, b} \frac{1}{2} \|\mathbf{w}\|^2 \]
subject to:
\[ y_i (\mathbf{w} \cdot x_i + b) \geq 1, \text{ for all } i \]

#### 2.2 Non-linear SVMs
To handle non-linearly separable data, SVMs use a technique called the kernel trick. This approach involves mapping data to a higher-dimensional space where a linear separator might exist. Common kernels include the polynomial and radial basis function (RBF) kerne

*[truncated — see source for full prompt]*