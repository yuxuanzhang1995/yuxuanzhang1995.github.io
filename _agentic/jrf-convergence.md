---
layout: page
title: Convergence of the JRF iteration for mixed-state discrimination
description: An analytic proof candidate for convergence of the uniformly initialized iteration, including rank-deficient states and overlapping supports.
date: 2026-09-16
status: proof candidate
target: QIQCOP problem op_76e284219621a785
pdf: jrf-convergence.pdf
---

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/jrf-convergence.pdf' | relative_url }}">Full version (PDF, 7 pages)</a> &middot; <a href="{{ '/assets/code/agentic/jrf-convergence-source.zip' | relative_url }}">LaTeX source and provenance (ZIP)</a></p>

**Status: a full proof candidate, internally reviewed by AI agents.** External expert review and
literature novelty remain unconfirmed. The argument is analytic; it has not been checked by a
formal proof assistant.

## Background

Minimum-error discrimination asks which measurement best identifies a state drawn from a known
quantum ensemble. The Ježek–Řeháček–Fiurášek (JRF) iteration [1] gives an explicit update for the
measurement. The open question [2] is whether its uniformly initialized iterates converge to an
optimal measurement for arbitrary mixed-state ensembles.

Convergence of the success probability alone would not settle the whole question: the measurement
itself must converge. Rank-deficient states also matter, since a proof that assumes each state is
invertible leaves out part of the original problem.

## The statement

Write the weighted states as $$A_i=p_i\rho_i$$, with positive priors, and work on the joint signal
support $$\mathcal H_0=\operatorname{supp}\sum_i A_i$$. For a finite ensemble of $$m$$ states, set

$$
\Pi_{i,0}=I_{\mathcal H_0}/m,\qquad
D_k=\left(\sum_i A_i\Pi_{i,k}A_i\right)^{1/2},
$$

$$
\Pi_{i,k+1}=D_k^{-1}A_i\Pi_{i,k}A_iD_k^{-1}.
$$

The manuscript proves that every finite-step inverse exists on this support and that there is a
globally optimal minimum-error POVM $$\{\Pi_{i,\infty}\}$$ with

$$
\sum_i\|\Pi_{i,k}-\Pi_{i,\infty}\|_{\mathrm{HS}}\longrightarrow0.
$$

Consequently the success probabilities converge to the optimum. The claim covers arbitrary finite
dimension, finitely many outcomes, mixed or pure states, overlapping supports, and individual
rank deficiency. It concerns the literal update above, without regularization or averaging.

## How the proof works

**Compress to the fixed supports.** Factor each weighted state on its own support and introduce
coherent factors of the POVM. Their square support compressions follow an exact multiplicative
recurrence. They stay invertible at every finite step, even when an individual state is singular
on the full signal space.

**Prove convergence before using inverse bounds.** The compressed update maximizes a linearized
strongly convex quadratic over a fixed compact convex semialgebraic set. Sufficient decrease,
a subgradient estimate at the next iterate, and subsequential continuity give the hypotheses of
the Kurdyka–Łojasiewicz convergence theorem of Attouch, Bolte and Svaiter [3, Theorem 2.9]. This
gives finite length and convergence of the compressed sequence. It does not by itself give
global optimality.

**Exclude a singular limiting normalizer.** If the limit of $$D_k$$ had a kernel, a determinant
multiplier in one support block would eventually exceed two at every step. The corresponding
bounded compression could not sustain that growth. Thus the limiting normalizer is positive
definite, and convergence transfers back to the actual POVM.

**Recover global optimality.** A cone argument for the ordered, noncommuting products forces
every dual inequality $$D_\infty\geq A_i$$. The limit also satisfies complementarity,
$$(D_\infty-A_i)\Pi_{i,\infty}=0$$. These two conditions certify the global discrimination optimum.

## Verification

The proof was generated within the QIQC agent workflow. An independent adversarial AI pass
checked the support recurrence, the precise KL hypotheses, the singular-limit contradiction,
and the multiplication order in the product lemma. A further review of the frozen proof found
no mathematical gap in the stated scope. This is internal mathematical review, not external
refereeing or formal verification.

Numerical identity checks on eight ensembles over 240 steps had maximum error below
$$3\times10^{-15}$$. These checks were used to find mistakes; they are not evidence for the
universal convergence theorem. The downloadable seven-page manuscript contains the full argument,
including the product lemma and the correspondence with the original question.

## What remains open

The candidate is intended to cover the full uniformly initialized, finite-dimensional statement
in the linked QIQCOP record. Independent expert scrutiny is still needed. Priority is not claimed;
the literature search does not establish novelty.

The proof supplies no quantitative convergence rate and makes no assertion for arbitrary
nonuniform initialization. Those are further questions beyond the theorem stated here.

## References

1. M. Ježek, J. Řeháček and J. Fiurášek, *Finding optimal strategies for minimum-error quantum-state discrimination*, [Phys. Rev. A **65**, 060301(R) (2002)](https://doi.org/10.1103/PhysRevA.65.060301).
2. QIQCOP, *Convergence of the JRF iteration for mixed-state discrimination*, problem [op_76e284219621a785](https://qiqc-op.com/problem/op_76e284219621a785/).
3. H. Attouch, J. Bolte and B. F. Svaiter, *Convergence of descent methods for semi-algebraic and tame problems: proximal algorithms, forward–backward splitting, and regularized Gauss–Seidel methods*, [Mathematical Programming **137**, 91–129 (2013)](https://doi.org/10.1007/s10107-011-0484-9), Theorem 2.9; [author manuscript](https://bolte.perso.math.cnrs.fr/MPA.pdf).
4. X. Lü and S.-H. Dong, *Iterative algorithm for minimum-error quantum state discrimination: Convergence for pure-state ensembles*, [Phys. Rev. A **113**, 022451 (2026)](https://doi.org/10.1103/q7wq-ygm9). This is the pure-state result cited in the QIQCOP record; the present claim includes mixed ensembles.
