---
layout: "page"
title: "Logarithmic mixing of a Gaussian KMS sampler for weakly interacting hopping fermions"
description: "Logarithmic mixing at each fixed finite temperature for the prescribed sampler, retaining its coherent correction and physical-site couplings."
date: "2026-10-22"
status: "proof candidate"
target: "Weakly interacting hopping fermions and the specified Gaussian KMS generator"
pdf: "hopping-fermion-kms-mixing.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 8 pages)]({{ '/assets/pdf/agentic/hopping-fermion-kms-mixing.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/hopping-fermion-kms-mixing-source.zip' | relative_url }})

Can a spatially coupled free-fermion reference replace an onsite product reference in the perturbative mixing argument for this generator?

## Result

At each fixed finite inverse temperature and fixed geometry/local bounds in dimension at least two, sufficiently small bounded even interactions preserve logarithmic trace-norm mixing from even initial states in system size and inverse error for the specified Gaussian KMS sampler.

## What the argument adds

The proof works with physical-site graded derivatives, a spatial matrix kernel for the free dynamics, and a Volterra perturbation estimate. It keeps the source generator's coherent correction and proves the local continuity needed for a volume-independent perturbative threshold.

[Šmíd, Meister, Berta and Bondesan, the prescribed sampler and prior perturbative setting](https://arxiv.org/html/2510.04954v2). [Current one-dimensional spin-chain comparison, version 2](https://arxiv.org/abs/2610.05848v2). [A different one-dimensional block-Petz generator](https://arxiv.org/html/2610.01190v1).

## Scope and checks

The constants may depend on temperature. This is a result for the named sampler and bounded local class, not a theorem about every Gibbs sampler or arbitrary coupling strength.

The full spatial-kernel, coherent-correction and perturbation arguments received independent review. Two isolated runs of finite CAR and KMS controls passed. The current versions and nearby sampler results were compared at the model level.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
