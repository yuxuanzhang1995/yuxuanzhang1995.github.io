---
layout: page
title: Universality from every fixed non-Gaussian polynomial generator
description: Gaussian controls and any fixed essentially self-adjoint higher-degree Weyl polynomial strongly approximate every unitary.
date: 2026-09-20
last_revised: 2026-09-21
status: proof candidate
target: QIQCOP problem op_64046727b81b4024
pdf: fixed-nongaussian-universality.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/fixed-nongaussian-universality.pdf' | relative_url }}">Full manuscript (PDF, 6 pages)</a> &middot; <a href="{{ '/assets/code/agentic/fixed-nongaussian-universality-source.zip' | relative_url }}">LaTeX source, proof and checks (ZIP)</a></p>

**Status: a complete proof candidate, internally checked with AI assistance.** External expert review and publication priority remain unconfirmed. This is the round-17 result, prepared for publication on 20 September 2026. It has not been formally verified by a proof assistant.

**Revision, 21 September 2026:** Lemma 3 now spells out the fixed-vector telescoping identity and the generator condition needed for Chernoff's product formula. The theorem and its hypotheses are unchanged. This is a clarification checked by AI, with external review still pending in [QIQCOP issue #93](https://github.com/Naixu-Guo/quantum-open-problems/issues/93).


## The question and hypotheses

The [QIQCOP problem](https://qiqc-op.com/problem/op_64046727b81b4024/) fixes a real Weyl-ordered polynomial $$H_*$$ of degree greater than two, essentially self-adjoint on Schwartz space, in a finite number of bosonic modes. Available gates are all Gaussian unitaries and $$e^{-it\overline{H_*}}$$ for arbitrary real $$t$$.

The goal is approximation uniformly over input states of bounded mean photon number, including arbitrary entangled reference systems.

## The candidate theorem

For every finite mode count and every fixed $$H_*$$ satisfying those hypotheses, **finite allowed products are strongly dense in the full unitary group**.

In particular, for every target unitary $$U$$, finite $$E\geq0$$ and $$\varepsilon>0$$, an allowed finite product $$V$$ satisfies

$$
\sup_{R,\rho_{AR}:\operatorname{Tr}(\rho_A N)\leq E}
\|[(\mathcal U-\mathcal V)\otimes\mathrm{id}_R](\rho_{AR})\|_1<\varepsilon.
$$

The theorem even removes the catalog's Schwartz-preservation condition on the target. It retains essential self-adjointness of the given generator and access to both signs of its evolution time.

## Proof structure

1. A metaplectic transformation and a squeezing limit isolate a nonzero pure position power. Convergence on a self-adjoint core justifies the limiting exponentials, without assuming that the original generator's evolution preserves Schwartz space.
2. Commuting finite differences produce a cubic phase. Cubic conjugation of the quadratic momentum operator, followed by a justified product formula, yields quartic phases.
3. Quartic phases generate a diagonal drift $$F=(\sum_j\alpha_jN_j)^2$$ with positive, rationally independent $$\alpha_j$$. Its transition frequencies within each mode are positive and distinct.
4. Spectral filters isolate bounded Hamiltonians for individual Fock-basis edges. Analytic-vector estimates establish essential self-adjointness of every finite unbounded filter before its exponential is used.
5. Those bounded edges generate special unitaries on finite connected Fock boxes, which are strongly dense in all unitaries. A photon cutoff then converts strong approximation into the required uniform reference-assisted bound.

The last step is explicit. If $$P_K$$ projects onto total photon number at most $$K$$, then

$$
d_E(U,V)\leq2\|(U-V)P_K\|+4\sqrt{\frac E{K+1}}.
$$

First choose a large enough cutoff, then use strong density on its finite-dimensional range.

## Verification and relation to prior work

The product derivative in Lemma 3 is now explicit. Write $$U_l(s)=e^{isB_l}$$ and $$P_{l-1}(s)=U_1(s)\cdots U_{l-1}(s)$$, with $$P_0(s)=I$$. Then

$$
\frac{U_1(s)\cdots U_r(s)-I}{s}\psi
=\sum_{l=1}^r P_{l-1}(s)\frac{U_l(s)-I}{s}\psi.
$$

Each difference quotient acts on the fixed vector $$\psi\in\bigcap_l\operatorname{Dom}(B_l)$$. The prefix is unitary and converges strongly to the identity, so every summand converges to $$iB_l\psi$$. This needs no invariance of the common core under individual evolutions. The revised manuscript also checks that the full strong derivative has closure $$iA$$, where $$A$$ is the self-adjoint closure of the sum on that core.

Internal adversarial reviews checked the cores, product formula, filter domains, frequency separation, finite-block generation and reference-assisted estimate. The archive contains symbolic finite-difference and quartic identities, plus finite spectral-filter diagnostics. Those scripts do not certify the infinite-dimensional limits; the manuscript proves them analytically.

[Arzani–Booth–Chabaud, arXiv:2501.13857](https://arxiv.org/abs/2501.13857), uses target-dependent polynomial generators and explicitly distinguishes the fixed-generator question in its Discussion. [Keyl, arXiv:1812.09211](https://arxiv.org/abs/1812.09211), assumes bounded controls in its cited theorem. [Wu–Tarn–Li, quant-ph/0505063](https://arxiv.org/abs/quant-ph/0505063), concerns smooth state-orbit controllability. The manuscript addresses the domain and convergence steps required by the present fixed-generator statement, using the standard Chernoff product formula and Nelson analytic-vector theorem with explicit hypotheses.

This is a qualitative universality result. It supplies no efficient compiler, gate-count bound, finite-precision estimate or bound on intermediate energy. It requires no extra resource modes.


## Authorship and preparation

The proof, checking and exposition were developed with substantial AI assistance under the author's direction. Internal AI reviews do not constitute independent human peer review. [Scientific Agent Skills](https://arxiv.org/abs/2609.00065) informed manuscript preparation and evidence tracking and is cited in the PDF. Primary papers retain their own terms and are not bundled in the source archive.
