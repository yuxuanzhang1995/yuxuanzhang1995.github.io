---
layout: page
title: "The entropy photon-number inequality near a nonthermal vacuum boundary"
description: "Positive low-energy expansions for restricted one-mode inputs, including an exactly pure input with arbitrary relative phase."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_ba39e7a80122b256
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/epni-low-energy-boundary-source.zip">Full proofs, source and checks (ZIP)</a></p>

The entropy photon-number inequality predicts that mixing independent bosonic inputs cannot reduce their entropy-equivalent photon number below a weighted average. These notes prove positive asymptotic gaps for restricted nonthermal inputs near the vacuum, including a boundary where one input is exactly pure.

Use natural logarithms and $$g(x)=(x+1)\ln(x+1)-x\ln x$$. For a beam splitter with $$0<p<1$$ and $$q=1-p$$, retain the mode $$c=\sqrt p\,a_{\rm op}+\sqrt q\,b_{\rm op}$$. The gap is

$$
\Delta(t)=g^{-1}(S(\rho_C(t)))
-p\,g^{-1}(S(\rho_A(t)))-q\,g^{-1}(S(\rho_B(t))).
$$

## One exactly pure input

Fix complex $$x,y$$ with $$a=\vert x\vert ^2>0$$ and $$b>\vert y\vert ^2$$. On the vacuum/one-photon subspace, take independent inputs

$$
\rho_A(t)=\begin{pmatrix}1-at&x\sqrt{t(1-at)}\\\bar x\sqrt{t(1-at)}&at\end{pmatrix},\qquad
\rho_B(t)=\begin{pmatrix}1-bt&y\sqrt t\\\bar y\sqrt t&bt\end{pmatrix}.
$$

All other matrix entries vanish. With $$Y=\vert y\vert ^2$$ and $$B=b-Y>0$$, these are physical for $$0<t<\min\{1/a,B/b^2\}$$. The first state is exactly pure. Its square-root factor is essential; simply saturating a mixed-state asymptotic ansatz would give an unphysical input.

Let $$R=\operatorname{Re}(\bar x y)$$, $$L=\ln(1/t)$$ and

$$
H=pq\left[2BY+(a+Y)^2-4R^2\right]>0.
$$

For every fixed allowed parameter choice, the claimed expansion is

$$
\Delta(t)=Ht^2+B^2t^2\left[\frac q{L-\ln B}-\frac{q^2}{L-\ln(qB)}\right]+O(t^3).
$$

In particular, $$\Delta(t)=Ht^2+pqB^2t^2/L+O(t^2/L^2)>0$$ for sufficiently small positive $$t$$. Arbitrary complex relative phases are allowed. The eventual threshold and remainder constants may depend on the fixed parameters.

## Other retained boundary expansions

The archive also treats two genuinely mixed inputs whose coherences scale as $$\sqrt t$$, and an earlier family with coherences of order $$t$$. In the mixed/mixed case the gap is $$Ht^2+Qt^2/\ln(1/t)+o(t^2/\ln(1/t))$$ with explicit coefficients. The leading coefficient is positive when either input has nonzero coherence; when both coherences vanish, the next coefficient is positive. The exact hypotheses and coefficients are in the frozen statement.

The proof starts from the full three-dimensional beam-splitter output, expands its small eigenvalues, and controls the entropy inversion. For the pure-input case, a cancellation in the output determinant makes the smallest eigenvalue of order $$t^3$$. Symbolic checks verify that cancellation. High-precision numerical controls support the expansion but do not prove the asymptotic remainder.

The exactly thermal environment case, including vacuum, is already covered by [De Palma, Trevisan and Giovannetti (2017)](https://arxiv.org/abs/1610.09970), Theorem 4, Eq. (24). That known result is credited separately. Our inputs generally have a nonthermal second port. The [general EPnI](https://qiqc-op.com/problem/op_ba39e7a80122b256/) remains open: these notes provide no uniform finite-energy threshold, no arbitrary-input theorem, and no result for multimode correlations.


## Proofs and reproducibility

- [Round 39, record 140: exact statement and full proof]({{ '/assets/code/agentic/epni-low-energy-boundary/round-39-record-140-proof.txt' | relative_url }}).
- [Round 40, record 145: exact statement and full proof]({{ '/assets/code/agentic/epni-low-energy-boundary/round-40-record-145-proof.txt' | relative_url }}).
- [Round 41, record 150: exact statement and full proof]({{ '/assets/code/agentic/epni-low-energy-boundary/round-41-record-150-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
