---
layout: "page"
title: "Geometric convergence of an exact randomized two-excitation cooling channel"
description: "A full infinite-dimensional trace-distance bound for the specified random-time cooling channel, including initial-state tails and work accounting."
date: "2026-10-22"
status: "proof candidate"
target: "Exact random-time two-excitation cooling from the specified thermal initial state"
pdf: "randomized-two-excitation-cooling.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 7 pages)]({{ '/assets/pdf/agentic/randomized-two-excitation-cooling.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/randomized-two-excitation-cooling-source.zip' | relative_url }})

Does the exact infinite-dimensional collision channel converge to the colder thermal state, beyond a short-pulse expansion or a finite numerical truncation?

## Result

For interaction $$H=ab^{\dagger2}+a^\dagger b^2$$, fresh bath state $$\tau_1$$, and uniform collision time in $$[1/100,1/50]$$, the averaged channel obeys $$\frac12\|\Phi^N(\tau_1)-\tau_2\|_1\leq500001\exp[-N/(2\cdot10^{12})]$$. The paper also bounds energy convergence and the second moment on the full Fock space.

## What the argument adds

A downward-transition bound gives a positive gap, random times control possible spectrum near −1, and an explicit initial-tail argument handles a density outside the stationary L² space. The complete state, rather than only low moments, is controlled.

[Png, Hu and Scarani, iterative non-Gaussian cooling](https://arxiv.org/html/2512.10703v2).

## Scope and checks

The constants are conservative and do not establish practical convergence speed. The result concerns this channel and initial state, with an unbounded interaction operator. Averaged-state and history-conditioned gross-work conventions are stated separately.

Fresh independent review checked the infinite-space argument and both work conventions. Exact constant checks, endpoint-moment controls and the separate arithmetic audit accompany the manuscript.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
