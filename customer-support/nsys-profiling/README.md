# Nsys Profiling

> NeMo RL supports Nsight profiling for Ray workers through environment variable pattern matching.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Profile GPU with Nsys

NeMo RL supports Nsight profiling for Ray workers through environment variable pattern matching. This allows you to selectively profile specific worker types without modifying code or affecting the performance of workers that don't need profiling.

**Note**: To prevent profile files from becoming too large, consider limiting profiling to a smaller number of steps (e.g., 10 steps).

## Prerequisites

* Install NVIDIA Nsight Systems (`nsys`) on the compute nodes where workers will run. For Ubuntu installation instructions, see the [NVIDIA Nsight Systems Installation Guide](https://docs.nvidia.com/nsight-systems/InstallationGuide/index.html#package-manager-installation).

**Note: If you're using NeMo RL containers, `nsys` is already installed.**

* Ensure the workers you want to profile have GPU access

## Configure the Environment Variables

Set the `NRL_NSYS_WORKER_PATTERNS` environment variable with a comma-separated list of patterns to match worker names:

```bash
export NRL_NSYS_WORKER_PATTERNS="*policy*,*vllm*"
```

Set the `NRL_NSYS_PROFILE_STEP_RANGE` environment variable to control which training steps the profiler captures. Its
format is colon separated integers representing `start:stop`, where `start` is inclusive and `stop` is exclusive
(same as slice syntax `arr[start:stop]`). Note that the `start` is 1-indexed, so `NRL_NSYS_PROFILE_STEP_RANGE=0:10` would error.

```bash
export NRL_NSYS_PROFILE_STEP_RANGE=3:5
```

### Pattern Format

- Use shell-style wildcards (`*`, `?`, `[seq]`, `[!seq]`)
- Patterns are matched against worker names using `fnmatch`
- Multiple patterns are separated by commas
- Whitespace around patterns is automatically stripped
- Empty patterns are ignored

### Supported Workers

The supported worker types are:
- **DTensorPolicyWorker**: Pattern matched against `"dtensor_policy_worker"`
- **VllmGenerationWorker**: Pattern matched against `"vllm_generation_worker"`

## Example Usage

### Profile Only Policy Worker

*[truncated — see source for full prompt]*