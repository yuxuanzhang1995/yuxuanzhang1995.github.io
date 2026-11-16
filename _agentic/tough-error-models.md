---
layout: page
title: "Scalar compressions and asymptotically optimal tough error models"
description: "Asymptotically matching tough-error bounds, now with a quantitative approximate-code search and a recovery channel with a proved error guarantee."
date: "2026-11-16T00:00:00+01:00"
permalink: /agentic-research/tough-error-models/
status: "Version 2 · constructive extension · internal review"
target: "QIQCOP · Tough error models"
pdf: "tough-error-models-v2.pdf"
---

16 November 2026 · Review version 2.0 · Yuxuan Zhang

If an error space has dimension e and acts on an n-dimensional quantum
system, how much quantum information must remain exactly correctable,
regardless of the particular errors? The
[tough-error-model problem](https://qiqc-op.com/problem/op_b1b41f737f9b4aeb/)
asks for this worst-case guarantee and for explicit error spaces that
nearly attain it.

Version 2 adds a constructive result to the earlier asymptotically matching
bounds: an explicit search for approximate codes, a proved bound on the
number of search steps, and a recovery channel with a quantitative error
guarantee. The full paper is now 13 pages; Sections 4–6 contain the new
proofs.

The earlier exact bounds still differ by at most one code dimension. The
new search guarantee is in ideal arithmetic and, for the physical recovery
corollary, assumes normalized Kraus operators and the stated dimension
threshold. It does not settle all finite integer values of the original
problem.

The integrated manuscript and reproducible checks have passed sequential
internal review. Independent expert review and comprehensive novelty
assessment remain outstanding.

[Full paper (PDF)]({{ '/assets/pdf/agentic/tough-error-models-v2.pdf' | relative_url }})
· [LaTeX source]({{ '/assets/code/agentic/tough-error-models-v2.tex' | relative_url }})
· [Source and exact checks (ZIP)]({{ '/assets/code/agentic/tough-error-models-v2.zip' | relative_url }})
· [Version and SHA-256 metadata]({{ '/assets/code/agentic/tough-error-models-v2.json' | relative_url }})

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
normalization is assumed. The result concerns the dimension of a code. The constructive extension
below supplies a separate approximate search guarantee in ideal arithmetic.
Some exact finite values remain open; the displayed bounds leave
1 ≤ c(2,6) ≤ 2.

## New in version 2: search and recovery

The existence proof can now be made quantitative. For Hermitian observables
H₁,…,Hₘ, let F be the sum of squared traceless compression residuals on a
rank-k code. Whenever k ≥ 2 and n ≥ (m+1)k−1, Theorem 4.1 proves

$$
F\le\frac{(k-1)\sqrt{k+1}}{4}\|\operatorname{grad}F\|_{\mathrm F}
 +\frac{k}{4}\max\{0,-\lambda_{\min}(\operatorname{Hess}F)\}.
$$

The gradient and Hessian use the real Frobenius metric on the Grassmannian.
A point with large residual must therefore have either a useful gradient
or a direction of negative curvature. The search takes a gradient step in
the first case; in the second, it finds a direction using one singular-vector
calculation and tests both signs of a column rotation. The complete Hessian
and decrease estimates appear in the paper.

With β = k∑ⱼhⱼ², where hⱼ ≥ ‖Hⱼ‖op, every step before reaching the target
obeys

$$
F_{\mathrm{next}}\le F-\frac{F^2}{48\beta k^3}.
$$

Consequently, at most ceil(48βk³/τ) steps attain F ≤ τ. For an arbitrary
specified error basis A₁,…,Aₑ, this controls the approximate
Knill–Laflamme residual at n ≥ (e²+1)k−1. The residual is measured relative
to that basis; rescaling the errors changes its size.

For a **physical channel**, assume instead

$$
\mathcal N(\rho)=\sum_{i=1}^e A_i\rho A_i^*,\qquad
\sum_{i=1}^e A_i^*A_i=I_n.
$$

Here e counts the supplied Kraus operators. When e ≥ 2, k ≥ 2 and
n ≥ e²k−1, Corollary 6.2 constructs an encoding X and a completely
positive, trace-preserving recovery channel D such that

$$
\|\mathcal D\circ\mathcal N\circ\mathcal E_X-\operatorname{id}_k\|_\diamond
\le\varepsilon,
\qquad \mathcal E_X(\rho)=X\rho X^*,
$$

using at most

$$
\left\lceil\frac{768e^2(e^2-1)k^4}{\varepsilon^4}\right\rceil
$$

search iterations, followed by a polar decomposition and isometric
completion, for 0 < ε ≤ 2. The decoder is specified on the whole output
space and the proof includes singular Gram matrices. Its residual bound is
2√e F^(1/4), capped at 2, in the full diamond-norm convention.

These are ideal matrix-arithmetic iteration bounds. The result does not
yet provide certified finite-precision complexity, a procedure polynomial
in the number of qubits, or exact finite termination at ε = 0. The
normalized-channel threshold does not replace the arbitrary-error threshold
in the original c(e,n) problem.

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

The variance optimization objective is already present in
[Gupta et al., Section VI.1, Eq. (103)](https://arxiv.org/html/2604.21800).
The recovery agrees on the noisy code support with the standard
[transpose/Petz map of Ng and Mandayam, Eq. (4)](https://arxiv.org/html/0909.0931).
General approximate error-correction conditions are developed by
[Bény and Oreshkov](https://arxiv.org/abs/0907.5391), with broader dilation
continuity results due to
[Kretschmann, Schlingemann and Werner](https://arxiv.org/abs/0710.2495).
The proposed extension is the uniform quantitative search analysis at the
stated dimension threshold and its explicit recovery consequence.

These are comparisons with specific primary-source statements. They do
not establish exhaustive priority. The full integer-threshold conjecture
for general operator systems remains outside the result proved here.

## Review and reproducibility

The integrated proof was read analytically in full, with separate checks
of the exact original statement, dimension assumptions, derivative
constants, singular-matrix cases and normalized-channel reduction. During
integration, one auxiliary statement about a literal left kernel was
corrected to require n > (m+1)k. The main quantitative theorem, its
threshold n ≥ (m+1)k−1, and the search bounds are unchanged.

The portable package replays the inherited exact checks, 18 exact
boundary/extension controls, and four fixed floating search runs. All
four reached their declared targets, including a run that exercised the
negative-curvature branch. Finite checks support the calculations; the
universal guarantees rest on the analytic proofs. Floating residuals are
not interval-certified numerical diamond bounds.

The package includes the complete manuscript, executable checks, clean
replay results, the review and correction record, and file hashes. The
13-page PDF was compiled and every page inspected. The derivation,
literature work, computation and drafting used AI assistance under human
direction; the proof review was sequential within the same agent. No
independent expert acceptance, formal proof-assistant certification or
verified first-publication claim is asserted.

## Earlier versions

[Website version 1.0 (PDF)]({{ '/assets/pdf/agentic/tough-error-models-v1.pdf' | relative_url }})
remains available. The
[earlier archival version 1.1](https://zenodo.org/records/24207864) and its
[catalog progress report](https://github.com/Naixu-Guo/quantum-open-problems/issues/154)
precede the constructive extension. This website release is version 2.0;
those external records have not been updated to it.
