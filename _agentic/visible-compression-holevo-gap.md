---
layout: page
title: "A fixed-source gap above the Holevo rate for visible quantum compression"
description: "A finite four-qubit ensemble has Holevo information one bit but requires at least 1.12098 qubits per signal, even with free shared classical randomness."
date: "2026-11-16T00:00:00+01:00"
permalink: /agentic-research/visible-compression-holevo-gap/
status: "Complete proof candidate · internal review"
target: "Visible quantum compression · Winter's common-randomness conjecture"
pdf: "visible-compression-holevo-gap-v1.pdf"
---

Yuxuan Zhang · 16 November 2026 · Version 1.0

If Alice knows which mixed quantum state Bob should receive, can she compress
it to its Holevo information when they share as much classical randomness as
they like? This manuscript gives an explicit counterexample: a fixed
ensemble of four-qubit states has Holevo information one bit, while every
asymptotically accurate protocol needs at least **1.12098 qubits per signal**.

The result covers arbitrary mixed encodings, collective decoding channels,
and any amount of independent shared classical randomness. It is a complete
proof candidate that has passed sequential internal analytical review and
exact diagnostic checks. Independent expert review and publication priority
remain unconfirmed.

[Full paper (PDF)]({{ '/assets/pdf/agentic/visible-compression-holevo-gap-v1.pdf' | relative_url }})
· [Source, checks and review (ZIP)]({{ '/assets/code/agentic/visible-compression-holevo-gap-v1.zip' | relative_url }})
· [Version and SHA-256 metadata]({{ '/assets/code/agentic/visible-compression-holevo-gap-v1.json' | relative_url }})

## The source and the bound

Take the 255 nonidentity Hermitian four-qubit Pauli operators, each with
both signs. The resulting 510 labels are equally likely, and the signal is

$$
W_{P,b}=\frac{I+bP}{16},\qquad b\in\{-1,1\}.
$$

Each state is maximally mixed on an eight-dimensional subspace, with entropy
three bits. Their average is the maximally mixed four-qubit state, with
entropy four. The Holevo information is therefore exactly one bit.

For every blocklength $$n$$ and message dimension $$m$$, the average block
trace-distance error obeys

$$
1-\varepsilon_n\le m^{3/4}\left(\frac{53}{170}\right)^{n/2}.
$$

It follows that the communication rate satisfies

$$
R_{\mathrm{vis},q,\mathrm{cr}}
\ge \frac23\log_2\frac{170}{53}
=1.1209803210\ldots>1.
$$

Below this lower bound by $$\delta$$ qubits per signal, the error is at
least $$1-2^{-3\delta n/4}$$. The exact optimal rate of this ensemble is
still unknown; directly sending the state gives an upper bound of four.

The shared seed is averaged **before** taking the trace distance:

$$
\widehat W_{x^n}=\sum_s q_n(s)\mathcal D_{n,s}(\tau_{x^n,s}),
\qquad
\varepsilon_n=\frac12\sum_{x^n}p^n(x^n)
\|W_{x^n}-\widehat W_{x^n}\|_1.
$$

This is the error criterion in the
[QIQCOP problem](https://qiqc-op.com/problem/op_1ab8b10386bddd66/).
No shared entanglement or additional communication is allowed.

## Why the bound survives collective decoding

Each target state lies inside the support projector
$$Q_{P,b}=(I+bP)/2$$. Accurate reconstruction must pass the corresponding
support test with high probability. Averaging two copies of these projectors
gives a particularly simple operator:

$$
\mathbb E_x Q_x\otimes Q_x
=\frac{127}{510}I+\frac{4}{255}F,
$$

where $$F$$ exchanges the two copies. For an independent block of labels,
the moment expands into operators that exchange any subset of the sites.

For an arbitrary collective decoder, the contribution of each subset is
the purity of the Choi matrix of that decoder after tracing out the other
output sites. A channel from dimension $$m$$ to dimension $$d$$ has
unnormalized Choi purity at most $$\min(m^2,md)$$. Applying both bounds
across all subsets gives the tensor-power estimate above.

The estimate holds for every decoder separately. Mixing decoders with a
shared random seed preserves it because the support-test acceptance
probability is affine in the reconstructed state. No restriction to product
decoders or pure messages enters the argument.

## Relation to earlier work

[Winter's 2002 Conjecture 23](https://arxiv.org/abs/quant-ph/0208131) proposes
Holevo-rate visible compression with common randomness at a prescribed
rate. The present counterexample allows an unrestricted amount of that
resource, so it also contradicts the proposed communication rate.

One-shot separations between information and compression cost were already
known. [Jain, Radhakrishnan and Sen](https://arxiv.org/abs/cs/0304020)
used random-subspace ensembles and support tests;
[Bab Hadiashar and Nayak](https://arxiv.org/abs/1905.02110) established
one-shot incompressibility with general decoding channels. The contribution
here is a fixed finite Pauli ensemble with a converse for every tensor
power, including arbitrary shared classical randomness.

[Hayashi's formula](https://arxiv.org/abs/quant-ph/0511267) concerns the
unassisted visible rate. [Nator and Pereg](https://arxiv.org/abs/2404.18297)
study classical communication with shared randomness, and
[Baghali Khanian](https://arxiv.org/abs/2206.09415v2) gives strong-converse
bounds in an unassisted compression model. These results address related
resource settings. The source package records the theorem-level comparison;
the targeted search did not identify an equivalent fixed-source result.

## Checks and limits

The review traced the Pauli moment, the partial-Choi identity, the dimension
bound and the seed-averaging step for arbitrary blocklength. Finite checks
include Pauli basis identities through four qubits, arbitrary-channel
moment comparisons, extremal channels and deliberately incorrect versions
that the checks reject.

A separately implemented exact calculation uses a complex rational
collective decoder with a three-dimensional message and two output qubits.
Direct enumeration of all 36 labels and the partial-Choi calculation both
give the moment $$10442900/25431849$$. This is an internal diagnostic,
not an independent proof of the arbitrary-blocklength theorem.

The manuscript was developed with AI assistance for derivation, literature
comparison, computations and drafting under the author's research direction.
Its mathematical claim is open to external scrutiny. The website release
does not establish first priority or acceptance by the problem catalog.
