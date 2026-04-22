# Fp8

> This module provides a suite of tools to enable FP8 quantization for large language models.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# FP8 Quantization in NeMo RL

This module provides a suite of tools to enable FP8 quantization for large language models. It is currently under active development.

## Supported Features

### FP8 Generation
- Implements **Deepseek-style FP8** quantization using **sub-channel scaling**.

### FP8 Training
- Uses **TransformerEngine** for linear layer implementation.
- Supports both **Deepseek-style sub-channel scaling** and **per-tensor scaling**.

### Recommended recipe
- For Hopper GPUs we recommend to use FP8 (Deepseek-style) precision for both generation and training for best convergence and speedup
- For Blackwell GPUs, FP8 (deepseek-style) with FP32 scaling factor is not supported in training. Currently we recommend to use FP8 precision for generation and BF16 for training. We are actively exploring other recipes for better performance.

## Integration with NeMo RL

NeMo RL applies monkey patches to several core `vLLM` components to enable FP8 generation for reinforcement learning.  
When the `init_fp8` function is called, it modifies the following:

### RayDistributedExecutor
- For multi-GPU inference, the executor is patched to ensure that every worker process applies the same FP8 patches **before model initialization**.

### Quantization Utilities
- Functions within `vllm.model_executor.layers.quantization` are replaced with custom implementations that support:
  - **Power-of-2 scaling**
  - Other custom features

### Weight Loading
- A custom `load_weights` function performs on-the-fly quantization of model weights from higher-precision formats to FP8.


## Usage

FP8 generations are recommended to be configured with the following settings:

   ```
    loss_fn:
        # importance sampling helps improve stability
        use_importance_sampling_correction: true

    policy:
        generation:
            vllm_cfg:
                precision: 'fp8'
                # DeepGemm is much more performant than vLLM's default cutlass fp8 subchannel scaling kernels


*[truncated — see source for full prompt]*