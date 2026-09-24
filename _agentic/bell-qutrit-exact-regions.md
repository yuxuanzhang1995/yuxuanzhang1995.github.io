---
layout: page
title: "Exact entanglement of formation in regions of a qutrit Bell triangle"
description: "Three near-vertex triangles and a small interior region have explicit optimal ensembles; the rest of the Bell simplex remains open."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_a3a8680c50800797
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/bell-qutrit-exact-regions-source.zip">Full proofs, source and checks (ZIP)</a> &middot; <a href="https://github.com/Naixu-Guo/quantum-open-problems/issues/100">QIQC report #100</a></p>

Mixing maximally entangled states can reduce their entanglement, but determining the exact reduction requires minimizing over every pure-state decomposition. For qutrit Bell-diagonal states, that convex-roof problem is still open in general. These notes identify regions of one three-state face where both the minimum and an attaining ensemble can be written explicitly.

The states are

$$
B_0=\Phi_{0,0},\quad B_1=\Phi_{1,0},\quad B_2=\Phi_{0,1},\qquad
\rho(r)=\sum_{i=0}^2 r_i\vert B_i\rangle\langle B_i\vert ,
$$

where $$\Phi_{a,b}=(I\otimes X^aZ^b)(\vert 00\rangle+\vert 11\rangle+\vert 22\rangle)/\sqrt3$$, $$X\vert j\rangle=\vert j+1\bmod3\rangle$$ and $$Z\vert j\rangle=e^{2\pi i j/3}\vert j\rangle$$. The probabilities are nonnegative and sum to one. Entropies below are in bits.

## Exact regions near the three vertices

Set $$L=\log_2 3$$ and

$$
u(z)=2\sqrt{z(1-z)},\qquad
f(z)=H\!\left(\frac{1-u(z)}3,\frac{2+u(z)}6,\frac{2+u(z)}6\right).
$$

There is a unique $$a\in(1/2,1)$$ satisfying

$$
(1-a)f'(a)+f(a)-L=0.
$$

The proof brackets it by $$9/10<a<16/17$$. Define $$C=(L-f(a))/(1-a)$$. For every probability triple with $$m=\max_i r_i\geq a$$, the claimed exact value is

$$
E_F(\rho(r))=L-C(1-m).
$$

These are three two-dimensional triangles, one at each vertex. An optimal ensemble has at most nineteen states. If $$i$$ is the dominant label, take the nine local Weyl images of $$\sqrt a B_i+e^{i\pi/3}\sqrt{1-a}B_j$$ for each $$j\ne i$$, each with weight $$r_j/[9(1-a)]$$, and add $$B_i$$ with weight $$(r_i-a)/(1-a)$$. The local action is $$\overline W\otimes W$$, with $$W=X^sZ^t$$ and $$s,t\in\mathbb Z_3$$.

The ensemble gives an upper bound immediately. The difficult step is the matching lower bound against *all* decompositions. Phase minimization reduces each pure component to an entropy determined by a cubic. An analytic argument handles the high-probability strip; an outward interval calculation covers the remaining ordered probability wedge. Together they give a global affine lower bound. The certificate checks closed-box coverage, exact geometric pruning, and a strictly positive margin, rather than just sampling states.

## A separate interior region

The earlier note proves another exact formula when $$\vert r_0-1/2\vert <2^{-36}$$ and $$\vert r_1-r_2\vert <2^{-36}$$. Here $$E_F$$ is the entropy of the three roots of

$$
\lambda^3-\lambda^2+\frac{1+\sum_i r_i^2}{6}\lambda
-\frac{(r_0^{3/2}-r_1^{3/2}-r_2^{3/2})^2}{27}=0.
$$

A nine-state Weyl ensemble attains it. The radius is deliberately conservative. This interior result and the near-vertex result leave much of the face undetermined.

## Scope and sources

The finite-Weyl symmetry and convex-roof framework are credited to [Vollbrecht and Werner, *Entanglement Measures under Symmetry*](https://arxiv.org/abs/quant-ph/0010095). The notes supply particular regions and ensembles within that framework. They do not give the value for an arbitrary qutrit Bell-diagonal state, or for arbitrary dimension in the [QIQCOP question](https://qiqc-op.com/problem/op_a3a8680c50800797/).

The interval code is a trusted computational dependency. Internal review and reproduction support this computer-assisted claim; they do not establish formal verification or publication priority. The archive retains the first corrected point proof, its extension to an open region, and the later terminal-region proof. The initial point proof used the equivalent convention with the Weyl operator on the first subsystem; its record is preserved unchanged.


## Proofs and reproducibility

- [Round 39, record 135: exact statement and full proof]({{ '/assets/code/agentic/bell-qutrit-exact-regions/round-39-record-135-proof.txt' | relative_url }}).
- [Round 40, record 144: exact statement and full proof]({{ '/assets/code/agentic/bell-qutrit-exact-regions/round-40-record-144-proof.txt' | relative_url }}).
- [Round 41, record 148: exact statement and full proof]({{ '/assets/code/agentic/bell-qutrit-exact-regions/round-41-record-148-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
