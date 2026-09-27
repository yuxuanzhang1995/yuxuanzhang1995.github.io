---
layout: page
title: Additivity of minimum output Rényi entropy can fail first at three copies
description: A complete proof candidate gives an explicit channel whose minimum output Rényi entropy is additive for one and two copies but strictly subadditive for three.
date: 2026-09-27
status: proof candidate
target: QIQCOP problem op_c0b1045a614d2353
pdf: delayed-onset-additivity.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Full manuscript (PDF, 5 pages)]({{ '/assets/pdf/agentic/delayed-onset-additivity.pdf' | relative_url }}) · [Manuscript source, exact checker, reviews and provenance (ZIP)]({{ '/assets/code/agentic/delayed-onset-additivity-source.zip' | relative_url }})

**A complete proof candidate.** An internal AI review of the complete proof and a final internal audit
of the manuscript and program found no mathematical gap. External specialist confirmation and literature
priority remain unverified; arXiv was searched through 27 September 2026. Two steps are
computer-certified — a two-copy positivity certificate and the numerical inequalities at $$p=1/1000$$ —
and both reproduce exactly with a program that needs only the Python standard library.

## The question

For a channel $$\Phi$$ and $$p>0$$, the minimum output Rényi entropy is
$$S_{p,\min}(\Phi)=\min_\rho S_p(\Phi(\rho))$$. Product inputs give
$$S_{p,\min}(\Phi^{\otimes n})\le n\,S_{p,\min}(\Phi)$$, and additivity is known to fail: Hastings found
violations at $$p=1$$ [2], Cubitt, Harrow, Leung, Montanaro and Winter at $$p$$ close to $$0$$ [3], and
Derksen and Lovitz gave explicit violations for every $$p>1$$ [4]. The constructions we are aware of
exhibit the violation already for two channel uses.

Ruskai asked whether additivity can hold for all tensor powers below some order $$m$$ and fail first at
the $$m$$th [1]. The question [6] asks for $$p>0$$, $$m\ge3$$ and a channel with
$$S_{p,\min}(\Phi^{\otimes n})=n\,S_{p,\min}(\Phi)$$ for $$n<m$$ and strict inequality at $$n=m$$.

**It can, with $$m=3$$.**

## The channel

Let $$\Psi$$ map $$\mathbb C^4$$ to $$\mathbb C^3$$ with six Kraus operators, each supported on two
matrix entries: $$K_j=(|r_1\rangle\langle k_1|+\theta_j|r_2\rangle\langle k_2|)/\sqrt3$$ on the cell pairs
$$((0,0),(2,2))$$, $$((0,1),(1,2))$$, $$((0,2),(2,1))$$, $$((0,3),(1,0))$$, $$((1,1),(2,3))$$,
$$((1,3),(2,0))$$ of the $$3\times4$$ grid, with $$\theta=(1,1,1,1,1,\omega)$$ and $$\omega=e^{2\pi i/3}$$.
Let $$\Phi$$ be the flagged direct sum of $$\Psi$$ and the constant channel whose output is
$$\tau_\star=\mathrm{diag}(1-2^{-20},2^{-21},2^{-21})$$. Then at $$p=1/1000$$

$$S_{p,\min}(\Phi^{\otimes2})=2\,S_{p,\min}(\Phi),\qquad S_{p,\min}(\Phi^{\otimes3})<3\,S_{p,\min}(\Phi).$$

At every sufficiently small $$p>0$$, the same holds with a $$p$$-dependent constant block.

## Why it works

At small $$p$$ the Rényi entropy is governed by rank. Every output of $$\Psi$$ has rank $$3$$, and every
output of $$\Psi\otimes\Psi$$ has full rank $$9=3^2$$, so the minimum output rank is multiplicative up to two
copies. An input with a three-party GHZ structure makes an output of $$\Psi^{\otimes3}$$ lose a dimension:
its rank is at most $$26<27$$. The flagged constant block turns these rank facts into exact additivity at
two copies and strict subadditivity at three.

