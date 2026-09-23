---
layout: page
title: Polynomial-time local-unitary equivalence of graph states
description: Generating incidence constraints by closure gives a proposed polynomial-time algorithm for graph-state LU equivalence.
date: 2026-09-22
last_revised: 2026-09-23
status: proof candidate
pdf: graph-lu-polynomial.pdf
target: QIQCOP problem op_66affd4b198fd445
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 22 September 2026

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/graph-lu-polynomial.pdf' | relative_url }}">Manuscript (PDF, 16 pages)</a> &middot; <a href="{{ '/assets/code/agentic/graph-lu-polynomial-source.zip' | relative_url }}">Source and exact checks (ZIP)</a> &middot; <a href="https://github.com/Naixu-Guo/quantum-open-problems/issues/97">QIQC submission</a></p>

A graph is a compact description of a quantum state: put a qubit at each vertex, prepare every qubit in the state $$|+\rangle$$, and apply a controlled-Z gate along each edge. Two graphs can then describe states related by a separate change of basis on each qubit. The question is whether an efficient calculation on the graphs can decide if those local unitaries exist.

This manuscript gives a proposed polynomial-time decision algorithm. It builds on the quasipolynomial algorithm of [Claudet and Perdrix](https://doi.org/10.4230/LIPIcs.ICALP.2025.59), replacing the part that enumerates high-order incidence constraints. **The result is a proof candidate; independent expert review and priority verification are pending.**

## The decision problem

Given graphs $$G,H$$ on the same labelled set of $$n$$ vertices, decide whether

$$
|H\rangle=e^{i\phi}\left(\bigotimes_{v=1}^{n}U_v\right)|G\rangle
$$

for some single-qubit unitaries $$U_v$$ and an overall phase $$\phi$$. Vertex labels stay fixed. The input consists of the two adjacency matrices, and the equality is exact.

For local Clifford operations, graph equivalence already has a polynomial-time algorithm. Allowing arbitrary single-qubit unitaries gives a larger relation, so that test alone is insufficient. Claudet and Perdrix described the additional transformations through generalized local complementation and obtained a running time of $$n^{\log_2 n+O(1)}$$. The [QIQCOP problem](https://qiqc-op.com/problem/op_66affd4b198fd445/) asks whether the general labelled decision problem admits a polynomial-time algorithm.

## Why the subset enumeration can be avoided

The expensive step has a concrete form. After putting the graphs in standard form, the algorithm considers a generalized operation on an independent set $$X$$. A vector records how many times each vertex of $$X$$ participates. Valid vectors must satisfy congruences involving the common neighbors of pairs, triples, and larger subsets. Listing all those subsets is what produces the quasipolynomial cost.

The rows of this system are not arbitrary. Let $$a_v$$ record the neighbors of $$v$$ in $$X$$. Once a constraint row for a set of at least three vertices is known, adding a new vertex applies the map

$$
T_v(z)=2a_v\odot z,
$$

where $$\odot$$ is coordinatewise multiplication. All the larger rows can therefore be generated from the triple rows. Pair rows are included separately: pairs and triples have the same weight, so applying this map to a pair would give the triple row an extra factor of two.

The computation keeps an integer Hermite basis instead of the subsets that produced the rows. If $$|X|=m$$, at most $$m$$ rows need to be retained, and their entries are bounded by $$2^r$$. The closure stabilizes after at most $$\max\{0,\min(r-2,t-3)\}$$ strict enlargements, where $$t$$ is the number of vertices outside $$X$$. Since the graph-state reduction needs only $$r=O(\log n)$$, these operations take polynomial time.

It is also necessary to recover every admissible edge change. The congruences live over $$\mathbb Z/2^r\mathbb Z$$, whose kernels need not behave like vector spaces over a field. The manuscript computes the complete kernel using an integer lattice, then maps its generators to the binary space of edge changes. A multiplicity vector is retained for each basis element. This gives precisely the space required by the remaining Claudet–Perdrix reduction.

## What the result establishes

The theorem concerns worst-case decision complexity for arbitrary finite simple graphs, including disconnected graphs. The algebraic construction and its use in the graph reduction are proved in the main text. Appendix C gives the constrained Clifford equations and the determinant test used at the final stage; Appendix B records exact source locators.

The full algorithm has not yet been implemented. The supplied code checks the incidence computation, modular kernels, edge-change spaces, and a restricted graph-reduction step. Appendix A records the test families, exclusions, and deliberately incorrect variants used as controls. One test uses the known [27-vertex construction of Tsimakuridze and Gühne](https://arxiv.org/abs/1611.06938): the generalized operation succeeds while ordinary LC equivalence fails. That graph pair and its LU-but-not-LC property belong to their work.

The remaining implementation work includes the polynomial minimal-local-set cover and standardization procedures. The auxiliary graphs can also be large, so the practical running time needs separate study.

The original result arose in round 21 of the research campaign. Its [frozen proof]({{ '/assets/code/agentic/graph-lu-polynomial-proof.txt' | relative_url }}) and historical review record are preserved in the source archive, alongside the revised manuscript, references, scripts, and outputs. The arguments, code, and exposition were developed with substantial AI assistance. [Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065) was used for writing and evidence tracking; the public record is [QIQC issue #97](https://github.com/Naixu-Guo/quantum-open-problems/issues/97).
