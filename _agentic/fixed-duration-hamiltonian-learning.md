---
layout: page
title: Heisenberg-scaling sparse Hamiltonian learning with a fixed minimum query duration
description: A complete proof candidate for learning unknown sparse Pauli interactions at inverse-linear precision cost when every evolution call has a fixed minimum duration.
date: 2026-10-01
status: proof candidate
target: QIQCOP problem op_30954594cf01ebb3
pdf: fixed-duration-hamiltonian-learning.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 1 October 2026 (PDF, 11 pages)]({{ '/assets/pdf/agentic/fixed-duration-hamiltonian-learning.pdf' | relative_url }}) · [LaTeX source, frozen proof and verification records (ZIP)]({{ '/assets/code/agentic/fixed-duration-hamiltonian-learning-source.zip' | relative_url }})

**Can an unknown sparse Hamiltonian be learned efficiently when every experiment must let it evolve for at least a fixed amount of time?** This manuscript gives an affirmative proof candidate for the [complete original question](https://qiqc-op.com/problem/op_30954594cf01ebb3/), including unknown interaction labels and Heisenberg scaling in the desired precision.

The underlying proof and its explicit resource supplement passed two frozen AI reviews. The expanded manuscript was checked against those records. These were internal checks within the same model family; external expert confirmation, exhaustive literature priority and catalog acceptance remain unestablished.

## The guarantee

Consider a traceless Hamiltonian on $$n$$ qubits,

$$
H=\sum_{P\ne I}a_P P,\qquad |\operatorname{supp}(a)|\le m,\qquad
\|H\|_{\mathrm{op}}\le1.
$$

The Pauli labels and coefficients are unknown, and the interactions need not be local. Fix any $$T>0$$ independently of $$n,m,\varepsilon$$. The oracle supplies ordinary forward evolution $$e^{-iHt}$$ only for durations $$t\ge T$$; known controls and ancillas are allowed between calls.

The algorithm returns at most $$m$$ labels, interpreting unlisted coefficients as zero, and achieves

$$
\max_{P\ne I}|\widehat a_P-a_P|\le\varepsilon
$$

with probability at least $$5/6$$. Total unknown evolution time and query count are

$$
\widetilde O_T\!\left(\frac{\operatorname{poly}(m)}{\varepsilon}\right).
$$

Known circuit and classical-processing costs are polynomial in $$n,m,\varepsilon^{-1}$$ on every measurement history. Thus polynomial sparsity gives polynomial costs for every fixed minimum duration. Constants and the initialization polynomial's degree may depend on $$T$$.

This is a minimum-duration guarantee. It allows two programmable durations to differ by a small amount, and does not assume a fixed timing grid. The algorithm uses neither controlled unknown evolution nor an unknown inverse. It does use known interleaved controls, whose gate cost is accounted for separately from unknown evolution time.

## Why two long times help

A coarse learner first samples Pauli labels from long-time Choi states. Polynomial extrapolation shows that every sufficiently large Hamiltonian coefficient appears with inverse-polynomial probability. A two-copy measurement estimates the coefficients without controlling the unknown evolution.

Once a coarse estimate is available, known controls compensate for it. A single long evolution can still hide part of the remaining error because its linear response has spectral zeros. The construction uses two allowed durations separated by one quarter: their response functions have no common zero on the relevant spectral interval.

A filter built from a bounded sum of known unitaries inverts that response after averaging the two experiments. Its normalization is independent of dimension and target precision. Repeating compensated queries then amplifies the residual. Each refinement stage needs only polynomially many experiments in the sparsity; geometrically increasing the repetitions gives inverse-linear precision scaling.

The proof includes filter failures, signed coefficient estimation, finite gate precision, sparse truncation and computation on unsuccessful measurement histories. The conservative refinement bound is $$\widetilde O_T(m^8/\varepsilon)$$. Initialization has a separate polynomial cost, so this expression is not claimed as the full sparsity bound uniformly in $$T$$.

## Relation to prior work

[Hu and coauthors](https://arxiv.org/abs/2502.11900v2) established unknown-support Heisenberg scaling with short-time reshaping. [Shin, Lee and Oh](https://arxiv.org/abs/2604.27838v1) obtained fixed-minimum-duration learning for logarithmic sparsity and a duration–sparsity tradeoff for larger supports. The question here is the polynomial-sparsity, arbitrary-fixed-duration gap stated after their Theorem 2.

[Learning Hamiltonians at Long Times](https://arxiv.org/abs/2606.05690v1) addresses generic local identification of a Hamiltonian direction. [Zhou and Gong's in-situ algorithm](https://arxiv.org/abs/2606.19486v1) uses a control-free model with inverse-quadratic precision dependence. [Shin and Tong's eigenphase-engineering approach](https://arxiv.org/abs/2609.26596v1) uses a step size that decreases logarithmically with precision; its sparse-learning theorem also assumes fixed locality.

The manuscript attributes the inherited learning architecture and compares these precise interfaces. The contribution claimed here is the bounded two-time residual inverse and its implementation for arbitrary unknown sparse support. The checked sources do not supply the same guarantee; this targeted comparison does not establish exhaustive historical novelty.

## Verification and release

The result emerged in round 58 of the author-directed, AI-assisted research campaign. The source download preserves the frozen analytic argument, resource supplement, relevant model-review records and finite diagnostic controls. Those controls test identities and error bounds on specific matrices; the analytic proof carries the universal statement.

This is a website release of version 1.0. It has not been deposited in the manuscript collection on Zenodo or reported as a new QIQC catalog resolution. Human and AI contributions are stated in the manuscript and on the [research-log page]({{ '/agentic-research/' | relative_url }}).
