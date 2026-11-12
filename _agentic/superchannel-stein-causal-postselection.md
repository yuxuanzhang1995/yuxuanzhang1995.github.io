---
layout: page
title: "Causal postselection and the Stein exponent for quantum superchannels"
description: "A proof candidate that general causal interleavings, nested strategies and parallel strategies have the same superchannel Stein exponent, with an exponential strong converse."
date: "2026-11-13T00:00:00+01:00"
permalink: /agentic-research/superchannel-stein-causal-postselection/
status: "Complete proof candidate · sequential internal review"
target: "QIQCOP · Adaptive discrimination of quantum superchannels"
pdf: "superchannel-stein-causal-postselection-v1.pdf"
---

Yuxuan Zhang · 13 November 2026 · Version 1.0

A quantum superchannel transforms one channel into another. Physically, it
has a first component, an accessible channel slot, and a second component
connected to the first by a hidden memory. When many uses are available,
a tester can nest them or interleave their components while respecting
causality. Can this improve the asymptotic discrimination rate?

The proposed theorem says that it cannot in the Stein setting:

$$
\zeta_{\mathrm{general}}
=\zeta_{\mathrm{nested}}
=\zeta_{\mathrm{parallel}}
=D_{\mathrm{sc}}^\infty(\Theta_1\Vert\Theta_2).
$$

It covers every finite-dimensional pair, with arbitrary finite tester
memory and no access to the superchannels' internal memories. At a type-II
rate strictly above the displayed value, the probability of accepting the
null hypothesis tends to zero exponentially.

This is a complete proof candidate with sequential internal analytical
review. Independent expert review and comprehensive priority assessment
remain outstanding.

[Full paper (PDF)]({{ '/assets/pdf/agentic/superchannel-stein-causal-postselection-v1.pdf' | relative_url }})
· [Source, checks and review (ZIP)]({{ '/assets/code/agentic/superchannel-stein-causal-postselection-v1.zip' | relative_url }})
· [Version and SHA-256 metadata]({{ '/assets/code/agentic/superchannel-stein-causal-postselection-v1.json' | relative_url }})

## Two catalogue questions, one result

The [nested-versus-parallel question](https://qiqc-op.com/problem/op_a4600b38b94042a8/)
asks whether nesting improves the vanishing-type-I Stein exponent. The
[general-versus-nested question](https://qiqc-op.com/problem/op_02bb8f8228649ac3/)
also allows the first and second components of different uses to be
interleaved, provided each first component precedes its matched second.

The theorem answers both with the same equality. The nested result is a
corollary, so these are overlapping answers rather than two independent
discoveries. The paper uses precisely this causal access model; it does not
grant the tester access to the hidden memories.

## The causal constraint in the proof

For ordinary channels, positive-slack and postselection methods can turn a
parallel approximation into a bound for more general testers. A superchannel
adds a constraint: its second input cannot affect its first output. A generic
channel approximation on the combined slots need not preserve that constraint.

The first step here gives a polynomial domination of a symmetric joint
two-stage comb by a mixture of tensor powers of physical one-copy combs.
Canonical dilations keep their memory dimensions in tensor-power form and
make the required permutation covariance explicit. Fixed-marginal
postselection is applied at each stage, followed by contraction of the
internal memory legs.

The second step constructs one approximation that works for every parallel
tester. A strategy norm measures its error. Tensor amplification makes the
error exponential, while the causal postselection costs only a fixed-degree
polynomial. Every permitted general tester is normalized on the physical
iid combs in that mixture, which completes the converse.

## What is inherited

[Hirche](https://arxiv.org/html/2103.02404v2) develops the superchannel
strategy classes and parallel rate. The amplification argument is adapted
from [Gao, Ji and Liu](https://arxiv.org/html/2609.27196v1), and the
positive-slack and postselection approach closely parallels
[Zhu and Wang's ordinary-channel theorem](https://arxiv.org/html/2609.30268v1).

The isometry domination uses the fixed-marginal result of
[Nahar and collaborators](https://arxiv.org/html/2403.11851v3).
[Gutoski and Watrous](https://arxiv.org/html/quant-ph/0611234v2) supply the
finite-strategy realization and positive domination duality. These ingredients
are credited to their sources. The proposed extension is their combination
with physical two-stage postselection and the strategy-amplitude norm.

The package distinguishes this finite-n statement from infinite
exchangeability for causal processes and from ordinary-channel marginal
de Finetti results. The specific comparisons support the stated difference;
they do not establish exhaustive priority.

## Review and a corrected detail

Review found that a fixed rank-deficient tester's dual optimization need
not attain its infimum. The package contains a physical qubit-channel
counterexample, including one above the relevant regularized rate. The
paper now keeps an infimum at that step and proves attainment only after
optimizing uniformly over testers. A full-rank tester supplies the needed
compactness, so the theorem's scope is unchanged.

Exact controls also reconstruct the Haar normalization through a permutation
Gram pseudoinverse at two and three qubit copies, including a singular Gram
matrix. Incorrect constants are detected. The all-dimensional claim rests
on the analytic proof, not these finite controls.

An alternative nested-only proof is included in the source package. It uses
the external CP trace-nonincreasing approximation theorem with a success
flag and a uniform limit argument; it is not counted again as a new result.

The author directed the research and workflow. AI systems assisted with
derivation, literature comparison, computation and drafting. This website
release is separate from journal review, archival submission and catalogue
acceptance.
