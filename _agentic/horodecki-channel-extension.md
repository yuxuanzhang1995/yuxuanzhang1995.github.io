---
layout: page
title: "An explicit symmetric extension rules out a channel candidate family"
description: "A known Horodecki PPT-entangled family yields antidegradable channels and ordinarily degradable complements."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_7e7e4a25fef5c994
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/horodecki-channel-extension-source.zip">Full proofs, source and checks (ZIP)</a> &middot; <a href="https://github.com/Naixu-Guo/quantum-open-problems/issues/105">QIQC report #105</a></p>

A candidate for separating transpose degradability from ordinary degradability needs more than a PPT-entangled complementary Choi state. This note eliminates one entire family by constructing an ordinary degrading map through a positive symmetric extension.

For $$0<t<1$$ put $$s=1-t^2$$, $$\vert p\rangle=\vert 00\rangle+\vert 11\rangle+\vert 22\rangle$$ and $$\vert v\rangle=\vert 20\rangle+t\vert 22\rangle$$. On two qutrits define

$$
H_t=s\left[\vert p\rangle\langle p\vert +
\sum_{ij\in\{01,02,10,12,21\}}\vert ij\rangle\langle ij\vert \right]
+\vert v\rangle\langle v\vert .
$$

Its input marginal is $$M_t=\operatorname{diag}(3s,3s,s+2)$$. With $$W_t=M_t^{-1/2}$$, the operator $$J_t=(W_t\otimes I)H_t(W_t\otimes I)$$ is a Choi operator in the convention $$\operatorname{Tr}_EJ_t=I_A$$. It defines a channel $$\Psi_t:\mathcal L(\mathbb C^3)\to\mathcal L(\mathbb C^3)$$.

The underlying states are **Horodecki's known PPT-entangled family**, not new states: $$H_t=(9-7t^2)\rho_a$$ with $$a=(1-t^2)/(1+t^2)$$ in [Horodecki (1997)](https://arxiv.org/abs/quant-ph/9703004). Their ranks are seven before partial transpose and six after it. That mismatch rules out an output-unitary implementation of the transpose, but says nothing by itself about degradability.

## The extension

Order the three tensor factors as $$A,E,E'$$ and set

$$
\vert w\rangle=\vert 000\rangle+\vert 101\rangle+\vert 110\rangle+\vert 202\rangle+\vert 220\rangle+t\vert 222\rangle,
$$

$$
\vert z\rangle=\vert 2\rangle\otimes(\vert 0\rangle+t\vert 2\rangle)\otimes(\vert 0\rangle+t\vert 2\rangle).
$$

Then

$$
\Omega_t=s\left[\vert w\rangle\langle w\vert +
\sum_{u\in\{011,022,122,211\}}\vert u\rangle\langle u\vert \right]
+\frac{t^2}{1+t^2}\vert z\rangle\langle z\vert
$$

is positive, symmetric under exchanging $$E,E'$$, and has both two-party marginals equal to $$H_t$$. Whitening its input gives a channel with two identical marginals $$\Psi_t$$. Minimal Stinespring uniqueness then supplies an ordinary degrading channel for every minimal complement $$\Phi_t:\mathcal L(\mathbb C^3)\to\mathcal L(\mathbb C^7)$$. Equivalently, $$\Psi_t$$ is antidegradable.

The exact partial-trace identities are checked symbolically in the archive. The analytic proof applies throughout $$0<t<1$$, not just at the numerical test point. The potential contribution is this explicit extension and its exclusion consequence; the symmetric-extension criterion and the original state family are credited background, and priority for the displayed extension is unconfirmed.

The [original separation question](https://qiqc-op.com/problem/op_7e7e4a25fef5c994/) remains open. This note proves ordinary degradability of the specified complements. It makes no claim that they are transpose degradable and supplies no separating example elsewhere.


## Proofs and reproducibility

- [Round 41, record 149: exact statement and full proof]({{ '/assets/code/agentic/horodecki-channel-extension/round-41-record-149-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
