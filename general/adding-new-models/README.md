# Adding New Models

> This guide outlines how to integrate and validate a new model within NeMo RL.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Add New Models

This guide outlines how to integrate and validate a new model within NeMo RL. Each new model must pass a standard set of compatibility tests before being considered ready to be used in RL pipelines. The guide also details diagnostic scripts to help identify and resolve common issues during model integration.

## Importance of Log Probability Consistency in Training and Inference

In on-policy RL, we sample tokens (actions) from the latest version of the policy. This means the sampling distribution of token probabilities produced by the inference framework must closely match those from the training framework. If the inference framework produces significantly different probabilities, we effectively sample from a different distribution, leading to errors in the loss estimation.

As an example, we would see errors in naive KL estimation:

$$\text{KL} = E_{x \sim \pi}[\pi(x) - \pi_{\text{ref}}(x)]$$

When summed/integrated, replacing the $x \sim \pi$ with $x \sim \pi_{\text{wrong}}$ leads to an error of:

$$\sum_{x} \left( \pi(x) - \pi_{\text{ref}}(x) \right) \left( \pi_{\text{wrong}}(x) - \pi(x) \right)$$

So, to verify correctness, we calculate:

$$
\frac{1}{n}\sum_{i=1}^{n\text{(tokens)}}\exp\left(\left\|\text{logprobs-train-fwk}_i - \text{logprobs-inference-fwk}_i\right\|\right)
$$

as a measure of multiplicative probability error for sampled tokens, where samples are drawn as $x \sim \pi_{\text{inference-framework}}$.

Note that this is not exhaustive (the inference framework could lack distribution support and we wouldn't catch it here, as $x \sim \pi_{\text{inference-framework}}$). To get a much stricter guarantee on correctness, you should run this metric twice and average the results, where in the second run, you sample $x \sim \pi_{\text{training-framework}}$. In practice, we use just the former in our tests and find it sufficient.

## Understand Discrepancies Between Backends

When validating models across different backends, you may encounte

*[truncated — see source for full prompt]*