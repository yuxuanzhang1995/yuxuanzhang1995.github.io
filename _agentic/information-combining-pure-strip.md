---
layout: page
title: "An erasure-bound strip for quantum information combining"
description: "A strict quantitative upper-bound regime for two qubit-output channels when the first conditional outputs are pure."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_d2e499b973f792e7
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/information-combining-pure-strip-source.zip">Full proofs, source and checks (ZIP)</a></p>

For two independent uniform bits with quantum side information, the erasure-channel conjecture proposes

$$
H(X_1\oplus X_2\mid B_1B_2)\leq s_1+s_2-s_1s_2,
\qquad s_i=H(X_i\mid B_i),
$$

with entropies in bits. These notes establish a strict quantitative region when the side information consists of qubits and the first channel has pure conditional outputs.

Consider

$$
\rho_\pm^{(1)}=\frac{I+aZ\pm\sqrt{1-a^2}X}{2},\qquad
\rho_\pm^{(2)}=\frac{I+cZ\pm\sqrt yX}{2},
$$

where $$0\leq a,c\leq1$$ and $$0\leq y\leq1-c^2$$. Let $$\Delta$$ be the conjectured right-hand side minus its left-hand side. For $$a,c<1$$, define

$$
h(t)=h_2((1+t)/2),\quad f(t)=\frac{\operatorname{atanh}t}{t},\quad f(0)=1,
$$

$$
L(t)=\frac{f(t)}{2\ln2},\qquad
T(a)=\frac{(1-a^2)f(a)}{h(a)},\qquad
F(q)=\sum_{n\geq1}\frac{q^{n-1}}{n(2n-1)},\quad q=\frac y{1-c^2}.
$$

The claimed estimate is

$$
\Delta\geq h(a)yL(c)\,[T(a)-F(q)].
$$

It gives the explicit uniform strip

$$
\frac{63}{64}\leq a<1,\quad 0\leq c<1,\quad
0\leq y\leq\frac{1-c^2}{2}
\quad\Longrightarrow\quad
\Delta\geq\frac{h(a)yL(c)}{120}.
$$

The inequality is strict when $$y>0$$. If $$a=1$$ or $$c=1$$, the gap is zero. More generally, $$T(a)\to2\ln2$$ as $$a\to1$$, so each fixed $$q<1$$ is eventually covered as $$a$$ approaches one, uniformly in $$c$$.

The proof retains the exact entropy contribution of the pure first channel. It combines the output's block spectrum with convexity and integral comparisons to obtain the displayed bound. The small exact-arithmetic checker verifies the decisive constants; finite random searches are not the proof of the strip.

The conjecture is [Hirche and Reeb, Conjecture VII.2](https://arxiv.org/html/1706.09752v2), and the [QIQCOP question](https://qiqc-op.com/problem/op_d2e499b973f792e7/) permits arbitrary quantum side information. This note does not establish that general statement or even the whole one-pure qubit boundary. Strong second signals at general $$a$$ remain outside the sufficient condition. The result has internal AI review; novelty and independent human confirmation remain unverified.


## Proofs and reproducibility

- [Round 39, record 136: exact statement and full proof]({{ '/assets/code/agentic/information-combining-pure-strip/round-39-record-136-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
