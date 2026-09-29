---
layout: page
title: Eight-copy universal CCZ concentration beyond the two-thirds candidate optimum
description: An explicit catalyst-free stabilizer protocol turns eight copies of any unknown pure qubit into an exact CCZ state with probability m₃, not the candidate optimum (2/3)m₃.
date: 2026-09-28
status: solved (negative)
target: QIQCOP problem op_bc61eaba5c332fec
pdf: eight-copy-ccz-concentration.pdf
author: Yuxuan Zhang
archive_doi: 10.5281/zenodo.23032999
archive_pdf: https://zenodo.org/records/23032999/files/eight-copy-ccz-concentration.pdf
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 28 September 2026 (PDF, 7 pages)]({{ '/assets/pdf/agentic/eight-copy-ccz-concentration.pdf' | relative_url }}) · [Manuscript source, exact checker, mutation tests and review records (ZIP)]({{ '/assets/code/agentic/eight-copy-ccz-concentration-source.zip' | relative_url }})

**Archival source:** [Manuscript PDF on Zenodo](https://zenodo.org/records/23032999/files/eight-copy-ccz-concentration.pdf), manuscript 19 in [*Agentic Proofs for QIQC: Collected Manuscripts*, version 1.2](https://doi.org/10.5281/zenodo.23032999) (29 September 2026). [QIQC report #121](https://github.com/Naixu-Guo/quantum-open-problems/issues/121) documents the manuscript; submission does not change the catalog status.

**The candidate optimum fails at every non-stabilizer input.** A fixed protocol built only from Pauli
measurements, classical feedforward, Clifford unitaries and discarding turns $$\psi^{\otimes8}$$ into an exact
$$\lvert CCZ\rangle$$ with probability exactly $$m_3(\psi)=(1-x^6-y^6-z^6)/2$$, for every pure qubit $$\psi$$ with
Bloch vector $$(x,y,z)$$. The proposed optimum was $$\tfrac23m_3$$. With the upper bound of Rizzo and Leone,
$$m_3\le p_8^\star\le\tfrac76m_3$$.

This is a complete negative answer to [the catalog's eight-copy CCZ question](https://qiqc-op.com/problem/op_bc61eaba5c332fec/).
“Solved (negative)” is the label in this research log. An isolated internal AI review of the complete proof, an independent
simulation, a requirements audit against the catalog record and a blind reconstruction from the bare
statements found no defect. External specialist review, historical
priority and QIQCOP acceptance remain unconfirmed.

## The question

In universal magic-state concentration [1] a fixed stabilizer protocol, chosen without knowing the input,
must turn copies of an unknown pure qubit into an exact target magic state; it may fail, and it must fail on
stabilizer inputs. For eight copies and the target
$$\lvert CCZ\rangle=2^{-3/2}\sum_{x}(-1)^{x_1x_2x_3}\lvert x\rangle$$, Rizzo and Leone give a protocol with success
probability $$\tfrac23m_3(\psi)$$, prove that no protocol exceeds $$\tfrac76m_3(\psi)$$, and leave eight-copy
optimality open. The question [2] asks whether $$\tfrac23m_3$$ is the optimum for every pure $$\psi$$.

## The protocol

1. Measure $$X^{\otimes8}$$ and $$Z^{\otimes8}$$. The outcome $$(+1,+1)$$ is rejected; the other three outcome pairs
   select a sector $$P\in\{Z,X,Y\}$$.
2. In sector $$P$$, measure $$P$$ on qubits $$\{0,1,2,3\}$$. On $$-1$$, measure $$P_0P_1$$ and accept either result.
   On $$+1$$, measure $$P$$ on qubits $$\{0,3,4,5\}$$ and accept only $$-1$$.
3. On each of the nine accepted branches, an explicit Clifford circuit of at most 21 gates, preceded in sectors
   $$X$$ and $$Y$$ by one layer of single-qubit Cliffords, maps the state exactly to $$\lvert CCZ\rangle$$ on three
   qubits, with the other five in $$\lvert0\rangle$$. They are discarded.

The protocol uses no ancillas and no catalyst, and it does not depend on $$\psi$$.

## Why it works

On the symmetric subspace, every accepted branch projects onto a single line, so its output does not depend
on $$\psi$$. In each sector the only part of $$\psi^{\otimes8}$$ that can reach an accepted branch is its component
along one vector $$E_P$$. The three vectors span the three-dimensional part of the symmetric subspace that is
orthogonal to $$\tau^{\otimes8}$$ for all six single-qubit stabilizer states $$\tau$$, and the three squared components
add up to $$\tfrac76m_3(\psi)$$. Rizzo and Leone's filter keeps $$\tfrac47$$ of each sector
direction. The new branch recycles part of the branch they reject and keeps another $$\tfrac27$$, so the protocol
keeps $$\tfrac67\cdot\tfrac76m_3=m_3$$.

The last $$\tfrac17$$ of each direction reaches only the rejected branch. On the symmetric subspace that branch's
image is spanned by two stabilizer states, so no continuation of this tree can turn it into $$\lvert CCZ\rangle$$. Whether any protocol reaches $$\tfrac76m_3$$ remains open. For the $$T$$-type state, the
protocol succeeds with probability $$4/9$$, against $$8/27$$ for the candidate optimum and the upper bound $$14/27$$.

## Checks

The standalone checker uses only the Python standard library, with exact integer and rational arithmetic. It
checks:

- that every measurement path commutes and that the 13 branches are complete;
- that all nine accepted branches have rank one on the symmetric subspace, each capturing $$\tfrac27$$;
- the three decoders, gate by gate, and the transfer to sectors $$X$$ and $$Y$$;
- the exact $$9\times9$$ identity that gives $$p=m_3$$, with a second route at exact Gaussian-rational inputs;
- positive and negative controls.

It prints 21 lines in under a second. Its output is byte-identical on a laptop and in a container without
network access. All 25 single-point mutations of the checker are detected. The checker confirms only that the
program computes what it prints; the argument itself is in the manuscript.

## What this establishes, and what it does not

For every non-stabilizer pure qubit, the optimal eight-copy success probability is at least $$m_3$$. This
refutes the candidate $$\tfrac23m_3$$ and narrows the open window from a factor $$\tfrac74$$ to $$\tfrac76$$. The
exact value of $$p_8^\star$$ is not determined, and nothing is claimed for other copy numbers, other targets,
catalytic protocols or protocols optimized for a known input.

The protocol was found in round 46 of the AI-assisted campaign. The manuscript discloses AI assistance,
the internal review and the independent checks. K-Dense's [Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065)
guided the evidence record and writing.

## References

1. J. Rizzo and L. Leone, *Universal magic state concentration*, [arXiv:2608.13376](https://arxiv.org/abs/2608.13376).
2. Quantum Information and Quantum Computation Open Problem Zoo, [Optimal universal eight-copy concentration to a CCZ state](https://qiqc-op.com/problem/op_bc61eaba5c332fec/).
3. S. Bravyi and A. Kitaev, *Universal quantum computation with ideal Clifford gates and noisy ancillas*, Phys. Rev. A 71, 022316 (2005), [doi:10.1103/PhysRevA.71.022316](https://doi.org/10.1103/PhysRevA.71.022316).
4. T. Kassis, V. Agarwal, Y. He, D. Patel and A. M. Brueckner, *Scientific Agent Skills: A Library of Procedural Knowledge for Research Agents*, [arXiv:2609.00065v2](https://arxiv.org/abs/2609.00065v2).
