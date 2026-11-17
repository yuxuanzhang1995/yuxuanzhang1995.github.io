---
layout: page
title: Optimal check weight for two-logical-qubit codes of lengths eleven and twelve
description: Weight five is necessary and sufficient in both distance-four cases, with an analytic eleven-qubit converse and a complete classification-based twelve-qubit exclusion.
date: 2026-11-17
status: Complete proof candidate · sequential internal review
target: Finite stabilizer codes · Wei et al., Table 2
pdf: lowweight-two-logical-distance-four-v1.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang · Version 1.0, 17 November 2026**

[Full manuscript (PDF)]({{ '/assets/pdf/agentic/lowweight-two-logical-distance-four-v1.pdf' | relative_url }}) · [Source and executable certificate (ZIP)]({{ '/assets/code/agentic/lowweight-two-logical-distance-four-v1.zip' | relative_url }}) · [Release metadata]({{ '/assets/code/agentic/lowweight-two-logical-distance-four-v1.json' | relative_url }})

A stabilizer code can have many different generating sets. The lightest
presentation minimizes the largest Pauli support among the generators. We
determine this optimum for codes encoding two logical qubits at distance at
least four, using either eleven or twelve physical qubits:

$$
W_{\mathrm{opt}}(11,2,d\ge4)=W_{\mathrm{opt}}(12,2,d\ge4)=5.
$$

The minimization includes all binary stabilizer codes and all generating
bases, including degenerate and non-CSS codes. Both entries were left at
**4–6** in [Wei et al., *Theory of low-weight quantum codes*, version 2,
Table 2](https://arxiv.org/html/2601.19848v2). This result closes those two
finite intervals.

## Why four is not enough

At eleven qubits, an exact shadow-enumerator identity bounds the number of
short stabilizer elements. Nine independent generators of weight at most
four would saturate that bound. A weight-one generator would shorten to an
impossible ten-qubit code; weight-three elements are excluded by equality.
All nine generators would therefore have even weight. Weight parity is
linear on a commuting Pauli space, so the entire stabilizer would have even
weight, contradicting another equality condition in the same certificate.
The manuscript gives the two exact identities and the shortening argument.

At twelve qubits, the converse uses the
[Danielsen–Parker classification](https://arxiv.org/abs/math/0504522v4).
Every possible stabilizer extends to a maximal commuting Pauli space, and
each such parent is equivalent to a classified graph code. Inside a fixed
parent, all candidate stabilizers are indexed by binary two-dimensional
subspaces. Two explicit syndrome tests enforce distance at least four;
one of them handles low-weight stabilizers and is needed for degeneracy.
A rank test then decides whether *any* weight-four generating basis exists.

The complete calculation reads **1,323,363 parent representatives**, including
decomposable codes. After a necessary parent-rank test, it examines
**320,777,184 admissible subspaces**. None has the required rank ten among
its weight-at-most-four elements. The largest rank found is nine. This is
an exhaustive finite exclusion using a published classification, rather than
a timeout or a search restricted to one family of displayed generators.

## Matching constructions

The manuscript lists a weight-five generating basis at each length. Exact
enumeration checks commutation, independence, stabilizer signs and the entire
symplectic dual. Both codes have distance exactly four: their numbers of
weight-four logical Paulis are 60 and 54, respectively.

Appending a fixed qubit to the eleven-qubit construction also proves the
twelve-qubit upper bound and supplies a degenerate positive control. A
separate twelve-qubit construction without weight-one stabilizers is listed
as well.

## Reproduction and scope

Extract the source package into an empty directory and run:

```sh
python3 reproduce.py
```

Python 3.10 or later and a C++17 compiler are sufficient. The package includes
the classification input with its source and checksum, so the checks need
no network connection. The runner recomputes the witnesses, analytic
identities and controls, then reruns the complete twelve-qubit exclusion.

The source comparison also checks the two public
[QEC Challenge distance-four constructions](https://github.com/unitaryfoundation/qldpc-challenge/tree/main/codes).
For each, the span of *all* stabilizer elements of weight at most five has
rank six, while weight six gives rank ten. Their actual optimum is six;
changing the displayed basis does not already produce the new upper bound.

The contribution is a pair of exact finite optima. Shadow enumerators,
shortening, graph-code classification and rank tests are inherited methods.
The result does not settle the general asymptotic question about low-weight
quantum codes.

**Review status.** The full proof received sequential internal review, and
three separately implemented classification calculations agreed. This is
not independent expert review or formal verification. The twelve-qubit
converse depends on the published self-dual classification. The checked
primary sources support a distinct contribution; worldwide first priority
has not been established. This website release is not a claim of journal or
problem-catalog acceptance.

The author directed the research and revision. AI assistance contributed to
candidate derivations, literature comparison, implementation, checking and
drafting. The manuscript records the same scope and review status.
