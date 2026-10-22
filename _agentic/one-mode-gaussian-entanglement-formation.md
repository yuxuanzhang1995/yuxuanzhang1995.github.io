---
layout: "page"
title: "Gaussian entanglement of formation for one mode versus finitely many modes"
description: "A rank-two saturation witness reduces finite one-versus-many Gaussian formation to an extractable two-mode affine bound."
date: "2026-10-22"
status: "proof candidate"
target: "Entanglement of formation of generic finite one-mode versus many-mode Gaussian states"
pdf: "one-mode-gaussian-entanglement-formation.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 9 pages)]({{ '/assets/pdf/agentic/one-mode-gaussian-entanglement-formation.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/one-mode-gaussian-entanglement-formation-source.zip' | relative_url }})

Does restricting pure-state decompositions to Gaussian states change entanglement of formation for a generic one-versus-many Gaussian state?

## Result

For every finite-energy bipartite Gaussian state with one mode on one side and any finite number on the other, the paper establishes $$E_F=E_F^{\rm G}$$. The argument allows arbitrary q/p cross-correlations, physical-boundary covariances and unrestricted decomposition measures.

## What the argument adds

The new step is a qualified pure-covariance multiplier argument: its positive multiplier has rank two and yields a saturated EPR witness on one locally extractable mode. Adesso's affine two-mode entropy theorem and the Gaussian covariance-roof formula are imported and attributed. The proof extends beyond the two-mode and bisymmetric cases covered by the checked source.

[Adesso, the imported affine EPR inequality, Theorem 1](https://arxiv.org/html/2608.01909v3). [Wolf and coauthors, the Gaussian covariance roof](https://arxiv.org/abs/quant-ph/0306177v2). [Pure Gaussian mode decomposition](https://arxiv.org/abs/quant-ph/0209026v4).

## Scope and checks

The theorem is finite one-versus-many. It does not assert the general many-versus-many case, additivity or entanglement cost. Whitening is an algebraic proof step, not a local physical operation; the mixed state need not factorize.

Independent review checked the pure-manifold constraint qualification, rank argument, witness parameters, boundary limit and measure-theoretic extension. Exact rational/radical controls probe the algebra. The external affine theorem was checked at its interface and remains an imported theorem.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
