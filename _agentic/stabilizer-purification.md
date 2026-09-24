---
layout: page
title: Purifying an unknown qubit with stabilizer operations
description: A five-copy deterministic protocol improves every pure qubit at a specified noise level, refuting the arbitrary-copy no-go equality.
date: 2026-09-24
status: counterexample candidate
target: QIQCOP problem op_a64dc63d6ae49127
pdf: stabilizer-purification.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Full manuscript (PDF)]({{ '/assets/pdf/agentic/stabilizer-purification.pdf' | relative_url }}) · [Proof, exact checker, reviews and manuscript source (ZIP)]({{ '/assets/code/agentic/stabilizer-purification-source.zip' | relative_url }})

**A complete counterexample candidate from round 35.** The exact arithmetic and the argument passed internal review. External expert confirmation and literature priority are still unverified.

The question is whether classically simulable operations can purify an unknown noisy quantum state. The two-copy no-go theorem is an established result. The stronger conjecture in the [QIQCOP statement](https://qiqc-op.com/problem/op_a64dc63d6ae49127/) asks for the same obstruction at every copy number.

Five copies suffice to break that stronger claim. The protocol is small enough to describe in full:

1. Pick one of the six signed Pauli axes uniformly.
2. Measure four inputs in that basis.
3. If all four outcomes match the chosen sign, prepare that Pauli eigenstate. Otherwise keep the untouched fifth input.

Every operation is a stabilizer operation. The protocol always produces an output, and it does not know the target state.

Submitted for specialist review as [QIQC issue #108](https://github.com/Naixu-Guo/quantum-open-problems/issues/108). The issue is pending; no catalog acceptance is implied.

## The exact gain

Write the input as $$\rho_t(r)=(I+t\,r\cdot\sigma)/2$$, with $$\lVert r\rVert=1$$ and noise $$\delta=1-t$$. Keeping one input has target fidelity $$(1+t)/2$$. The protocol improves it by exactly

$$
G_t(r)=\frac{t-6t^3+(4t^3-t^5)(r_x^4+r_y^4+r_z^4)}{96}.
$$

At $$\delta=2/3$$, the inequality $$r_x^4+r_y^4+r_z^4\ge1/3$$ gives

$$
F(r)\ge\frac{11693}{17496}=\frac23+\frac{29}{17496}>\frac23
$$

for **every** pure qubit target. Its Haar average is $$325/486=2/3+1/486$$. This is a pointwise guarantee, without postselection on a favorable set of targets.

The manuscript also gives a four-copy postselection example at $$\delta=1/2$$. Measuring all four inputs in the computational basis, accepting only 0000, and preparing $$|0\rangle$$ gives average success $$121/1280$$ and Haar-conditional fidelity $$547/726>3/4$$. This shorter example uses the success-weighted definition in the source; it does not improve every individual target.

## What the result resolves

An admissible counterexample is enough to refute the original universally quantified equality. The result does not determine the optimal fidelity for each copy number, and it does not contradict the analytical two-copy theorem.

The four-copy example conflicts with the numerical four-copy no-go statement in [He et al., arXiv:2504.10516v2](https://arxiv.org/abs/2504.10516v2), under its displayed fidelity definition. The manuscript identifies that precise discrepancy without speculating about an unpublished implementation. The final subscription-only article and supplement were not checked in full.

## How it was checked

The proof establishes complete stabilizer preservation, including arbitrary reference systems. Exact rational calculations verify the displayed fractions, the signed-axis polynomial, and 1024 Pauli Choi coefficients for the four-copy branch. The archived checker was rerun twice in isolated processes before publication. Its job is to check those identities; it does not replace the protocol argument.

The archive retains the unchanged round-35 proof, internal review, reproduction outputs, and this manuscript's source. It also records a corrected arithmetic error from an earlier draft. K-Dense's [scientific-writing skill](https://doi.org/10.48550/arXiv.2609.00065) helped organize the evidence and exposition. This is an AI-assisted research result awaiting specialist review.
