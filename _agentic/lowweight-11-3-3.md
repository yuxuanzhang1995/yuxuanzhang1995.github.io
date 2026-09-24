---
layout: page
title: The optimal check weight of an [[11,3,3]] stabilizer code is five
description: No eight weight-four generators exist, closing the one entry the low-weight-codes table leaves open at k=3, d=3.
date: 2026-09-21
status: solved (negative)
target: QIQCOP problem op_458e9e86ccbddccb
pdf: lowweight-11-3-3.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/lowweight-11-3-3.pdf' | relative_url }}">Full article (PDF, 6 pages)</a> &middot; <a href="{{ '/assets/code/agentic/lowweight-11-3-3-source.zip' | relative_url }}">LaTeX source, verification program and provenance (ZIP)</a></p>

**Status: a negative solution, internally reviewed by two independent AI agents.** External expert
review and literature novelty remain unconfirmed. The argument is combinatorial, and the finite
enumeration it ends in is reproducible exactly.

## The question

A stabilizer code can be presented by many different generating sets, and for fault tolerance the
one that matters is the lightest. Write $$\mathrm{W}_{\mathrm{opt}}(n,k,d)$$ for the least
achievable maximum generator weight over all generating sets of the stabilizer group.

Wei, Han, He, Li and Liu [1] introduced this quantity and pinned it down for most small
parameters. At $$k=3$$, $$d=3$$ their Eq. (4) gives the value for every $$n\le 9$$ and for
$$n\ge 15$$, and the caption of their Table 2 adds $$\mathrm{W}_{\mathrm{opt}}(10,3,3)\ge 5$$.
One entry is left open. Their Table 2 records $$n=11$$ as "$$4-5$$": their general bound returns
$$\lceil 125/32\rceil = 4$$, their weight-constrained linear program also stops at four, and their
Appendix J lists an $$[\![11,3,3;5]\!]$$ code as not known to be optimal. The question [2] is
whether eight independent commuting Pauli operators of weight at most four can generate an
$$[\![11,3,d]\!]$$ stabilizer group with $$d\ge 3$$.

**They cannot. The value is five.**

## Why the published route stops at four

The obstruction is the weight-two stabilizers. Appendix F.2 of [1] handles them by *counting*:
with $$\ell=\dim L_2(G)$$ and an $$L_2$$-adapted basis, an incidence inequality (their Eq. (73))
combines with column-degree and matching estimates to give their Eq. (80), and hence the general
bound of their Theorem 4. At $$(n,k)=(11,3)$$ that chain yields four, which is exactly why the
table entry is open.

The present argument keeps the same starting points — the weight-one reduction is their Lemma 8,
and the basis adaptation is their Lemma 19(iii), neither claimed here as new — but treats
$$L_2(G)$$ *structurally* rather than by counting.

## The argument

A minimal counterexample can have no weight-one stabilizer and at most one weight-two stabilizer
per pair of qubits, since either lets one delete qubits while keeping $$k=3$$, the distance and a
weight-four basis. The surviving weight-two stabilizers then turn out to be highly constrained:
the graph they form on the qubits has cliques as its connected components, and every edge at a
given qubit carries the same Pauli label there. After local Cliffords each clique becomes a block
of $$ZZ$$ stabilizers — a *cluster*.

Each cluster can then be contracted to a single coordinate by a map that preserves the symplectic
form, carrying a *lifted weight* that records what a contracted vector costs upstairs. The
residual problem lives in $$\mathbb{F}_2^{2\tilde n}$$ with $$\tilde n$$ the number of clusters,
and the distance condition becomes a statement about syndromes there. Five counting conditions
follow: every cluster must produce a nonzero syndrome; the syndromes of the light errors must be
pairwise distinct, which bounds how many of them can be low weight; total incidence is bounded;
anticommutation incidences are even; and a refinement forces enough anticommutation to pay for
the tight pairs and a separate family of cluster pairs.

Those conditions depend only on the multiset of *cluster types*, not on the generators themselves,
which turns the search into a small enumeration. It runs in about eighty seconds and leaves
nothing for any $$n\le 11$$.

## Verification

