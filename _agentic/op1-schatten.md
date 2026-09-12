---
layout: page
title: Open Problem 1 of Alhejji–Knill is false
description: A counterexample to the word-trace bridge lemma for fractional Schatten norms.
date: 2026-06-17
status: solved (negative)
target: Open Problem 1 of arXiv:2307.06894
pdf: op1-schatten.pdf
---

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/op1-schatten.pdf' | relative_url }}">Full version (PDF)</a></p>

## Background

Quantum capacity is given by a regularised expression, and the regularisation is genuinely
necessary: no finite number of channel uses suffices in general [4], capacity is non-additive even
in very simple channels [3], and the general problem is undecidable [5]. Progress comes from
finding structured families where the regularisation collapses.

The spin-alignment conjecture of Alhejji and Knill [1] is one such route, proved there for integer
Schatten norms, classical states, and two-state mixtures. Carrying it to *all* Schatten norms — and
so, by continuation, to the von Neumann entropy — would give a single-letter quantum capacity for
platypus-type families. Among their concluding remarks is a bridge lemma that would supply exactly
that extension.

## The problem

Let *A*₀, *A*₁, *B*₀, *B*₁ be positive semidefinite with λ(*A*₀) = λ(*B*₀) and λ(*A*₁) = λ(*B*₁),
and write Π<sub>s</sub> for the product along a binary word *s*. Suppose **word-trace dominance**
holds:

> tr Π<sub>s</sub>(*A*) ≥ |tr Π<sub>s</sub>(*B*)| for every word *s*.  (H)

Does it follow that ‖*A*₀ + *A*₁‖<sub>p</sub> ≥ ‖*B*₀ + *B*₁‖<sub>p</sub> for every
*p* ∈ [1, ∞)?  (C)

The hypothesis constrains only *integer* moments; the conclusion is about *fractional* powers of a
spectrum. Whether the former controls the latter is the whole content of the question — and since
it is posed as a question, an instance satisfying (H) and violating (C) settles it.

## A commuting counterexample

**The answer is no.** Take

> *A*₀ = diag(176, 0, 64) · *A*₁ = diag(80, 49, 0) · *B*₀ = diag(64, 176, 0) · *B*₁ = *A*₁

Spectra match and all four are positive semidefinite. Everything commutes, so every word collapses
to a product of powers and (H) reduces to one analytic statement,
(64/176)<sup>k</sup> + (49/80)<sup>m</sup> ≤ 859/880 < 1. The conclusion fails at *p* = 3/2, where
the two spectral sums are **4951 and 5103** — a comparison between integers, with no numerical
tolerance anywhere.

So **the failure is classical**: non-commutativity plays no part in it.

A non-commuting 3×3 instance, found first, fails on the whole interval *p* ∈ (1, *p**) with
*p** = 1.97584…, and a separate argument rules out *d* = 2, making qutrits minimal.

## Verification

Exact rational or 100-digit arithmetic throughout. The 3×3 instance was re-derived from scratch by
an independent agent with its own frame and cone argument, reaching the same resonance constant;
hostile search covered every exact word to length 13 with no violation. The diagonal family came
from a container-isolated run with no network and no sight of the earlier work.

## What remains open

1. **A referee-grade write-up of the 3×3 case.** Every scalar inequality was discharged
   symbolically, so this is a write-up obligation, not a gap — but no one has typeset it as a proof
   a referee could read linearly.
2. **The kernel lemma for the diagonal family**, corroborated on thousands of draws but not yet
   proved symbolically. Since the family commutes this should be routine, and it would make the
   counterexample self-contained on half a page.
3. **The conjecture itself.** This blocks the overlap-lemma route from integer to fractional
   Schatten norms. It does *not* refute spin alignment — in the instance above the *A*-side is not
   aligned — and the weaker compatible-marginal statement of [2] is still open.

## References

1. M. A. Alhejji and E. Knill, *Towards a resolution of the spin alignment problem*, [arXiv:2307.06894](https://arxiv.org/abs/2307.06894).
2. Z. Song and L. Chen, *A counterexample to the strong spin alignment conjecture*, [arXiv:2603.25410](https://arxiv.org/abs/2603.25410).
3. F. Leditzky, D. Leung, V. Siddhu, G. Smith and J. A. Smolin, *Generic nonadditivity of quantum capacity in simple channels*, [arXiv:2202.08377](https://arxiv.org/abs/2202.08377).
4. T. Cubitt, D. Elkouss, W. Matthews, M. Ozols, D. Pérez-García and S. Strelchuk, *Unbounded number of channel uses are required to see quantum capacity*, [arXiv:1408.5115](https://arxiv.org/abs/1408.5115).
5. A. Bhattacharyya, A. Mehta and Y. Zhao, *On the undecidability of quantum channel capacities*, [arXiv:2601.22471](https://arxiv.org/abs/2601.22471).
