---
layout: page
title: A finite certificate for Gaussian attainment of the Holevo bound
description: A complete proof candidate characterizes equality for arbitrary faithful Gaussian models and constructs an attaining measurement.
date: 2026-09-24
status: proof candidate
target: QIQCOP problem op_8f1853475db7ea27
pdf: gaussian-holevo-criterion.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Full manuscript (PDF)]({{ '/assets/pdf/agentic/gaussian-holevo-criterion.pdf' | relative_url }}) · [Frozen proof, exact examples, reviews and manuscript source (ZIP)]({{ '/assets/code/agentic/gaussian-holevo-criterion-source.zip' | relative_url }})

**A complete proof candidate from round 42.** Two separate internal AI reviews found no mathematical gap. External specialist confirmation and literature priority remain unverified.

For a Gaussian quantum state, the best possible precision bound need not be attainable with Gaussian measurements. Even when the state is simple to describe, the measurement that reaches its Holevo bound may require more than Gaussian ancillas, Gaussian unitaries, and homodyne detection.

The [QIQCOP question](https://qiqc-op.com/problem/op_8f1853475db7ea27/) asks exactly when the optimal single-copy Gaussian-measurement cost $$C_G$$ equals the Holevo bound $$C_H$$. It allows any finite number of modes and parameters, changes in both displacement and covariance, and limiting measurement sequences. The manuscript proposes a necessary-and-sufficient answer for the entire stated class.

## What the answer looks like

The answer is a finite matrix certificate built from the local mean, covariance, their first derivatives, and the weight matrix. It does not require either unknown optimal cost as input.

Write $$m_j=\partial_j d$$, $$D_j=\partial_j V$$, and $$\Gamma=V+i\Omega/2$$. A real symmetric matrix $$G$$ represents the measurement precision. Physical realizability is exactly

$$
G\succeq0,\qquad \Gamma^{-1}-G\succeq0.
$$

The associated classical Fisher matrix is

$$
F_{j\ell}(G)=m_j^{\mathsf T}Gm_\ell+rac12\operatorname{tr}(GD_jGD_\ell).
$$

The rest of the certificate ties the efficient estimator of this measurement to a dual witness for the Holevo problem. It consists of positive-semidefinite conditions and polynomial equations. Theorem 1 of the PDF gives every matrix and every condition explicitly.

If the conditions have a solution, they supply a measurement attaining the bound. If they have no solution, Gaussian measurements have strictly larger cost. The proof also shows that the Gaussian infimum is attained, so the classification includes the limiting sequences allowed in the original question.

This is **implicit semialgebraic feasibility**. Finding a feasible certificate may be difficult. The result claims neither a polynomial-time algorithm nor a short geometric classification.

## Why the proof goes beyond computing the bound

[Chang, Genoni, and Albarelli](https://doi.org/10.1038/s42005-026-02550-6) already reduced the Holevo optimization for Gaussian models to linear and quadratic observables. That finite semidefinite program is a published input to this work. Gaussian attainability for displacement-only models is also [known](https://doi.org/10.1103/PhysRevA.97.012106), as is the [structure of general Gaussian observables](https://doi.org/10.1134/S0081543821020085).

The proposed equality argument combines those ingredients with an explicit description of the efficient Gaussian score. The key step is to require that this particular score, pulled back to system observables, satisfy Holevo dual complementarity. A feasible certificate then proves a global optimum and specifies how to measure it.

The manuscript treats singular precision matrices directly. These include noiseless homodyne directions and can still carry full information about the parameters. The construction uses finitely many ancillary Gaussian modes and does not require an infinitely squeezed ancillary state.

## Checks and status

The frozen symbolic checker verifies two exact certificates: a two-parameter displacement example with common cost $$3$$ and a one-parameter model with both mean and covariance derivatives, attained by homodyne, with common cost $$2/3$$. Both examples were reproduced in two isolated runs for publication. Additional diagnostic controls and their outputs are in the archive.

These checks test specific identities and instances. The all-mode, all-parameter statement rests on the analytic proof, which passed two internal reviews. The result assumes faithful states, nonsingular SLD Fisher information, and a strictly positive weight, exactly as in the original question.

An earlier note on restricted one-mode cases was withdrawn because it did not resolve the full question. This article presents the subsequent general certificate. Novelty and external acceptance remain separate from the internal proof assessment.

The manuscript and proof were prepared with AI assistance. K-Dense's [scientific-writing skill](https://doi.org/10.48550/arXiv.2609.00065) helped organize the evidence and exposition.
