---
layout: page
title: "The error prefactor for sequential discrimination of trine states"
description: "For three equally likely qubit states, reading and discarding one copy at a time doubles the leading error probability. Both optimal errors decay as 4⁻ᴺ."
date: "2026-11-05"
permalink: /agentic-research/trine-error-prefactor/
status: "research note · internally reviewed"
target: "Geometrically uniform states · the error-ratio formulation of Vienna Problem 31"
pdf: "trine-error-prefactor-v1.pdf"
---

Yuxuan Zhang · 5 November 2026 · Version 1.0

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

The collective coefficient follows from the exact square-root measurement on the three product states. Earlier work treats the collective trine, optimal sequential discrimination on two copies, and the binary continuation used here. The note combines these results with the first-outcome bound. [Collective trine](https://doi.org/10.1007/s11128-022-03772-7) · [Finite-copy LOCC comparison](https://arxiv.org/abs/1308.1737) · [Two-copy sequential protocol](https://arxiv.org/abs/1704.01409) · [Adaptive binary discrimination](https://arxiv.org/abs/quant-ph/0410097).

The derivation and checks used AI assistance under human direction. Review was internal. The comparison with Wen-Hai Zhang's paper uses the publisher's abstract. Further overlap and independent expert review remain open.

[Read the paper (PDF)]({{ '/assets/pdf/agentic/trine-error-prefactor-v1.pdf' | relative_url }}) · [LaTeX source and exact checks (ZIP)]({{ '/assets/code/agentic/trine-error-prefactor-v1.zip' | relative_url }}) · [Version and checksums (JSON)]({{ '/assets/code/agentic/trine-error-prefactor-v1.json' | relative_url }})
