---
layout: "page"
title: "Polynomial critical-distance bounds for weak-field Ising Gibbs preparation"
description: "A proof candidate with a polynomial transverse-field window and explicit near-linear-volume preparation costs approaching the classical critical point."
date: "2026-10-26"
status: "proof candidate · sequential review"
target: "G02 · Actual mixed Gibbs-state preparation on square tori"
pdf: "near-critical-ising-gibbs-preparation.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang · EPFL; Princeton University**

[Manuscript, version 1, 26 October 2026 (PDF, 13 pages)]({{ '/assets/pdf/agentic/near-critical-ising-gibbs-preparation.pdf' | relative_url }}) · [LaTeX source, original target, proof records and audit (ZIP)]({{ '/assets/code/agentic/near-critical-ising-gibbs-preparation-source.zip' | relative_url }})

Can a weak-field Gibbs preparation guarantee remain quantitatively efficient as temperature approaches the classical two-dimensional Ising critical point?

## Result

On the L × L square torus, with N = L², the Hamiltonian is

$$
H(g)=-\frac14\sum_{\langle i,j\rangle}Z_iZ_j-g\sum_iX_i.
$$

Let δ = βc − β > 0, where βc = 2 log(1 + √2), and keep a fixed positive lower bound on β. The candidate theorem gives fixed constants and exponents such that, for |g| ≤ cδᵖ, the actual mixed Gibbs state can be prepared to global trace-distance error ε using at most

$$
CN\max(1,\delta^{-q})[1+\log(N/\varepsilon)]^a\operatorname{poly}(b)
$$

elementary gates and classical bit operations. The input parameters have finite bit length b; ancillary space obeys the same bound. The circuit uses a standard finite universal gate set with arbitrary connectivity.

## What the argument adds

The proof connects classical mixing estimates to an exact doubled-space parent, a quantitative perturbative gap, and a circuit with explicit coefficient access. The global finite-volume remainder annihilates the reference ground state exactly; using the finite-torus reference gap turns it into a relative form bound and removes an unnecessary volume crossover.

The compiler uses connected Pauli paths and pays for growing spatial patches. It assumes no dense matrix oracle, qRAM, free Gibbs input or successful postselection.

The fixed-temperature weak-field baseline is due to [Rouzé–Stilck França](https://arxiv.org/abs/2610.03578). The classical inputs are [Lubetzky–Sly](https://arxiv.org/abs/1001.1613) and [Duminil-Copin–Garban–Pete](https://arxiv.org/abs/1111.0144). Spectral-flow stability and simulation are established methods; the manuscript gives the parameter bookkeeping and explicit access construction needed for the displayed near-critical cost.

## Scope and review

The constants and exponents are conservative, and the allowed field prefactor may be very small. The result concerns a sufficient window below the classical critical inverse temperature, not criticality or the whole quantum phase diagram. It does not prove rapid mixing of an arbitrary natural bath. **It establishes no quantum advantage over general classical sampling algorithms.**

The full manuscript received a **sequential audit by the assembling agent** of the local kernels, classical rate and boundary conventions, perturbation norm, all-volume gap argument, coefficient access and global circuit-error budget. No specific unresolved defect or direct covering theorem was identified in those checks. **Independent review of the complete proof and its novelty remains outstanding.** Publication does not mark G02 independently solved, externally refereed or formally certified.

The source package retains the historical proof stages and records the current corrections, including the attribution of [arXiv:2610.27939](https://arxiv.org/abs/2610.27939) to Xun, Cao and Watanabe.

This paper belongs to the [26 October 2026 two-paper release]({{ '/agentic-research/2026-10-26/' | relative_url }}).

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, checks and scientific writing. The [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and research harness.
