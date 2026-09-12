---
layout: page
permalink: /agentic-research/
title: agentic research
description: A dated log of fully AI-generated attacks on known open problems.
nav: true
nav_order: 3
---

<style>
.arbox{border-left:3px solid var(--global-theme-color);background:rgba(128,128,128,.05);
  padding:.7rem 1rem;border-radius:3px;margin:1.6rem 0}
.arlog{list-style:none;padding:0;margin:1.2rem 0 0}
.arlog>li{padding:1.1rem 0;border-bottom:1px solid var(--global-divider-color)}
.arlog>li:last-child{border-bottom:0}
.arhead{display:flex;flex-wrap:wrap;align-items:baseline;gap:.6rem;margin-bottom:.15rem}
.ardate{color:var(--global-text-color-light);font-size:.85rem;letter-spacing:.03em;
  white-space:nowrap;font-variant-numeric:tabular-nums}
.arpill{font-size:.74rem;letter-spacing:.04em;text-transform:uppercase;padding:.1rem .45rem;
  border-radius:3px;border:1px solid var(--global-divider-color);color:var(--global-text-color-light);
  white-space:nowrap}
.arpill-hit{border-color:var(--global-theme-color);color:var(--global-theme-color)}
.artitle{font-weight:600;display:block;margin:.1rem 0}
.arsrc{color:var(--global-text-color-light);font-size:.9rem;display:block;margin-bottom:.45rem}
.arnote{color:var(--global-text-color-light);font-size:.9rem}
</style>

Over the last year I have watched AI systems go from fumbling textbook exercises to closing real
gaps in research mathematics. The question I keep coming back to is how much of that carries into
the problems I actually work on — quantum information, complexity, quantum many-body physics. The
only honest way to find out is to run the experiment.

The tempting way to report it would be to post the results to arXiv. I would rather not. The
literature does not need more machine-written preprints, and a proof no human has read carefully
has no business being cited. So it goes here instead, where it can be looked at without pretending
to be something it is not.

What follows is a dated log of attempts by AI agents on known open problems. **The proofs are
machine-generated end to end.** My own role sits upstream of the writing: I choose the problems,
supply the intuition about where a proof might come from, and design the system that carries it
out — how a claim gets attacked, who plays adversary, what is allowed to count as verified. Once an
attack is running I do not intervene in it.

Failures are logged too. A record that keeps only the hits tells you nothing about the base rate,
and the base rate is the thing I actually want to measure.

<div class="arbox">
<strong>What “verified” means here.</strong> Computer-verified: exact rational arithmetic wherever
the problem allows it, a second agent re-deriving the result from scratch on its own construction,
and an adversarial agent paid to break it. It does not mean refereed. For most entries no human has
typeset a proof you could read in a journal. Read each one as a claim with its working attached,
not as a result.
</div>

## Log

<ul class="arlog">

<li>
<div class="arhead">
  <span class="ardate">19 June 2026</span>
  <span class="arpill arpill-hit">counterexample</span>
</div>
<span class="artitle">Schatten norms of non-integer order</span>
<span class="arsrc">Open Problem 1 of <a href="https://arxiv.org/abs/2307.06894">arXiv:2307.06894</a> (posed as a question)</span>

An explicit 3&times;3 counterexample, in exact rationals. Two pairs of positive semidefinite
matrices with matched spectra and equal trace, for which the Schatten-<em>p</em> inequality reverses
on <em>p</em> &isin; (1, <em>p</em>*), with <em>p</em>* = 1.9758&hellip;. The load-bearing step is a
cone lemma on a family of two-by-two transfer blocks, with a resonance constant
<em>r</em>* = 297499/63112 at which the inequality saturates asymptotically from below without ever
crossing.

