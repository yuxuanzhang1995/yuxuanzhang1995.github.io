---
layout: page
title: Repairing the linearization radius in shadow tomography
description: A published lemma that does not close as printed, and the bound that fixes it.
date: 2026-06-17
status: improved
target: Chen–Li–Liu, arXiv:2407.13874
---

**Target.** The linearization argument underlying Chen, Li and Liu's shadow-tomography bounds
([arXiv:2407.13874](https://arxiv.org/abs/2407.13874), with the moment lemma proved in
[arXiv:2402.16353](https://arxiv.org/abs/2402.16353)). The argument is valid only inside a radius
‖*E*‖<sub>F</sub> ≤ (0.01/*t*)⁴, and that fourth power is what confines the whole analysis to very
high precision.

**What was found.** Two things, and the smaller-sounding one is the more serious.

First, **the lemma does not close as printed.** The *j* = 2 term of the tail sum exceeds the stated
(100*t*)⁴ bound by a factor of order 10¹¹, and the failure is independent of the radius — shrinking
‖*E*‖ does not rescue it. So the replacement below repairs the lemma rather than merely sharpening
it.

Second, the constant in the underlying Haar-moment estimate is enormously slack. Working from the
exact identity that expresses the operator norm of the *t*-th moment as a maximum of Schur
functions over partitions divided by the dimension of the corresponding irreducible, the per-term
constant collapses, and the tail resums under

> ‖*E*‖<sub>F</sub> ≤ 1/(4e*t*)

in place of (0.01/*t*)⁴ — **exponent four down to exponent one**, with a better constant besides.
Downstream this moves the precision exponent from 12 to 5/2 for balanced and structured
observables, and to 11/2 in general, with the copy count unchanged at
*O*(log(1/δ)/ε²).

**Verification.** The Murnaghan–Nakayama table was rebuilt from scratch and cross-checked against
both the power-sum and bialternant formulas; the logical link was confirmed on 40k signed traceless
spectra with zero violations; the tail ratio stays below 0.78 uniformly out to *t* = 5000. Two
accounting gaps found by the adversarial pass were closed, both exponent-neutral. One of them is an
exposition slip in the source paper, where a median bound is used as though it were a mean — the
quantity is recoverable by an exact Schur–Weyl second moment, so nothing downstream breaks.

**Honest placement.** All of this lives *inside* the linearization framework, and that framework
was subsequently bypassed: [arXiv:2510.07788](https://arxiv.org/abs/2510.07788) gives an exactly
unbiased estimator, which has no bias radius to respect and reaches ε ≲ *d*⁻¹ directly. So this
entry is of interest for the technique and for the record on the lemma, not for the state of the
art on the problem.
