---
layout: page
title: Deterministic quadratic-size graphs for labelled vertex-minors
description: An explicit graph on O(k²) vertices can prepare any graph on any k prescribed surviving labels.
date: 2026-11-27
status: Complete proof candidate · internal review
target: QIQCOP Zoo · Deterministic quadratic-size vertex-minor-universal graphs
pdf: labelled-vertex-minor-universal-graphs-v1.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang<sup>1,2</sup>** · Version 1.0 · 27 November 2026

<sup>1</sup> École Polytechnique Fédérale de Lausanne  
<sup>2</sup> Princeton University

[Manuscript (PDF)]({{ '/assets/pdf/agentic/labelled-vertex-minor-universal-graphs-v1.pdf' | relative_url }}) · [Paper source, review and checks (ZIP)]({{ '/assets/code/agentic/labelled-vertex-minor-universal-graphs-v1.zip' | relative_url }}) · [Original problem](https://qiqc-op.com/problem/op_4154bf4cbe0d288e/)

Suppose a network of qubits has already been built. Someone chooses any $$k$$ of its sites and specifies a graph state to be left on exactly those sites. How small can the network be if a deterministic algorithm has to produce its wiring? The prescribed sites can include any of the qubits used to control the network.

The manuscript gives a deterministic polynomial-time algorithm producing a graph with at most $$Ck^2$$ vertices for an absolute constant $$C$$. For every requested labelled graph, a sequence of local complementations and vertex deletions realizes it. The theorem concerns the cost of generating the initial graph. The proof establishes existence of the operations for a given target; finding those operations efficiently remains a separate question.

## How the construction works

Each group of switches controls one hub. Complementing at selected switches selects the hub's neighborhood. Complementing at the hub then toggles all edges within that neighborhood. Different groups only allow particular sets of choices. A subspace design ensures that, taken together, they generate every edge pattern on the surviving data vertices.

The challenge is that the recipient can ask to keep a switch or a hub itself. Each switch also touches a private error-correcting code. This lets the construction find data vertices to stand in for the prescribed controls, even after other vertices have been reserved. A final sequence of single-qubit operations transfers the programmed edges to the requested labels.

## Evidence and prior work

Cautrès and colleagues proved that the quadratic size is possible and gave deterministic constructions of quartic size. Ascoli and colleagues and Chao and Xu gave probabilistic guarantees for random graphs. This construction attains quadratic size with a deterministic graph generator. [Cautrès et al.](https://arxiv.org/abs/2402.06260) · [Ascoli et al.](https://doi.org/10.4230/LIPIcs.APPROX/RANDOM.2026.38) · [Chao and Xu](https://arxiv.org/abs/2603.13600)

The internal review checked the count of split places used in the subspace design, the field-trace rank bound and the transfer of mixed terminal types. Direct graph operations agree with the derived rule in all 4,096 incidence and selection cases of a three-switch test. Omitting the final hub operation changes the answer in 1,792 cases. The supplement also tests 903 finite-field projections and 1,116 transfer amplitudes. These tests concern individual proof steps. An implementation of the full large-parameter generator, independent specialist review and a priority determination remain outstanding.
