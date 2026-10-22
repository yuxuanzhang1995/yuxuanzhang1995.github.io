---
layout: "page"
title: "A certified memory advantage in four-collision non-Gaussian cooling"
description: "One feasible retained-memory protocol beats a certified lower bound for every reset schedule at the same four-collision budget."
date: "2026-10-22"
status: "proof candidate"
target: "Retained memory versus all allowed reset schedules at total time 4/5"
pdf: "four-collision-memory-cooling.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 7 pages)]({{ '/assets/pdf/agentic/four-collision-memory-cooling.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/four-collision-memory-cooling-source.zip' | relative_url }})

Can retaining a bath mode help beyond every allowed reset schedule when the collision count and total interaction time are fixed?

## Result

At four collisions and total budget $$T=4/5$$, the explicit retained-memory protocol has $$E_{\rm mem}\leq0.259092738049$$, while every allowed reset schedule satisfies $$E_{\rm reset}\geq0.259313063246$$. These are outward certified bounds and establish a strict separation.

## What the argument adds

The comparison is global over the continuous reset domain, rather than against a local numerical optimum. A separate Arb/Acb audit supplies the stronger manuscript bounds using verified eigensystems, direct matrix exponentials, complete interval coverage and the omitted infinite-dimensional tails.

[Png, Hu and Scarani, non-Gaussian collision cooling background](https://arxiv.org/html/2512.10703v2).

## Scope and checks

The memory protocol is a feasible witness. The paper does not claim global optimality within all memory protocols or isolate coherence as the sole cause of the advantage.

The independent arithmetic implementation was reproduced in two clean runs and covers all 14,049 reset leaves. It uses a different computational route from the earlier candidate estimate. The manuscript and source package identify the exact stronger certificate.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
