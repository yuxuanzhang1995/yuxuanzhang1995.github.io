---
layout: page
title: "Full-output classical simulation of lossy boson sampling at arbitrary mode density"
description: "A complete internally checked candidate for fixed-transmission, Haar-average simulation, including every collision pattern and finite-bit complexity."
date: "2026-10-31"
permalink: /agentic-research/full-output-lossy-boson-sampling/
status: "complete solution candidate · internally checked"
target: "Supplied P60 · Full Fock-output simulation at fixed photon transmission"
---

**Research manuscript, version 1.0 · 31 October 2026.** This note accompanies a complete solution candidate for the model below. The proof has undergone internal analytic review and exact small-case checks. **Independent expert review and comprehensive novelty confirmation remain outstanding.**

Download the [full manuscript (PDF)]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.pdf' | relative_url }}), [source and exact-check supplement]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.zip' | relative_url }}), and [version manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.json' | relative_url }}).

## What the candidate establishes

Inject one indistinguishable photon into each of the first $$n$$ inputs of an $$m$$-mode interferometer, with $$m\ge n$$. Each photon survives independently with fixed rational probability $$0<\eta<1$$. The interferometer $$U$$ is drawn from Haar measure. Detect the complete photon-count pattern, including repeated photons in the same mode and the vacuum event.

The candidate constructs a classical randomized sampler whose output law $$q_U$$ satisfies

$$
\mathbb E_{U\sim\mathrm{Haar}}\operatorname{TV}(q_U,p_{\eta,U})\le\varepsilon
$$

in time polynomial in $$n,m,1/\varepsilon$$ and the binary input length. The exponent can depend on fixed $$\eta$$, but not on $$\varepsilon$$. Matrix encoding uses polynomially many bits in $$n,m,\log(1/\varepsilon)$$; its error contribution is at most $$\varepsilon/2$$. Finite random bits and worst-case runtime are included in the manuscript.

This is the supplied P60 statement, matching the [public problem formulation](https://qiqc-op.com/problem/op_d436ff9fb9cb0ce5/). The guarantee averages over interferometers. It does not assert accuracy for every individual interferometer, an efficient limit as transmission approaches one with system size, or a useful practical runtime at current experimental sizes.

## Why the density of modes matters

When there are very many modes, collisions can be rare enough to absorb into an error budget. When the number of modes is comparable to the number of input photons, that shortcut is unavailable. Individual collision outcomes must be represented and sampled.

The closest comparison is Go and Jeong's [constant-fraction-loss simulation algorithm](https://arxiv.org/html/2610.27065v1). Its full Fock-output guarantee uses a dilute-mode condition and a birthday bound; Section XI explicitly identifies saturated-mode full-output simulation as a further direction. The present candidate addresses all $$m\ge n$$ under the stated Haar-average criterion. This checked scope difference supports the proposed extension, without establishing worldwide priority.

## The construction in three steps

**1. Work with the exact Haar harmonic decomposition.** The proof uses the passive-bosonic representation and measurement-frame formulas of [Arienzo, Grinko, Kliesch and Heinrich](https://arxiv.org/html/2408.11111v2). Trace-one particle reduction gives a factorial cancellation. For the loss-conditioned mixture, the remaining high-degree contribution obeys

$$
\mathbb E_U\|p_{\eta,U}-q_{U,r}\|_1
\le\left(\sum_{l=r+1}^{n}\eta^l\right)^{1/2}.
$$

Thus degree $$r=O_\eta(1+\log(1/\varepsilon))$$ suffices. The estimate includes every collision and every survivor number; it does not use a Haar-to-Gaussian approximation.

**2. Resolve collisions in the prefix evaluator.** At harmonic degree $$l$$, separate heavy modes, occupied at least twice, from singleton modes. A deficit cutoff bounds the number of heavy supports that must be enumerated. Input and singleton-output colors compress the remaining sums. An inverse-determinant coefficient identity retains the heavy-mode binomial weights, singleton spectators and both harmonic projections. Its cost is polynomial in $$n,m$$ times $$\exp(O(l))$$.

**3. Sample one consistent signed law.** The fixed color collection defines compatible particle marginals of a single normalized signed distribution. Clipping and normalizing child-prefix weights gives a proper sampler. A stability estimate handles arbitrarily small prefix probabilities, while explicit guard bits control matrix rounding. Finite-bit categorical choices remove the need for ideal exact rational draws.

The representation inputs, color-coding framework, inverse-determinant technique and signed-prefix method have prior sources. The proposed contribution is their exact-Haar, collision-resolving interface at arbitrary mode density.

## What has actually been checked

The manuscript contains the full analytic argument. A newly implemented exact checker verifies 329 frame/factorial identities and inequalities, and eight coefficient cases at degrees 2, 3 and 4. The latter include spectators, full collisions, two heavy modes and an empty input-color class. Deliberately deleting each of three essential factors produces detectable discrepancies.

The arithmetic uses exact rational real and imaginary parts. The checker uses a determinant expansion and finite geometric inverse, distinct from the earlier control's trace-power implementation. These finite checks probe fragile identities; they do not prove the all-size estimates or provide a production sampler. The derivation, checks and review were performed with AI assistance under human direction, by the same root agent.

To reproduce the packaged exact checks, extract the supplement and run:

```text
python3 reproduce.py
```

Python 3.10 or later and its standard library are sufficient. The runner checks file hashes, executes the exact comparisons and mutation controls, and compares the scientific results with the frozen reference. The supplement also includes the manuscript source and the source comparison. It contains no unrelated question bank, conversation or research ledger.

This is a research candidate with visible review limits. Public dissemination does not establish independent acceptance or change an external problem catalog's status.

[Back to the research log]({{ '/agentic-research/' | relative_url }}).
