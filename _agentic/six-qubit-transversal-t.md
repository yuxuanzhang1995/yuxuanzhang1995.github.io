---
layout: page
title: No six-qubit distance-three code admits a transversal T gate
description: An arbitrary-angle reduction and exact exhaustive certificate exclude six qubits, matching the known seven-qubit construction.
date: 2026-09-28
status: solved (negative)
target: QIQCOP problem op_ddfbbe7ca0ead0c8
pdf: six-qubit-transversal-t.pdf
author: Yuxuan Zhang
archive_doi: 10.5281/zenodo.23022433
archive_pdf: https://zenodo.org/records/23022433/files/six-qubit-transversal-t.pdf
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 28 September 2026 (PDF, 7 pages)]({{ '/assets/pdf/agentic/six-qubit-transversal-t.pdf' | relative_url }}) · [Proof, executable certificate and independent checks (ZIP)]({{ '/assets/code/agentic/six-qubit-transversal-t-source.zip' | relative_url }})

**Archival source:** [Manuscript PDF on Zenodo](https://zenodo.org/records/23022433/files/six-qubit-transversal-t.pdf), manuscript 16 in [*Agentic Proofs for QIQC: Collected Manuscripts*, version 1.1](https://doi.org/10.5281/zenodo.23022433) (28 September 2026). [QIQC report #118](https://github.com/Naixu-Guo/quantum-open-problems/issues/118) documents the manuscript; submission does not change the catalog status.

**Six qubits are insufficient for an exact transversal logical T gate on a code that corrects arbitrary single-qubit errors.** This holds even when the six physical gates differ, their angles and eigenbases are unrestricted, and the code is degenerate. Together with the existing seven-qubit construction, the exclusion makes seven the minimum block length under these assumptions.

The note gives a complete negative answer to [QIQCOP's six-qubit nonadditive-code question](https://qiqc-op.com/problem/op_ddfbbe7ca0ead0c8/). The theorem is stronger: it excludes every rank-two six-qubit code with the required error-detection property. “Solved (negative)” is this research log's label. Two distinct frozen AI reviews and exact computational controls passed; external specialist review, priority and catalog acceptance remain unconfirmed.

## Why a finite search can answer an arbitrary-angle question

The physical gate is a product of six arbitrary one-qubit unitaries. After choosing each local eigenbasis, its action is diagonal. The two logical eigenvectors must occupy different phase classes of computational basis strings.

There is still a continuous family of local angles. The key reduction replaces any proposed angles by rational ones while preserving every occupied-string phase equation. A determinant bound then shows that an appropriate power of the replacement gate has local eigenvalue ratios among the **64th roots of unity**, while still acting as the same logical T. The code and its distance are preserved.

This reduces the question to exactly **119,877,472 sorted angle vectors**. It is a completeness theorem for the search, rather than a choice to examine only a convenient family of physical gates.

## What rules out the candidates

Error correction forces the probability distributions of the two logical codewords to have the same first and second moments in the computational bits. For most allowed support pairs, a quadratic polynomial has strictly positive values on one support and strictly negative values on the other. Such a polynomial makes equal moments impossible.

Linear programming proposes these polynomials, but the proof accepts only **integer coefficients with exactly checked signs on every allowed vertex**. A failed numerical search never counts as an exclusion.

The exceptional order-eight cases require more than diagonal moments. All nine reduce by explicit local maps to two support patterns. Their off-diagonal error-detection equations contradict the nonzero amplitudes forced by the diagonal equations. The manuscript gives both contradictions, including arbitrary complex phases and the boundary cases where other amplitudes can vanish.

Lower-denominator reductions and exact support checks then close the higher-order cases:

| Modulus | Sorted angle vectors | Residual support pairs checked | Uncertified pairs |
|---|---:|---:|---:|
| 32 | 2,324,784 | 89,598 | 0 |
| 64 | 119,877,472 | 139,817 | 0 |

The residual-pair counts come after explicitly justified reductions and support exclusions. The source archive contains the complete partition counts and every verification rule.

## What was checked

The standalone certificate regenerates the finite coverage and checks the decisive integer inequalities. Both frozen reviews ran it twice in clean verifier processes. A separately written Gray-code enumeration produced exactly the same support-pair sets, and a further check validated saved integer witnesses without calling an optimizer.

As a positive boundary control, the published seven-qubit construction was reconstructed and all 211 Pauli compressions of weight at most two, together with its transversal logical phase, were checked exactly. The full proof needs both parts: the finite computation and the analytic reduction connecting it to arbitrary local gates.

The initial compiled-helper version could not run inside the verifier's temporary-folder restrictions. That failed record is retained. The released certificate uses Python and NumPy within the existing sandbox; no permissions or verification limits were relaxed.

## Relation to earlier work

[Zhang, Wu, Huang and Zeng](https://arxiv.org/abs/2504.20847) introduced the subset-sum/linear-programming method used here and supplied the seven-qubit transversal-T construction. Their six-qubit table recorded that no example had been found, without claiming a general exclusion. [He, Lu and Zeng](https://arxiv.org/abs/2510.20728) exactly classified twelve seven-qubit candidates in a complementary binary-dihedral setting; their catalog on at most six qubits concerns distance two.

The contribution here is the arbitrary-angle completeness reduction and exhaustive six-qubit exclusion. The result concerns the exact transversal model in the question. It does not rule out different non-Clifford logical phases, or protocols using measurements, code switching or additional qubits.

This result emerged in round 48 of the AI-assisted campaign. The full proof was assembled by the coordinator from reviewed lower-order results and new exact coverage checks; the last discovery block's narrower lemma remains separately recorded. The manuscript discloses substantial AI assistance. K-Dense's [Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065) guided the evidence outline, consistency checks and exposition.
