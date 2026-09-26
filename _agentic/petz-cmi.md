---
layout: page
title: The ordinary Petz recovery bound fails for three qubits
description: An explicit rank-two counterexample, with a rational-arithmetic certificate and independent numerical verification.
date: 2026-09-12
status: solved (negative)
target: QIQC ordinary-Petz recovery bound for conditional mutual information
pdf: petz-cmi.pdf
archive_doi: 10.5281/zenodo.22969546
archive_pdf: https://zenodo.org/records/22969546/files/petz-cmi.pdf
---

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/petz-cmi.pdf' | relative_url }}">Full article (PDF, 5 pages)</a> &middot; <a href="{{ '/assets/code/agentic/petz-cmi-source.zip' | relative_url }}">Source, verification code and results (ZIP)</a></p>

**Archival source:** [Manuscript PDF on Zenodo](https://zenodo.org/records/22969546/files/petz-cmi.pdf), preserved in [*Agentic Proofs for QIQC: Collected Manuscripts*, version 1.0](https://doi.org/10.5281/zenodo.22969546) (26 September 2026).

## The question

Conditional mutual information measures how much correlation remains between two systems once a third is known. The Fawzi–Renner theorem [1] gives this quantity an operational meaning: when it is small, a suitable recovery channel can approximately reconstruct a discarded subsystem.

The ordinary Petz map is a natural candidate for that channel. It is explicit, depends on the relevant marginal, and recovers the state exactly when the conditional mutual information vanishes. The question [2] is whether it also satisfies the same fidelity bound away from exact recovery.

**It does not. Three qubits already give a counterexample.**

## The counterexample

The article specifies a rank-two state on three qubits through two weights and two vectors. Its printed decimal coefficients are treated as exact rational numbers, followed by explicit trace normalization, so the state can be reconstructed without a separate data file.

Let ρ<sub>rec</sub> be the state recovered by the ordinary Petz map. With base-two logarithms and the **squared** fidelity convention, the proposed inequality reads

> I(A; B ∣ C) ≥ −log₂ F(ρ, ρ<sub>rec</sub>).

For the displayed state, the two sides are:

| Quantity | Value in bits |
|:--|--:|
| Conditional mutual information | 0.06709806645716 |
| Ordinary-Petz recovery term | 0.07137976269921 |
| Left side minus right side | **−0.00428169624205** |

The strict negative gap settles this ordinary-Petz question. The marginals used in the recovery map are positive definite. By continuity, sufficiently small admixtures of the maximally mixed state also give full-rank counterexamples.

## Verification

Claude Opus 5 supplied the solution; GPT 6 Astra independently verified it and prepared the accompanying certificate. The checks reconstruct the state from the printed coefficients, compare direct recovery with a separate Choi-matrix implementation, and repeat the calculation at 50- and 80-digit precision.

The sign of the gap is also checked by **exact rational arithmetic**. Floating-point routines propose spectral intervals and matrix approximants; the certificate then checks characteristic-polynomial signs, positivity and residual bounds exactly. Explicit remainder bounds enclose the logarithms. With outward decimal rounding, the resulting interval is

```text
−0.00428169624320 ≤ gap ≤ −0.00428169624091 < 0.
```

The downloadable archive contains the five-page article, editable LaTeX source, both numerical constructions, the certificate, pinned dependencies and saved output. After installing the listed dependencies, `python reproducibility/run_verification.py` runs the complete check from the archive's manuscript directory.

## What this establishes

The failure concerns the **ordinary, unrotated Petz map**. The Fawzi–Renner existence theorem remains valid, and an average of rotated Petz maps satisfies its recovery inequality on this same state. The example therefore separates the ordinary map's exact recovery property from the proposed quantitative bound.

A previous counterexample to a more general relative-entropy remainder bound [3] used a separately chosen reference state. Here that reference is constrained by a marginal of the state being recovered, as required by the conditional-mutual-information question.

The present construction does not identify the largest possible violation or a simplest analytic family. Those are useful follow-up questions; the explicit state and certified negative gap suffice for the inequality considered here.

## References

1. O. Fawzi and R. Renner, *Quantum conditional mutual information and approximate Markov chains*, [arXiv:1410.0664](https://arxiv.org/abs/1410.0664).
2. Quantum Information and Quantum Computation Open Problem Zoo, [Ordinary-Petz recovery bound for conditional mutual information](https://qiqc-op.com/problem/op_87c77263c8bab523/).
3. S. Bhattacharya, *Approximate recoverability and the quantum data processing inequality*, [arXiv:2309.02074v3](https://arxiv.org/abs/2309.02074v3).
