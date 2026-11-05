---
layout: page
title: "The error prefactor for sequential discrimination of trine states"
description: "For three equally likely qubit states, reading and discarding one copy at a time doubles the leading error probability. Both optimal errors decay as 4⁻ᴺ."
date: "2026-11-05"
permalink: /agentic-research/trine-error-prefactor/
status: "research note · internally reviewed"
target: "Geometrically uniform states · the error-ratio formulation of Vienna Problem 31"
pdf: "trine-error-prefactor-v1.1.pdf"
---

Yuxuan Zhang · 5 November 2026 · Version 1.1

A source chooses one of three equally spaced pure qubit states, the *trine*, and sends $$N$$ identical copies. One receiver measures each copy once, discards it and uses the classical outcomes to choose subsequent measurements. A second receiver can hold the copies and measure them together. How much does the first receiver lose?

For both receivers the optimal error falls by about a factor of four with each extra copy. The difference survives in the leading constant. Writing $$P_{\rm seq}$$ and $$P_{\rm coll}$$ for the two minimum error probabilities, respectively, the result is

$$
P_{\rm seq}(N)=4^{-N}+O(16^{-N}),\qquad
P_{\rm coll}(N)=\bigl(\tfrac12+o(1)\bigr)4^{-N}.
$$

Their ratio tends to **two**. This trine therefore gives a counterexample to the claim that the error ratio tends to one for every finite cyclic pure-state orbit. It addresses the ratio interpretation of asymptotic attainment in [Vienna Problem 31](https://oqp.iqoqi.oeaw.ac.at/individual-measurement-strategies-on-geometrically-uniform-states/). The known equality of error exponents for pure states is consistent with this factor. [Nair, Guha and Tan](https://arxiv.org/abs/1212.2048).

### Where the factor comes from

After any first-copy measurement outcome, let $$p_0,p_1,p_2$$ be the probabilities of the three labels. The trine geometry gives $$\sum_j p_j^2\leq 1/2$$. As a result $$\sum_{i<j}p_i p_j\geq 1/4$$, even if the measurement rules out one of the states. The remaining $$N-1$$ copies have pairwise squared overlap $$4^{-(N-1)}$$. Applying Montanaro's fidelity bound with these conditional probabilities gives error at least $$4^{-N}$$, even with a joint measurement on all the remaining copies. [Montanaro, Theorem 1](https://arxiv.org/html/0711.2012).

A receiver can attain that leading coefficient. The antitrine measurement on the first copy eliminates one label and leaves the other two equally likely. Adaptive binary Helstrom measurements on the remaining copies give the upper bound below. For $$t=4^{-N}$$ and every $$N\geq 2$$,

$$
t\leq P_{\rm seq}(N)\leq \frac{1-\sqrt{1-4t}}{2}.
$$

### What earlier work establishes

The collective coefficient of one half follows from a published formula. Chitambar, Duan and Hsieh give the exact collective success in the proof of Theorem 12. Wang, Guo and Zhang obtain the same expression in Eq. (29). They apply a joint unitary to all copies in Eq. (22) and set the probability of unambiguous identification to zero to recover minimum-error discrimination. Expanding either expression gives the coefficient directly. [Chitambar, Duan and Hsieh, Sec. IV-B3](https://arxiv.org/html/1308.1737) · [Wang, Guo and Zhang, Eqs. (22) and (29)](https://doi.org/10.1360/SSPMA-2024-0534).

On the sequential side, the optimal two-copy protocol and the adaptive binary measurement are known. Applying Montanaro's bound after the first outcome gives a lower bound for every sequential receiver and fixes its leading coefficient at one. Wen-Hai Zhang's 2023 publisher abstract describes optimal joint detection. Checking that article for the sequential bound or the factor two still requires the full text. The note makes no priority claim. [Two-copy sequential protocol](https://arxiv.org/abs/1704.01409) · [Adaptive binary measurement](https://arxiv.org/abs/quant-ph/0410097) · [Zhang's 2023 article](https://doi.org/10.1007/s11128-022-03772-7).

The derivation and source review used AI assistance under human direction. Independent expert review remains open.

[Read the paper (PDF)]({{ '/assets/pdf/agentic/trine-error-prefactor-v1.1.pdf' | relative_url }}) · [Source, literature review and exact checks (ZIP)]({{ '/assets/code/agentic/trine-error-prefactor-v1.1.zip' | relative_url }}) · [Version and checksums (JSON)]({{ '/assets/code/agentic/trine-error-prefactor-v1.1.json' | relative_url }})
