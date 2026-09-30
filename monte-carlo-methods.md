# Monte Carlo Methods

**Monte Carlo methods** are a broad family of computational algorithms that rely on repeated random sampling to obtain numerical results. They are used whenever an exact analytic solution is intractable — integrals, expectations, distributions of complex systems, or high-dimensional inference.

## Core Idea

Instead of computing a quantity $I$ exactly, draw $N$ independent random samples from an appropriate distribution and form a sample average that converges to $I$ as $N \to \infty$ (by the law of large numbers). Error typically decreases as $O(1/\sqrt{N})$.

## Main Categories

### 1. Crude / Simple Monte Carlo

Estimate an expectation

$$\mathbb{E}[f(X)] \approx \frac{1}{N}\sum_{i=1}^N f(X_i), \qquad X_i \sim p.$$

Used for integrals, option pricing, reliability analysis, etc.

### 2. Monte Carlo Simulation of Stochastic Processes

Generate many trajectories of a system (e.g., match scorelines under a Poisson or Dixon-Coles model) and examine the empirical distribution of outcomes, totals, or tournament winners.

### 3. Markov Chain Monte Carlo (MCMC)

Construct a Markov chain whose stationary distribution is the target posterior. Classic algorithms:

- Metropolis–Hastings
- Gibbs sampling
- Hamiltonian Monte Carlo (HMC) / NUTS

Widely used for Bayesian inference when the posterior is high-dimensional or non-conjugate (e.g., hierarchical dynamic rating models).

### 4. Sequential Monte Carlo (Particle Filters)

Propagate a set of weighted particles through time to approximate filtering distributions $p(x_t \mid y_{1:t})$.

Natural non-linear / non-Gaussian counterpart to the Kalman filter family discussed earlier.

### 5. Importance Sampling & Variants

Sample from a proposal distribution and re-weight to target the desired distribution. Foundation of many advanced techniques (annealed importance sampling, sequential Monte Carlo, etc.).

## Relevance to the Preceding Topics

### Sports modelling

- Once attack/defence parameters (or a full posterior) are obtained, thousands of match scorelines can be simulated from the Poisson / Dixon-Coles distribution to produce probabilities for 1X2, totals, Asian handicaps, correct scores, or entire tournament trees.
- Monte Carlo evaluation of expected free energy or policy values appears in active-inference formulations.
- Closing-line value and long-run ROI of a betting strategy are themselves estimated by Monte Carlo on historical or bootstrapped data.

### Sequential estimation

- Particle filters extend the Kalman / EKF / UKF ideas to strongly non-linear or non-Gaussian observation models (exact Poisson likelihoods, discrete outcomes, etc.).
- Square-root and ensemble Kalman filters can be viewed as moment-matching or Monte-Carlo-inspired approximations.

### Bayesian dynamic models

- Full posterior sampling over time-varying team strengths is routinely performed with MCMC or sequential Monte Carlo when conjugate structure is abandoned.

## Practical Considerations

- **Variance reduction**: antithetic variates, control variates, stratified sampling, quasi-Monte Carlo (low-discrepancy sequences).
- **Convergence diagnostics**: effective sample size, trace plots, Gelman–Rubin statistic (MCMC), weight degeneracy (particle filters).
- **Computational cost**: embarrassingly parallel for independent simulations; sequential methods require careful resampling strategies.

## Summary

Monte Carlo methods turn probabilistic models into concrete numerical answers by sampling. In the present knowledge chain they serve three complementary roles:

1. Forward simulation of match and tournament outcomes from statistical rating models,
2. Approximate Bayesian inference for complex dynamic or hierarchical models,
3. Non-linear sequential state estimation via particle filters.

They therefore form a natural computational bridge between the generative models (Poisson, Dixon-Coles, state-space) and the practical quantities required for prediction, decision-making, or uncertainty quantification.