The two-copy statement is the heart of the proof. It is certified by an exact decomposable
block-positivity certificate over $$\mathbb Z[\omega]$$: a $$144\times144$$ matrix $$W$$ built from the
Kraus operators satisfies $$W-2^{-14}I=P+Q^\Gamma$$ with $$P$$ positive definite and $$Q$$ positive
semidefinite. This bounds the smallest eigenvalue of every two-copy output below by $$2^{-14}/9$$. The sixth
phase matters: with all $$\theta_j=1$$, the two-copy outputs lose rank.

## Verification

The argument and the program were produced by an AI research agent. The program uses only the Python
standard library and exact arithmetic, and prints 21 lines in under a second:

```text
python3 check_delayed_onset.py | diff - expected_stdout.txt
```

It proves the positive definiteness of $$P$$ twice, by independent routes: fraction-free elimination
over $$\mathbb Z[\omega]$$, and an embedded Gram factor with an exact Frobenius-norm bound. It checks the
216 three-copy identities and a negative control. It certifies the inequalities at $$p=1/1000$$ as exact
big-integer statements, including $$X^{500}>26^{333}$$ and the admissible window for $$\tau_\star$$. Thirty
single-point mutations each make it fail, and isolated runs reproduce its output byte for byte.

The review rebuilt $$W$$ from the Kraus operators and proved $$P\succ0$$ with its own exact certificate.
It also tested the partial-transpose convention against alternatives that would fail silently. The final
audit recomputed every number in the manuscript; at its request the constant block was made explicit.

Reproduction establishes only that the program computes what it prints. The reductions it relies on are
established by the written argument.

## What this establishes, and what it does not

A first violation of additivity at $$m=3$$ exists, at $$p=1/1000$$, for an explicit finite-dimensional
channel from $$\mathbb C^5$$ to $$\mathbb C^6$$. That answers the question as posed.

Nothing is claimed for $$p\ge1$$, including the von Neumann entropy, or for a first violation at
$$m\ge4$$. Nor is anything claimed for a single channel without the flagged constant block. The
mechanism is related to the non-multiplicative minimum output rank of Cubitt, Harrow, Leung, Montanaro
and Winter [3], who used a pair of different channels. What is new here is that a single channel's rank
stays multiplicative at two copies and first fails at three.

## References

1. M. B. Ruskai, *Some open problems in quantum information theory*, [arXiv:0708.1902](https://arxiv.org/abs/0708.1902), Problem 19.
2. M. B. Hastings, *Superadditivity of communication capacity using entangled inputs*, Nature Physics 5, 255 (2009), [arXiv:0809.3972](https://arxiv.org/abs/0809.3972).
3. T. Cubitt, A. W. Harrow, D. Leung, A. Montanaro and A. Winter, *Counterexamples to additivity of minimum output p-Rényi entropy for p close to 0*, Commun. Math. Phys. 284, 281–290 (2008), [arXiv:0712.3628](https://arxiv.org/abs/0712.3628).
4. H. Derksen and B. Lovitz, *Constructive counterexamples to the additivity of minimum output Rényi entropy of quantum channels for all p>1*, [arXiv:2510.07547](https://arxiv.org/abs/2510.07547).
5. L. Shou and A. V. Gorshkov, *A constructive violation of additivity of minimum output von Neumann entropy*, [arXiv:2609.23946](https://arxiv.org/abs/2609.23946). Recent related work on two-use violations.
6. Quantum Information and Quantum Computation Open Problem Zoo, [Delayed-onset additivity violation for minimum output Rényi entropy](https://qiqc-op.com/problem/op_c0b1045a614d2353/).
7. T. Kassis, V. Agarwal, Y. He, D. Patel and A. M. Brueckner, *Scientific Agent Skills: A Library of Procedural Knowledge for Research Agents*, [arXiv:2609.00065v2](https://arxiv.org/abs/2609.00065v2). Writing guidance consulted at commit `330c8e764435`.
