---
layout: page
title: Polynomial-time local-unitary equivalence of graph states
description: A complete edge-change space connects incidence compression to the graph-state LU decision problem.
date: 2026-09-22
last_revised: 2026-09-23
status: proof candidate
pdf: graph-lu-polynomial.pdf
target: QIQCOP problem op_66affd4b198fd445
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 22 September 2026

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/graph-lu-polynomial.pdf' | relative_url }}">Manuscript (PDF)</a> &middot; <a href="{{ '/assets/code/agentic/graph-lu-polynomial-source.zip' | relative_url }}">Source and exact checks (ZIP)</a> &middot; <a href="https://github.com/Naixu-Guo/quantum-open-problems/issues/97">QIQC submission</a></p>

Can two graph states be transformed into one another by changing the basis of each qubit separately? The states are specified by finite graphs, but the allowed transformations range over arbitrary single-qubit unitaries. [Claudet and Perdrix](https://doi.org/10.4230/LIPIcs.ICALP.2025.59) gave an exact quasipolynomial-time algorithm. This manuscript proposes a polynomial-time replacement for its expensive incidence computation.

**The result is a proof candidate; independent expert review and priority verification are pending.**

## Local-unitary equivalence

For graphs $$G,H$$ on the same labelled set of $$n$$ vertices, the decision problem asks whether

$$
|H\rangle=e^{i\phi}\left(\bigotimes_{v=1}^{n}U_v\right)|G\rangle
$$

for single-qubit unitaries $$U_v$$ and a global phase $$\phi$$. The input is the two adjacency matrices. Equality is exact, and vertex labels stay fixed. This is the [QIQCOP problem](https://qiqc-op.com/problem/op_66affd4b198fd445/) addressed here.

The local-Clifford version already has a polynomial-time algorithm: its graph operations are ordinary local complementations. Arbitrary local unitaries give a larger equivalence relation. Claudet and Perdrix handle the additional freedom by first putting the graphs into a common standard form. A surviving pair can then be related by one generalized complementation on an independent set $$X$$, followed by ordinary complementations on a separate set $$W$$.

This reduces the task to understanding the generalized operation. Its input is a vector of multiplicities on $$X$$. Only vectors satisfying certain common-neighbor congruences are valid. Each valid vector determines which edges the operation toggles.

## Admissible edge changes

Let $$\Sigma$$ be the set of valid multiplicity vectors, and let $$f(s)$$ record the edges toggled by $$s$$. The set

$$
\Omega=f(\Sigma)
$$

is a binary vector space. The graph reduction needs a basis of this **complete space**, with multiplicities realizing the basis vectors.

A basis suffices because each basis vector can be represented by a group of degree-two auxiliary vertices. Complementing the entire group produces that edge change. Constraints require each group to be used in its entirety or left unused. The constrained local-Clifford algorithm then decides whether some combination of these groups, together with the allowed ordinary operations, reaches the target graph. It makes this decision in polynomial time without enumerating all combinations.

Proposition 2.4 in the manuscript states this input-output relation explicitly. The task left to our construction is therefore precise: compute all of $$\Omega$$ efficiently. The existing algorithm obtains it by writing one incidence constraint for each of many vertex subsets. At the required level $$r=O(\log n)$$, this enumeration produces the quasipolynomial running time.

## Incidence compression

Let $$a_v$$ record the neighbors of a vertex $$v$$ in $$X$$, and let $$a_K$$ be the coordinatewise product of the vectors indexed by a set $$K$$. After expressing every congruence modulo $$2^r$$, its row is $$2a_K$$ for pairs and triples, then $$2^{|K|-2}a_K$$ for larger sets.

These rows are related. Once $$|K|\geq3$$, adding a vertex to $$K$$ applies the fixed map

$$
T_v(z)=2a_v\odot z.
$$

Starting with pair and triple rows and closing under these maps generates every required constraint. Both kinds of starting row are necessary: pairs and triples have the same coefficient, whereas applying $$T_v$$ introduces another factor of two.

An integer Hermite basis represents the generated row module with at most $$|X|$$ rows. Its retained entries are bounded by $$2^r$$, and closure stabilizes after at most $$\max\{0,\min(r-2,t-3)\}$$ strict enlargements, where $$t$$ is the number of vertices outside $$X$$. The manuscript proves both the equality of the generated module and the polynomial bit complexity of its computation.

The compressed matrix has exactly the same solutions $$\Sigma$$ as the original congruences. To recover them all, the construction uses an integer lattice to generate the entire kernel over $$\mathbb Z/2^r\mathbb Z$$, including when that kernel is not free. Mapping those generators through $$f$$ and performing binary elimination gives a basis of $$\Omega$$. The corresponding multiplicities are carried through the elimination, so every output basis vector has a witness.

## The decision algorithm

The two parts now fit together. The graph reduction needs the complete edge-change space; the algebraic construction computes it in polynomial time. The final algorithm handles connected components separately, runs the standard-form reduction, computes $$\Omega$$, and invokes the constrained Clifford test. If $$\Omega$$ is zero, a separate branch uses ordinary LC equivalence on the original standard forms. Section 5 combines the correctness statements and the bit-complexity bounds to prove the main theorem.

The theorem concerns worst-case complexity for arbitrary finite simple graphs. The full algorithm has not yet been implemented: the supplied code checks the algebraic construction and a restricted graph-reduction step, while the polynomial minimal-local-set cover and standardization routines remain to be implemented. The auxiliary graphs can also be large, so practical running time requires separate study.

Appendix A supplies the graph-reduction details, Appendix B records the exact computations and their exclusions, Appendix C gives source locators, and Appendix D expands the constrained Clifford test. The checks include the known [27-vertex construction of Tsimakuridze and Gühne](https://arxiv.org/abs/1611.06938), whose states are LU-equivalent but not LC-equivalent; that graph pair and its separation are credited to their work.

The result arose in round 21 of the research campaign. The [frozen proof]({{ '/assets/code/agentic/graph-lu-polynomial-proof.txt' | relative_url }}) and historical review record remain in the source archive. The arguments, code, and manuscript involved substantial AI assistance. [Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065) supplied writing and evidence-tracking guidance. The public submission is [QIQC issue #97](https://github.com/Naixu-Guo/quantum-open-problems/issues/97).
