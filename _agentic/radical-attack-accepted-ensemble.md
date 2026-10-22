---
layout: "page"
title: "A rigorous success regime for the Radical Attack under uniform accepted-instance sampling"
description: "An explicit failure-probability bound that accounts for acceptance bias and constrained code full support."
date: "2026-10-22"
status: "proof candidate"
target: "Radical Attack success for the exact uniform accepted block-matrix ensemble"
pdf: "radical-attack-accepted-ensemble.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 7 pages)]({{ '/assets/pdf/agentic/radical-attack-accepted-ensemble.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/radical-attack-accepted-ensemble-source.zip' | relative_url }})

Under the precisely specified accepted-instance law, how likely is the planted radical subspace to expose every secret row?

## Result

For the manuscript's admissible uniform accepted ensemble, the attack failure probability is at most $$2m_1 2^{-d}+m_1 2^{-w}+2^{1-w}$$ for sufficiently large admissible dimensions and $$w\geq1$$. Here $$d$$ is the doubly-even block dimension and $$w=n-g-m_2$$. It tends to zero when both $$d-\log_2m_1$$ and $$w-\log_2m_1$$ diverge.

## What the argument adds

The attack itself is due to Gross and Hangleiter. This paper derives the accepted lower-block law, quotient lifting multiplicities and the shortening ratios for all relevant quadratic-space types, resolving the full-support estimate without assuming independent code coordinates.

[Gross and Hangleiter, Algorithm 1 and the unresolved constrained-code step](https://arxiv.org/html/2312.10156v2). [Bremner, Cheng and Ji, the modified construction with a different law](https://arxiv.org/html/2308.07152v2).

## Scope and checks

Uniform sampling conditioned on acceptance is essential. The theorem does not identify this law with a sequential generator or the modified sparse construction, and it does not claim a new attack algorithm.

Independent review checked the conditioning, characteristic-two rank identities and all shortening cases. Small-code enumeration and accepted-law controls were replayed twice; the arbitrary-dimension bound is analytic.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
