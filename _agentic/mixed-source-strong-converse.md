---
layout: page
title: An exponential strong converse for general mixed-state quantum compression
description: Below the full Koashi–Imoto entropy, every quantum compression code has exponentially vanishing reference-preserving fidelity.
date: 2026-09-29
status: proof candidate
target: QIQCOP problem op_c9b532d3a7389c77
pdf: mixed-source-strong-converse.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 29 September 2026 (PDF, 8 pages)]({{ '/assets/pdf/agentic/mixed-source-strong-converse.pdf' | relative_url }}) · [LaTeX source, frozen proof, reviews and diagnostic checks (ZIP)]({{ '/assets/code/agentic/mixed-source-strong-converse-source.zip' | relative_url }})

**Compressing below the information that a quantum source must retain causes its fidelity to vanish exponentially.** The manuscript gives a complete proof candidate for [QIQCOP's general mixed-state compression strong converse](https://qiqc-op.com/problem/op_c9b532d3a7389c77/), allowing arbitrary completely positive trace-preserving encoders and decoders.

The original-scope argument passed two distinct frozen AI reviews and finite diagnostic checks. “Proof candidate” records the limits of that verification: external specialist review, priority and catalog acceptance remain unconfirmed. The archival deposit and source-linked QIQC report are being prepared.

## What information must be kept?

A mixed state can contain local randomness that has no bearing on its correlations with the outside world. The Koashi–Imoto decomposition separates this redundant part from a classical sector label and an irredundant quantum system. For the reduced marginal

$$
\tau=\bigoplus_j p_j\tau_j,
$$

the known optimal compression rate is

$$
S(\tau)=H(p)+\sum_j p_jS(\tau_j).
$$

This counts both the sector label and its quantum information. The task is to preserve the source together with its inaccessible reference, not merely to prepare the same local density matrix.

## The result

Fix any finite-dimensional source and a rate $$0\le r<S(\tau)$$. There is a constant $$\gamma>0$$, depending only on that source and rate, such that every blocklength $$n$$ and every code using a memory of dimension at most $$2^{nr}$$ satisfy

$$
F_n\le\min\{1,16e^{-n\gamma}\}.
$$

Here $$F_n$$ is squared fidelity with the original source, including its reference. The code may use arbitrary CPTP maps; the decoder need not be unital. The model provides no free classical side channel or shared entanglement. The theorem does not optimize the error exponent or give a second-order expansion.

## Why the proof needs the actual memory

The proof builds a finite collection of statistical tests from the source. A recent sufficiency theorem shows that these tests retain its whole irredundant algebra. They produce a positive operator whose kernel remembers every classical sector.

The difficult counting step then uses the actual encoder and decoder. An entanglement-only estimate would miss the cost of reproducing a classical label: a perfectly correlated classical state is separable, but its label still consumes memory. Summing over orthogonal sector supports makes that classical cost appear in the bound on memory dimension.

A reference filter and a typical projector turn the resulting memory constraint into an exponentially reliable distinguishing test. The filter can fail to commute with the reference state; the proof keeps that noncommutativity throughout.

## Relation to earlier work

[Koashi and Imoto](https://arxiv.org/abs/quant-ph/0103128) developed the source decomposition. [Khanian and Winter](https://arxiv.org/abs/1912.08506) established the first-order rate in the general reference-preserving model. [Version 2 of Khanian's strong-converse paper](https://arxiv.org/abs/2206.09415v2) proves a converse with an effective-decoder super-unitality restriction.

The principal imported ingredient here is [van Luijk and Wilming's sufficiency theorem](https://arxiv.org/abs/2604.08380v2), specifically Theorem 8.5 and Corollary 8.6. It concerns statistical recovery, not compression. The manuscript combines that theorem with the source decomposition and an encoder–decoder packing argument to remove the decoder restriction. These sources are background references; the linked manuscript reports the present compression claim.

## What was checked

Both frozen reviews examined the same complete mathematical claim. Additional checks tested the multi-sector parent kernel, complex noncommuting filters, and actual finite-dimensional encoder–decoder factorizations. A separate control confirms why a Schmidt-number relaxation cannot charge classical memory correctly. These are diagnostic tests, not a proof of the all-blocklength theorem.

The result emerged in round 54 of the AI-assisted research campaign. The source archive preserves the exact claim and review records, alongside the readable manuscript and the limits of the literature comparison.
