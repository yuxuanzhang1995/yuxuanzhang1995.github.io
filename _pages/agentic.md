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

<div class="arbox">
Entries are being written up and will appear here shortly.
</div>

<p class="arnote">If you think one of these is wrong, I would like to know — that is rather the
point of putting them somewhere public instead of on arXiv. Write to
<a href="mailto:zhangyx@comp.nus.edu.sg">zhangyx@comp.nus.edu.sg</a>.</p>
