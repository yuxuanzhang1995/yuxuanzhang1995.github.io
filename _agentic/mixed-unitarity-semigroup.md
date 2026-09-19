---
layout: page
title: A qutrit semigroup can lose mixed unitarity after a positive time
description: An explicit analytic counterexample candidate, with exact membership at one positive time and a separating witness at a later time.
date: 2026-09-16
last_revised: 2026-09-19
status: counterexample candidate
target: QIQCOP problem op_722706a9205dcff2
pdf: mixed-unitarity-semigroup.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**<br>
Department of Physics, Princeton University, Princeton, New Jersey 08544, USA<br>
Institute of Physics, École Polytechnique Fédérale de Lausanne (EPFL), CH-1015 Lausanne, Switzerland

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/mixed-unitarity-semigroup.pdf' | relative_url }}">Full version (PDF, 7 pages)</a> &middot; <a href="{{ '/assets/code/agentic/mixed-unitarity-semigroup-source.zip' | relative_url }}">LaTeX source and supplementary check (ZIP)</a></p>

**Revision: 19 September 2026.** The formal manuscript, independent audit summary, primary-source evidence and reproducible checks have been updated.

**Status: a full counterexample candidate, internally reviewed by AI agents.** External expert
review and literature novelty remain unconfirmed. Both endpoint claims have analytic proofs;
the supplementary numerical check is not a proof certificate.

## The question

A mixed-unitary quantum channel is a finite probabilistic mixture of unitary conjugations.
Bhat and Devendra prove that every continuous semigroup of unital quantum channels eventually
becomes mixed unitary [1, Theorem 4.12]. The question recorded in QIQCOP [2] concerns the journey
to that eventual regime: can a semigroup be mixed unitary at a positive time, then cease to be
mixed unitary at a later time?

The manuscript gives an explicit qutrit construction with exactly that behavior. It is consistent
with eventual mixed unitarity: membership at an earlier time need not persist continuously from
that time onward.

## The construction

Let

$$
R=\begin{pmatrix}0&-1\\1&0\end{pmatrix},\qquad
B=\operatorname{diag}(1,R),\qquad H=\operatorname{diag}(30,0,0),
$$

and define a fixed generator on complex $$3\times3$$ matrices by

$$
\mathcal L(X)=\frac{\operatorname{Tr}(X)I_3-BX^T B^*}{2}-X-i[H,X].
$$

Here $$T$$ is transpose in the displayed basis and $$*$$ is adjoint. This is a unital Lindblad
generator, so $$\Phi_u=e^{u\mathcal L}$$ is a norm-continuous unital CPTP semigroup. The two times are

$$
s=\frac{2\pi}{\sqrt{3601}},\qquad t=\frac{3\pi}{\sqrt{3601}}>s.
$$

The conclusion is **mixed unitary at $$s$$ and not mixed unitary at $$t$$**, for the same generator.

The dissipative construction comes from Bhat–Devendra [1, Lemma 5.7 and Example 5.11], as does
the twisted-swap separation method [1, Lemmas 5.5–5.7]. The additional ingredient here is the
specified Hamiltonian and the exact refocusing calculation that supplies the two endpoints.

## Why the earlier channel is mixed unitary

An explicit solution of the block evolution gives

$$
\Phi_s=\operatorname{Ad}_Q\circ e^{s\mathcal D_0},\qquad
Q=\operatorname{diag}(-1,1,1),
$$

where $$\operatorname{Ad}_Q(X)=QXQ^*$$ and $$\mathcal D_0$$ is a sum of five Hermitian-jump
Lindblad generators. Each individual exponential is a Gaussian average of unitary conjugations.
The finite-dimensional convex hull of unitary conjugations is compact, so these averages,
their products, and the Lie-product limit all belong to that hull. This proves existence of a
**finite** mixed-unitary representation of $$\Phi_s$$, without replacing finite mixtures by a
larger class of infinite mixtures.

## Why the later channel is not mixed unitary

Use the normalized Choi matrix
$$J(\Psi)=(\operatorname{id}\otimes\Psi)(|\Omega\rangle\langle\Omega|)$$,
where $$|\Omega\rangle=(|00\rangle+|11\rangle+|22\rangle)/\sqrt3$$. With $$F$$ the swap operator, set

$$
C=\operatorname{diag}(-1,R),\qquad
W=(I_3\otimes C)F(I_3\otimes C^*)+I_9/3.
$$

For every mixed-unitary channel $$\Psi$$, one has $$\operatorname{Tr}(WJ(\Psi))\geq0$$.
The proof applies to all complex qutrit unitaries: the skew-symmetric part of a unitary has
rank at most two and operator norm at most one. Convexity then extends the bound to mixtures.

Direct evaluation at the later time gives

$$
\operatorname{Tr}(WJ(\Phi_t))
=\frac{2+e^{-3t/2}-3e^{-t/2}-4e^{-t}/\sqrt{3601}}{3}
<-\frac{456}{38125}<0.
$$

The final inequality follows from elementary rational bounds on the exponentials and on $$t$$.
It rules out every mixed-unitary decomposition, without optimizing over a sampled family of
unitaries or relying on a numerical solver's tolerance.

## Verification

The complete revised manuscript received a fresh independent adversarial AI review on 19 September 2026: **PASS, exact claim–proof alignment**, with no mathematical gap identified. The executable supplement reproduced twice in clean verifier processes. The main mathematical argument is unchanged from the earlier working draft; this is a publication revalidation, not a new discovery. External expert review, formal proof verification and broad novelty confirmation remain outstanding.

The audit checked the unital Lindblad representation, all complex matrix blocks, exact refocusing, finite convex-hull membership, the witness for every complex unitary, and the strict rational negative bound. The new supplement checks 18 exact matrix-unit identities, 23 channel time samples and 400 complex-unitary diagnostics. The refocusing residual was below $$3\times10^{-16}$$, and the later witness evaluates to approximately $$-0.0134293096502358$$, consistent with the analytic bound $$-456/38125$$. Random unitary sampling is only a diagnostic; the rank argument supplies the universal witness proof.

The seven-page manuscript includes the complete analytic argument and a reproducibility appendix. Its source archive contains LaTeX, the checker, detailed results, pinned package versions, the AI audit summary, and a primary-source evidence manifest. Scientific Agent Skills informed the evidence-tracking and writing process and is cited in the paper.

## What remains open

The construction is intended to answer the existence question in the linked QIQCOP record in
full. It does not determine the first positive mixed-unitary time, the eventual membership
threshold, or the complete set of intermediate membership times.

External mathematical review and broader literature checking remain necessary. No priority
claim is made, and the ingredients inherited from [1] should retain their attribution.

## References

1. B. V. Rajarama Bhat and R. Devendra, *On regions of mixed unitarity for semigroups of unital quantum channels*, [arXiv:2512.23598v3](https://arxiv.org/html/2512.23598v3), revised 9 September 2026. See Theorems 4.12 and 5.4, the open question following Theorem 5.4, Lemmas 5.5–5.7, and Example 5.11.
2. QIQCOP, *Loss of mixed unitarity after a positive time in a quantum dynamical semigroup*, problem [op_722706a9205dcff2](https://qiqc-op.com/problem/op_722706a9205dcff2/).
