# Linear Svm

> A Linear Support Vector Machine (SVM) is a type of supervised machine learning algorithm primarily used for classification tasks.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Linear SVM

A Linear Support Vector Machine (SVM) is a type of supervised machine learning algorithm primarily used for classification tasks. It can also be adapted for regression under the name Support Vector Regression (SVR). The fundamental goal of a linear SVM is to find the best linear hyperplane that separates the data into two classes. Here's a detailed breakdown of how it works and how it can be used:

### How Linear SVM Works:

1. **Maximizing Margin**: SVM aims to find a decision boundary (a hyperplane in higher dimensions) that maximally separates the two classes in the feature space. The hyperplane is chosen to maximize the distance (margin) between the nearest data points of each class and the hyperplane itself. These nearest data points are called support vectors, as they support the hyperplane in its optimal position.

2. **Optimization Problem**: Finding the optimal hyperplane is an optimization problem. For a linear SVM, the problem can be formulated as minimizing the norm of the vector (weight vector) perpendicular to the hyperplane, subject to the constraint that the samples are correctly classified, allowing for some misclassifications. This is controlled by a regularization parameter \( C \) which determines the trade-off between achieving a low error on the training data and minimizing the norm of the weights, helping to ensure that the model generalizes well on unseen data.

3. **Linear Separability**: The linear SVM works best when the data is linearly separable. However, if the data isn't perfectly linearly separable, the algorithm can still operate effectively by allowing some misclassifications, which is managed by the \( C \) parameter.

4. **Loss Function**: The typical loss function used in SVM is hinge loss. This loss function penalizes misclassified points, but only those that lie on the wrong side of the margin boundary.

### Using a Linear SVM:

1. **Data Preparation**: As with most machine learning algorithms, data should be prep

*[truncated — see source for full prompt]*