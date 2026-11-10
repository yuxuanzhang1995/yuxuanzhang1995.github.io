---
layout: page
title: "Nineteen qubits are necessary and sufficient for symmetric quantum codes correcting two errors"
description: "An exact computer-assisted exclusion of every shorter symmetric logical-qubit code, including arbitrary complex coefficients and both length parities."
date: "2026-11-10"
permalink: /agentic-research/symmetric-two-error-code-length/
status: "Complete proof candidate · independent model review"
target: "QIQCOP · Minimum length of permutation-invariant quantum codes"
pdf: "symmetric-two-error-code-length-v1.pdf"
---

Yuxuan Zhang · 10 November 2026 · Version 1.0

A logical qubit encoded in the fully symmetric subspace needs **at least
nineteen physical qubits** to correct every error on two qubits. A
nineteen-qubit construction is already known, so the lower bound determines
the minimum length:

$$
n_{\min}^{\mathrm{PI}}(2)=19.
$$

The theorem answers the [original QIQC Open Problems catalogue
question](https://qiqc-op.com/problem/op_a72722e455d85d55/). This is a
complete computer-assisted proof candidate, reviewed by a separate AI agent
in a fresh context. External expert review is outstanding.

[Full paper (PDF)]({{ '/assets/pdf/agentic/symmetric-two-error-code-length-v1.pdf' | relative_url }})
· [Source, certificates and review (ZIP)]({{ '/assets/code/agentic/symmetric-two-error-code-length-v1.zip' | relative_url }})
· [Version and SHA-256 metadata]({{ '/assets/code/agentic/symmetric-two-error-code-length-v1.json' | relative_url }})

## What is being minimized

Every state in the code must be unchanged when the physical qubits are
permuted. Each logical basis vector is therefore a linear combination of
Dicke states. The coefficients may be complex, and neither parity of the
length nor any extra symmetry of the logical basis is assumed.

The code must correct arbitrary errors supported on at most two qubits,
including their linear combinations. Equivalently, it detects all Pauli
operators of weight at most four. The theorem includes degenerate codes.
It concerns the fully symmetric physical subspace; it is not a lower bound
for general quantum error-correcting codes.

## Why eighteen qubits are the key case

[Aydin, Alekseyev and Barg](https://doi.org/10.22331/q-2024-04-30-1321)
constructed a nineteen-qubit code in 2024 using the real
Pollatsek–Ruskai family. Their Section 7 reports interval certification
of solutions to the corresponding polynomial equations. We use this
published existence result for the upper bound.

The scalar single-spin linear-programming framework goes back to
[Bumgardner](https://arxiv.org/abs/1205.4517v1).
[Okada's dissertation](https://arxiv.org/abs/2502.14165v1), Table 3.1,
reports distance-five dimension bounds of 1 through seventeen qubits,
2.019 at eighteen and 2.096 at nineteen. The latter bounds still allow a
two-dimensional code. The text discusses agreement with exact rational
solvers for smaller cases, without giving a cutoff for the table.

The decisive new exclusion here is **eighteen qubits**. We also supply
exact certificates for every length from nine through seventeen, so that
the finite exclusion is self-contained. Those earlier bounds are credited
to the literature, not counted again as new results.
[Bond and collaborators](https://arxiv.org/abs/2603.10981v1) conjecture
the more general formula $$3t^2+3t+1$$ from numerical searches.
This result settles its two-error case, not the formula for arbitrary
numbers of errors. The targeted primary-source review found no prior
proof of the unrestricted eighteen-qubit exclusion; its source comparison
is included in the package.

## How the lower bound works

A putative code projector gives a positive third moment after averaging
over collective spin rotations. Error detection becomes a set of linear
constraints on this moment. Permutation symmetry and positivity after
partial time reversal impose further constraints.

Two details keep the relaxation valid for every code. Complex conjugation
is averaged at the level of moments, so complex code coefficients remain
covered. The standard representation of the three-copy permutation group
is retained alongside the symmetric component; discarding it would
incorrectly exclude valid projectors.

Angular-momentum identities then express the constraints in rational
coordinates. For each length from nine to eighteen, an exact dual
certificate proves that this necessary relaxation is infeasible. The
checker regenerates all coefficients, verifies the dual identity, and
checks positive matrix pivots and a strictly negative rational right-hand
side. It does not accept a numerical solver's infeasibility status as a
proof. The quantum Singleton bound excludes lengths at most eight.

The scalar enumerator and time-reversal ingredients have prior
single-spin formulations, including Okada's work and the more recent
[intrinsic MacWilliams identities](https://arxiv.org/abs/2604.16023v2).
The contribution is the three-copy relaxation with partial time reversal
and its exact exclusion at eighteen qubits.

## Evidence and review

The ten certificates contain **435 nonnegative scalar multipliers and
2,496 positive rational matrix pivots**. The release runner checks file
hashes and verifies every certificate in a fresh temporary directory
without an optimizer or cached coefficient matrices.

The independent model review examined the analytic necessity of the
constraints, not only their computational replay. Its controls include
generic complex rank-two projectors, independently constructed partial
transposes, exact Clebsch–Gordan contractions, and a known twenty-one-qubit
distance-five code. It also checks the source distinction between an
unrestricted code and the real Pollatsek–Ruskai family.

The package records both the proof review and its limits. The nineteen-qubit
upper bound is inherited from the published construction, rather than
recertified by this package. The calculations support the finite
certificates and the formulas they use; the written argument establishes
why all admissible codes enter the relaxation.

The author directed the research and workflow. AI systems assisted with
derivation, source comparison, computation and drafting. Review by a
separate model context is not external expert or proof-assistant
verification. This website release is separate from journal review,
archival submission and catalogue acceptance.
