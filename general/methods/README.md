# METHODS

> In this Triton kernel, x_ptr, w_ptr, b_ptr, and y_ptr are raw pointers to GPU memory.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
In this Triton kernel, x_ptr, w_ptr, b_ptr, and y_ptr are raw pointers to GPU memory. They are the “base addresses” of the input matrix X, the weight matrix W, the bias vector b, and the output matrix Y. Triton does not automatically know shapes or layouts from these pointers; it only knows “there is a flat chunk of memory starting here”, so everything else (sizes and strides) tells Triton how to interpret that memory as matrices and vectors.

M, N, and K define the logical sizes of the computation. X is treated as a matrix of shape [M, K], W as [N, K], b as [N], and the output Y as [M, N]. Conceptually, the kernel computes Y = GELU(X @ W^T + b). Here, M is the number of rows of X (often “number of tokens” after flattening batch and sequence), K is the input feature dimension (the reduction dimension in the dot product), and N is the output feature dimension (the number of neurons/out_features). These sizes are also used for boundary masking when a tile goes past the real matrix edge.

The stride arguments (stride_xm, stride_xk, stride_wn, stride_wk, stride_ym, stride_yn) describe the memory layout of each tensor. A 2D tensor is stored as a 1D buffer in memory; strides tell you how many elements you must jump in that 1D buffer when you increment an index in a given dimension. For example, the address of X[m, k] is computed as x_ptr + m * stride_xm + k * stride_xk. Similarly, W[n, k] is located at w_ptr + n * stride_wn + k * stride_wk, and Y[m, n] is stored at y_ptr + m * stride_ym + n * stride_yn. In PyTorch and Triton, these strides are in units of “elements” (not bytes), and they allow the kernel to work correctly even when tensors are views or have non-standard layouts.

The tiling parameters (BM, BN, BK) control how the computation is chunked for performance. Each Triton “program” (roughly analogous to a CUDA thread block) computes one output tile of shape [BM, BN]: BM rows along the M dimension and BN columns along the N dimension. The K dimension is processed 

*[truncated — see source for full prompt]*