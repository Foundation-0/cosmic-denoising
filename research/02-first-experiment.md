# Proposed first experiment: a deliberately narrow null test

**Status: proposal only. No code, training, measurements or cosmological inference yet.**

## Question

Can an explicitly specified diffusion model reproduce the statistics of a simple growing density field, and does it add anything beyond an analytic Gaussian baseline?

This tests a modeling analogy, not whether the universe is a simulation.

## Minimal setup

1. Define a periodic finite grid, a Fourier convention and a synthetic nonnegative initial power spectrum. Do not call it a measured cosmological spectrum.
2. Generate real, mean-zero Gaussian density-contrast fields using recorded seeds and Hermitian-symmetric Fourier coefficients.
3. Apply the simplified linear-growth rule `δ_k(a) = D(a) δ_k(a₀)`, with a declared dimensionless growth factor. This is a restricted test system, not a full gravity solver.
4. Construct a separate, analytically specified Gaussian corruption process and its exact reverse-distribution sampler. Use analytic scores first; no neural network, paid training or downloaded code is needed for this initial null test.
5. Compare the resulting ensembles with a direct Gaussian sampler having the same target covariance.

**Expected limitation:** linear growth preserves Gaussianity and rescales the power spectrum. A covariance-matched Gaussian sampler can already reproduce this endpoint distribution. A denoiser succeeding here is an implementation sanity check, not evidence for a deep cosmological mechanism.

## Declare before running

- Grid size, number of independent seeds, covariance, Fourier normalization, noise schedule and numerical discretization.
- Which axis is scale factor and which is artificial diffusion time. Do not equate them without an explicit mapping.
- Distinct comparisons for (a) endpoint distributions and (b) trajectories from shared initial fields. Matching (a) is not matching (b).
- Metrics: mean and covariance residuals, binned power-spectrum ratios, cross-correlation with the corresponding evolved field, and sensitivity to time-step/grid refinement.
- Numerical tolerances and uncertainty estimation fixed before seeing comparative results; publish all seeds and failed cases.
- A maximum runtime and memory budget suitable for an ordinary local CPU before authorizing execution.

## Ways this can fail usefully

- The reverse sampler misses known Gaussian statistics: numerical or implementation failure.
- Endpoints match but trajectories do not: distributional resemblance, not a demonstrated dynamical equivalence.
- An apparent advantage vanishes against the covariance-matched baseline: no added explanatory value.
- Results depend on relabeling axes or selecting attractive examples: reject the claimed match.

Only after this null test is sound should we consider a nonlinear physical system with appropriate conservation laws and a more demanding baseline. Model selection and extra complexity must be justified by out-of-sample prediction, not visual appeal.

## What would not follow even from success

No evidence of a black-hole computer, dark-matter substrate, simulated consciousness, nested realities or a route to AGI. Those need their own definitions, evidence and tests.

## Stop condition

A reproducible report of the analytic baseline and the sampler's agreement or disagreement is a complete first result. Do not turn this proposal into an open-ended platform or automatically initiate the next experiment.
