---
layout: page
title: "When Gaussian measurements attain the Holevo bound"
description: "Equality classifications for several one-mode models, including displacement changes, with strict gaps outside the stated cases."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_8f1853475db7ea27
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/gaussian-holevo-equality-source.zip">Full proofs, source and checks (ZIP)</a></p>

The Holevo bound describes the best local precision permitted by quantum mechanics. Gaussian measurements are experimentally natural, but they need not reach that bound. These notes classify equality in several one-mode models and identify the measurement when equality holds.

The convention is $$[q,p]=i$$ and $$\Omega=\begin{pmatrix}0&1\\-1&0\end{pmatrix}$$. Write $$C_G(W)$$ for the optimum over the single-copy Gaussian measurements in the [QIQCOP statement](https://qiqc-op.com/problem/op_8f1853475db7ea27/), including homodyne limits, and $$C_H(W)$$ for the Holevo bound. All models below are smooth and faithful, and $$W$$ is positive definite.

## A traceless covariance plane with changing means

For two parameters, choose canonical coordinates in which

$$
V=vI_2,\quad v>1/2,\qquad
D_1=\partial_1V=\begin{pmatrix}1&0\\0&-1\end{pmatrix},\quad
D_2=\partial_2V=\begin{pmatrix}0&1\\1&0\end{pmatrix}.
$$

Let $$m_j=\partial_jd$$ be the mean derivatives. Then the claimed classification is

$$
C_G(W)=C_H(W)
\quad\Longleftrightarrow\quad
m_2=-\Omega m_1\ \text{and}\ W=wI_2\quad(w>0).
$$

Heterodyne measurement, with noise seed $$I_2/2$$, attains the common value

$$
\frac{2w(v+1/2)^2}{1+(v+1/2)\lVert m_1\rVert^2}.
$$

Otherwise the gap is strict, even after taking infima over arbitrarily squeezed measurements. A general tangent plane that becomes traceless after whitening can be expressed in this basis; its mean derivatives and weight must be transformed with the parameter coordinates.

## A one-dimensional covariance tangent space

Now suppose the model has two parameters, nonsingular SLD Fisher information, and $$\dim\operatorname{span}_{\mathbb R}\{\partial_1V,\partial_2V\}=1$$. Put $$v=\sqrt{\det V}$$, $$S=\sqrt v\,V^{-1/2}$$, $$m_j=S\partial_jd$$ and $$D_j=S(\partial_jV)S^{\mathsf T}$$. Equality holds exactly when some real unit vector $$l$$ satisfies, for both parameters,

$$
m_j\in\mathbb R l,\qquad
D_j\in\mathbb R\!\left[v^2ll^{\mathsf T}-\frac{(\Omega l)(\Omega l)^{\mathsf T}}4\right].
$$

Homodyne measurement of $$l^{\mathsf T}S(R-d)$$ then attains the bound for every positive weight. Its Fisher matrix is $$F_l=aa^{\mathsf T}/v+bb^{\mathsf T}/(2v^2)$$, where $$a_j=l^{\mathsf T}m_j$$ and $$b_j=l^{\mathsf T}D_jl$$. The common cost is $$\operatorname{tr}(WF_l^{-1})$$. Outside the stated condition, the gap is strict.

## Earlier covariance-only classifications

The archive also contains a complete equality classification for two independent covariance derivatives with zero mean derivatives, and strict-gap results for the full three-parameter covariance model and a specified mixed mean/covariance model. The covariance-only classification gives an explicit squeezed seed and weight condition when the tangent plane has a trace component. These statements have separate frozen proofs; they are not counted as four solutions of the original problem.

## What is known already

[Chang, Genoni and Albarelli, *Communications Physics* 9, 126 (2026)](https://www.nature.com/articles/s42005-026-02550-6), give the finite Gaussian Holevo optimization and an analytic two-parameter covariance formula. Their final published Eq. (76) already contains a formula independently recovered in our round 39. That formula is **not a new result of this project**. The archive includes the explicit source comparison; the publisher's covariance convention is $$\sigma=2V$$.

The present notes concern measurement attainability. Their proofs compare the Gaussian measurement noise with the full observable optimization and control homodyne boundaries. They leave general trace-bearing planes with arbitrary mean derivatives, general parameter counts, and multiple modes unresolved. The specific classifications have internal AI review; exhaustive priority checking and independent human confirmation remain pending.


## Proofs and reproducibility

- [Round 40, record 141: exact statement and full proof]({{ '/assets/code/agentic/gaussian-holevo-equality/round-40-record-141-proof.txt' | relative_url }}).
- [Round 40, record 142: exact statement and full proof]({{ '/assets/code/agentic/gaussian-holevo-equality/round-40-record-142-proof.txt' | relative_url }}).
- [Round 41, record 146: exact statement and full proof]({{ '/assets/code/agentic/gaussian-holevo-equality/round-41-record-146-proof.txt' | relative_url }}).
- [Round 41, record 147: exact statement and full proof]({{ '/assets/code/agentic/gaussian-holevo-equality/round-41-record-147-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