<span class="arnote">Corroboration: an independent agent rebuilt the counterexample from scratch
using its own support-projection frame and its own cone argument, and arrived at the same
<em>r</em>*. Hostile search covered roughly 470k profiles and every exact string up to length 13
with no violation. — Caveats: one adversarial lens (Birkhoff/Perron/SOS) stalled before finishing
its heterogeneous-profile hunt, so the gauntlet is not complete; and this refutes one route to the
spin-alignment conjecture, not the conjecture itself.</span>
</li>

<li>
<div class="arhead">
  <span class="ardate">19 June 2026</span>
  <span class="arpill">already solved</span>
</div>
<span class="artitle">Shadow tomography at moderate precision</span>
<span class="arsrc">The gap &epsilon; &isin; [<em>d</em><sup>&minus;12</sup>, <em>d</em><sup>&minus;1</sup>] for general observables, left open by <a href="https://arxiv.org/abs/2407.13874">arXiv:2407.13874</a></span>

The attack turned up the answer in the literature rather than deriving it: the gap was closed by
<a href="https://arxiv.org/abs/2510.07788">arXiv:2510.07788</a>, whose debiased estimator is exactly
unbiased and so never incurs the bias radius that walled off the earlier approach. The agent then
re-verified the mechanism from its own code instead of trusting the write-up — unbiasedness exactly
at one copy and by Monte Carlo at two, the sign structure of the second-moment identity, the
variance bound under adversarial search, and the end-to-end threshold derivation.

<span class="arnote">Logged as a result about novelty rather than about mathematics, which is the
most useful thing a literature-sweeping agent does and the least interesting to write up.</span>
</li>

<li>
<div class="arhead">
  <span class="ardate">19 June 2026</span>
  <span class="arpill">no counterexample</span>
</div>
<span class="artitle">Compatible-marginal majorization at <em>n</em> = 4</span>
<span class="arsrc">Conjecture 2 of <a href="https://arxiv.org/abs/2603.25410">arXiv:2603.25410</a>, at the maximally mixed reference</span>

A triple-optimizer counterexample hunt found nothing for <em>k</em> = 2 and <em>k</em> = 3, with the
worst observed margin around 10<sup>&minus;15</sup>. The <em>k</em> = 3 telescoping step closes, but
the full sum needs a two-body marginal lemma that does not reduce to the one-local argument that
works at <em>n</em> = 3. At <em>k</em> = 2 the telescoping fails outright, so the non-uniform case
needs a genuinely different idea.

<span class="arnote">Still open. Recorded because the shape of what failed is more informative than
the search that found nothing.</span>
</li>

<li>
<div class="arhead">
  <span class="ardate">17 June 2026</span>
  <span class="arpill arpill-hit">improved bound</span>
</div>
<span class="artitle">Precision exponent for shadow tomography</span>
<span class="arsrc">The linearization validity radius in <a href="https://arxiv.org/abs/2407.13874">arXiv:2407.13874</a>, via <a href="https://arxiv.org/abs/2402.16353">arXiv:2402.16353</a></span>

The published argument carries a validity radius with a fourth-power dependence. Working from an
exact Schur-function identity for the relevant Haar moment, the agent showed the constant in that
lemma is enormously slack and replaced the exponent 4 with exponent 1. Downstream this moves the
precision exponent from 12 to 5/2 for balanced and structured observables, and to 11/2 in general,
with the copy count unchanged at <em>O</em>(log(1/&delta;)/&epsilon;<sup>2</sup>).

<span class="arnote">The adversarial agent found two accounting gaps and both were closed, both
exponent-neutral; one of them is an exposition slip in the source paper, where a median bound is
used as if it were a mean. — Caveat: this is a constant-exponent gain deep in the high-precision
regime, and it does not reach the frontier.</span>
</li>

</ul>

<p class="arnote">If you think one of these is wrong, I would like to know — that is rather the
point of putting them somewhere public instead of on arXiv. Write to
<a href="mailto:zhangyx@comp.nus.edu.sg">zhangyx@comp.nus.edu.sg</a>.</p>
