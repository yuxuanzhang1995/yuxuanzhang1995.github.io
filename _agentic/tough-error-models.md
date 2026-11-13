---
layout: page
title: "Scalar compressions and asymptotically optimal tough error models"
description: "A complete candidate for the asymptotic tough-error-model problem: universal bounds differ by at most one code dimension, with explicit nearly worst-case error spaces."
date: "2026-11-13T00:00:00+01:00"
permalink: /agentic-research/tough-error-models/
status: "Complete asymptotic proof candidate · internal review"
target: "QIQCOP · Tough error models"
pdf: "tough-error-models-v1.pdf"
---

13 November 2026 · Review version 1.0

If an error space has dimension e and acts on an n-dimensional quantum
system, how much quantum information must remain exactly correctable,
regardless of the particular errors? The
[tough-error-model problem](https://qiqc-op.com/problem/op_b1b41f737f9b4aeb/)
asks for this worst-case guarantee and for explicit error spaces that
nearly attain it.

The manuscript gives a complete proof candidate for the original question's
asymptotically matching-bounds option. Its two bounds differ by at most one
code dimension. The proof has received sequential internal analytical
review; independent review and comprehensive novelty assessment remain
outstanding.

[Full paper (PDF)]({{ '/assets/pdf/agentic/tough-error-models-v1.pdf' | relative_url }})
· [LaTeX source]({{ '/assets/code/agentic/tough-error-models-v1.tex' | relative_url }})
· [Source and exact checks (ZIP)]({{ '/assets/code/agentic/tough-error-models-v1.zip' | relative_url }})
· [Version and SHA-256 metadata]({{ '/assets/code/agentic/tough-error-models-v1.json' | relative_url }})

## The result and its scope

Let an error model be an arbitrary complex linear space
$$\mathcal E\subseteq M_n(\mathbb C)$$ of dimension e. A subspace C
corrects it when its projection satisfies the Knill–Laflamme conditions

$$
P_C A^*B P_C=\lambda(A,B)P_C
\qquad\text{for every }A,B\in\mathcal E.
$$

Let c(e,n) be the minimum, over these error spaces, of the largest
correcting-code dimension. For every integer n ≥ 1 and 1 ≤ e ≤ n²,
the proposed bounds are

$$
\max\left\{1,\left\lfloor\frac{n+1}{e^2+1}\right\rfloor\right\}
\le c(e,n)\le
\left\lceil\frac{n}{e^2+1}\right\rceil.
$$

The upper bound is attained by explicit error spaces. Their largest codes
are therefore within one dimension of the worst possible value. Uniformly,

$$
\left|c(e,n)-\frac{n}{e^2+1}\right|<1,
$$

and the ratio of c(e,n) to n/(e²+1) tends to one whenever n/(e²+1) tends
to infinity, including when e varies with n.

This is the arbitrary linear-error formulation of the original problem.
The errors need not include the identity, and no trace-preserving Kraus
normalization is assumed. The result concerns the dimension of a code,
not the logarithm of that dimension or an efficient algorithm for finding it.
Some exact finite values remain open; the displayed bounds leave
1 ≤ c(2,6) ≤ 2.

## Why a large scalar compression must exist

The lower bound follows from a theorem about any D-dimensional operator
system: a complex matrix space that contains the identity and is closed
under adjoints. Such a system has a rank-k scalar compression whenever
2 ≤ k ≤ n and n ≥ Dk − 1. For an error space, the relevant system is

$$
\mathcal V_{\mathcal E}
=\operatorname{span}_{\mathbb C}\{I,A_i^*A_j:1\le i,j\le e\},
\qquad \dim\mathcal V_{\mathcal E}\le e^2+1.
$$

Choose a Hermitian basis containing the identity and D − 1 observables,
and an n-by-k isometry X. Write

$$
G_j=X^*H_jX,\qquad
T_j=G_j-\frac{\operatorname{Tr}G_j}{k}I_k,\qquad
F(X)=\sum_j\operatorname{Tr}(T_j^2).
$$

The nonnegative function F vanishes precisely at a scalar compression.
It attains a minimum because the space of isometries is compact. Suppose
that minimum were positive. Stationarity gives

$$
\sum_jH_jXT_j=XS,\qquad S=\sum_jG_jT_j.
$$

Consequently, the matrices

$$
M=[X,H_1X,\ldots,H_{D-1}X],\qquad
B=[-S;T_1;\ldots;T_{D-1}]
$$

satisfy MB = 0, where the semicolons indicate vertical blocks. At least
one traceless Hermitian block is nonzero, so B has rank at least two.
Thus rank M ≤ Dk − 2 < n. There is a unit vector y orthogonal to every
column of M.

Rotate column a of X toward y while leaving the other columns fixed.
Each rotation remains an isometry. Common orthogonality makes the first
variation of every compressed observable vanish. The second variations
of F along the k rotations satisfy

$$
\sum_{a=1}^k F_a''(0)=-4F(X)<0.
$$

At a minimum all those second derivatives must be nonnegative. This
contradiction forces F(X) = 0. The PDF derives the differential, the
rank defect, and the second-variation identity explicitly.

## Explicit tough models

For e < n, split the ambient space into min(n,e²+1) balanced coordinate
blocks. Label them by zero and a truncated list of vectors

$$
u_i,\qquad u_i+u_j,\qquad u_i+\mathrm{i}u_j\quad(i<j),
$$

with all coordinate vectors u_i first. Define error A_a to be the a-th
coordinate of the label on each block. The e errors are independent.
Their pairwise products, together with the identity, span all the block
projections: cross-products isolate pair labels, diagonal products isolate
coordinate labels, and the identity supplies the zero block.

If a code scalar-compresses every block projection, at least one compressed
projection is a positive multiple of the code projection. Its rank bounds
the code dimension by the largest block. That block is itself a code, so
the largest code has exactly ceil(n/(e²+1)) dimensions. The argument also
covers subspaces whose vectors extend across several blocks. For e ≥ n,
including all rank-one coordinate projections among the errors and
extending to dimension e gives largest-code dimension one.

For example, on five dimensions,

$$
A_1=\operatorname{diag}(0,1,0,1,1),\qquad
A_2=\operatorname{diag}(0,0,1,1,\mathrm{i})
$$

have no two-dimensional correcting code. Replacing the five coordinates
by balanced blocks gives the upper construction for two errors at larger n.

## Relation to earlier work

The original collection of
[Krüger and Werner](https://arxiv.org/abs/quant-ph/0504166) records the
[Knill–Laflamme–Viola](https://arxiv.org/abs/quant-ph/9908066) guarantee
of order n/[e²(e²+1)].
[Weaver's operator-system theorem](https://msp.org/pjm/2019/301-1/pjm-v301-n1-p14-p.pdf)
uses diagonal compression followed by a convex partition.
[Allen and Kornell, Theorem 2.7](https://arxiv.org/html/2507.04128v2)
improve the small-dimensional bounds; for two errors their theorem gives
ceil(n/9), compared with the asymptotic coefficient 1/5 here. Their
dimension-three scalar-compression threshold is sharper than the universal
threshold used in this manuscript.

The rank-one spanning vectors are inherited from
[Li and Tam](https://doi.org/10.1137/S0895479892240683), and the block-rank
obstruction is Weaver's Proposition 2.1. The proposed new ingredient is
the variational lower bound for arbitrary operator systems. Recent work
by [Gupta and collaborators](https://arxiv.org/abs/2604.21800) and
[Sun and collaborators](https://arxiv.org/abs/2610.01992) studies related
compression geometry for Pauli detection; the inspected statements do
not imply this unconditional dimension guarantee. The manuscript also
compares Reimpell's earlier tough-model analysis.

These are comparisons with specific primary-source statements. They do
not establish exhaustive priority. The full integer-threshold conjecture
for general operator systems remains outside the result proved here.

## Review and reproducibility

The proof and its original-problem scope were read analytically in full.
Exact arithmetic checks reconstruct nine local second-variation identities
and reject nine controls that violate the common-orthogonality hypothesis.
A separate checker exercises the block construction, its dimension and
normalization assumptions, and deliberately incorrect variants.
These finite checks support calculations; the universal theorem rests
on the analytic proof.

The source package includes the full manuscript, both checkers, a replay
command, hashes and review scope. The PDF is the same seven-page review
draft approved for this website release. The derivation, literature work,
computation and drafting used AI assistance under human direction; the
current proof review was sequential within the same agent. There has been
no independent expert acceptance, formal proof-assistant certification or
verified first-publication claim.
