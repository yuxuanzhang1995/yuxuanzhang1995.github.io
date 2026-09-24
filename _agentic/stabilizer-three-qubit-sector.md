---
layout: page
title: "A sharp stabilizer-polar bound in a three-qubit spectral sector"
description: "The complete (1,1,6) spectral sector satisfies the proposed polar purity bound, with all equality cases characterized."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_6d9a72b32070a900
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/stabilizer-three-qubit-sector-source.zip">Full proofs, source and checks (ZIP)</a> &middot; <a href="https://github.com/Naixu-Guo/quantum-open-problems/issues/102">QIQC report #102</a></p>

The stabilizer inradius problem asks how mixed a state must be before it is guaranteed to be a convex mixture of stabilizer states. A useful equivalent formulation bounds the purity of operators that are nonnegative on every stabilizer state. These notes establish the proposed sharp bound in one complete three-qubit spectral sector.

Let $$A$$ be a Hermitian operator on three qubits such that

$$
\operatorname{Tr}A=1,\qquad \langle s\vert A\vert s\rangle\geq0
\quad\text{for every pure three-qubit stabilizer state }\vert s\rangle.
$$

The operator need not be positive semidefinite. Suppose

$$
A=cI+aP+bQ,
$$

where $$P,Q$$ are orthogonal rank-one projectors and $$a,b,c$$ are arbitrary real numbers. Thus six eigenvalues coincide, while the remaining two are unrestricted. The claimed bound is

$$
\operatorname{Tr}(A^2)\leq2.
$$

Equality holds precisely for Clifford conjugates of

$$
\frac{I+X+Y+Z}{2}\otimes\vert 00\rangle\langle00\vert .
$$

Here $$X,Y,Z$$ are the single-qubit Pauli matrices. The statement includes every eigenvalue ordering, both signs of the coefficients, and eigenvalue coalescences within this representation.

The proof combines Pauli decompositions, rank-two compression, and the known two-qubit bound. Separate arguments control coefficients of the same sign and of opposite signs. Tracking equality through these estimates forces a stabilizer-code structure and yields the displayed Clifford orbit. The accompanying code checks exact polynomial inequalities and rational bounds used in the argument. Finite stabilizer-state enumeration was an additional control, not a substitute for the general argument over $$P,Q$$.

The [QIQCOP conjecture](https://qiqc-op.com/problem/op_6d9a72b32070a900/) asks for the inradius for every number of qubits. [Zurel and Davis](https://arxiv.org/html/2602.22336v1), Conjecture 2 and Theorem 7, give the dual formulation and establish low-dimensional cases used here. This note does not settle even the unrestricted three-qubit case: operators with other spectral multiplicities remain outside the theorem. The result is a restricted sharp bound with an equality classification, internally reviewed and awaiting independent confirmation and priority checking.


## Proofs and reproducibility

- [Round 40, record 143: exact statement and full proof]({{ '/assets/code/agentic/stabilizer-three-qubit-sector/round-40-record-143-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
