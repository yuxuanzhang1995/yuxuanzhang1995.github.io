---
layout: page
title: Optimal precision dependence of low-energy Hamiltonian simulation
description: Matching query bounds improve the intermediate-regime precision dependence for exact factor access and clean-output vector error.
date: 2026-09-21
last_revised: 2026-09-21
status: proof candidate
target: QIQCOP problem op_25d9dee5435ea835
pdf: low-energy-precision.pdf
author: Yuxuan Zhang
archive_doi: 10.5281/zenodo.22969546
archive_pdf: https://zenodo.org/records/22969546/files/low-energy-precision.pdf
---

**Yuxuan Zhang**

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/low-energy-precision.pdf' | relative_url }}">Full manuscript (PDF, 10 pages)</a> &middot; <a href="{{ '/assets/code/agentic/low-energy-precision-source.zip' | relative_url }}">LaTeX source, proof and checks (ZIP)</a></p>

**Archival source:** [Manuscript PDF on Zenodo](https://zenodo.org/records/22969546/files/low-energy-precision.pdf), preserved in [*Agentic Proofs for QIQC: Collected Manuscripts*, version 1.0](https://doi.org/10.5281/zenodo.22969546) (26 September 2026).

**Status: a complete proof candidate, internally checked with AI assistance.** Independent expert review and publication priority remain unconfirmed. This is the round-23 result, prepared as a manuscript on 21 September 2026. It has not been formally verified by a proof assistant.

## The question

Suppose a quantum algorithm is given an exact block encoding of a contraction $$A$$, with controlled access to that encoding and its inverse. The Hamiltonian is $$H=\lambda A^\dagger A$$, and the input lies in its spectral subspace with energies at most $$\Delta$$. Only oracle queries are charged; the other gates must be independent of the unknown oracle.

The [QIQCOP problem](https://qiqc-op.com/problem/op_25d9dee5435ea835/) asks for the optimal precision dependence of simulating this low-energy evolution. Its error convention requires the full output vector to approximate the desired evolution, including returning every workspace register to zero. The output phase is fixed, so this is stronger than merely approximating the output density operator.

Write

$$
T=t\lambda,\qquad s=t\Delta,\qquad L=\log(1/\epsilon).
$$

The question concerns every asymptotic family with

$$
\epsilon\to0,\qquad \epsilon=o(s),\qquad s=o(L),\qquad L=o(T).
$$

[Zlokapa and Somma](https://doi.org/10.22331/q-2024-08-27-1449) give an upper bound that becomes $$O(\sqrt{TL})$$ in this regime. The remaining question is how much of the precision factor is necessary.

## The candidate theorem

Theorem 1.1 of the manuscript gives matching upper and lower query bounds:

$$
Q_{\mathrm{opt}}(T,s,\epsilon)
=\Theta\!\left(\sqrt{\frac{TL}{\log(2+L/s)}}\right).
$$

The constants are absolute and independent of the system and encoding dimensions. The inequalities hold eventually along each permitted asymptotic family; the threshold may depend on the family.

For fixed $$s>0$$, this becomes $$\Theta(\sqrt{TL/\log L})$$. The improvement over the previous upper-bound scale is a factor of $$\sqrt{\log(2+L/s)}$$, which diverges throughout the stipulated regime. The statement also includes families in which $$s$$ tends to zero. For example, $$s=\epsilon L$$ gives $$\Theta(\sqrt T)$$ queries, provided $$L=o(T)$$.

## How the upper bound works

A pair of reflections built from the factor encoding produces a quantum walk. On a singular-value plane of $$A$$, powering this walk maps the small singular value $$\sigma$$ to

$$
z=\sin^2(r\arcsin\sigma).
$$

The proof chooses $$r$$ so that the promised spectrum stays on a single inverse-sine branch. Approximating the function

$$
\exp\!\left[-iT\sin^2\!\left(\frac{\arcsin\sqrt z}{r}\right)\right]
$$

then recovers the desired phase exactly before the polynomial approximation error is introduced.

The main constraint is global: the polynomial must stay bounded by one on the entire interval $$[0,1]$$, even though it only needs to be accurate near zero. A truncated Taylor polynomial alone does not ensure this. Multiplying it by an explicit binomial-tail cutoff supplies enough margin for contractivity while preserving a local error bound of $$(64z)^M$$.

Taking $$M$$ of order $$L/\log(2+L/s)$$ and $$r$$ of order $$\sqrt{T/M}$$ gives the claimed query count. A Laurent-polynomial unitary completion implements the construction. An overlap estimate then bounds the full vector error, including ancillary leakage. The circuit uses no postselection or free low-energy projector. The synthesis principle is established quantum signal processing machinery, credited to [Haah](https://doi.org/10.22331/q-2019-10-07-190); the manuscript includes the necessary degree-counting argument.

## Why the lower bound matches

The lower bound starts with scalar factors and one-ancilla reflection encodings. A circuit making $$Q$$ queries has a return amplitude that is a polynomial of total degree at most $$Q$$ in the encoding entries, even with arbitrary workspace and controlled or inverse calls.

Averaging over four sign choices turns that amplitude into a polynomial in $$y=\sigma^2$$ of degree at most $$\lfloor Q/2\rfloor$$. Unitarity bounds it on all of $$[0,1]$$, while the simulation guarantee makes it approximate $$e^{-iTy}$$ on $$[0,s/T]$$. Finite differences force a large derivative on the short interval; a complex-polynomial derivative estimate then forces the matching degree. The argument treats the first finite difference separately, so it also covers families where $$L/\log(2+L/s)$$ remains bounded.

## Verification and limits

The frozen round-23 proof received separate internal AI reviews. Manuscript preparation rechecked the model, the binomial cutoff, unitary completion, inverse-sine branch, full-output error, and the rounding in both bounds. The accompanying code reproduces 1,854 polynomial evaluations at 160 decimal digits, plus 9 general complex factor-encoding cases, 5 unitary degree-stripping examples, and 8 circuit-polynomialization examples. These finite diagnostics support the formulas; they do not replace the analytic proof.

The model matters. Factor access is supplied as part of the input. The oracle is exact, and oracle-independent gates and classical preprocessing are uncharged. The scalar lower bound uses the phase-sensitive vector-error convention. The manuscript therefore does not establish the same optimality result for gate counts, imperfect encodings, or errors measured only on density operators. [Zlokapa, Allen, and Harrow](https://arxiv.org/abs/2607.19852) study lower bounds under access to individual Hamiltonian terms, a different resource model.

If the proof is confirmed, it settles the literal precision question under the catalog's assumptions. The source comparison remains a bounded literature check, not a certification of priority.

## Authorship and preparation

The proof, numerical checks, internal reviews and exposition were developed with substantial AI assistance under the author's direction. The coordinating assistant was also an AI component; its work is not counted as human mathematical verification. [Scientific Agent Skills](https://arxiv.org/abs/2609.00065) guided manuscript preparation and evidence tracking and is cited in the PDF. Third-party papers retain their own terms and are not bundled in the source archive.