Claude Opus 5 produced the argument and the program. Two further AI agents reviewed it
adversarially in isolated contexts, neither seeing the other's report. Each wrote its own
enumeration from the written argument alone, without reading the program, and reproduced every
counter; the second added controls at $$n=13,14,15$$ — 4088, 45881 and 370512 surviving
configurations — confirming the sieve is nowhere near vacuous, so the zeros below are not an
artefact of over-pruning.

| Block length | after (C3) | after (C2) | after (C4) | after (C5) |
|:--|--:|--:|--:|--:|
| 9 | 717 | 0 | 0 | 0 |
| 10 | 4692 | 6 | 4 | 0 |
| **11** | **28032** | **244** | **114** | **0** |
| 12 | 155364 | 3236 | 1614 | 191 |

The program uses only the Python standard library, so it needs no environment at all:

```text
python3 check_lowweight.py | diff - expected_stdout.txt
```

Six isolated runs with networking disabled produced byte-identical output. It also checks the
conditions against genuine distance-three codes — three copies of $$[\![5,1,3]\!]$$, the Steane
code, repetition-extended codes with clusters of sizes two and three, and 75 random
$$[\![7,k,3]\!]$$ codes — since a condition that failed there would be a condition that is not
necessary.

Reproduction establishes only that the program computes those counters. Whether the five
conditions are genuinely necessary is settled by the written argument, not by the program.

## What this establishes, and what it does not

The closed entry is $$\mathrm{W}_{\mathrm{opt}}(11,3,3)=5$$. The same argument gives
$$\mathrm{W}_{\mathrm{opt}}(n,3,3)\ge 5$$ for every $$3\le n\le 11$$, but **only $$n=11$$ is new**
— the smaller lengths are already in [1], and they are kept only because the same enumeration
produces them, which makes them a consistency check on the method rather than a contribution.

Nothing here is claimed for $$n\ge 12$$: at $$n=12$$ the conditions leave 191 configurations
standing, so $$\mathrm{W}_{\mathrm{opt}}(12,3,3)$$ remains open, and the least length at which
weight four becomes achievable is now confined to $$\{12,13,14\}$$.

One warning for anyone checking this. Both reviewers initially misread the convention in
Lemma 5.1 — the count of errors at a singleton cluster whose syndrome is a weight-two vector on
two generators that differ there, where the relevant Pauli may be one that *no* generator carries.
Read with the wrong convention, thirteen configurations survive at $$n=11$$ instead of none. That
lemma is the load-bearing step and is where a reader should start.

## Additional verification

**Additional verification record, 24 September 2026.** A separate round-37 derivation reaches
the same complete conclusion through elimination of low-weight stabilizers, three incidence
profiles, two analytic exclusions, and an exact search of the final two templates. It passed
two frozen internal reviews and was reproduced again before this update. Its
[unchanged proof, checker, reviews and provenance]({{ '/assets/code/agentic/lowweight-round37-source.zip' | relative_url }})
are supplied alongside the article's original cluster-based proof. These are distinct
derivations of the same result, not two solved problems. The archived proof's initial
“awaiting audit” wording records its submission time; the attached reviews record the
subsequent outcome. External expert confirmation remains pending.

Submitted for specialist review as [QIQC issue #110](https://github.com/Naixu-Guo/quantum-open-problems/issues/110). The issue is pending; no catalog acceptance is implied.

## References

1. F. Wei, Z. Han, A. Y. He, Z. Li and Z.-W. Liu, *Theory of low-weight quantum codes*, [arXiv:2601.19848v2](https://arxiv.org/abs/2601.19848v2).
2. Quantum Information and Quantum Computation Open Problem Zoo, [Weight-four generators for an [[11,3,3]] stabilizer code](https://qiqc-op.com/problem/op_458e9e86ccbddccb/).
3. Y. Wang, A. Z. Liu, R. Li, A. Kubica and Y. Gu, *Check-weight-constrained quantum codes: Bounds and examples*, [arXiv:2601.15446](https://arxiv.org/abs/2601.15446). Concurrent independent work; it does not address this finite question.
4. T. Kassis, V. Agarwal, Y. He, D. Patel and A. M. Brueckner, *Scientific Agent Skills: A Library of Procedural Knowledge for Research Agents*, [arXiv:2609.00065v2](https://arxiv.org/abs/2609.00065v2). Writing guidance consulted at commit `330c8e764435`.
