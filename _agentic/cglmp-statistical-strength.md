---
layout: page
title: CGLMP measurements need not maximize statistical strength
description: A four-dimensional counterexample on the fixed maximally entangled state, with an exact separation exceeding 0.022 bits.
date: 2026-09-28
status: solved (negative)
target: QIQCOP problem op_a34f0e2d6489068f
pdf: cglmp-statistical-strength.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 28 September 2026 (PDF, 5 pages)]({{ '/assets/pdf/agentic/cglmp-statistical-strength.pdf' | relative_url }}) · [Source, exact certificate, physical checks and review records (ZIP)]({{ '/assets/code/agentic/cglmp-statistical-strength-source.zip' | relative_url }})

**The conjectured optimality fails at dimension four.** On the same maximally entangled state, two simple product measurements give statistical strength greater than **0.087 bits**. The standard CGLMP measurements give less than **0.065 bits**, even after their setting distribution is optimized. Both inequalities have exact rational certificates.

This is a complete negative answer to [the catalog's statistical-strength question](https://qiqc-op.com/problem/op_a34f0e2d6489068f/). “Solved (negative)” is the label in this research log. Two separate frozen AI reviews found no defect; external specialist review, historical priority and QIQCOP acceptance remain unconfirmed.

## What is being compared?

Statistical strength asks how well a Bell experiment can distinguish its observed correlations from the best local explanation. It is the relative entropy to the entire local polytope, with the distribution of measurement settings also optimized:

$$
S^\star(p)=\sup_\mu\inf_{\ell\in\mathcal L}
\sum_{x,y,a,b}\mu(x,y)p(a,b\mid x,y)
\log_2\frac{p(a,b\mid x,y)}{\ell(a,b\mid x,y)}.
$$

The state, local dimension, number of settings and number of outcomes are fixed. The question is whether the usual CGLMP Fourier–phase bases always maximize this quantity. A counterexample in one dimension disproves the universal claim.

## The construction

Write each four-dimensional local system as two qubits. Under this identification, the prescribed state $$|\Phi_4\rangle$$ is two Bell pairs. Alice's two settings measure both her qubits in the $$Z$$ basis or both in the $$X$$ basis. Bob's two settings measure both in the eigenbasis of $$(Z+X)/\sqrt2$$ or both in the eigenbasis of $$(Z-X)/\sqrt2$$.

Each party reports two bits as one of four outcomes. There are still exactly **two settings per party**, and each measurement consists of four rank-one projectors. The setting labels are shared by the two component qubits.

Let $$K$$ count how many of the two component CHSH conditions are satisfied. For uniformly sampled settings, every local four-outcome strategy obeys $$\mathbb E K\leq3/2$$. This remains true when its two response bits are arbitrarily correlated. With

$$
f(K)=1+\frac{K-3/2}{2},
$$

the relative-entropy variational inequality gives a lower bound $$L>0.087$$ bits for our experiment. The proof never assumes that the best local explanation factors into two independent models.

## Why CGLMP cannot catch up by changing the setting distribution

The second half of the proof supplies one explicit local behavior for the CGLMP experiment. After the appropriate modular relabeling, its outcome-difference probabilities are

$$
r=\left(\frac7{10},\frac1{20},\frac1{20},\frac15\right).
$$

The manuscript constructs this behavior as a rational mixture of deterministic local strategies. Its divergence from the quantum CGLMP behavior is the same in every setting pair. Therefore it gives an upper bound $$U<0.065$$ bits for **every** setting distribution, including distributions with some zero probabilities.

The decisive comparison is

$$
S^\star(p_T)\geq L>0.087>0.065>U\geq S^\star(p_{\mathrm{CGLMP}}).
$$

For reference, $$L\approx0.0878892114243$$ and $$U\approx0.0627382117716$$. These are bounds, not claims to know either experiment's exact optimum.

## Checks and prior work

The standalone certificate uses Python integers and exact fractions to enclose the square roots and logarithms. It directly asserts the two strength bounds and a separation greater than 0.022 bits, checks all 256 deterministic local strategies, and checks the local construction. A separately written calculation reconstructs all four physical bases and all 64 conditional probability entries. The analytic argument and exact arithmetic carry the proof; the high-precision matrix calculation is an additional control.

[Van Dam, Gill and Grünwald](https://doi.org/10.1109/TIT.2005.851738) developed the statistical-strength framework. [Acín, Gill and Gisin](https://doi.org/10.1103/PhysRevLett.95.210402) studied numerical optimization and discussed independent copies with more settings. [Gill](https://doi.org/10.1214/074921707000000328) reported searches supporting CGLMP optimality on a fixed maximally entangled state. The present proof keeps two settings and treats the full local polytope directly. The focused source comparison found no matching certified counterexample, but does not prove novelty.

The result concerns the catalog's relative-entropy criterion. It does not settle maximal linear CGLMP violation, classify Bell facets, or find optimal measurements in every dimension.

The candidate arose in round 48 of the AI-assisted campaign. The manuscript discloses the model, the two subsequent frozen reviews and the independent computational checks. K-Dense's [Scientific Agent Skills](https://doi.org/10.48550/arXiv.2609.00065) guided the evidence record and writing. A Zenodo addition and QIQC report are pending; the earlier collection DOI does not yet archive this manuscript.
