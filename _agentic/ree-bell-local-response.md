---
layout: page
title: "Local response of two-qubit relative entropy of entanglement"
description: "Explicit nearest-separable-state derivatives and an entanglement Hessian around full-rank entangled Bell-diagonal states."
date: 2026-09-24
status: partial result
target: QIQCOP problem op_e2149f4ced34d1a8
author: Yuxuan Zhang
---

**Yuxuan Zhang** · 24 September 2026

**Partial result — the original QIQCOP problem remains unresolved by this note.**

<p><a href="https://yuxuanzhang1995.github.io/assets/code/agentic/ree-bell-local-response-source.zip">Full proofs, source and checks (ZIP)</a></p>

Relative entropy of entanglement asks for the separable state closest to a given quantum state. Even for two qubits, a general explicit answer is missing. These notes give a local forward formula around every full-rank entangled Bell-diagonal state: they compute how the closest separable state changes in all fifteen perturbation directions, and the resulting entanglement Hessian.

Work in the real Bell basis $$(\Phi^+,\Phi^-,\Psi^+,\Psi^-)$$, indexed by $$0,1,2,3$$, with natural logarithms. Let

$$
\rho_* = \operatorname{diag}(p_0,p_1,p_2,p_3),\qquad
p_i>0,\quad \sum_i p_i=1,\quad p_0>1/2.
$$

Write $$q=1-p_0$$ and $$S=\operatorname{diag}(1/2,p_1/(2q),p_2/(2q),p_3/(2q))$$. The known closest separable state at the base point is $$S$$.

## The local formula

In a neighborhood of $$\rho_*$$, the closest separable state $$\sigma(\rho)$$ is unique and real analytic. For every small trace-zero Hermitian perturbation $$K$$,

$$
\sigma(\rho_*+K)=S+X(K)+O(\lVert K\rVert^2),
$$

$$
E_R(\rho_*+K)=\ln2+p_0\ln p_0+q\ln q
+K_{00}\ln(p_0/q)+\tfrac12Q(K)+O(\lVert K\rVert^3).
$$

The frozen statement gives every coefficient of the linear map $$X$$ and the quadratic form $$Q$$. In particular,

$$
X_{00}=0,\qquad X_{ii}=\frac{K_{ii}+p_iK_{00}/q}{2q}\quad(i>0).
$$

Each real or imaginary off-diagonal component is multiplied by an explicit positive-denominator coefficient built from logarithmic divided differences and the partial-transpose curvature. The formulas have continuous limits at repeated positive eigenvalues; no distinct-eigenvalue assumption is imposed. Dividing the value expansion by $$\ln2$$ converts it to bits without changing the optimizer.

## Why the local optimizer is valid

For two qubits, the separable set is the positive-partial-transpose set. At $$S$$ the partial transpose has a simple zero eigenvalue. The associated supporting witness proves global optimality, while strict convexity gives uniqueness. An invertible constrained stationarity system then gives an analytic branch of true optimizers. Differentiating that system produces the response coefficients; differentiating the optimized objective gives the Hessian.

The supporting-witness and inverse-optimization frameworks are known. They are credited to [Miranowicz and Ishizaka (2008)](https://arxiv.org/abs/0805.3134) and [Friedland and Gour (2011)](https://arxiv.org/abs/1007.4544). The contribution submitted here is the explicit local forward evaluation, with analytic remainder control, rather than a claim to have invented those frameworks.

The checker tests exact Bell-basis partial-transpose identities and floating-point stationarity residuals. Those residuals are diagnostics, not interval certificates. The mathematical claim rests on the written proof. The neighborhood radius is existential, not an explicit error-control radius for a supplied state. A global formula for arbitrary two-qubit inputs, rank-deficient boundary cases, and historical novelty remain unresolved.


## Proofs and reproducibility

- [Round 41, record 151: exact statement and full proof]({{ '/assets/code/agentic/ree-bell-local-response/round-41-record-151-proof.txt' | relative_url }}).

The source archive contains the unchanged mathematical submissions, review records, executable checks where supplied, expected outputs, and publication reruns. The README distinguishes analytic proofs, interval certificates, and finite diagnostics. Claims without an executable check rely on their written proof.

These are AI-generated research notes, prepared and checked with AI assistance under Yuxuan Zhang’s direction. Separate internal AI review found no error in the frozen claims, but this is not independent human peer review or proof-assistant verification. Historical novelty remains unverified.

The evidence and attribution audit used [K-Dense Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065).
