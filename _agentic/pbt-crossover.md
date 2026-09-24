---
layout: page
title: The high-dimensional crossover of optimized port-based teleportation
description: A complete proof candidate gives the joint-limit fidelity for every fixed ratio of ports to dimension squared.
date: 2026-09-24
status: proof candidate
target: QIQCOP problem op_25342dbb8d64e728
pdf: pbt-crossover.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Full manuscript (PDF)]({{ '/assets/pdf/agentic/pbt-crossover.pdf' | relative_url }}) · [Frozen proof, finite checker, reviews and manuscript source (ZIP)]({{ '/assets/code/agentic/pbt-crossover-source.zip' | relative_url }})

**A complete proof candidate from round 36.** Two frozen internal reviews found no mathematical gap. The asymptotic proof has not been externally refereed, and literature priority remains unverified.

Port-based teleportation lets the receiver recover a state by selecting a port, without applying a correcting unitary. More ports improve fidelity. The question here is what happens when both the number of ports and the input dimension grow, with their ratio $$N/d^2$$ approaching a fixed positive number $$c$$.

Let $$F_d^*(N)$$ be the optimal **entanglement fidelity**, optimizing both the resource state and Alice's measurement. The [QIQCOP problem](https://qiqc-op.com/problem/op_25342dbb8d64e728/) asks whether

$$
\varphi(c)=\lim_{d\to\infty}F_d^*(\max\{1,\lfloor cd^2\rfloor\})
$$

exists for every $$c>0$$, and what it equals. The manuscript proposes a complete answer.

Submitted for specialist review as [QIQC issue #109](https://github.com/Naixu-Guo/quantum-open-problems/issues/109). The issue is pending; no catalog acceptance is implied.

## The formula

For $$0<c\le1/4$$, the answer is simply $$\varphi(c)=c$$. Above that threshold, define

$$
I_j(\mu)=\frac1\pi\int_0^\pi(\cos p-\mu)_+^j\,dp,\qquad j=1,2.
$$

There is a unique $$\mu\in(-1,1)$$ satisfying

$$
c+\frac12=\frac{I_2(\mu)}{2I_1(\mu)^2}.
$$

Then

$$
\varphi(c)=\left(\mu+\frac{I_2(\mu)}{I_1(\mu)}\right)^2.
$$

These are elementary trigonometric integrals, with their explicit evaluation in the manuscript. For example, $$\varphi(1/2)\approx0.47286612$$; a rational interval check places it between 0.472865 and 0.472867.

## Why the two limits need care

The finite optimization was already characterized by a teleportation matrix in [Mozrzymas et al.](https://arxiv.org/abs/1707.08456). A fixed-dimensional expansion cannot simply be evaluated at growing $$d$$: its remainder may depend on dimension. The proposed proof instead treats the joint limit directly.

Young diagrams become fermion configurations on a half-line, and removing a box becomes one-step hopping. An occupation bound makes the hopping commutator uniformly bounded. This controls the passage from an exact number of boxes to an average number. A one-particle trace limit then gives the upper bound.

For the lower bound, the proof constructs Slater states from sine orbitals on disjoint blocks. A variance estimate shows that their diagram size exceeds the target number of ports with probability tending to zero. Monotonicity in the number of ports brings the bound back to exactly the required $$N$$. The bounds agree for every fixed $$c>0$$.

## Scope and checks

This is a candidate answer to the entire stated crossover question, not just a new lower bound. It does not provide a finite-dimension error rate or an efficient implementation of the optimal resources.

The complete proof passed two separate frozen reviews. The finite checker verifies the branching commutator on 60 partition layers. Additional finite spectral controls and the interval evaluation test specific ingredients. They do not certify the asymptotic theorem; that rests on the written argument, especially the two transfers between fixed and mean size.

[Christandl et al., Section 8](https://doi.org/10.1007/s00220-020-03884-0), explicitly discuss the fixed-ratio limit. The [PBT–unitary-estimation correspondence](https://arxiv.org/abs/2408.11902) supplies related order estimates, which do not determine this entire function. The manuscript attributes these inputs and retains the original frozen proof for comparison. A targeted literature search found no matching formula, but that is not an exhaustive priority check.

K-Dense's [scientific-writing skill](https://doi.org/10.48550/arXiv.2609.00065) helped organize the evidence and exposition. This is an AI-assisted research manuscript awaiting independent specialist review.
