---
layout: page
published: false
title: Open Problem 1 of Alhejji–Knill is false
description: A counterexample to the word-trace bridge lemma for fractional Schatten norms.
date: 2026-06-17
status: solved (negative)
target: Open Problem 1 of arXiv:2307.06894
---

**Target.** The first concluding open problem of Alhejji and Knill
([arXiv:2307.06894](https://arxiv.org/abs/2307.06894)). Take positive semidefinite
*A*₀, *A*₁, *B*₀, *B*₁ with λ(*A*₀) = λ(*B*₀) and λ(*A*₁) = λ(*B*₁), and write Π<sub>s</sub> for the
product along a binary word *s*. **If** tr Π<sub>s</sub>(*A*) ≥ |tr Π<sub>s</sub>(*B*)| for every
word, must ‖*A*₀ + *A*₁‖<sub>p</sub> ≥ ‖*B*₀ + *B*₁‖<sub>p</sub> for every *p* ∈ [1, ∞)?

A yes would carry spin-alignment from integer Schatten norms to *all* Schatten norms and to the von
Neumann entropy, which is the bridge to a single-letter quantum capacity for platypus-type channel
families. It is posed as a question, so a hypothesis-satisfying instance that violates the
conclusion settles it.

**The answer is no**, and the cleanest witness is commuting and diagonal:

> *A*₀ = diag(176, 0, 64) · *A*₁ = diag(80, 49, 0) · *B*₀ = diag(64, 176, 0) · *B*₁ = *A*₁

Word dominance is analytic here — every word reduces to (64/176)<sup>k</sup> + (49/80)<sup>m</sup>
≤ 859/880 < 1 — and the conclusion fails in exact integers at *p* = 3/2, where the two spectral
sums are 4951 and 5103. The structural reading is that **the failure of this implication is
classical: non-commutativity is irrelevant to it.**

A separate non-commuting 3×3 instance, found first, fails on the whole interval
*p* ∈ (1, *p**) with *p** = 1.97584…, the endpoints pinned by a Descartes/Laguerre sign argument.
A minimality theorem rules out *d* = 2, so qutrits are the smallest dimension where any of this can
happen.

**Verification.** Everything load-bearing is exact rational or 100-digit arithmetic. The 3×3
instance was re-derived from scratch by an independent agent using its own frame and its own cone
argument, reaching the same resonance constant. Hostile search covered every exact word up to
length 13 and roughly 470k profiles with no violation; the asymptotic family saturates from below
without crossing. The diagonal family came from a container-isolated run with no network and no
access to any of the earlier work, which is about as independent as corroboration gets.

**What is missing.** A human-typeset, referee-grade proof of the all-lengths word-dominance step
for the 3×3 instance — every scalar inequality in it was discharged symbolically, so this is a
write-up obligation rather than a gap. For the diagonal family the kernel lemma is corroborated on
thousands of draws but not yet proved symbolically. One adversarial lens stalled before finishing.
