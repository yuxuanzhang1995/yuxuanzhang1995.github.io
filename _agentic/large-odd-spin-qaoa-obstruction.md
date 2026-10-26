---
layout: "page"
title: "QAOA energy bounds at large interaction order"
description: "A proof candidate for the large odd-order fixed-depth Gaussian obstruction, with a logarithmic-depth bound in the signed sparse model."
date: "2026-10-26"
status: "proof candidate · sequential review"
target: "M26 · Large odd interaction order, deterministic instance-independent QAOA angles"
pdf: "large-odd-spin-qaoa-obstruction.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang · EPFL; Princeton University**

[Manuscript, version 1, 26 October 2026 (PDF, 7 pages)]({{ '/assets/pdf/agentic/large-odd-spin-qaoa-obstruction.pdf' | relative_url }}) · [LaTeX source, original target, proof records and audit (ZIP)]({{ '/assets/code/agentic/large-odd-spin-qaoa-obstruction-source.zip' | relative_url }})

How much positive energy can fixed-depth QAOA obtain in a random spin model when the interaction order becomes large, including odd orders?

## Result

For the ordered Gaussian q-spin model normalized to have variance n at each assignment, the candidate theorem bounds the limiting expected achieved energy per spin by any prescribed positive α once q exceeds a threshold depending only on α. That threshold is independent of the fixed number of QAOA layers. The thermodynamic limit comes before optimization over deterministic, instance-independent angles.

In the signed ordered Poisson hypergraph model, the manuscript also gives a bound of α + n⁻¹⁄⁸ for up to κ log n layers, with fixed q and density and a sufficiently small positive κ.

## What the argument adds

The proof computes the covariance of masked instances at different interpolation times, uses an exact Poisson moment bound, and glues QAOA outputs along a tree while preserving every Born marginal. An elementary metric lemma then selects a forbidden configuration using only m² branches.

Local quantum coupling and concentration are established background in [Chou–Love–Sandhu–Shi](https://arxiv.org/abs/2108.06049). The dense conclusion uses the fixed-depth correspondence of [Basso–Gamarnik–Mei–Zhou](https://arxiv.org/abs/2204.10306). [Mints–Anschuetz](https://arxiv.org/abs/2609.10838) supply related tree/Ramsey methodology for a different quantum model. General odd-order overlap gaps are already known from [Gamarnik–Jagannath–Kızıldağ](https://arxiv.org/abs/2307.07461).

The proposed contribution is the precise mixed-time composition for this signed model. The manuscript does not claim a new general overlap-gap principle or the first logarithmic-depth QAOA obstruction.

## Scope and review

The Gaussian result does not cover q = 3, angles learned from the instance, or logarithmic depth in the dense model. The sparse depth extension is stated separately. Setting all angles to zero gives a zero-energy baseline consistent with the bound; this is a limitation of a specified QAOA family, not of all quantum algorithms.

The full manuscript received a **sequential audit by the assembling agent**. The audit checked the normalization, covariance mask, marginal coupling, tail constants, growing-depth costs and source-theorem quantifiers. No specific unresolved defect or direct covering theorem was identified in those checks. **Independent review of the complete manuscript and its novelty remains outstanding.** Publication is not external peer review, formal proof verification, or acceptance of M26 as solved by a problem catalog.

The source package preserves the earlier arguments and identifies the mixed-time proof that supersedes the older equal-time Ramsey route.

This paper belongs to the [26 October 2026 two-paper release]({{ '/agentic-research/2026-10-26/' | relative_url }}).

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, checks and scientific writing. The [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and research harness.
