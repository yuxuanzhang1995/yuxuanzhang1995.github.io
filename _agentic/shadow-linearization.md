---
layout: page
title: Repairing the linearization radius in shadow estimation
description: A published lemma that does not close as printed, and the bound that fixes it.
date: 2026-06-17
status: improved
target: Chen–Li–Liu, arXiv:2407.13874
pdf: shadow-linearization.pdf
---

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/shadow-linearization.pdf' | relative_url }}">Full version (PDF)</a></p>

## Background

Shadow tomography asks for the expectation values of *m* observables on an unknown *d*-dimensional
state to accuracy ε, using as few copies as possible [1]. Classical shadows [2] made it practical,
and the conjectured optimum is Θ(log *m*/ε²) copies with no poly(*d*) overhead.

Chen, Li and Liu [3] prove this in the high-precision regime. Their argument linearizes around the
maximally mixed state, and the linearization is controlled only for ‖*E*‖<sub>F</sub> ≤ (0.01/*t*)⁴,
with the supporting moment lemma in [4]. That fourth power is what confines the result to
ε ≤ *d*⁻¹², and closing the gap down to ε ∼ *d*⁻¹ was the stated open problem.

## The problem

The tail of the linearization error is bounded in [3] by

> Σ<sub>j≥2</sub> 2<sup>j</sup> C(*t*,*j*)² (8*j*)<sup>8j</sup> ‖*E*‖<sup>2j</sup> ≤ (100*t*)⁴‖*E*‖⁴,

valid inside that radius. How large can the radius be made — and is the inequality correct as
printed?

## The lemma does not close as printed

The *j* = 2 term alone exceeds the claimed bound by a factor of order **1.8 × 10¹¹**, and the excess
is independent of ‖*E*‖ — shrinking the radius does not rescue it. So the replacement below
**repairs** the lemma rather than sharpening it, which matters for anyone citing the step.

## The repaired radius

Using the exact identity expressing the operator norm of the *t*-th Haar moment as a maximum of
Schur functions over partitions divided by the dimension of the corresponding irreducible, the
per-term constant collapses and the tail resums under

> ‖*E*‖<sub>F</sub> ≤ 1/(4e*t*)

in place of (0.01/*t*)⁴ — **fourth power to first**, with a better constant besides. Downstream the
precision exponent falls from 12 to 5/2 for balanced and structured observables and to 11/2 in
general, with copy complexity unchanged at *O*(log(1/δ)/ε²).

## Verification, and an exposition slip

The Murnaghan–Nakayama table was rebuilt from scratch and cross-checked against the power-sum and
bialternant formulas; the logical link held on 40k signed traceless spectra; the tail ratio stays
below 0.78 uniformly out to *t* = 5000. Two accounting gaps found adversarially were closed, both
exponent-neutral. One is an exposition slip in [3], where a median bound is used as though it were a
mean — recoverable from an exact Schur–Weyl second moment, so nothing downstream breaks.

## What remains open — and where this now sits

The honest placement matters more than the result. All of this lives *inside* the linearization
framework, and that framework has since been bypassed: Pelecanos, Spilecki and Wright [5] give an
**exactly unbiased** estimator, which has no bias radius to respect, reaches ε ≲ *d*⁻¹ directly, and
disproves the conjectured optimal scaling of [3]. So this entry is of interest for the technique and
for the record on the lemma — not for the state of the art.

Genuinely open: matching **lower** bounds showing [5] optimal across the range, which those authors
conjecture but do not prove; and the low-accuracy regime ε ≳ *d*⁻¹, where the
*d*<sup>2/3</sup>/ε<sup>4/3</sup> term dominates and no lower bound is known.

## References

1. S. Aaronson, *Shadow tomography of quantum states*, [arXiv:1711.01053](https://arxiv.org/abs/1711.01053).
2. H.-Y. Huang, R. Kueng and J. Preskill, *Predicting many properties of a quantum system from very few measurements*, [arXiv:2002.08953](https://arxiv.org/abs/2002.08953).
3. S. Chen, J. Li and A. Liu, *Optimal high-precision shadow estimation*, [arXiv:2407.13874](https://arxiv.org/abs/2407.13874).
4. S. Chen, J. Li and A. Liu, *An optimal tradeoff between entanglement and copy complexity for state tomography*, [arXiv:2402.16353](https://arxiv.org/abs/2402.16353).
5. A. Pelecanos, J. Spilecki and J. Wright, *The debiased Keyl's algorithm: a new unbiased estimator for full state tomography*, [arXiv:2510.07788](https://arxiv.org/abs/2510.07788).
