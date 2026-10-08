# noise-as-compute

Experiments in computing with noise-driven physical dynamics.

Thermodynamic computing treats noise as a resource: a physical system that relaxes to thermal equilibrium can encode the answer to a computation in the statistics of its fluctuations. This repository collects small, self-contained experiments that explore that idea, from the substrate (what equilibrium dynamics can compute) towards the workloads (which machine-learning operations tolerate or exploit stochastic execution).

## Experiments

| Experiment | What it shows |
|---|---|
| [thermodynamic-matrix-inversion](thermodynamic-matrix-inversion/) ([live demo](https://esbenfthomas.github.io/noise-as-compute/thermodynamic-matrix-inversion/)) | The equilibrium covariance of two noisy, coupled oscillators converges to the inverse of their stiffness matrix, so sampling a thermal equilibrium computes a matrix inverse. Interactive, runs in the browser. |

## Background

- Aifer et al., [Thermodynamic Linear Algebra](https://arxiv.org/abs/2308.05660) (2023)
- Melanson et al., [Thermodynamic computing system for AI applications](https://doi.org/10.1038/s41467-025-59011-x), Nature Communications (arXiv [2312.04836](https://arxiv.org/abs/2312.04836))

## Author

Esben Folger Thomas, Ph.D. in Chemical Physics (Technical University of Denmark).
