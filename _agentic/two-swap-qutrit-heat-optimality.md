---
layout: "page"
title: "Certified global heat optimality of two full swaps for a qutrit cooling task"
description: "Two full swaps attain the exact two-collision optimum, against arbitrary allowed unitaries and classical randomization."
date: "2026-10-22"
status: "proof candidate"
target: "The specified two-collision qutrit task, gap range, exact target and work budget"
pdf: "two-swap-qutrit-heat-optimality.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 8 pages)]({{ '/assets/pdf/agentic/two-swap-qutrit-heat-optimality.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/two-swap-qutrit-heat-optimality-source.zip' | relative_url }})

Are the best two full swaps globally optimal when all allowed quantum unitaries and classical randomization are admitted?

## Result

For the task specified in the manuscript, $$Q_*=Q_{\rm swap}=0.4647890802734670691\ldots$$. Full swaps with gaps $$(a_*,2)$$ attain it, where $$a_*=1.4459206660687878334\ldots$$ is the unique root of the displayed analytic equation. Their gross supplied work is $$0.1890623706570403958\ldots<2$$. The decimals describe exact equation-defined quantities.

## What the argument adds

An affine terminal-state witness reduces arbitrary quantum protocols to a finite family of grouped permutations and a certified continuous optimization. Because the witness is affine, it also covers random branches whose individual final states differ from the target but whose unconditioned final state is exact.

[Taranto and coauthors, qubit optimality and swap-path background](https://arxiv.org/html/2404.06649v2).

## Scope and checks

This is an exact result for the prescribed two-collision problem. It does not establish a universal optimal-schedule theorem for qutrits or higher-dimensional machines.

The checker reconstructs all 1,006 remote leaves, the local Hessian certificate and competing branches. Independent review also checked the quantum reduction and used a separately grouped permutation control. A deliberately raised support floor is rejected.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
