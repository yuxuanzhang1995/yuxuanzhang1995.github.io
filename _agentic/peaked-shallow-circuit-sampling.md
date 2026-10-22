---
layout: "page"
title: "Polynomial-time sampling from peaked shallow quantum circuits with arbitrary connectivity"
description: "Global L1 control and a polynomially normalized positive proposal turn peaked-circuit probability estimates into a bounded-time sampler."
date: "2026-10-22"
status: "proof candidate"
target: "Sampling peaked fixed-depth circuits with arbitrary connectivity"
pdf: "peaked-shallow-circuit-sampling.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 9 pages)]({{ '/assets/pdf/agentic/peaked-shallow-circuit-sampling.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/peaked-shallow-circuit-sampling-source.zip' | relative_url }})

Can the point-probability methods for peaked shallow circuits be converted into a polynomial-time sampler without assuming a heavy output string is supplied?

## Result

Fix depth $$d$$ and peak exponent $$k$$. For an n-qubit circuit with arbitrary connectivity, bounded-degree algebraic gate descriptions of bit length $$b$$, and maximum output probability at least $$n^{-k}$$, the algorithm samples within total-variation error $$\varepsilon$$ in $$\operatorname{poly}_{d,k}(n,b)$$ worst-case time whenever $$n^{-k}\leq\varepsilon\leq1/4$$. The heavy string is not given to the algorithm.

## What the argument adds

The cluster and rooted-expansion methods substantially overlap the existing point-probability analysis. The added steps are a global L1 error regrouping and a positive moment envelope with polynomial normalization. Together they support rejection sampling with a deterministic runtime cap and fully charged finite-bit arithmetic.

[Coudron, Gullans, Nelson, Rajakumar and Tan, point-probability evaluation](https://arxiv.org/html/2610.02146v1). [Bravyi, Gosset and Liu, previous peaked-circuit sampling bounds](https://arxiv.org/html/2309.08405v1).

## Scope and checks

Depth and peak exponent are fixed, accuracy is inverse polynomial, and the polynomial exponents can be very large. The statement is an asymptotic complexity result rather than a practical runtime claim or a simulation theorem for arbitrary shallow circuits.

Fresh independent review checked the global error sum, unique proposal representation, invalid-proposal rejection and the precision of acceptance probabilities. Exact finite-circuit and parity-law controls were replayed separately; the asymptotic result comes from the proof.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
