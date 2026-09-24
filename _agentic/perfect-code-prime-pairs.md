---
layout: page
title: "Excluded prime-pair dimensions for perfect two-error quantum codes"
description: "A direct quantum Lloyd argument excludes two infinite mixed-prime families without a stabilizer assumption."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_644f1aced78f36c9
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/perfect-code-prime-pairs-source.zip">Full proofs, source and checks (ZIP)</a> &middot; <a href="https://github.com/Naixu-Guo/quantum-open-problems/issues/107">QIQC report #107</a></p>

A perfect two-error quantum code would partition the entire physical Hilbert space into mutually orthogonal correctable-error subspaces. For local dimensions with more than one prime factor, the general existence question remains open. These notes exclude an infinite collection of such dimensions by a direct quantum Lloyd argument.

Let $$p,\ell$$ be distinct odd primes satisfying

$$
p\equiv2\pmod3,\qquad \ell\equiv7\pmod{24},\qquad
\left(\frac p\ell\right)=-1,
$$

where the last expression is the Legendre symbol. For every pair of integers $$a,b\geq1$$, set $$q=p^a\ell^b$$. The claimed theorem rules out a pure perfect quantum code of any length $$n$$ and any integer code dimension $$K>1$$ in $$(\mathbb C^q)^{\otimes n}$$, correcting the cyclic Weyl errors of weight at most two.

In particular, it excludes

$$
q=5^a7^b\quad\text{and}\quad q=17^a7^b
\qquad(a,b\geq1).
$$

No stabilizer structure is assumed, and $$K$$ need not be a power of $$q$$. Purity and perfection mean, respectively,

$$
PE^\dagger FP=\delta_{E,F}P\quad(E,F\in\mathcal E_2),
$$

$$
K\left[1+n(q^2-1)+\binom n2(q^2-1)^2\right]=q^n,
$$

where $$P$$ is the code projector and $$\mathcal E_2$$ is the phase-free tensor Weyl error set of weight at most two. These are the conventions of the [catalog problem](https://qiqc-op.com/problem/op_644f1aced78f36c9/).

## The obstruction

The proof first derives the quantum Lloyd condition directly for arbitrary integer $$q$$: the degree-two Lloyd polynomial must have two distinct integer roots in $$[5,n]$$. The sum and product of those roots restrict their prime support. Quadratic reciprocity then forces an odd exponent of $$p$$, while reduction modulo three makes the root discriminant both zero and one modulo three. The contradiction excludes the stated prime pairs.

The [Li–Xing classification](https://arxiv.org/abs/0907.0049) supplies important prime-power background. The present argument establishes its needed quantum premise rather than assuming a classical code theorem automatically applies to quantum codes. The classical arithmetic literature may overlap with portions of the exclusion, so no claim of a new classical theorem or established priority is made.

The accompanying exact checker verifies representative prime conditions and arithmetic identities. The universal conclusion relies on the analytic proof, not finite enumeration. A separate attempt to transfer a broader small-prime classification has an unresolved source/enumeration discrepancy; it is documented in the archive and is **not** part of this theorem. Local dimensions outside the proved families, degenerate codes outside the purity assumption, and the general existence question remain unresolved.


## Proofs and reproducibility

- [Round 39, record 137: exact statement and full proof]({{ '/assets/code/agentic/perfect-code-prime-pairs/round-39-record-137-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
