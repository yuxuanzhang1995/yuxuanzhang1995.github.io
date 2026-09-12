---
layout: page
title: Song–Chen Conjecture 2 at n = 4 — the uniform case
description: A complete proof for uniform weights; the general case reduced to a finite linear program.
date: 2026-06-20
status: partially solved
target: Conjecture 2 of arXiv:2603.25410
pdf: songchen-n4.pdf
---

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/songchen-n4.pdf' | relative_url }}">Full version (PDF)</a></p>

## Background

The spin-alignment conjecture of Alhejji and Knill [2] would, in its strong form, single-letterise
the quantum capacity of platypus-type families — capacities otherwise out of reach, since
regularisation is genuinely needed [4] and non-additivity is generic [3].

Song and Chen [1] refuted the strong form with an explicit *n* = 3 counterexample, and in the same
work isolated a weaker statement — their **Conjecture 2**, a compatible-marginal majorization
inequality — which survives that counterexample and would still serve several of the intended
applications. They prove it at *n* = 3 for the maximally mixed reference with weights on 2-subsets.
The next case is *n* = 4.

## The problem

For a state ρ on four qubits and a weight μ on subsets, let *H* be the Hamiltonian assembled from
the compatible marginals of ρ and let *T* be the reference spectrum. Conjecture 2 asserts that for
every *r*,

> *S<sub>r</sub>*(λ(*H*)) ≤ *S<sub>r</sub>*(*T*),

where *S<sub>r</sub>* is the sum of the *r* largest entries. The inequality is not vacuous: fed the
*n* = 3 counterexample of [1], the same quantity reaches 0.8344… > 5/6.

## Uniform weights

**For uniform μ the inequality holds at *n* = 4, for every *r*.**

The obstruction was one tail inequality previously argued on a grid. Because the slack is *exactly*
zero — attained at the all-zeros vertex — a grid cannot certify it, and the step has to be made
finite and exact.

Writing the spectrum as *d*(*x*) = 1 + ⟨ε(*x*), *u*⟩ with ε ∈ {±1}⁴ and *u* ∈ [0, ½]⁴, the
complementary pairing *d*(*x*) + *d*(*x̄*) = 2 holds exactly, so the sixteen values sort into eight
pair-minima below eight pair-maxima. Each tail sum then becomes a *minimum over which pair to
drop* — piecewise linear on an arrangement with exactly **seventeen vertices**, small enough to
enumerate in exact rationals. All six tail inequalities hold, each meeting its threshold with slack
exactly zero.

Clipping is essential: the naive bound fails, so the vertex enumeration is necessary rather than a
convenience.

## General weights

The linear-programming bound of [2, Thm. 3.2] applies and its validity was confirmed to machine
precision. But the reduction to the target holds only after taking a **minimum over the three
matching-groupings** — any fixed grouping overshoots. That makes the remaining obligation sharper
than it first looked.

## Verification

The search ran on an independently built embedding agreeing with the original to machine zero, with
the detector validated by firing correctly on the *n* = 3 counterexample. Roughly 120k structured
non-uniform weight configurations, a differential-evolution attack on the joint problem in (ρ, μ),
and 60-digit arithmetic on the delicate cases returned no violation.

## What remains open

1. **General weights at *n* = 4.** The LP route is a verified computational lead, not a proof; the
   min-over-groupings requirement is the specific obstacle.
2. **General *n*.** Nothing here is tied to *n* = 4 except the size of the arrangement, which grows
   fast. The complementary pairing is the part worth trying to preserve.
3. **What the conjecture would buy.** Even granting Conjecture 2 in full, the route to a
   single-letter capacity runs through the bridge lemma of [2] — which is false. What survives of
   the original programme deserves restating carefully.

## References

1. Z. Song and L. Chen, *A counterexample to the strong spin alignment conjecture*, [arXiv:2603.25410](https://arxiv.org/abs/2603.25410).
2. M. A. Alhejji and E. Knill, *Towards a resolution of the spin alignment problem*, [arXiv:2307.06894](https://arxiv.org/abs/2307.06894).
3. F. Leditzky, D. Leung, V. Siddhu, G. Smith and J. A. Smolin, *Generic nonadditivity of quantum capacity in simple channels*, [arXiv:2202.08377](https://arxiv.org/abs/2202.08377).
4. T. Cubitt, D. Elkouss, W. Matthews, M. Ozols, D. Pérez-García and S. Strelchuk, *Unbounded number of channel uses are required to see quantum capacity*, [arXiv:1408.5115](https://arxiv.org/abs/1408.5115).
