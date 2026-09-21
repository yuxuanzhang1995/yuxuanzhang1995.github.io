---
layout: page
title: Anticoncentration of independent complex Gaussian hafnians
description: An all-dimension inverse-variance bound gives polynomial lower-tail control for the independent complex symmetric ensemble.
date: 2026-09-20
last_revised: 2026-09-20
status: proof candidate
target: QIQCOP problem op_55be40726cdf7304
pdf: complex-gaussian-hafnian.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**<br>
Department of Physics, Princeton University, Princeton, New Jersey 08544, USA<br>
Institute of Physics, École Polytechnique Fédérale de Lausanne (EPFL), CH-1015 Lausanne, Switzerland

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/complex-gaussian-hafnian.pdf' | relative_url }}">Full manuscript (PDF, 5 pages)</a> &middot; <a href="{{ '/assets/code/agentic/complex-gaussian-hafnian-source.zip' | relative_url }}">LaTeX source, proof and checks (ZIP)</a></p>

**Status: a complete proof candidate, internally checked with AI assistance.** External expert review and publication priority remain unconfirmed. This is the round-17 result, prepared for publication on 20 September 2026. It has not been formally verified by a proof assistant.


## The question

Let $$X$$ be a symmetric $$2n\times2n$$ matrix with zero diagonal and independent $$\mathcal{CN}(0,1)$$ entries above it, normalized by $$\mathbb E\lvert X_{ij}\rvert^2=1$$. The [QIQCOP problem](https://qiqc-op.com/problem/op_55be40726cdf7304/) asks for one polynomial $$p$$ such that, for every $$n\geq1$$ and $$0<\delta<1$$,

$$
\Pr\!\left(|\operatorname{Haf}(X)|<\frac{\sqrt{(2n-1)!!}}{p(n,1/\delta)}\right)<\delta.
$$

## The candidate theorem

Write $$H_n=\operatorname{Haf}(X)$$ and

$$
V_n=\sum_{j=2}^{2n}|\operatorname{Haf}(X\text{ with vertices }1,j\text{ removed})|^2.
$$

The manuscript proves

$$
\mathbb E[V_n^{-1}]\leq\frac1{(2n-2)!!},\qquad 0!!=1.
$$

Consequently, for every complex center $$z$$ and every $$\varepsilon\geq0$$,

$$
\Pr\bigl(|H_n-z|\leq\varepsilon\sqrt{(2n-1)!!}\bigr)
\leq\min\left\{1,\frac2{\sqrt\pi}\sqrt n\,\varepsilon^2\right\}.
$$

In particular, **$$p(n,u)=2nu$$** satisfies the exact catalog question, including strict inequality for all $$0<\delta<1$$.

## Why the correlated minors can be handled

Conditioning on all edges outside the first row makes the hafnian a circular Gaussian with variance $$V_n$$. The problem is therefore to control an inverse moment of that variance.

An exact partition of perfect matchings exposes two vertices and expresses the hafnian as a complex Gaussian bilinear form plus linear terms. After realification, a Gaussian integral has positive endpoint values and a purely imaginary mixed term. Hölder's inequality then permits two first-row coordinates to be compressed into one without increasing the comparison bound.

Repeated compression reduces the dimension. With an independent $$G\sim\operatorname{Gamma}(2n-1,1)$$, the resulting comparison is

$$
\mathbb E e^{-sV_n}\leq\mathbb E e^{-sGV_{n-1}}\qquad(s\geq0).
$$

Integrating this inequality gives the recurrence $$\mathbb E V_n^{-1}\leq(2n-2)^{-1}\mathbb E V_{n-1}^{-1}$$. The base case is $$V_1=1$$. At no step are different hafnian minors treated as independent.

## Verification and attribution

Separate internal reviews checked the phase reduction, exact matching partition, conditional endpoint positivity, Laplace-order direction and all-dimension induction. The archive also checks 60 matching decompositions and 60 vertex-phase identities exactly over Gaussian integers for $$n=2,\ldots,6$$. These finite checks support the algebra; the theorem rests on the analytic proof.

The Gaussian-kernel and coordinate-compression method is adapted from [Koehler–Leung, arXiv:2607.20329v1](https://arxiv.org/abs/2607.20329v1), on permanents, and [Zhao, arXiv:2609.06526v1](https://arxiv.org/abs/2609.06526v1), whose Theorem 2.3 concerns independent **real** symmetric Gaussian hafnians. [Zhao, arXiv:2608.17065](https://arxiv.org/abs/2608.17065), treats a different complex **Gram** ensemble. The manuscript derives the independent-complex adaptation explicitly.

This resolves the literal lower-tail statement if the proof is confirmed. It does not transfer a bound to correlated Gram matrices or prove the separate average-case hardness assumptions motivated by [Gaussian boson sampling](https://arxiv.org/abs/1612.01199).


## Authorship and preparation

The proof, checking and exposition were developed with substantial AI assistance under the author's direction. Internal AI reviews do not constitute independent human peer review. [Scientific Agent Skills](https://arxiv.org/abs/2609.00065) informed manuscript preparation and evidence tracking and is cited in the PDF. Primary papers retain their own terms and are not bundled in the source archive.
