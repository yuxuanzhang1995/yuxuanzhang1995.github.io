---
layout: page
title: Feedback-enhanced quantum Chernoff discrimination
description: "Retaining quantum outputs for a second visit improves discrimination even for faithful qubits. Version 2 adds an unbounded additive gap, existence of the LOCC exponent, and exact rates for a flagged class."
date: 2026-10-29
original_date: 2026-10-16
status: counterexample
target: Copywise Chernoff exponents — feedback, local quantum memory and asymptotic rates
pdf: chernoff-two-pass.pdf
author: Yuxuan Zhang and Mao-Sheng Li
---

**Yuxuan Zhang and Mao-Sheng Li**

[Manuscript, version 2.0, 29 October 2026 (PDF, 17 pages)]({{ '/assets/pdf/agentic/chernoff-two-pass.pdf' | relative_url }}) · [LaTeX source and checking records (ZIP)]({{ '/assets/code/agentic/chernoff-two-pass-source.zip' | relative_url }})

Version 2 expands the earlier four-dimensional counterexample with Mao-Sheng Li's qubit construction, an existence theorem for the optimal LOCC exponent, and rate formulas for orthogonally flagged states. The earlier single-author paper, *Two-pass local measurements beat the measured Chernoff exponent*, remains archived as [version 1.0, 16 October 2026](https://zenodo.org/records/23417491/files/chernoff-two-pass.pdf), with its [original source package](https://zenodo.org/records/23417491/files/chernoff-two-pass-source.zip). That Zenodo record and [QIQC issue #139](https://github.com/Naixu-Guo/quantum-open-problems/issues/139) describe v1; the present website release is v2.

When quantum systems must be measured separately, classical communication still leaves room for a useful form of feedback. A laboratory can make a partial measurement, share its outcome, and retain a quantum output. After hearing from the other laboratories, it can choose how to measure that output. This second visit improves the exponential rate at which the discrimination error falls, even when each input is a qubit.

