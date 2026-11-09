---
layout: page
title: "One ebit is necessary and sufficient for the elegant joint measurement"
description: "An exact LOCC lower bound for arbitrary finite-dimensional pure resources, closing the higher-Schmidt-rank gap for the tetrahedral two-qubit measurement."
date: "2026-11-09"
permalink: /agentic-research/elegant-joint-measurement-cost/
status: "Complete proof candidate · internally reviewed"
target: "QIQCOP · Exact LOCC entanglement cost of the elegant joint measurement"
pdf: "elegant-joint-measurement-cost-v1.pdf"
---

Yuxuan Zhang · 9 November 2026 · Version 1.0

**Result.** The exact deterministic LOCC entanglement cost of the two-qubit
elegant joint measurement is **one ebit**, even when the supplied pure
resource may have arbitrary finite Schmidt rank. The theorem covers the
[original QIQC Open Problems catalogue question](https://qiqc-op.com/problem/op_d40d1f65b5aaaefd/).
This release contains a complete proof candidate with internal review;
independent expert review is still outstanding.

[Full paper (PDF)]({{ '/assets/pdf/agentic/elegant-joint-measurement-cost-v1.pdf' | relative_url }})
· [Source and exact checks (ZIP)]({{ '/assets/code/agentic/elegant-joint-measurement-cost-v1.zip' | relative_url }})
· [Version and SHA-256 metadata]({{ '/assets/code/agentic/elegant-joint-measurement-cost-v1.json' | relative_url }})

## The question

Alice and Bob each hold one qubit. They want to perform the tetrahedral
elegant joint measurement using local operations, classical communication,
and a shared entangled state. The required output is a classical label
known to both parties; no quantum postmeasurement state is prescribed.

One shared Bell pair suffices: Alice teleports her qubit to Bob, who measures
both qubits and communicates the outcome. The question is whether a more
complicated pure resource, with more Schmidt coefficients but less than one
bit of entanglement entropy, could do the same job exactly.

The theorem rules this out. If $$\lambda$$ is the vector of Schmidt
probabilities of any admissible finite-dimensional pure resource, then

$$
H(\lambda)\geq 1.
$$

Equality requires the nonzero probabilities to be $$(1/2,1/2)$$. All supplied
shared entanglement is included in the cost. The lower bound holds for every
finite resource rank before taking the infimum over ranks.

## What closes the higher-rank gap

The proof combines two constraints. A coherent detector gives
$$\lambda_1\leq 2/3$$. For the second constraint, write

$$
p=\lambda_1,\qquad q=\lambda_2,\qquad
\delta=\sum_{a\geq3}\lambda_a.
$$

Every exact separable implementation of the measurement satisfies

$$
(p-q)^2\leq 4\delta(1-\delta).
$$

This inequality follows from a two-dimensional adjugate identity and
completeness of the entire measurement. It controls the imbalance of the
two leading probabilities through the total tail, with no factor depending
on the resource dimension. Combining it with the detector constraint yields
the entropy lower bound. The full paper supplies the analytic argument,
including zero-contraction branches and arbitrary finite resource rank.

## Relation to prior work

[Akibue, Miyazaki and Osaka](https://arxiv.org/html/2501.17394v4) prove a
matched-rank necessity theorem that settles rank-two resources for this
measurement. Their Section 5.3 leaves higher-rank resources open.
[Bandyopadhyay's 3 November 2026 paper](https://arxiv.org/html/2611.05317v1)
gives a simpler proof of that matched-rank result and retains the higher-rank
EJM question in Section 5.2. The contraction and effect-eigenvector reductions
used here are inherited from that line of work.

The new step proposed here is the quantitative adjugate/completeness tail
bound and its combination with the detector and entropy arguments. The
detector framework itself comes from
[Bandyopadhyay, Brassard, Kimmel and Wootters](https://arxiv.org/abs/0809.2264).
The source package includes a theorem-level comparison. Targeted primary-source
checks support the difference from the inspected papers; they do not amount
to an exhaustive priority survey.

The result is specific to the EJM. Other two-qubit bases can admit higher-rank
resources with less than one ebit. Measurement localization without
communication during the local measurement stage also uses a different
operational model from the LOCC task considered here.

## Evidence and review status

The package contains 37 exact detector checks, 90 exact algebraic and
physical-protocol checks, and a second implementation of the central
polynomial identity in 15 formal variables. A rank-three positive control
implements Bell-pair concentration followed by teleportation. Negative
controls detect incorrect algebra and an incomplete measurement. The release
runner verifies file hashes and reruns the programs in a fresh temporary
directory against their complete expected outputs.

These computations support ingredients of the written proof. They are not
a numerical extrapolation to arbitrary rank or a formal proof of the theorem.
Derivation, source comparison, computation and drafting used AI assistance
under the author's direction. Review to date is sequential and internal,
with no independent expert or proof-assistant verification.

The theorem concerns exact single-implementation cost with pure resources.
It makes no claim about mixed-resource cost, approximation, asymptotic net
consumption, or communication-free localization. This website release is
separate from journal review, arXiv submission and catalogue acceptance.
