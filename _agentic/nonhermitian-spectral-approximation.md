---
layout: page
title: Low-rank approximation of non-Hermitian operators from spectral entangling strength
description: A dimension-independent operator-norm approximation bound for every alpha below one third, with an optimal rank exponent and no Hermiticity or locality assumption.
date: 2026-11-18
status: Complete proof candidate · sequential internal review
target: Non-Hermitian low-order approximation · Kim et al., discussion following Conjecture 2
pdf: nonhermitian-spectral-approximation-v1.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang · Version 1.0, 18 November 2026**

[Manuscript (PDF)]({{ '/assets/pdf/agentic/nonhermitian-spectral-approximation-v1.pdf' | relative_url }}) · [Source and supplementary checks (ZIP)]({{ '/assets/code/agentic/nonhermitian-spectral-approximation-v1.zip' | relative_url }}) · [Release metadata]({{ '/assets/code/agentic/nonhermitian-spectral-approximation-v1.json' | relative_url }})

If an operator produces a rapidly decaying Schmidt spectrum from every
product input, including inputs with local ancillas, must the operator itself
be approximable by a short sum of product operators?

This manuscript gives a dimension-independent answer for arbitrary complex
operators at sufficiently low spectral order. For every $$0<\alpha<1/3$$,
every operator $$X$$ on finite-dimensional $$A\otimes B$$, and every integer
$$D\geq0$$, it proves

$$
\min_{\operatorname{OSR}(Y)\leq D}\|X-Y\|_{\mathrm{op}}
\leq J_\alpha(X)(D+1)^{-\left(1/(2\alpha)-3/2\right)}.
$$

Here $$\operatorname{OSR}$$ is the number of product operators needed to
write $$Y$$. The strength $$J_\alpha(X)$$ is the largest
$$\ell_{2\alpha}$$ norm of the unnormalized output Schmidt coefficients over
all normalized product inputs with arbitrary local ancillas. Neither the
constant nor the rank exponent depends on the local dimensions.

## What the theorem adds

[Kim et al., *Spectral Small-Incremental Entangling*, PRX 16, 041035
(2026)](https://doi.org/10.1103/8fcr-5tf4) introduce this strength and discuss
its relation to operator approximation. Their published Note added reports
the Hermitian positive result and a non-Hermitian obstruction at
$$\alpha\geq1/3$$. The present proof supplies the positive guarantee for
general non-Hermitian operators throughout $$0<\alpha<1/3$$.

The rank-one obstruction already reported in that source also shows that
the power $$1/(2\alpha)-3/2$$ cannot be increased uniformly. The theorem's
upper constant one is not claimed to be optimal.

**Priority remains unconfirmed.** The source cites an unpublished follow-up
by Kim, Kusunoki and Kuwahara as reference 93. Its complete manuscript was
not found in the public sources checked on 18 November 2026, including the
team's publication and preprint lists. Possible overlap cannot be excluded.
This release makes no claim of being the first solution.

## Why the dimension factor disappears

Truncating the usual operator Schmidt decomposition controls a
Hilbert–Schmidt error. That need not give the desired dimension-independent
operator-norm bound. Instead, the proof chooses local input densities that
maximize the output spectral strength, with a small positive floor on their
eigenvalues. Undoing those input filters gives a tensor decomposition

$$
X=\sum_s\lambda_s A_s\otimes B_s.
$$

First variations of the two input densities bound both weighted column
square sums, $$\sum_s\lambda_s^{2\alpha}A_s^\dagger A_s$$ and
$$\sum_s\lambda_s^{2\alpha}B_s^\dagger B_s$$. A Cauchy–Schwarz estimate
then controls the full operator norm of the discarded terms. The tail
decays precisely when $$\alpha<1/3$$. Finally, a compactness argument removes
the positive floor while preserving the rank bound.

The estimates apply to arbitrary input vectors in the operator norm,
including entangled ones. The derivative calculation also treats repeated
and zero Schmidt coefficients: positive input filters keep the realignment
rank fixed throughout the differentiation.

## Accuracy and scope

For fixed $$\alpha$$, the sufficient rank scales as

$$
D=O_\alpha\!\left((J_\alpha(X)/\epsilon)^{2\alpha/(1-3\alpha)}\right).
$$

For example, the accuracy exponent is $$2/3$$ at $$\alpha=1/6$$,
$$2$$ at $$\alpha=1/4$$, and $$6$$ at $$\alpha=3/10$$.
It diverges as $$\alpha$$ approaches $$1/3$$.

This is an existence and rank theorem. The proof does not give a
polynomial-time method to find the globally maximizing inputs. The
approximant need not be positive, Hermitian, unitary, or a physical channel.
No locality assumption is imposed. The related
[bounded-strength evolution result]({{ '/agentic-research/bounded-se-operator-schmidt-rank/' | relative_url }})
has a different hypothesis and conclusion and is not used in this proof.

## Checks and review status

The source package includes the full LaTeX manuscript, a source comparison,
fixed-seed diagnostics, and a hash-verifying reproduction runner. Extract it
into an empty directory and run `python3 reproduce.py` with NumPy and SciPy
installed; the checks require no network access.

There are 12 complex factorization cases, 24 finite-difference gradient
checks, two local stationarity diagnostics, and eight detected invalid
substitutions. An exact rational control rejects an incorrectly stronger
rank exponent. The local optimizations do not certify global maxima, and
these finite checks do not replace the analytic proof.

The manuscript has received sequential internal proof and source review.
Independent expert review and formal verification have not been performed.
The author directed the research and manuscript preparation. AI assistance
contributed to derivation, literature comparison, computation, checking and
drafting.
