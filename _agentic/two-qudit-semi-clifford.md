---
layout: page
title: A fourth-level non-semi-Clifford gate on two qudits
description: An explicit counterexample in every odd prime dimension, with an algebraic proof and exact reproducible checks.
date: 2026-09-20
last_revised: 2026-09-21
status: solved (negative)
target: QIQCOP problem op_cdd1f718ccfbccf6
pdf: two-qudit-semi-clifford.pdf
author: Yuxuan Zhang
archive_doi: 10.5281/zenodo.22969546
archive_pdf: https://zenodo.org/records/22969546/files/two-qudit-semi-clifford.pdf
---

**Yuxuan Zhang**

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/two-qudit-semi-clifford.pdf' | relative_url }}">Full version (PDF, 5 pages)</a> &middot; <a href="{{ '/assets/code/agentic/two-qudit-semi-clifford-source.zip' | relative_url }}">LaTeX source and exact checks (ZIP)</a></p>

**Archival source:** [Manuscript PDF on Zenodo](https://zenodo.org/records/22969546/files/two-qudit-semi-clifford.pdf), preserved in [*Agentic Proofs for QIQC: Collected Manuscripts*, version 1.0](https://doi.org/10.5281/zenodo.22969546) (26 September 2026).

**Status in this research log: solved (negative), supported by an algebraic proof and exact finite checks.** External expert review and publication priority remain unconfirmed; [QIQCOP issue #90](https://github.com/Naixu-Guo/quantum-open-problems/issues/90) remains open for review. This is the round-13 result. The published computational checks were rerun on 21 September 2026. The arbitrary-prime claim relies on the algebraic proof, not extrapolation from the tested primes. The manuscript remains unrefereed and has not been formally verified by a proof assistant.

## The question

A semi-Clifford gate admits a decomposition $$C_L E C_R$$, with Clifford factors $$C_L,C_R$$ and a computational-basis diagonal gate $$E$$. The [QIQCOP question](https://qiqc-op.com/problem/op_cdd1f718ccfbccf6/) asks whether every two-qudit gate in every hierarchy level $$k\geq4$$ is semi-Clifford, for every odd prime local dimension. The third-level statement is known [2]; the all-level one-qudit statement is also known [3].

The construction below supplies a negative answer for two qudits. It uses their ordinary Pauli group, without an encoded multiqubit subspace.

## The construction

Let $$p$$ be any odd prime, $$\omega=e^{2\pi i/p}$$, and $$x,y\in\mathbb F_p$$. Define

$$
S|x,y\rangle=|x,y+x^2\rangle,\qquad
D|x,y\rangle=\omega^{xy^2}|x,y\rangle,\qquad U=DS.
$$

Thus the full action, with operator order explicit, is

$$
U|x,y\rangle=\omega^{x(y+x^2)^2}|x,y+x^2\rangle.
$$

**Theorem 1 of the manuscript:** $$U\in\mathcal C_4(2,p)\setminus\mathcal C_3(2,p)$$ and $$U$$ is not semi-Clifford. The hierarchy is nested, so the same gate disproves the universal statement at every $$k\geq4$$.

## Why it works

For a Pauli $$P=X_1^aX_2^bZ_1^cZ_2^d$$, direct conjugation gives

$$
UPU^\dagger|x,y\rangle=\omega^{h(x,y)}|A_{a,b}(x,y)\rangle,
$$

$$
A_{a,b}(x,y)=(x+a,y+b+2ax+a^2),
$$

$$
h(x,y)=cx+d(y-x^2)+f(A_{a,b}(x,y))-f(x,y),\qquad f(x,y)=xy^2.
$$

**Membership in level four.** The permutation is invertible affine and therefore Clifford. The phase has degree at most three; finite differences prove that its diagonal gate lies in level three. Multiplication by a Clifford preserves that level. This checks every Pauli, without assuming that level three is a group, and remains valid at $$p=3$$.

**Failure of semi-Cliffordness.** If $$a\ne0$$, the permutation is not a translation, so the image is not Pauli. For $$a=0$$ the phase is

$$
(c+b^2)x+dy-dx^2+2bxy.
$$

Its second differences force $$b=d=0$$ for a Pauli image. Exactly the $$p$$ classes $$Z_1^c$$ survive. A two-qudit semi-Clifford decomposition would send a conjugate of the diagonal Pauli subgroup, containing $$p^2$$ classes, to Paulis. That is impossible.

**The level is exactly four.** Put $$V=UX_1U^\dagger$$. Then

$$
VX_2V^\dagger|x,y\rangle=\omega^{4x^2-6x+2y+3}|x,y+1\rangle.
$$

The phase has second difference $$8\ne0$$ in every odd prime field, so this is not Pauli. Hence $$V$$ is not Clifford and $$U\notin\mathcal C_3$$.

## Verification and reproducibility

Two separate exact implementations reproduce the two-qutrit instance: a monomial permutation/phase checker and a dense matrix checker over $$\mathbb Z[\omega]$$. Neither uses floating-point tolerances. An exhaustive recursive audit using the dense backend checks all 81 Pauli classes at every successful hierarchy node and confirms level four, failure of level three, and exactly three Pauli-to-Pauli classes.

Direct modular checks also test the conjugation formula and Pauli-image count for every label and basis vector at $$p=3,5,7,11$$. The universal claim rests on the algebraic proof, rather than those finite examples. The download includes the manuscript source, both implementations, the recursive audit, outputs, environment versions, and source-evidence records. No research API key is needed to reproduce the checks.

The original claim received an independent AI review with exact claim–proof alignment; the later audit rederived the formulas and compared the original problem's quantifiers. These are internal checks, not external peer review. Scientific Agent Skills informed the writing and evidence tracking and is cited in the paper.

## Scope and priority

This gate **is generalized semi-Clifford**: $$U=S(S^\dagger DS)$$ is a permutation times a diagonal. The result concerns ordinary semi-Cliffordness and is distinct from the recent five-qubit counterexample to generalized semi-Cliffordness [4].

There is a specific priority caveat: Section 8 of [4] announces forthcoming qudit counterexamples, without specifying their size, level, or construction there. The source comparison did not identify this explicit gate, but it is not an exhaustive novelty assessment. No priority claim is made; specialist review and comparison with forthcoming work remain necessary.

## References

1. N. de Silva, *Efficient quantum gate teleportation in higher dimensions*, [Proc. R. Soc. A **477**, 20200865 (2021)](https://doi.org/10.1098/rspa.2020.0865), Sections V.C and VI; [arXiv:2011.00127](https://arxiv.org/abs/2011.00127).
2. I. Chen and N. de Silva, *Characterising semi-Clifford gates using algebraic sets*, [Commun. Math. Phys. **405**, 201 (2024)](https://doi.org/10.1007/s00220-024-05050-2), Theorem 1; [arXiv:2309.15184](https://arxiv.org/abs/2309.15184).
3. N. de Silva and O. Lautsch, *The Clifford hierarchy for one qubit or qudit*, [Proc. R. Soc. A **481**, 20250035 (2025)](https://doi.org/10.1098/rspa.2025.0035), Theorem 6 and Section 5, Conjecture 1; [arXiv:2501.07939](https://arxiv.org/abs/2501.07939).
4. N. de Silva and O. Lautsch, *The generalised semi-Clifford conjecture is false*, [arXiv:2609.11903](https://arxiv.org/abs/2609.11903), preliminary preprint, version dated 10 September 2026; Section 8, final paragraph.
