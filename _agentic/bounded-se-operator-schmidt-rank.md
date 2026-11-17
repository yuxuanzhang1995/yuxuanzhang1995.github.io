---
layout: page
title: Operator Schmidt rank under bounded spectral entangling strength
description: A squared-logarithmic rank bound for full quantum dynamics at fixed time and operator-norm accuracy, without spatial locality or bounds on local Hamiltonians.
date: 2026-11-17
status: Complete proof candidate · sequential internal review
target: Bounded spectral entangling strength · Kim et al., question after Proposition 9
pdf: bounded-se-operator-schmidt-rank-v1.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang · Version 1.0, 17 November 2026**

[Full manuscript (PDF)]({{ '/assets/pdf/agentic/bounded-se-operator-schmidt-rank-v1.pdf' | relative_url }}) · [Source and supplementary checks (ZIP)]({{ '/assets/code/agentic/bounded-se-operator-schmidt-rank-v1.zip' | relative_url }}) · [Release metadata]({{ '/assets/code/agentic/bounded-se-operator-schmidt-rank-v1.json' | relative_url }})

An interaction may generate little entanglement from every product input,
yet its full time-evolution operator can still require a growing number of
product terms. How fast can that number grow with dimension?

For an arbitrary finite bipartite Hamiltonian

$$
H=H_A\otimes I_B+I_A\otimes H_B+V,
\qquad V=V^*,\qquad \mathcal J(V)\le1,
$$

the manuscript gives an operator-norm approximation satisfying

$$
\left\|e^{-itH}-\widetilde U\right\|\le\epsilon,
\qquad
\operatorname{OSR}(\widetilde U)
\le C_{t,\epsilon}\,[\log(2D)]^2,
\qquad D=d_A d_B.
$$

Here operator Schmidt rank is the number of product operators needed to
write the approximation. The strength $$\mathcal J$$ is the largest sum of
output Schmidt coefficients when the interaction acts on a normalized
product input, including arbitrary local ancillas. Time and accuracy are
fixed independently of dimension. Both local Hamiltonians are arbitrary;
their norms need not be bounded across the family.

This is an existence theorem for approximating the **entire evolution in
operator norm**. It does not provide an efficient algorithm for finding
the factors, and the approximant need not itself be unitary.

## The question it addresses

[Kim et al., *Spectral Small-Incremental Entangling*, published in PRX
16, 041035 (2026)](https://doi.org/10.1103/8fcr-5tf4), show in Proposition 9
that bounded spectral entangling strength does not guarantee a fixed rank
independent of dimension. They then ask whether a fixed-time, fixed-error
approximation can require rank growing as a positive power of $$D$$.

The bound above answers that question negatively: for every fixed
$$c>0$$, $$(\log D)^2=o(D^c)$$. It is compatible with their example,
which rules out constant rank and admits a logarithmic-dimensional
approximation.

## The step that controls dimension

The proof first establishes a uniform approximation theorem for Hermitian
operators. If $$\mathcal J(V)\le1$$, then for every $$\delta>0$$ there is
a nearby operator

$$
W=\sum_s A_s\otimes B_s,
\qquad \|V-W\|\le\delta,
$$

whose four local square sums
$$\sum_s A_s^*A_s$$, $$\sum_s A_sA_s^*$$,
$$\sum_s B_s^*B_s$$, and $$\sum_s B_sB_s^*$$
are all bounded by the same dimension-independent number. One explicit
bound is $$O(\delta^{-4}\log^5(2/\delta))$$.

A theorem of
[Arhancet and Kriegler](https://doi.org/10.24033/msmf.485) supplies a
completely positive dilation controlled in the Hilbert–Schmidt norm.
Positive weights built from its diagonal maps define local dyadic spectral
bands. The proof bounds each pair of bands in two ways: one estimate decays
with the sum of their indices, the other with their difference. Together
they control every direction in the index plane. The tail is summable
without a bound on the weights' condition numbers, which is where
dimension disappears from the approximation error.

The evolution-strength inequality
$$\mathcal J(e^{-itH})\le e^{|t|}$$ is already Corollary 6 of Kim et al.
Applying the new approximation theorem to the two Hermitian parts of the
full unitary gives a balanced tensor decomposition. Correlated Gaussian
local factors then produce unbiased rank-one product samples. Their two
matrix second moments are bounded independently of dimension; clipping and
matrix Bernstein concentration give the squared logarithm.

## Parameters and relation to other results

With $$T=|t|$$, $$q=1+T+\log(1/\epsilon)$$, and $$0<\epsilon\le1$$,
the proof supplies the explicit, nonoptimal form

$$
\operatorname{OSR}(\widetilde U)
\le C e^{10T}\epsilon^{-10}q^{10}
\log(2D)\,[\log(2D)+q].
$$

The universal constant is large. Improving the error dependence and deciding
whether one logarithm always suffices remain quantitative questions.

[Mackay et al., *Optimal low-rank compression of quantum
dynamics*](https://arxiv.org/abs/2609.27497v1) prove stronger compression
results under spatial locality and bounded local-strength assumptions.
The present result instead assumes only the bipartite strength bound.
The $$\alpha<1/2$$ result announced in the Note added of Kim et al.
also has a different hypothesis from the endpoint treated here.

## Supplementary checks and review status

The package includes the complete LaTeX source and two standalone checkers.
Run `python3 reproduce.py` after extracting it into an empty directory.
Python, NumPy, SciPy and SymPy are required; the calculations need no network
connection. The runner verifies file hashes before executing the checks.

The local-band checker runs **374 finite assertions**, using floating-point
matrix controls and a rational large-star reduction. The direct-transfer
checker runs **71 exact assertions**, including finite quadrature for the
Gaussian moment identities and checks of the error constants. The two
checkers detect three and four classes of invalid substitution, respectively.
These checks supplement the analytic proof; they do not certify an
all-dimensional theorem by enumeration.

The manuscript has received sequential internal proof and source review.
Independent expert review and formal verification have not been performed.
The full unpublished work listed as reference 93 of Kim et al. was unavailable
for comparison, and worldwide first-publication priority is not established.
This is a research preprint, with no claim of journal or catalog acceptance.

The author directed the research and manuscript preparation. AI assistance
contributed to derivation, literature comparison, implementation, checking
and drafting.
