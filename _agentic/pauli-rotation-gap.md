---
layout: page
title: The spectral gap of random Pauli rotations on four qubits is 1/15
description: A Clifford-invariant eigenvector in Λ⁸ℂ¹⁶ mixes more slowly than the conjectured fourth-moment mode, and a known lower bound then fixes the gap exactly.
date: 2026-09-28
status: solved (negative)
target: QIQCOP problem op_aaf9791beced84e4
pdf: pauli-rotation-gap.pdf
author: Yuxuan Zhang
archive_doi: 10.5281/zenodo.23032999
archive_pdf: https://zenodo.org/records/23032999/files/pauli-rotation-gap.pdf
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 28 September 2026 (PDF, 8 pages)]({{ '/assets/pdf/agentic/pauli-rotation-gap.pdf' | relative_url }}) · [Manuscript source, exact checker, mutation tests and review records (ZIP)]({{ '/assets/code/agentic/pauli-rotation-gap-source.zip' | relative_url }})

**Archival source:** [Manuscript PDF on Zenodo](https://zenodo.org/records/23032999/files/pauli-rotation-gap.pdf), manuscript 20 in [*Agentic Proofs for QIQC: Collected Manuscripts*, version 1.2](https://doi.org/10.5281/zenodo.23032999) (29 September 2026). [QIQC report #122](https://github.com/Naixu-Guo/quantum-open-problems/issues/122) documents the manuscript; submission does not change the catalog status.

**The conjectured gap fails at four qubits.** Consider the random walk on $$\mathrm{SU}(16)$$ that applies
$$e^{i\theta P}$$ with a uniformly random non-identity Pauli operator $$P$$ and a uniform angle $$\theta$$. Its
spectral gap is exactly $$1/15$$, below the conjectured $$26/255$$. The slowest mode lives in the representation
$$\Lambda^8\mathbb C^{16}$$, not in the fourth moment.

This is a complete negative answer to [the catalog's random-Pauli-rotation question](https://qiqc-op.com/problem/op_aaf9791beced84e4/).
“Solved (negative)” is the label in this research log. An isolated internal AI review of the complete proof, an independent
computation over all 255 Pauli operators, a requirements audit against the catalog record and a blind
reconstruction from the bare statements found no defect. External specialist review, historical
priority and QIQCOP acceptance remain unconfirmed.

## The question

Baer and Haah [1] proved

$$
\frac{4^n+16}{16(4^n-1)}\le\Delta_n\le\frac{2^n(2^n-3)}{8(4^n-1)}
$$

for the gap $$\Delta_n$$ of this walk on $$L^2_0(\mathrm{SU}(2^n))$$. Their Conjecture 3.48 states that the upper bound,
the value of the fourth-moment representation, is exact for $$n\ge3$$. The question [2] asks whether it holds for every
$$n\ge4$$. At $$n=4$$ the bounds read $$1/15\le\Delta_4\le26/255$$.

## The slow mode

Label the basis of $$\mathbb C^{16}$$ by $$\mathbb F_2^4$$. Each of the 30 affine hyperplanes $$A$$ of
$$\mathbb F_2^4$$ has eight points. Let $$e_A$$ be the wedge product of their basis vectors in increasing
binary order, and let

$$
w=\sum_A e_A\in\Lambda^8\mathbb C^{16}.
$$

Then $$Mw=\tfrac{14}{15}w$$ for $$M=\mathbb E_{P,\theta}\Lambda^8(e^{i\theta P})$$, and $$\|M\|=\tfrac{14}{15}$$ on
$$\Lambda^8\mathbb C^{16}$$. This irreducible representation occurs in $$L^2(\mathrm{SU}(16))$$, so
$$\Delta_4\le1/15<26/255$$, which already answers the question. The Baer–Haah lower bound equals $$1/15$$ at
$$n=4$$, so $$\Delta_4=1/15$$ exactly.

The mode can be written as a function: with $$B_0=\{0,\dots,7\}$$,
$$f(U)=\sum_A\det U[A,B_0]$$, a sum of $$8\times8$$ minors, has mean zero and satisfies
$$K_4f=\tfrac{14}{15}f$$.

## Why it works

For a $$Z$$-type Pauli operator, 28 of the 30 hyperplane wedges have charge zero, so $$P$$ keeps
$$\tfrac{28}{30}=\tfrac{14}{15}$$ of $$w$$ in its fixed space. The Clifford group fixes $$w$$ and acts
transitively on the non-identity Pauli operators, so every $$P$$ behaves in the same way. The Hadamard step
uses the self-duality of the Reed–Muller code $$\mathrm{RM}(1,3)$$.

Two independent arguments give the matching upper bound $$\|M\|\le\tfrac{14}{15}$$: a quadratic Casimir
identity, and a selection rule based on Walsh-charge divisibility and the Bose–Burton theorem. The
selection rule also shows that no irreducible representation $$\lambda$$ with $$8\nmid|\lambda|$$ can violate
the conjectured value, for any $$n\ge3$$.

## Checks

The standalone checker uses only the Python standard library. It prints 22 tagged checks: 21 are exact and
one is a floating-point check of the eigenfunction. They include:

- the charge counts;
- the order lemma and the wedge signs under all affine maps of $$\mathbb F_2^4$$;
- Clifford invariance for 20 generators by exact exterior-algebra expansion;
- an independent Lie-algebra computation of $$Mw$$ on the full 12,870-dimensional space;
- the Casimir identity and the selection rule;
- positive controls reproducing $$\Delta_3=5/63$$ and the fourth-moment value $$229/255$$;
- negative controls.

It runs in about ten seconds, and its output is byte-identical on a laptop and in a container without
network access. All 32 single-point mutations of the checker are detected.

## What this establishes, and what it does not

At $$n=4$$ the conjectured value fails and the gap is $$1/15$$, so the answer to the question is no. The slow
mode is an unbalanced representation: the centre of $$\mathrm{SU}(16)$$ acts on it nontrivially. It therefore
says nothing about convergence of moments or unitary designs, which is governed by balanced
representations. That question at $$n=4$$ and the exact gap for $$n\ge5$$ remain open.

The witness was found in round 49 of the AI-assisted campaign, after earlier rounds settled the
fourth-moment sector. The manuscript discloses AI assistance, the internal review and the independent
checks. K-Dense's [Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065) guided the evidence
record and writing.

## References

1. T. Baer and J. Haah, *Random unitary circuits with constant spectral gap*, [arXiv:2607.20919](https://arxiv.org/abs/2607.20919).
2. Quantum Information and Quantum Computation Open Problem Zoo, [Exact spectral gap of random Pauli rotations](https://qiqc-op.com/problem/op_aaf9791beced84e4/).
3. J. Haah, Y. Liu and X. Tan, *Efficient approximate unitary designs from random Pauli rotations*, Commun. Math. Phys. 406, 309 (2025), [arXiv:2402.05239](https://arxiv.org/abs/2402.05239).
4. R. C. Bose and R. C. Burton, *A characterization of flat spaces in a finite geometry and the uniqueness of the Hamming and the MacDonald codes*, J. Combin. Theory 1, 96–104 (1966).
5. T. Kassis, V. Agarwal, Y. He, D. Patel and A. M. Brueckner, *Scientific Agent Skills: A Library of Procedural Knowledge for Research Agents*, [arXiv:2609.00065v2](https://arxiv.org/abs/2609.00065v2).
