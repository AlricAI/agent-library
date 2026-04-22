# Cluster

> This guide explains how to run NeMo RL with Ray on Slurm or Kubernetes.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Set Up Clusters

This guide explains how to run NeMo RL with Ray on Slurm or Kubernetes.

## Use Slurm for Batched and Interactive Jobs

 The following code provides instructions on how to use Slurm to run batched job submissions and run jobs interactively.

### Batched Job Submission

```sh
# Run from the root of NeMo RL repo
NUM_ACTOR_NODES=1  # Total nodes requested (head is colocated on ray-worker-0)

COMMAND="uv run ./examples/run_grpo.py" \
CONTAINER=YOUR_CONTAINER \
MOUNTS="$PWD:$PWD" \
sbatch \
    --nodes=${NUM_ACTOR_NODES} \
    --account=YOUR_ACCOUNT \
    --job-name=YOUR_JOBNAME \
    --partition=YOUR_PARTITION \
    --time=1:0:0 \
    --gres=gpu:8 \
    ray.sub
```

> [!TIP]
> Depending on your Slurm cluster configuration, you may or may not need to include the `--gres=gpu:8` option in the `sbatch` command.

> [!NOTE]
> For GB200 systems with 4 GPUs per node, use `--gres=gpu:4` instead of `--gres=gpu:8`.

Upon successful submission, Slurm will print the `SLURM_JOB_ID`:
```text
Submitted batch job 1980204
```
Make a note of the job submission number. Once the job begins, you can track its process in the driver logs which you can `tail`:
```sh
tail -f 1980204-logs/ray-driver.log
```

### Interactive Launching

> [!TIP]
> A key advantage of running interactively on the head node is the ability to execute multiple multi-node jobs without needing to requeue in the Slurm job queue. This means that during debugging sessions, you can avoid submitting a new `sbatch` command each time. Instead, you can debug and re-submit your NeMo RL job directly from the interactive session.

To run interactively, launch the same command as [Batched Job Submission](#batched-job-submission), but omit the `COMMAND` line:
```sh
# Run from the root of NeMo RL repo
NUM_ACTOR_NODES=1  # Total nodes requested (head is colocated on ray-worker-0)

CONTAINER=YOUR_CONTAINER \
MOUNTS="$PWD:$PWD" \
sbatch \
    --nodes=${NUM_ACTOR_NODES} \
    --account=YOUR_ACCOUNT \
    --job-name=YOUR_

*[truncated — see source for full prompt]*