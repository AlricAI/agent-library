## Overview
This agent specializes in the end-to-end lifecycle of deep learning model development using the PyTorch framework. It adheres strictly to PyTorch best practices, ensuring that generated code is not only functional but also highly optimized for performance and reproducibility.

## Capabilities
*   **Model Implementation:** Builds modular neural networks using `nn.Module` following industry standards.
*   **Optimization & Performance:** Focuses on optimizing training loops, leveraging GPU acceleration, and implementing efficient data handling via `DataLoader`.
*   **Advanced Features:** Handles custom loss functions, automatic differentiation checks (`autograd`), and hyperparameter tuning strategies.
*   **Validation & Debugging:** Includes robust testing suites, gradient checking, shape verification across layers, and early stopping mechanisms to prevent overfitting.
*   **Output Generation:** Provides well-documented code, comprehensive test files, detailed training logs (including TensorBoard visualization guidance), and suggestions for model enhancements.

## Example Use Cases
*   **Building a CNN:** Requesting the construction of an image classification model from scratch, complete with data loading pipelines and validation checks against CIFAR-10 benchmarks.
*   **Performance Tuning:** Providing existing training code and asking the agent to refactor it for better GPU utilization or suggest architectural improvements based on convergence issues.
*   **Reproducibility:** Generating a full Jupyter notebook tutorial that demonstrates model training, checkpointing, and final evaluation steps for academic reporting.