The result refutes the universal equality with the measured Chernoff exponent in [QIQCOP's copywise discrimination problem](https://qiqc-op.com/problem/op_a370855db65d4d24/). Version 2 also establishes existence of the optimal LOCC exponent. The broader determination of optimal LOCC and separable exponents remains open.

## Local memory and feedback

[Hayashi's single-visit theorem](https://arxiv.org/abs/0804.0686) allows each measurement to depend on all preceding outcomes, but requires a copy to be measured to completion before moving on. Classical adaptation within this model has the same optimal exponent as the best fixed single-copy measurement.

The protocols here retain quantum information between visits. The four-dimensional construction reads an orthogonal flag without disturbing a conditional qubit. The qubit construction creates its branch label through a partial measurement, retaining an output on one branch. The final readout depends on the shared first-pass record.

Every operation acts on one input copy. The inputs are product states, and the protocols use local quantum storage and classical messages. A pass visits each relevant input; it may involve many operations and messages. The result does not establish a strict hierarchy between every successive number of communication rounds or visits.

## A faithful qubit separation

Let $$0<\epsilon<1/2$$, $$\delta=\epsilon^2$$, and $$L=\log(1/\epsilon)$$. Define

$$
|\phi\rangle=\sqrt\epsilon\,|0\rangle+\sqrt{1-\epsilon}\,|1\rangle,
$$

$$
\rho_\epsilon=(1-\delta)|0\rangle\langle0|+\delta|1\rangle\langle1|,
\qquad
\sigma_\epsilon=(1-\delta)|\phi\rangle\langle\phi|+\delta(I-|\phi\rangle\langle\phi|).
$$

Both states have strictly positive eigenvalues and do not commute. The measured exponent and an achievable LOCC exponent satisfy

$$
C_{\mathrm M}(\rho_\epsilon,\sigma_\epsilon)\le\frac23L,
\qquad
\xi_{\mathrm{LOCC}}(\rho_\epsilon,\sigma_\epsilon)\ge\frac{13}{18}L-\log3.
$$

Their difference is at least $$L/18-\log3$$. At $$\epsilon=2^{-36}$$ this is $$\log(4/3)>0$$, and the additive gap grows without bound as $$\epsilon\downarrow0$$. For each state pair, $$\epsilon$$ is fixed before the number of copies tends to infinity. The theorem gives an achievable bound, not the exact optimal qubit exponent.

The proof accounts for every first-pass string. With $$\beta_n=2p_{\mathrm e}(n)$$, the specified two-pass protocol obeys

$$
\beta_n\le(3\epsilon^{13/18})^n
\qquad(n\ge1).
$$

Dimension two is therefore sufficient, and minimal, for a strict asymptotic separation. The certified example has very small positive eigenvalues; it is an asymptotic construction rather than a claim of a large experimental noise margin.

## Existence and comparison of rates

For every finite-dimensional state pair, the optimal finite-round copywise LOCC errors satisfy

$$
\beta_{n+m}^{\mathrm{LOCC}}\ge
\beta_n^{\mathrm{LOCC}}\beta_m^{\mathrm{LOCC}}.
$$

This product inequality proves that the ordinary LOCC exponent exists. It applies to arbitrary finite LOCC protocol trees, including revisits and retained local quantum memory.

For orthogonally flagged pure conditional states, explicit formulas determine the measured and collective exponents. LOCC and separable tests attain the collective exponent. The local attainability follows from [Virmani, Sacchi, Plenio and Markham's binary pure-state discrimination theorem](https://arxiv.org/abs/quant-ph/0102073); the paper supplies the rate formulas, an elementary two-pass proof, and a sharp factor $$3/2$$ bound on the ratio to the measured exponent.

Faithful four-dimensional approximations approach the same ratio. The faithful-approximation proof uses conditional noise $$\delta=e^{-T^3}$$ with $$v=e^{-T}$$ and $$\eta=T^{-3/2}$$. The resulting rates are $$C_{\mathrm M}=T+o(1)$$ and $$\xi_{\mathrm{LOCC}}=3T/2-\log2+o(1)$$. This does not establish $$3/2$$ as an upper bound for all faithful pairs. For general faithful states, the standard fidelity comparison gives the upper bound two.

## The four-dimensional example

The original construction is retained in full. With $$\varepsilon=2^{-16}$$, $$a=1-\varepsilon$$, $$p=4/5$$, $$A=\operatorname{diag}(a,\varepsilon)$$ and $$B=HAH$$ for the qubit Hadamard matrix $$H$$, set

$$
\rho=pA\oplus(1-p)B,\qquad
\sigma=(1-p)B\oplus pA.
$$

Every fixed single-copy measurement has exponent $$C_{\mathrm M}<0.677144$$. The two-pass protocol has an exactly determined exponent

$$
E=\log(5/4)+\log2-h_2(u),\qquad
u=\frac{\log(2a)}{\log65535},
$$

where $$h_2$$ is binary entropy with natural logarithms. Rigorous bounds give

$$
0.68250256<E<0.68250257,
\qquad E-C_{\mathrm M}>0.005359.
$$

Matching finite-copy error bounds establish this exact protocol exponent. It remains a lower bound on the optimal-class exponents.

## Prior work, checks and remaining questions

Hayashi's Section V treats single-visit adaptation; Section IX leaves the corresponding two-way LOCC and SEP Chernoff question open. [Calsamiglia and coauthors](https://arxiv.org/abs/1004.5522) studied mixed qubits through finite-copy bounds and asymptotic fits; those fits do not give a converse uniform over all faithful qubit pairs. The copywise model here also differs from the two spatial laboratories of [Matthews and Winter](https://arxiv.org/abs/0710.4113), and from the retained collective receiver memory allowed by [Salek, Hayashi and Winter](https://arxiv.org/abs/2011.06569).

The complete v2 manuscript passed a fresh internal AI proof review of its exact stated claims. The combined checker ran twice in separate clean verifier processes. It checks the four-dimensional rational bounds, direct qubit matrix identities at five parameter values, 30 finite-transcript cases, and the faithful-approximation estimates with 100-digit arithmetic. The asymptotic conclusions rest on the analytic proofs. These checks are not external peer review or proof-assistant certification; the source package records their scope and results.

The optimal exponent of the faithful qubit family remains unknown. General SEP convergence, a possible separation between the optimal LOCC and SEP exponents, and a strict hierarchy for further visits remain open. The equality of LOCC, SEP and collective rates is established for the pure-conditional flagged class. The broader catalog problem is not claimed solved, and exhaustive historical priority has not been certified.

**Human and AI contributions.** Yuxuan Zhang set research directions, designed the harness coordinating model tasks, tools, memory, and checking, supplied physical and mathematical intuitions and proof skeletons, and guided the development and revision of the research ideas. In that work, AI models developed detailed candidate arguments and derivations, searched the literature, wrote and ran computational checks, and drafted and revised the manuscript under his supervision. Mao-Sheng Li supplied the complementary mathematical draft, including the LOCC product-value argument, the faithful qubit construction and the flagged-state analysis. AI assistance was also used to consolidate and revise the manuscript. K-Dense's [scientific-writing skill](https://arxiv.org/abs/2609.00065) assisted manuscript organization and evidence tracking.
