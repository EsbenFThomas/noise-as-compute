# Two oscillators and a matrix inverse

An interactive demonstration of how the equilibrium covariance of two noisy, coupled oscillators estimates the inverse of their stiffness matrix.

**Live demo:** https://esbenfthomas.github.io/noise-as-compute/thermodynamic-matrix-inversion/

## What it shows

Two masses on springs, coupled to each other and driven by thermal noise, settle into an equilibrium whose displacement covariance is T·K⁻¹, where K is the stiffness matrix. Sampling the equilibrium therefore computes a matrix inverse: the measured covariance converges to the exact inverse as observation time grows, with an error set by how long the dynamics run rather than by the number of recorded points. This is the principle behind thermodynamic linear algebra.

## Run

Open `index.html` in a modern browser. There is no build step, package installation, or internet requirement. All styling and simulation code are included in this one file.

## Explore

- Change the left and right support springs, k₁ and k₂, and the connecting spring, k꜀.
- Compare the exact inverse with the measured covariance.
- Set k꜀ to zero to remove the interaction.
- Use “Collect 900 more time units” to accumulate measurements quickly.
- Use Pause/Run to control the animation. Reduced-motion preferences start it paused.

Changing a spring starts a new measurement. The scatter plot shows the most recent 600 pairs; the covariance uses all samples collected since the parameter change. The dashed ellipse is the theoretical 95% probability region.

## Physics

For displacements x = (x₁, x₂), the potential energy is U = xᵀKx/2, where

```
K = [[k₁ + k꜀, −k꜀],
     [−k꜀, k₂ + k꜀]]
```

The simulated underdamped Langevin equations are

```
dx = v dt
dv = (−Kx − γv) dt + sqrt(2γT) dW
```

Mass, damping γ, and effective temperature T are each 1 in normalized units. The two driving noises are independent. At equilibrium, Cov(x) = T K⁻¹ = K⁻¹.

The simulator diagonalizes the stiffness matrix and uses the exact Gaussian transition for each independent mode at time step 0.03. It discards 60 time units for initial relaxation and then samples every 0.3 time units. Samples are correlated: uncertainty depends on observation time, rather than simply the number of recorded points. Covariance is estimated with online mean and second-moment updates. Matrix error is the relative Frobenius norm.

The moving masses are schematic: their visible displacement is compressed with tanh to keep the drawing legible. The scatter plot and covariance use uncompressed simulated displacements. At a fixed observation time, the covariance is an estimate; its error need not decrease monotonically.

This is a mechanical illustration of the covariance–inverse principle, not a simulation of Normal Computing's exact RLC circuit or CN101 chip. The nonnegative spring arrangement represents a restricted class of symmetric positive-definite matrices.

## Background

- [Thermodynamic Linear Algebra](https://arxiv.org/abs/2308.05660)
- [Thermodynamic computing system for AI applications](https://doi.org/10.1038/s41467-025-59011-x)

The implementation is plain HTML, CSS, and JavaScript; the plots use native SVG. It has no external runtime dependencies.
