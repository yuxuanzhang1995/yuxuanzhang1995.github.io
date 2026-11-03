---
layout: page
title: "Full-output classical simulation of lossy boson sampling with single-photon and equal-squeezing inputs"
description: "Research notes with corrected prior-work attribution, full-output sampling proofs, exchangeable and nonuniform input-loss corollaries, and reproducibility checks."
date: "2026-11-03"
permalink: /agentic-research/full-output-lossy-boson-sampling/
status: "research notes · prior-work attribution corrected"
target: "QIQC Open Problem Zoo · Constant-transmission sampling; known-covered main guarantees"
---

Yuxuan Zhang · Version 2.1 · 3 November 2026

**Literature correction.** The previous version missed [Youngrong Lim, *Boson sampling is fragile to loss*](https://arxiv.org/abs/2611.01434). Its Theorems 1–2 already cover the main Fock and equal-squeezing Gaussian guarantees presented here, and Appendix F.2 contains the same nonuniform-input thinning reduction. The earlier statement that no equivalent theorem had been found is withdrawn. These notes retain the proofs, explicit corollaries and reproducibility material without claiming priority for those results.

Version 2.1 integrates exchangeable loss through survival moments and independent nonuniform input loss through a short thinning proof. A reduced-purity bound removes the extra factor $$l+1$$ from the nonuniform harmonic estimate. The main Gaussian statement still assumes **every mode is equally squeezed**.

The manuscript has undergone internal proof review and computational checks. Independent expert review remains outstanding. Mathematical checks do not establish novelty.

Download the [manuscript (PDF)]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v2.1.pdf' | relative_url }}), [source, checks and numerical data]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.1.zip' | relative_url }}), and [release manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.1.json' | relative_url }}).

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

The Fock theorem covers the formulation in the [QIQC Open Problem Zoo](https://qiqc-op.com/problem/op_d436ff9fb9cb0ce5/), but this page does not claim a new resolution: the main guarantees are already covered by Lim's work. Running either algorithm at mean tolerance $$\varepsilon\delta$$ also gives TV at most $$\varepsilon$$ with Haar probability at least $$1-\delta$$, by Markov's inequality.

## Two loss-model corollaries

For exchangeable input loss, let $$K$$ be the survivor count and let

$$
\mu_l=\mathbb E\frac{(K)_l}{(n)_l}.
$$

Replacing $$\eta^l$$ by $$\mu_l$$ gives the truncation, collision-bias and color-variance bounds. A polynomial-time guarantee follows when $$\mu_l\le\gamma^l$$ for a fixed $$\gamma<1$$ and the count law is efficiently supplied. In particular, exactly $$k_0\le\gamma n$$ uniformly selected survivors are allowed at **every $$m\ge n$$**, with all output collisions retained. Exchangeability alone does not imply the required decay.

For independent input transmissions $$0\le\eta_i\le\gamma<1$$, first select input $$i$$ with probability $$\eta_i/\gamma$$, then call the uniform-$$\gamma$$ sampler on the selected inputs. Only one subset and one sampler call are needed. Haar invariance under column permutations and TV convexity preserve the error guarantee. This is the reduction already stated in Lim's Appendix F.2; the transmission profile must be independent of $$U$$.

The same mixture gives the stronger reduced-purity estimate

$$
\sum_{k=l}^n w_k\binom{k}{l}\|R_{k,l}\rho^{(k)}\|_{\mathrm{HS}}^2
\le\eta_{\max}^l.
$$

Consequently, the ideal harmonic tail obeys

$$
\mathbb E_U\|p_U-q_{U,r}\|_1
\le\left(\sum_{l=r+1}^n\eta_{\max}^l\right)^{1/2},
$$

without an additional $$l+1$$ factor. The all-zero transmission case is vacuum. This is a proved consequence of the mixture and reduction estimate, not a separate priority claim. General path-dependent attenuation and a guarantee based only on average transmission are outside this statement.

## Proof ingredients

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

[Lim, arXiv:2611.01434v1](https://arxiv.org/html/2611.01434v1), is the direct comparison for both main theorems and independent nonuniform input loss. Its exact Haar estimates and collision-aware low-order construction also overlap the analytic framework here; Appendix D.4 includes finite-bit complexity. The present notes use consistent signed-prefix sampling, whereas Lim uses bounded rejection. No speed or complexity advantage is claimed for that difference. The exchangeable fixed-count statement follows from the conditional estimate also present in Lim's equation (B.20).

The arXiv record gives a submission date of 1 November 2026 and reports an identical Zenodo version dated 21 October. That earlier date is attributed to the arXiv record; the Zenodo record was not independently verified in this review.

[Go and Jeong](https://arxiv.org/html/2610.27065v1), Corollary 4, give full-output Fock simulation under mode restrictions $$M\ge C_0k^2N$$ and $$M\ge C_Bk^2/(\varepsilon\delta)$$. The fixed-survivor corollary here gives a same-model statement for every $$m\ge n$$. Their color-coding, inverse-determinant and signed-prefix framework is an important antecedent. Uniform/fixed-count conversion predates both papers: see [Oszmaniec–Brod](https://arxiv.org/abs/1801.06166), Section III.A. [Brod–Oszmaniec](https://arxiv.org/abs/1906.06696v4) addresses nonuniform network loss under different, stronger-loss conditions with all-network guarantees.

For Gaussian inputs, [Lim's earlier paper](https://arxiv.org/html/2610.06526v1) proves a guarantee for every interferometer, with TV $$O(N\eta^3)$$ and a separate equal-squeezing pair construction reaching $$N^{3/4}$$ mean survivors at fixed accuracy. The later paper directly covers the fixed-transmission Haar-average theorem; comparison only with the earlier work would be incomplete.

Exact Haar representation methods and the measurement frame are credited to [Nezami](https://arxiv.org/abs/2104.06423), [Arienzo et al.](https://arxiv.org/html/2408.11111v2) and related work. The expanded bibliography also compares [Umanskii–Rubtsov](https://arxiv.org/html/2404.01004v1), [Oh et al.](https://arxiv.org/abs/2306.03709v2), [Renema](https://arxiv.org/abs/1911.10112v1), [Dodd et al.](https://arxiv.org/html/2511.14923v1) and [Liu et al.](https://arxiv.org/html/2512.10643v2). The source supplement records the checked assumptions and the correction to version 2.0's incomplete comparison.

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

Finite checks include the original 329 exact Fock identities and eight coefficient cases; 990 exact pair-reduction controls; 7,735 weight-ratio and 6,307 geometric-envelope checks; Gaussian prefix controls through degree eight; and nine exact matrix-rounding cases. The added loss-model suite has 6,957 exact assertions over 34 transmission profiles, including 328 two-stage probability checks and 102 weighted reduced-purity bounds. It also checks the alternative conditional coefficient identity through degree six. All three mutation families are detected. These are finite algebra controls, not new Haar sampling experiments or a benchmark of the all-size sampler.

Extract the supplement and run:

```text
python3 reproduce.py
```

Python 3.10 or later, NumPy and SymPy are required. The default run checks hashes, executes finite controls and reaggregates recorded Gaussian data. With Matplotlib installed, `python3 reproduce.py --haar` also reruns both full Haar grids. The numerical backend enumerates small Fock spaces exponentially; it is a validation tool. The all-size claims rest on the proofs.

Derivation, literature comparison, computation, internal review and drafting used AI assistance under human direction. The checks come from that workflow and do not constitute independent expert verification. The external catalog's status is maintained separately.

## Version history

Version 2.1 integrates the two loss-model corollaries, the bound without $$l+1$$, the ninth finite check suite and the corrected literature attribution. No new catalog resolution is credited.

Version 2.0 added the Gaussian proof, explicit Fock corollaries and numerical evidence. Its novelty comparison is superseded by the correction above. Preserved historical files: [PDF]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v2.0.pdf' | relative_url }}), [source and checks]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.0.zip' | relative_url }}), [manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v2.0.json' | relative_url }}).

Version 1.1: [PDF]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.1.pdf' | relative_url }}), [source and checks]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.1.zip' | relative_url }}), [manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.1.json' | relative_url }}).

Version 1.0: [PDF]({{ '/assets/pdf/agentic/full-output-lossy-boson-sampling-v1.pdf' | relative_url }}), [source and checks]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.zip' | relative_url }}), [manifest]({{ '/assets/code/agentic/full-output-lossy-boson-sampling-v1.json' | relative_url }}).

[Back to the research log]({{ '/agentic-research/' | relative_url }}).
