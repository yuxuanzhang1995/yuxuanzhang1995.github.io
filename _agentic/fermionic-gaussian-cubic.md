---
layout: page
title: Uniform single-copy tomography of fermionic Gaussian states
description: A complete proof candidate for spectrum-uniform cubic sample complexity, including pure modes and pairing, resolving Rubin's Conjecture 10.1.
date: 2026-10-12
status: proof candidate
target: Rubin Conjecture 10.1 (source-defined follow-up)
pdf: fermionic-gaussian-cubic.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 12 October 2026 (PDF, 10 pages)]({{ '/assets/pdf/agentic/fermionic-gaussian-cubic.pdf' | relative_url }}) · [LaTeX source, frozen arguments and verification records (ZIP)]({{ '/assets/code/agentic/fermionic-gaussian-cubic-source.zip' | relative_url }})

**How many separately measured preparations are needed to reconstruct an unknown fermionic Gaussian state?** This manuscript gives a protocol whose sample count grows cubically with the number of modes, up to logarithmic factors. Its guarantee holds uniformly over mixed states, including states with pure modes and arbitrary pairing. It supplies the upper bound requested in [Rubin's Conjecture 10.1](https://arxiv.org/html/2609.23189v1#S10).

The complete manuscript passed a frozen internal AI review, and three numerical diagnostics reproduced in separate containers. These checks support the proof candidate; they are not external peer review or formal verification. Historical priority has not been established by an exhaustive literature search.

## The guarantee

For any even fermionic Gaussian state $$\rho$$ on $$m\geq1$$ modes and any $$0<\varepsilon\leq1$$, the protocol returns a physical Gaussian estimate $$\widehat\rho$$ with

$$
\Pr\!\left(\|\widehat\rho-\rho\|_1\leq\varepsilon\right)\geq\frac23.
$$

It uses

$$
O\!\left[
\frac{m^3}{\varepsilon}
\log\!\left(24m\left\lceil\log_2\frac{8m}{\varepsilon}\right\rceil\right)
+\frac{m^3}{\varepsilon^2}
\right]
=\widetilde O(m^3/\varepsilon^2)
$$

input copies. Every measurement acts on one preparation and fresh ancillas. Later measurements can depend on earlier classical outcomes; no quantum register persists between preparations. The norm above is the full trace norm, twice the usual trace distance.

The constants do not depend on a purity gap or a known mode basis. Together with Rubin's cubic lower bound in its stated small-error range, this determines the worst-case sample complexity of this measurement model up to logarithmic factors. The lower bound and the resulting separation from collective measurements are credited to the prior work.

## Why the purity boundary matters

A Gaussian state is specified by its two-point correlations, so it is natural to estimate those correlations and reconstruct the state. The difficulty is that the same covariance error can produce very different state errors. Small errors spread over many almost-empty modes can add up to a significant mistake in the reconstructed state.

The protocol first learns a rough mode basis and then refines it at successively smaller scales. Almost-empty or almost-full sectors also have small measurement variance. Using that variance lets the preliminary estimate become sufficiently accurate without paying the cost of uniform absolute precision in every entry.

The final measurements use this estimated basis. A projection in a fixed quantum Fisher metric turns the resulting covariance estimate into a physical state with a controlled trace-norm error. A weak Gaussian attenuation channel handles exactly pure modes. Its extra noise is chosen small enough to stay within the error budget, and it uses fresh ancillas separately for every input copy.

## Relation to previous results

[Bittel, Mele, Eisert and Leone](https://arxiv.org/html/2409.17953v3#S5) gave a computationally efficient single-copy protocol with a general quartic sample bound. [Chen and coauthors](https://arxiv.org/abs/2607.11847v1) established the optimal quadratic rate when joint measurements across copies are available. [Rubin](https://arxiv.org/abs/2609.23189v1) proved the cubic single-copy lower bound and a matching upper bound away from the purity boundary, then asked whether the cubic upper bound holds uniformly.

The contribution here is the uniform upper bound. It combines an adaptive relative covariance estimate with a variance-sensitive conversion to state error. The Gaussian symmetric logarithmic derivative formula used in that conversion is established prior work of [Carollo, Spagnolo and Valenti](https://doi.org/10.3390/e20070485); the manuscript includes its derivation to make the proof self-contained.

This is a complete result for the explicitly selected follow-up conjecture. The earlier [QIQCOP Gaussian-tomography entry](https://qiqc-op.com/problem/op_91c81ca77b99eebf/) concerns the quadratic-copy measurement-resource question already addressed by the cited sources. This release is not counted as another solution of that catalog original.

## Extensions and limits

For an arbitrary parity-even input, the same procedure learns the Gaussian state with the same covariance. It does not reconstruct an arbitrary non-Gaussian state. A relative-entropy promise of near-Gaussianity gives a corresponding robustness bound; the manuscript attributes that notion of robustness to Bittel and coauthors.

The theorem concerns sample complexity. It specifies finite measurements and physical estimates on every history, but does not establish a finite-bit polynomial running time for the convex updates and measurement synthesis. Optimal rates for restricted local detectors and nonadaptive measurements remain separate questions.

## Verification and release

The complete candidate emerged in round 124, using the relative-estimation prerequisite developed in round 123. Rounds 125–126 examined extensions and limits. The 10-page manuscript incorporates the prerequisite proof rather than relying on an unpublished lemma by reference.

The released version received a fresh frozen review of the whole manuscript. Finite checks covered 36 Gaussian Fisher-metric identities, 24 attenuation-channel instances, and 45 matching-estimator instances, each reproduced twice with identical output. These are diagnostics of conventions and formulas; they do not prove the universal theorem. The source package preserves the proof versions, review, source comparison and check scripts.

This is the website release of version 1.0. No Zenodo deposit, QIQC issue update or catalog-status change accompanies this release. The manuscript and the [research-log page]({{ '/agentic-research/' | relative_url }}) state the author and AI contributions.
