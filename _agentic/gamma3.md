---
layout: page
title: A dimension-free lower bound on γ₃
description: An 8.65% improvement over the published constant — prover round only, not yet adversarially checked.
date: 2026-08-08
status: partially solved (unverified)
target: NPT bound-entanglement distillability, 3-copy endpoint
---

**Target.** The three-copy endpoint of NPT bound-entanglement distillability. The two-copy case
fell in July 2026 to four independent groups, two of them AI-assisted, which moved the live
frontier to three copies. The object is the constant γ₃; the published value is 1/6
([arXiv:2607.24479](https://arxiv.org/abs/2607.24479)).

**Claimed.** γ₃ ≥ (1 + 3<sup>1/3</sup> − 3<sup>2/3</sup>)/2 = 0.181083…, dimension-free — about
**8.65% over the published constant**. The route is a new lemma bounding the three-term sum by
4*N* + *T* through a balanced-frame estimate together with a swap-majorization
*F*₁ + *F*₂ + *F*₃ ≺ 2*I* + *F*₁*F*₂*F*₃, which yields
*q*₃(−*t*) ≥ (1 − 6*t* + 3*t*² − 2*t*³)*N*.

**Separately, the empirics point much higher.** Minimising over rank ≤ 2 gives exactly zero at
every dimension from 2 to 6, with no violation anywhere and the scan strictly positive above −½.
Every equality witness is rank-2 with equal singular values, and most are genuinely three-spread.
That is a clean conjecture: **γ₃ = 1/2, sharp** — which would be the real prize, not the increment
above.

**Status: not verified.** The adversarial round never ran; the workflow died on a usage limit after
the prover. What has been checked by hand: the swap-majorization minimum eigenvalue is exactly zero
at *d* = 2 and 3, the new lemma holds on 12k random rank-2 draws at *d* ≤ 4, the chain bound holds,
and the arithmetic for the constant is exact. That is spot-checking, not adversarial verification,
and on this page that distinction is the whole point. Treat the bound as a lead until the
adversarial pass has run against it.
