# Pppf Revision Memo

> - Location: Section `Introduction`, pp.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# A) Critical issues

- Location: Section `Introduction`, pp. 1-3. What was wrong: the old draft described “PPPF” as if it were one approximation object rather than a stack of horizon truncation, expectation approximation, local linearization, and localization choices. Why it matters: without that separation, likelihood gaps could not be attributed cleanly and the benchmark risked sounding more definitive than it was. Specific fix: the introduction now defines PPPF as a layered construction and states explicitly that the true kernel, the finite-horizon kernel, the linearized kernel, and the quadrature kernel are distinct objects.

- Location: Section `Nonlinear state-space model`, Table 1, p. 4. What was wrong: the old notation used `x_t` both for the generic latent state and for the NK output gap. Why it matters: the collision made the algorithm and benchmark sections hard to parse and obscured which state the filter actually propagated. Specific fix: the paper now reserves `z_t` for the generic latent state and keeps `x_t` for the NK output gap only.

- Location: Section `Nonlinear state-space model`, eqs. (1)-(3), p. 4. What was wrong: the old manuscript imposed a globally linear measurement equation in the generic exposition and then quietly treated the policy rate differently in the NK benchmark. Why it matters: the paper was implicitly claiming exact conditional Gaussian filtering where the implementation actually uses a moment-projected censored update for the interest-rate measurement. Specific fix: the revised text introduces a generic measurement density first, then a linear-Gaussian special case, and explicitly states that the NK policy-rate measurement is a separate approximation held fixed across ablations.

- Location: Section `From stacked equilibrium conditions to a conditional linear-Gaussian law`, eq. (4), p. 5. What was wrong: the old draft defined the stacked solve without a regime argument and therefore differentiated through a kink-prone object

*[truncated — see source for full prompt]*