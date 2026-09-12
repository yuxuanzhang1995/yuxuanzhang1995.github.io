---
layout: page
title: Song–Chen Conjecture 2 at n = 4 — the uniform case
description: A complete proof for uniform weights; the general case reduced to a finite linear program.
date: 2026-06-20
status: partially solved
target: Conjecture 2 of arXiv:2603.25410
pdf: songchen-n4.pdf
---

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/songchen-n4.pdf' | relative_url }}">Full version (PDF, 2 pp)</a></p>

**Target.** Song and Chen's [arXiv:2603.25410](https://arxiv.org/abs/2603.25410) gives a
counterexample to the strong spin-alignment conjecture, and leaves a weaker statement — their
Conjecture 2, a compatible-marginal majorization inequality — open. They prove it at *n* = 3 with
the maximally mixed reference and weights supported on 2-subsets. We attacked *n* = 4 at the same
reference.

**What was established.** For **uniform weights the inequality now has a complete, rigorous
proof.** For general weights it is reduced to a finite linear program and remains open.

The obstruction was one step that had been argued on a grid, which is not good enough when the
slack is exactly zero — and here it is, at the all-zeros vertex. The fix was to make the step
finite and exact. Writing the relevant spectrum as *d*(*x*) = 1 + ⟨ε(*x*), *u*⟩ with signs
ε ∈ {±1}⁴ and *u* ∈ [0, ½]⁴, the complementary pairing *d*(*x*) + *d*(*x̄*) = 2 holds exactly, so
the sixteen values sort into eight pair-minima below eight pair-maxima. Each tail sum then becomes
a minimum over which pair to drop, which is piecewise linear on an arrangement with only
**seventeen box-vertices** — small enough to enumerate in exact rationals. All six tail
inequalities hold, each meeting its threshold with slack exactly zero.

The naive bound one would reach for first fails: clipping is essential, so the vertex enumeration
is necessary rather than a convenience.

**Verification.** The search for a counterexample was run on an independently built embedding that
reproduced the original to machine zero, and the detector was validated by firing correctly on the
paper's own *n* = 3 counterexample. Roughly 120k structured non-uniform weight configurations, a
differential-evolution attack on the joint problem, and 60-digit arithmetic on the delicate cases
all returned no violation.

**What is still open.** The general-weight case. The linear-programming route works, but only if one
takes the minimum over the three matching-groupings — any single fixed grouping overshoots the
target. So the remaining obligation is sharper than it first looked: show that for every weight and
every state, at least one of the three groupings stays under. That is a verified computational
lead, not a proof.
