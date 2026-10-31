---
layout: page
title: "Full-output classical simulation of lossy boson sampling at arbitrary mode density"
description: "A complete internally checked candidate for fixed-transmission, Haar-average simulation, including every collision pattern and finite-bit complexity."
date: "2026-10-31"
permalink: /agentic-research/full-output-lossy-boson-sampling/
status: "complete solution candidate · internally checked"
target: "QIQC Open Problem Zoo · Fully polynomial sampling at constant photon transmission"
---

Yuxuan Zhang · Version 1.1 · 31 October 2026

This manuscript gives a complete solution candidate for the model below. Its proof has undergone internal analytic review and exact small-case checks. Independent expert review and comprehensive priority confirmation remain outstanding.

Download the [manuscript (PDF)]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.1.pdf' | relative_url }}), [source and exact-check supplement]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.1.zip' | relative_url }}), and [version manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.1.json' | relative_url }}).

## The sampling problem

Inject one indistinguishable photon into each of the first $$n$$ inputs of an $$m$$-mode interferometer, with $$m\ge n$$. Each photon survives independently with fixed rational probability $$0<\eta<1$$. Draw the interferometer $$U$$ from Haar measure and measure the full photon-count pattern, including collisions and the vacuum event.

The construction gives a classical randomized sampler whose output law $$q_U$$ satisfies

$$
\mathbb E_{U\sim\mathrm{Haar}}\operatorname{TV}(q_U,p_{\eta,U})\le\varepsilon
$$

in time polynomial in $$n,m,1/\varepsilon$$ and the binary input length. The polynomial's exponent can depend on fixed $$\eta$$. Matrix encoding uses polynomially many bits in $$n,m,\log(1/\varepsilon)$$ and contributes at most $$\varepsilon/2$$ to the error. The proof includes finite random bits and worst-case runtime.

This is the scope of the [QIQC Open Problem Zoo question](https://qiqc-op.com/problem/op_d436ff9fb9cb0ce5/). The guarantee averages over interferometers. Running at mean tolerance $$\varepsilon\delta$$ also gives error at most $$\varepsilon$$ with Haar probability at least $$1-\delta$$, by Markov's inequality, at polynomial cost in $$1/\delta$$.

## Relation to earlier work

The closest simulation result is [Go and Jeong (2026)](https://arxiv.org/html/2610.27065v1). With $$N$$ input photons, $$k$$ fixed survivors and $$M$$ modes, their full-output Corollary 4 assumes both $$M\ge C_0k^2N$$ and $$M\ge C_Bk^2/(\varepsilon\delta)$$. Their Section XI identifies the case of comparable mode and photon counts as an open direction. The present candidate covers every $$m\ge n$$. Its evaluator resolves individual collision outcomes even when collisions cannot be absorbed into an error budget.

Exact Haar methods have substantial antecedents. [Nezami (2021)](https://arxiv.org/abs/2104.06423) computes permanent moments using representation theory. [Arienzo, Grinko, Kliesch and Heinrich (2025)](https://arxiv.org/html/2408.11111v2) provide the operator decomposition and measurement frame used here. [Mhiri et al. (2026)](https://arxiv.org/html/2604.14323v1) express Haar second moments through irreducible projections and study anti-concentration beyond the dilute regime. The contribution proposed here is the loss estimate together with a compatible marginal evaluator that retains collisions and supports efficient sampling.

The manuscript also compares earlier noise and loss simulations, and cites the original color-coding and signed-prefix methods. Its bibliography and the supplement's source comparison identify which ingredients are inherited. These comparisons establish the stated scope differences, while priority relative to all concurrent work remains unsettled.

## How the construction works

Trace-one particle reduction gives a factorial cancellation in the exact Haar harmonic decomposition. Averaging over independent loss then suppresses harmonic degree $$l$$ by $$\eta^l$$. The resulting tail bound is

$$
\mathbb E_U\|p_{\eta,U}-q_{U,r}\|_1
\le\left(\sum_{l=r+1}^{n}\eta^l\right)^{1/2}.
$$

Degree $$r=O_\eta(1+\log(1/\varepsilon))$$ therefore suffices, without a Haar-to-Gaussian approximation.

At degree $$l$$, the evaluator separates modes occupied at least twice from singleton modes. A deficit cutoff limits the heavy supports that must be enumerated; random input and output colors compress the remaining sums. An inverse-determinant coefficient identity keeps the heavy-mode binomial weights, singleton spectators and both harmonic projections. Its cost is polynomial in $$n,m$$ times $$\exp(O(l))$$.

The colors remain fixed throughout each sample, so every queried prefix belongs to one normalized signed law. Clipping and normalizing the child weights gives a probability sampler. A stability estimate handles small prefix probabilities, and explicit precision bounds control matrix rounding and finite-bit random choices.

## How expensive is polynomial time?

The proof's color-average count $$T$$ has accuracy exponent

$$
\beta(\eta)=2+\frac{2\log 9}{\log(1/\eta)}.
$$

Each color collection still requires a collision-support search and finite-ring arithmetic. Unpacking those costs gives the conservative full arithmetic bound

$$
\operatorname{poly}(n,m)\,\widetilde O_\eta(\varepsilon^{-\alpha(\eta)}),
\qquad
\alpha(\eta)=4+\frac{2\log(288e^4)}{\log(1/\eta)}.
$$

The tilde hides powers of $$\log(1/\varepsilon)$$. Section 4.4 of the manuscript derives both estimates.

| Transmission $$\eta$$ | Color count exponent $$\beta$$ | Full arithmetic upper bound $$\alpha$$ |
| --- | ---: | ---: |
| 0.25 | 5.17 | 17.94 |
| 0.50 | 8.34 | 31.88 |
| 0.75 | 17.28 | 71.18 |
| 0.90 | 43.71 | 187.43 |

These exponents are unoptimized upper bounds, not measured runtimes. In particular, the exponents near 8 and 44 count color collections only. Polynomial scaling for each fixed transmission leaves the practical cost, especially near $$\eta=1$$, unresolved.

## Verification and reproduction

The exact checker verifies 329 frame/factorial identities and inequalities, plus eight coefficient cases at degrees 2, 3 and 4. Cases include spectators, full collisions, two heavy modes and an empty input-color class. Removing the spectator factor, second binomial denominator or heavy-mode weights produces discrepancies in 4, 7 and 5 cases respectively.

The checker uses exact rational real and imaginary parts, with a determinant expansion and finite geometric inverse. These tests check sensitive factors in the identities; the all-degree result and bit complexity rest on the analytic proof. The package does not implement or benchmark the full sampler.

To reproduce the checks, extract the supplement and run:

```text
python3 reproduce.py
```

Python 3.10 or later and its standard library suffice. The runner checks payload hashes, executes the comparisons and mutation controls, and compares the results with the included reference. The source, PDF and source comparison are in the supplement.

Derivation, literature comparison, computation, internal review and drafting used AI assistance under human direction. The checker and analytic audit were part of the same research workflow. The website publishes the candidate and its evidence; it does not assign a solved status in the external catalog.

## Version history

Version 1.1 adds the author line, expands the literature comparison, clarifies method attribution, removes internal research labels and derives the explicit accuracy-cost table. The main theorem and exact-check cases are unchanged.

Version 1.0 remains available: [PDF]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.pdf' | relative_url }}), [source and checks]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.zip' | relative_url }}), [manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.json' | relative_url }}).

[Back to the research log]({{ '/agentic-research/' | relative_url }}).
