---
layout: page
title: Fixed-photon-number codes and a proposed pure-loss converse
description: A zero-leakage shell-code construction exceeds the proposed occupation-constrained second-order upper bound.
date: 2026-09-20
last_revised: 2026-09-20
status: counterexample candidate
target: QIQCOP problem op_89fb664ba06ba5de
pdf: pure-loss-second-order.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**<br>
Department of Physics, Princeton University, Princeton, New Jersey 08544, USA<br>
Institute of Physics, École Polytechnique Fédérale de Lausanne (EPFL), CH-1015 Lausanne, Switzerland

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/pure-loss-second-order.pdf' | relative_url }}">Full manuscript (PDF, 4 pages)</a> &middot; <a href="{{ '/assets/code/agentic/pure-loss-second-order-source.zip' | relative_url }}">LaTeX source, proof and checks (ZIP)</a></p>

**Status: a complete counterexample candidate, internally checked with AI assistance.** External expert review and publication priority remain unconfirmed. This is the round-15 result, prepared for publication on 20 September 2026. It has not been formally verified by a proof assistant.


## The question

The [QIQCOP statement](https://qiqc-op.com/problem/op_89fb664ba06ba5de/) proposes a second-order upper bound on classical communication through a pure-loss bosonic channel. Codewords must place all but exponentially small average weight below a total-photon cutoff $$\lceil nN_S\rceil$$. Its proposed bound is

$$
\log_2 M^*\leq ng(\eta N_S)+\sqrt{nv(\eta N_S)}\,\Phi^{-1}(\varepsilon)+O(\log n),
$$

where $$g(x)=(x+1)\log_2(x+1)-x\log_2x$$ and $$v(x)=x(x+1)[\log_2(1+1/x)]^2$$. The page presents a strengthened formulation motivated by earlier coding papers. This note addresses that formulation; it does not identify a false theorem in those papers.

## The candidate result

For every fixed $$0<\eta<1$$, $$N_S>0$$ and $$0<\varepsilon<1$$, deterministic codes with **exactly** $$k=\lceil nN_S\rceil$$ photons achieve, for every sufficiently large $$n$$,

$$
\begin{aligned}
\log_2 M_n={}&ng(\eta N_S)
+\sqrt{n\eta(1-\eta)N_S}\log_2\!\left(1+\frac1{\eta N_S}\right)\Phi^{-1}(\varepsilon)\\
&-\frac32\log_2 n+O(1).
\end{aligned}
$$

Every input has zero cutoff leakage, so any prescribed positive leakage exponent is satisfied. For $$\varepsilon<1/2$$, the negative normal quantile makes this achieved rate exceed the proposed upper bound by a positive multiple of $$\sqrt n$$.

For example, $$\eta=1/2$$, $$N_S=2$$ and $$\varepsilon=\Phi(-1)$$ give

$$
\log_2 M_n=2n-\sqrt{n/2}-\tfrac32\log_2n+O(1),
$$

whereas the proposed converse would require $$\log_2M_n\leq2n-\sqrt{2n}+O(\log n)$$. A logarithmic remainder cannot absorb that difference.

## The finite-block argument

Choose independent unit vectors $$u_m\in\mathbb C^n$$ and encode message $$m$$ in the supermode number state

$$
|u_m;k\rangle=\frac{(\sum_i u_{m,i}a_i^\dagger)^k}{\sqrt{k!}}|0\rangle.
$$

After loss, the surviving photon number $$L$$ is binomial, and conditional output states are $$\lvert u_m;l\rangle$$. Haar averaging makes these states isotropic in the $$l$$-photon sector of dimension $$d_l=\binom{n+l-1}{l}$$. A Gram–Schmidt measurement has expected average error at most $$(M-1)/(2d_l)$$ in that sector.

One common codebook and a direct-sum POVM across sectors therefore give a deterministic code with error at most

$$
\Pr(L<t)+\frac{M-1}{2d_t},\qquad L\sim\operatorname{Bin}(k,\eta).
$$

Choose the discrete $$\varepsilon-1/n$$ quantile for $$t$$ and $$M=\lfloor d_t/n\rfloor$$. Berry–Esseen and Stirling estimates yield the stated rate. The full manuscript checks integer rounding, the bounded remainder, and completion to a POVM on the entire output space.

## Verification and prior work

The pure-loss Kraus output, exact shell moments and finite-code decoder identities were reproduced in clean containers. The analytic proof separately covers the asymptotic claim; finite numerical examples are not its justification. The source archive preserves the corrected review packet and the initial attachment failure.

Photon-sector isotropy, passive-interferometer ensembles and binomial number-state loss are established ingredients, explicitly credited to [Fanizza et al., Quantum 5, 608 (2021)](https://doi.org/10.22331/q-2021-12-23-608), §3.2 Eq. (9) and §5 Eq. (42). [Wilde–Renes–Guha](https://arxiv.org/abs/1408.5328), §6.1, gives a coherent-state occupation-constrained construction; [Wilde–Winter](https://arxiv.org/abs/1308.6732) proves a first-order strong converse. Priority for the precise operational second-order construction remains unconfirmed.

No optimal replacement dispersion, efficient encoder or practical decoder is claimed.


## Authorship and preparation

The proof, checking and exposition were developed with substantial AI assistance under the author's direction. Internal AI reviews do not constitute independent human peer review. [Scientific Agent Skills](https://arxiv.org/abs/2609.00065) informed manuscript preparation and evidence tracking and is cited in the PDF. Primary papers retain their own terms and are not bundled in the source archive.
