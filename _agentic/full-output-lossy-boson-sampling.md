---
layout: page
title: "Lossy boson sampling: an independent derivation"
description: "A small experiment in AI-assisted mathematical research, with proof notes, numerical checks and substantial overlap with earlier work."
date: "2026-11-03"
permalink: /agentic-research/full-output-lossy-boson-sampling/
status: "independent derivation · reproducibility notes"
target: "Research experiment · proof and reproducibility notes"
---

Yuxuan Zhang · 3 November 2026

This started as an experiment in AI-assisted mathematical research: how far could we get with lossy boson sampling by working through the proofs and checking the calculations?

We independently arrived at results that substantially overlap with [Youngrong Lim's *Boson sampling is fragile to loss*](https://arxiv.org/abs/2611.01434), which we found later in the project. I am keeping the derivations and reproducibility material here as a record of the exercise. The earlier novelty assessment on this page was incomplete; no new resolution is claimed.

## The mathematical idea

Photon loss suppresses contributions involving many interfering photons. If the remaining low-order terms can be evaluated efficiently, they give a classical approximation to the output distribution.

The nicest calculation in these notes uses exact Haar averages: large output-space dimension factors cancel, so the error bound survives even when photons frequently collide in the same mode. The resulting statements cover:

- **Single-photon inputs:** any number of modes at least as large as the input photon count, including every output collision pattern.
- **Gaussian inputs:** identical squeezing in every mode, again keeping the complete photon-count distribution.

For fixed transmission strictly between zero and one, the samplers have polynomial complexity in system size and inverse accuracy, with error measured in total variation averaged over Haar-random interferometers. The Gaussian statement also fixes the squeezing. The polynomial degrees can be large, so this is an asymptotic result rather than a practical simulation benchmark.

The notes also spell out fixed-survivor and exchangeable-loss corollaries, independent nonuniform input loss, and loss–accuracy dependence. These are retained as explicit consequences and proof details, without a separate novelty claim.

## Where it fits

Lim's Theorems 1–2 cover the main guarantees; Appendix F.2 gives the same nonuniform-input thinning reduction. Our signed-prefix sampling construction differs from his bounded-rejection construction, but we have not established a complexity advantage.

The public chronology is now checked: Lim's [Zenodo deposit](https://zenodo.org/records/23528696) dates to **21 October 2026**; our [first Fock-only website release](https://github.com/yuxuanzhang1995/yuxuanzhang1995.github.io/actions/runs/41229200308) was **31 October**; his arXiv submission followed on **1 November**. Our website preceded the arXiv submission, but the Zenodo manuscript was already public.

## Proofs and checks

The archive contains the proofs, source files, exact algebra checks, and small-system Haar tests: 1,536 Fock-input interferometers and 512 conditional Gaussian pair-state interferometers. These tests examine the harmonic approximations; they do not benchmark an implementation of the all-size sampler. The work used AI assistance under human direction and has had internal review, with independent expert review still outstanding.

Download the [technical notes (v2.1 PDF)]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v2.1.pdf' | relative_url }}), [source, checks and data]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.1.zip' | relative_url }}), or [release manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.1.json' | relative_url }}). After extracting the source archive, run `python3 reproduce.py` with Python 3.10 or later, NumPy and SymPy.

Those files are the frozen 3 November technical release. The verified Zenodo chronology above supersedes the PDF's earlier note that the deposit date had not yet been checked. Earlier PDFs remain available for the record: [v2.0]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v2.0.pdf' | relative_url }}), [v1.1]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.1.pdf' | relative_url }}) and [v1.0]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.pdf' | relative_url }}); their novelty discussions are superseded by this page.

[Back to the research log]({{ '/agentic-research/' | relative_url }}).
