# Model Acquisition And Cache

> Status: product-direction note for the install surface, cache policy, and safe local execution defaults.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Model Acquisition And Cache

Status: product-direction note for the install surface, cache policy, and safe local execution defaults.

## Purpose

`MLXR` should make model installation feel simple without collapsing three different storage concerns into one blurry "model folder".

Those three layers are:

1. source cache
2. portable artifact store
3. machine-local execution cache

They are related, but they are not the same thing.

## Default Source Behavior

For Hugging Face-backed models, the default user path should reuse the normal Hugging Face cache behavior instead of inventing a second private download cache.

The product default should be:

- resolve the supported model by stable `MLXR` model identity
- fetch source files through the Hugging Face provider
- reuse the user or machine's normal Hugging Face cache when possible
- preserve the resolved revision, license, access state, and remote-code policy in provenance

This keeps `MLXR` compatible with normal open-source expectations:

- `hf auth login` keeps working
- gated model access stays understandable
- users do not need to learn a second download tool before they can generate

## Why PyTorch Names Still Appear

Many upstream Hugging Face bundles use filenames like:

- `diffusion_pytorch_model.safetensors`
- `model.safetensors`
- `pytorch_model.bin`

Those names describe how the source bundle was packaged for the wider ecosystem.

They do not, by themselves, say anything about the runtime `MLXR` uses to execute the model.

In `MLXR`, the important split is:

```text
upstream bundle contract
    !=
runtime execution engine
```

So a file named `diffusion_pytorch_model.safetensors` can still be loaded into a fully owned MLX runtime as long as:

- we know the tensor naming contract
- we know the model config contract
- we map those tensors into our own MLX modules

`safetensors` is just a tensor container format. The filename may be PyTorch-flavored, but the file contents are still just named tensors.

T

*[truncated — see source for full prompt]*