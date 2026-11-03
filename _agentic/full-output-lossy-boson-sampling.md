---
layout: page
title: "Full-output classical simulation of lossy boson sampling with single-photon and equal-squeezing inputs"
description: "Two internally checked theorem candidates: dense Fock-input sampling and all-mode equal-squeezing Gaussian sampling at fixed loss, with full-output Haar-average guarantees."
date: "2026-11-03"
permalink: /agentic-research/full-output-lossy-boson-sampling/
status: "research manuscript · internally checked"
target: "QIQC Open Problem Zoo · Constant-transmission sampling, with a Gaussian extension"
---

Yuxuan Zhang · Version 2.0 · 3 November 2026

This version adds a Gaussian boson-sampling theorem to the original Fock-input result. When **every mode is equally squeezed** and transmission is fixed below one, the construction samples the complete photon-count distribution to Haar-average total variation error $$\varepsilon$$ in polynomial time. The mean number of surviving photons can grow linearly with the number of modes.

The manuscript has undergone internal proof review and computational checks. Independent expert review and comprehensive priority confirmation remain outstanding.

Download the [manuscript (PDF)]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v2.0.pdf' | relative_url }}), [source, checks and numerical data]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.0.zip' | relative_url }}), and [release manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.0.json' | relative_url }}).

## Two input models

Both theorems include vacuum, every collision pattern and the complete output photon count. For a Haar-random passive interferometer $$U$$, the algorithm's law $$q_U$$ satisfies

$$
\mathbb E_U\operatorname{TV}(q_U,p_U)\le\varepsilon.
$$

| Model | Input and loss assumptions | Guarantee |
| --- | --- | --- |
| Single-photon Fock inputs | One photon in each of $$n$$ inputs, every $$m\ge n$$, fixed rational survival probability $$0<\eta<1$$ | Worst-case bit complexity polynomial in $$n,m,1/\varepsilon$$ and input length |
| Equal-squeezing Gaussian inputs | Every one of the $$m$$ modes squeezed identically, fixed rational $$\zeta=\tanh^2 s\in(0,1)$$ and fixed rational $$\eta\in(0,1)$$ | Worst-case bit complexity polynomial in $$m,1/\varepsilon$$ and input length; mean detected photons $$m\eta\zeta/(1-\zeta)$$ |

The polynomial degrees may depend on the fixed physical parameters. Matrix precision and finite random bits are included in the proofs. The Gaussian theorem does not include extra vacuum inputs or unequal squeezing, and neither theorem gives an error guarantee for every deterministic interferometer. These are two distinct input families.

The Fock theorem covers the formulation in the [QIQC Open Problem Zoo](https://qiqc-op.com/problem/op_d436ff9fb9cb0ce5/). The Gaussian theorem is an additional restricted result, not another resolution of that catalog question. Running either algorithm at mean tolerance $$\varepsilon\delta$$ also gives TV at most $$\varepsilon$$ with Haar probability at least $$1-\delta$$, by Markov's inequality.

## What changed mathematically

For Fock inputs, exact particle reduction and the Haar measurement frame cancel the output-dimension factors. Independent loss then gives

$$
\mathbb E_U\|p_{\eta,U}-q_{U,r}\|_1
\le\left(\sum_{l=r+1}^{n}\eta^l\right)^{1/2}.
$$

This permits logarithmic harmonic truncation without a dilute-mode approximation. A collision-stratified permanent evaluator computes compatible marginals in time exponential only in the retained degree.

The Gaussian proof needs a different input estimate. Its fixed-number components are invariant pair states, proportional to

$$
\left(\sum_i(a_i^\dagger)^2\right)^{N/2}\lvert0\rangle.
$$

We derive their reduced-state spectrum and all-order harmonic norms. On a typical loss sector, their exact Haar error weights obey a geometric bound $$A_l\le\rho_{\star}^l$$ with $$\rho_{\star}<1$$ depending only on the fixed parameters. Explicit photon-number tails and a separate small-photon branch cover the remaining sectors.

A hafnian generating identity then evaluates the Gaussian marginals. The same collision cutoff and singleton color coding keep the cost exponential only in the logarithmic truncation order. Clipped-prefix sampling produces a proper probability law. The final proof controls matrix rounding in both branches, including the small-photon branch where raw rounded formulas need not remain consistent.

## Comparison with prior work

[Go and Jeong](https://arxiv.org/html/2610.27065v1), Corollary 4, give full-output Fock simulation under mode restrictions $$M\ge C_0k^2N$$ and $$M\ge C_Bk^2/(\varepsilon\delta)$$. The Fock theorem here allows every $$m\ge n$$. Their color-coding, inverse-determinant and signed-prefix framework is an important antecedent.

For Gaussian inputs, [Lim](https://arxiv.org/html/2610.06526v1) proves a guarantee for every interferometer, with TV $$O(N\eta^3)$$ and a separate equal-squeezing pair construction reaching $$N^{3/4}$$ mean survivors at fixed accuracy. Our restricted theorem permits a linear mean surviving count at fixed transmission, using Haar averaging. It does not improve the all-interferometer guarantee.

Exact Haar representation methods and the measurement frame are credited to [Nezami](https://arxiv.org/abs/2104.06423), [Arienzo et al.](https://arxiv.org/html/2408.11111v2) and related work. The expanded bibliography also compares [Umanskii–Rubtsov](https://arxiv.org/html/2404.01004v1), [Oh et al.](https://arxiv.org/abs/2306.03709v2), [Renema](https://arxiv.org/abs/1911.10112v1), [Dodd et al.](https://arxiv.org/html/2511.14923v1) and [Liu et al.](https://arxiv.org/html/2512.10643v2). The source supplement records the checked statements and their different assumptions. No equivalent complete restricted theorem was found in that comparison; it does not establish worldwide priority.

## Loss, precision and cost

The Fock construction has a uniform parameter bound. With $$s=1-\eta$$ and $$A=288e^4$$, it uses at most

$$
P(n,m,L_\eta,L_\varepsilon)\,\varepsilon^{-4}s^{-1}A^r,
\qquad
r=\min\!\left\{n,\left\lceil\frac{\log(64/(\varepsilon^2s))}{-\log\eta}\right\rceil\right\},
$$

bit operations, for one polynomial $$P$$ independent of $$\eta,\varepsilon$$. Here the $$L$$ terms are binary input lengths. In particular, loss may decrease as $$1-\eta\ge c\log\log n/\log n$$ while the algorithm stays polynomial for $$\varepsilon^{-1}=O((\log n)^b)$$. This statement does not cover inverse-polynomial accuracy in that same loss regime. It is a sufficient algorithmic region, not a complete hardness phase diagram, and it has not been extended uniformly to the Gaussian theorem.

For fixed Fock transmission, the conservative full arithmetic exponent is

$$
\alpha(\eta)=4+\frac{2\log(288e^4)}{\log(1/\eta)}.
$$

| Transmission $$\eta$$ | Full Fock arithmetic upper-bound exponent $$\alpha$$ |
| --- | ---: |
| 0.25 | 17.94 |
| 0.50 | 31.88 |
| 0.75 | 71.18 |
| 0.90 | 187.43 |

These are unoptimized theoretical upper bounds, not measured runtimes. The Gaussian construction has its own parameter-dependent constants. Neither result currently demonstrates a practical simulation speedup. A further Fock corollary handles the specified orthogonal bad-bit model of partial distinguishability; arbitrary internal overlap matrices remain outside the claim.

## Numerical and algebraic checks

The package includes 1,536 small Fock-input Haar interferometers and 512 conditional Gaussian pair-state interferometers. All physical output collisions and survivor sectors are enumerated. Across the tested nonzero second-moment cells, the largest measured discrepancies from the exact predictions are 1.870 and 1.385 estimated standard errors, respectively. Cells sharing a matrix are correlated; these are pointwise diagnostics.

![Conditional pair-state Haar tests: mean TV decreases with retained degree, and measured second moments agree with exact predictions within Monte Carlo error bars.]({{ '/assets/img/agentic/full-output-lossy-boson-sampling-v2.0-gaussian.png' | relative_url }})

The Gaussian plot starts from fixed-number pair states and uses ideal harmonic truncation. It does not simulate the complete unbounded squeezed-input mixture or benchmark the fast all-size oracle.

Finite checks include the original 329 exact Fock identities and eight coefficient cases; 990 exact pair-reduction controls; 7,735 weight-ratio and 6,307 geometric-envelope checks; Gaussian prefix controls through degree eight; and nine exact matrix-rounding cases. Deliberately corrupted formulas are detected. A finite-precision omission in an intermediate Gaussian draft was repaired analytically and tested before this release.

Extract the supplement and run:

```text
python3 reproduce.py
```

Python 3.10 or later, NumPy and SymPy are required. The default run checks hashes, executes finite controls and reaggregates recorded Gaussian data. With Matplotlib installed, `python3 reproduce.py --haar` also reruns both full Haar grids. The numerical backend enumerates small Fock spaces exponentially; it is a validation tool. The all-size claims rest on the proofs.

Derivation, literature comparison, computation, internal review and drafting used AI assistance under human direction. The checks come from that workflow and do not constitute independent expert verification. The external catalog's status is maintained separately.

## Version history

Version 2.0 adds the restricted Gaussian theorem and proof, the uniform Fock loss–accuracy bound, the orthogonal bad-bit corollary, both Haar datasets, the repaired Gaussian precision argument and an expanded literature comparison. The original Fock theorem is retained.

Version 1.1: [PDF]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.1.pdf' | relative_url }}), [source and checks]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.1.zip' | relative_url }}), [manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.1.json' | relative_url }}).

Version 1.0: [PDF]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.pdf' | relative_url }}), [source and checks]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.zip' | relative_url }}), [manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.json' | relative_url }}).

[Back to the research log]({{ '/agentic-research/' | relative_url }}).
