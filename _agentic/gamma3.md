---
layout: page
title: A dimension-free lower bound on γ₃
description: An 8.65% improvement over the published constant — prover round only, not yet adversarially checked.
date: 2026-08-08
status: partially solved (unverified)
target: NPT bound-entanglement distillability, 3-copy endpoint
pdf: gamma3.pdf
---

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/gamma3.pdf' | relative_url }}">Full version (PDF)</a></p>

## Background

A state with non-positive partial transpose may still be undistillable — a possibility raised
independently by DiVincenzo, Shor, Smolin, Terhal and Thapliyal [3] and by Dür, Cirac, Lewenstein
and Bruß [4], and unresolved for twenty-five years. It is Problem 5 in the list of Horodecki,
Rudnicki and Życzkowski [2].

In July 2026 the two-copy case fell. Bharti, Gajjala and Haug [1] prove a sharp dimension-free
partial-trace inequality and deduce that a Werner state ρ<sub>α</sub> is two-copy distillable **iff
α < −1/2**, settling Problem 5 at two copies. They also construct explicit constants γ<sub>k</sub>
with α ≥ −γ<sub>k</sub> implying *k*-copy undistillability in every dimension, which moves the live
frontier to three copies.

Worth noting for this page: their own abstract records that the initial proofs were machine-generated
and then verified and rewritten by the authors — the same division of labour as here.

## The problem

Determine the largest γ₃ such that α ≥ −γ₃ implies three-copy undistillability of ρ<sub>α</sub> in
every local dimension. Equivalently, at the endpoint α = −1/2, decide whether the endpoint
partial-trace form *q*₃ is nonnegative on every operator of rank at most two.

The published value is **γ₃ = 1/6** [1]; the two-copy answer is 1/2.

## The bound

The route is a lemma bounding the three-term sum, *A*₁ + *A*₂ + *A*₃ ≤ 4*N* + *T*, from a
balanced-frame estimate together with the swap majorization *F*₁ + *F*₂ + *F*₃ ≺ 2*I* + *F*₁*F*₂*F*₃.
This gives *q*₃(−*t*) ≥ (1 − 6*t* + 3*t*² − 2*t*³)*N*, and the largest root of the cubic yields

> γ₃ ≥ (1 + 3<sup>1/3</sup> − 3<sup>2/3</sup>)/2 = 0.181083…

dimension-free, against the published 1/6 = 0.1666… — an increase of about **8.65%**.

## The empirics point much higher

Minimising *q*₃(−½, ·)/‖*C*‖² over operators of rank at most two returns **exactly zero at
*d* = 2, 3, 4, 5, 6**, with no violation anywhere and the α-scan strictly positive above −½. Every
equality witness is rank-two with equal singular values, and most are genuinely three-spread, with
operator-Schmidt rank four across every cut. That suggests

> γ₃ = 1/2, sharp

matching the two-copy threshold of [1] — that is, **the third copy buys nothing at the endpoint**.
That, rather than the increment above, is the prize.

## Status: not adversarially verified

The verification round did not run; the workflow terminated on a usage limit after the prover pass.
What has been checked by hand: the swap-majorization minimum eigenvalue is exactly zero at
*d* = 2, 3; the lemma holds on 12k random rank-two draws at *d* ≤ 4; the chain bound holds; the
arithmetic for the constant is exact. That is spot-checking, not adversarial verification, and on
this record the distinction is the whole point.

## What remains open

1. **Verify or break the lemma.** The balanced-frame step is the one to attack. If it survives, the
   increment is publishable; if it does not, that is worth recording too.
2. **Prove γ₃ = 1/2.** The evidence is uniform across *d* = 2…6 and the equality witnesses are
   highly structured, which usually means an exact argument exists.
3. **All *k*.** If the third copy buys nothing, the question is whether any finite *k* does — which
   is the original NPT bound-entanglement problem [2,3,4].

## References

1. K. Bharti, R. Gajjala and T. Haug, *Two-copy nondistillability of Werner states: sharp partial-trace inequalities*, [arXiv:2607.24479](https://arxiv.org/abs/2607.24479).
2. P. Horodecki, Ł. Rudnicki and K. Życzkowski, *Five open problems in quantum information*, [arXiv:2002.03233](https://arxiv.org/abs/2002.03233).
3. D. P. DiVincenzo, P. W. Shor, J. A. Smolin, B. M. Terhal and A. V. Thapliyal, *Evidence for bound entangled states with negative partial transpose*, [quant-ph/9910026](https://arxiv.org/abs/quant-ph/9910026).
4. W. Dür, J. I. Cirac, M. Lewenstein and D. Bruß, *Distillability and partial transposition in bipartite systems*, [quant-ph/9910022](https://arxiv.org/abs/quant-ph/9910022).
