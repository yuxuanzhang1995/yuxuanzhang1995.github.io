---
layout: "page"
title: "Single-exponential temperature cost for one-dimensional Gibbs preparation"
description: "A fully charged implementation of recursive QBP preparation with exp(Cx³) temperature overhead, near-linear system size, and explicit input-bit costs."
date: "2026-10-22"
status: "proof candidate"
target: "The implementation gap in Rouzé–Stilck França, Remark 3.12"
pdf: "single-exponential-gibbs-preparation.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 13 pages)]({{ '/assets/pdf/agentic/single-exponential-gibbs-preparation.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/single-exponential-gibbs-preparation-source.zip' | relative_url }})

Can the proposed recursive preparation of thermal blocks remove the doubly exponential temperature cost without hiding block purifications, correction oracles or classical compilation?

## Result

For fixed local dimension and interaction range, put $$x=1+\beta J_{\rm int}$$ and $$Q=1+\log(N/\varepsilon)$$. The preparation has trace-distance error at most $$\varepsilon$$ and uses at most $$\exp(Cx^3)N(1+b)^cQ^{Cx+c}$$ elementary gates and classical bit operations, including the expanded circuit. Here $$b$$ records the actual input description lengths. Every random seed has bounded work.

## What the argument adds

Rouzé and Stilck França already propose recursive QBP purification and collective reset encoding. This paper completes their implementation analysis: coherent quantile arithmetic, charged child amplification and inverse circuits, a logarithmically normalized coherent correction, and finite-bit local-update sampling fit into one cost bound.

[Rouzé and Stilck França, Theorem 3.11 and Remark 3.12](https://arxiv.org/html/2610.03578v1). [Kim's one-dimensional block-Petz construction](https://arxiv.org/html/2610.01190v1). [The imported stacked-jump simulator](https://arxiv.org/html/2609.18757v1).

## Scope and checks

The power of the logarithm grows as O(x); a temperature-uniform exponent and the suggested quadratic temperature exponent are not proved. The result is state preparation, with discarded randomness included in the output state. Arbitrarily long binary inputs retain the displayed polynomial bit-cost factor.

Independent review read all five frozen proof stages and the exact source interfaces. Filter, recursive-amplification, correction and global-accounting controls were replayed in clean processes. These are analytic-complexity and finite-mechanism checks, not an end-to-end execution of a large-chain sampler.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
