---
layout: page
title: Two-pass local measurements beat the measured Chernoff exponent
description: "An explicit faithful four-dimensional counterexample: revisiting locally stored qubits strictly improves the asymptotic error exponent over every fixed single-copy measurement."
date: 2026-10-16
status: counterexample
target: Copywise Chernoff exponents — universal measured-exponent equality
pdf: chernoff-two-pass.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**

[Manuscript, version 1.0, 16 October 2026 (PDF, 10 pages)]({{ '/assets/pdf/agentic/chernoff-two-pass.pdf' | relative_url }}) · [LaTeX source, exact checker and verification records (ZIP)]({{ '/assets/code/agentic/chernoff-two-pass-source.zip' | relative_url }})

When many preparations of a quantum system must be measured separately, can exchanging classical information improve how quickly the discrimination error falls? The answer depends on whether each preparation is measured to completion on its first visit. This manuscript gives an explicit example in which retaining a qubit at each party, exchanging information, and returning for a second measurement strictly improves the asymptotic error exponent.

The result is a complete counterexample to the universal equality with the measured Chernoff exponent in [QIQCOP's copywise discrimination problem](https://qiqc-op.com/problem/op_a370855db65d4d24/). The entry's broader request to determine the optimal LOCC and separable exponents remains open.

## What the second pass changes

Each four-dimensional input has an orthogonal classical flag and a conditional qubit. The first pass reads the flag while leaving that qubit available. The parties share all their flags, then use the majority to choose the qubit measurement bases for the second pass. Finally, they make the optimal classical likelihood decision.

Every operation acts on one input copy. The protocol needs local storage and classical messages; it uses no shared entanglement or joint operation on different copies. A pass visits every party, so two passes should not be confused with just two individual LOCC operations.

[Hayashi's single-visit adaptive theorem](https://arxiv.org/abs/0804.0686) shows that choosing successive single-copy measurements from earlier classical outcomes does not improve the Chernoff exponent over the best fixed measurement. In the two-pass protocol, all flags can inform the final measurement of every retained qubit. That is the additional resource used here.

## The quantitative separation

All logarithms are natural. Put

$$
\varepsilon=2^{-16},\quad a=1-\varepsilon,\quad p=\frac45,\quad
A=\operatorname{diag}(a,\varepsilon),\quad B=HAH,
$$

where $$H$$ is the qubit Hadamard matrix, and define

$$
\rho=pA\oplus(1-p)B,\qquad
\sigma=(1-p)B\oplus pA.
$$

These states are noncommuting and have minimum eigenvalue $$1/327680>0$$. The best fixed single-copy measurement has exponent

$$
C_{\mathrm M}<\log(5/4)+0.454<0.677144.
$$

The displayed two-pass protocol has the exact exponent

$$
E=\log(5/4)+\log2-h_2(u),\qquad
u=\frac{\log(2a)}{\log65535},
$$

where $$h_2(u)=-u\log u-(1-u)\log(1-u)$$. Rigorous interval arithmetic gives

$$
0.68250256<E<0.68250257,
\qquad E-C_{\mathrm M}>0.005359.
$$

An error exponent describes decay roughly as $$e^{-nE}$$. A fixed positive improvement in the exponent therefore persists as the number of copies grows. The manuscript proves the separation analytically, including a rational lower bound of $$0.003$$ on the gap. The sharper decimal enclosure is supplementary.

For every integer $$n\ge1$$, the protocol's actual error obeys

$$
\frac{e^{-d-nE}}{4(n+1)^2}
\le p_{\mathrm e}^{\mathrm{tp}}(n)
\le \frac{n+1}{2}e^{-nE},
\qquad d=\log65535.
$$

These matching exponential bounds determine the protocol's exponent. Since the protocol is finite-round LOCC and its two decision effects are fully separable, both optimal lower exponents exceed $$C_{\mathrm M}$$ for this pair.

## Relation to earlier work

Hayashi's [Section V](https://arxiv.org/pdf/0804.0686) treats successive single-visit measurements; Section IX explicitly asks whether two-way LOCC improves asymptotic performance beyond the Stein setting. The protocol here retains quantum states for a later visit and addresses the symmetric Chernoff setting.

[Calsamiglia and coauthors](https://arxiv.org/abs/1004.5522) studied mixed qubits using finite-copy partial-transpose bounds and asymptotic fits. Their examples do not supply a converse for this four-dimensional pair. [Matthews and Winter](https://arxiv.org/abs/0710.4113) use a different partition, with two laboratories holding many local subsystems. [Salek, Hayashi and Winter's channel-discrimination framework](https://arxiv.org/abs/2011.06569) permits joint operations on a receiver's output memory and new channel outputs. The present model keeps every input copy at a separate party.

The single-copy bound uses a variational method related to measured Rényi quantities; this method is attributed to [Berta, Fawzi and Tomamichel](https://doi.org/10.1007/s11005-017-0990-7). The manuscript includes all inequalities needed for its particular bound. The checked closest sources do not contain the same counterexample; an exhaustive historical priority certification has not been completed.

## Verification and scope

The full manuscript received a fresh internal AI proof review without the earlier review verdicts. Its decisive checker ran twice in separate clean verifier processes. A separate integer implementation evaluates the protocol's transcript error, while outward rational intervals check the exponent, the uniform single-copy cap, and both error bounds for $$n=1,2,3,4,8,16,32,64,128$$. The universal conclusions come from the analytic proof, with finite calculations providing cross-checks. These checks are not external peer review or formal proof-assistant verification.

The paper establishes the counterexample and the exact exponent of its specified protocol. It does not identify the optimal unrestricted LOCC or separable exponent, prove that those two classes have equal exponents, or establish convergence of their optimal exponent sequences. It also makes no minimal-dimension or minimum-storage claim. The website label records a counterexample to the universal equality, rather than a complete determination of the broader catalog problem.

The source package contains the manuscript, standalone exact checker, frozen counterexample proofs, primary-source comparison and review records. This is the website release of version 1.0.

**Human and AI contributions.** The author set the research directions, designed the harness that coordinated model tasks, tools, memory, and checking, supplied physical and mathematical intuitions and proof skeletons, and guided the development and revision of the research ideas. AI models developed detailed candidate arguments and derivations, searched the literature, wrote and ran computational checks, and drafted and revised the manuscript under this supervision. K-Dense's [scientific-writing skill](https://arxiv.org/abs/2609.00065) assisted manuscript organization and evidence tracking.
