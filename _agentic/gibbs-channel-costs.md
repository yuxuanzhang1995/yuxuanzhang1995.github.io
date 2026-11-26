---
layout: page
title: One-shot coherence and deterministic work costs for Gibbs-preserving channels
description: A finite-clock criterion, the small-error coherence exponent, and sharp work costs for three thermal-bath conventions.
date: 2026-11-26
status: Complete proof candidate · sequential internal review
target: QIQCOP Zoo · Resources for implementing Gibbs-preserving channels
pdf: gibbs-channel-costs-v1.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang<sup>1,2</sup>** · Version 1.0 · 26 November 2026

<sup>1</sup> École Polytechnique Fédérale de Lausanne  
<sup>2</sup> Princeton University

[Manuscript (PDF)]({{ '/assets/pdf/agentic/gibbs-channel-costs-v1.pdf' | relative_url }}) · [Detailed proofs, manuscript source and checks (ZIP)]({{ '/assets/code/agentic/gibbs-channel-costs-v1.zip' | relative_url }}) · [Original problem](https://qiqc-op.com/problem/op_56578531a2c610fe/)

A quantum channel can leave a Gibbs state unchanged and still require a clock to implement it. How good must the clock be to act on an arbitrary input, including one entangled with a reference? A second question charges only the energy lost by a battery that must finish at one precise energy on every run. The two costs can behave quite differently.

Consider measuring a qubit in the $$X$$ basis when its energy is diagonal in the $$Z$$ basis. Write the answer into a classical bit with degenerate energy levels. An input Gibbs state gives a fair bit, so this channel is Gibbs preserving. To implement the measurement with a finite clock, its quantum Fisher information must grow as $$\varepsilon^{-2}$$ when the allowed error $$\varepsilon$$ tends to zero. With only a sharp-energy battery, the best achievable channel error is exactly $$1/\sqrt{2}$$. Time-translation covariance forces the same output on the two $$X$$ eigenstates, while the requested measurement gives opposite records.

## Finite clocks and vanishing error

For a general finite-dimensional channel, a finite clock can implement it exactly if a matrix polynomial on the system's energy lattice satisfies a coefficient positivity condition. The manuscript gives a finite structural test for any number of independent energy gaps, and matching upper and lower bounds on the least exact quantum Fisher information when the test succeeds. The decision procedure takes exact lattice labels and algebraic sector data. At positive error, finite semidefinite programs converge to the optimum from both sides.

The growth rate near zero error follows from a finite sequence of linear moment tests in a minimal Stinespring dilation. If order $$k$$ is the first inconsistent one, the cost grows as $$\Theta_\Phi(\varepsilon^{-2/k})$$. When every order passes, the small-positive-error cost stays bounded. A separate test at zero error is necessary because bounded-cost approximations can exist even when no finite clock realizes the channel exactly.

## A three-level example distinguishes the heat baths

In the work problem the battery is the only nonthermal input. At positive inverse temperature, with a countable bath whose Gibbs state is normalizable, finite work is possible precisely when the error ball contains a time-translation covariant channel. The proof gives a matching value from the energy blocks of the bath. For the explicit Gibbs-preserving three-level channel in the manuscript, the work cost at inverse temperature one and zero channel error is as follows.

| Allowed thermal process | Deterministic work cost |
| --- | --- |
| Finite Gibbs bath, battery exactly sharp | $$+\infty$$ |
| Countable bath with a normalizable Gibbs state, battery exactly sharp | $$\log 16$$ |
| Limit of finite joint processes at a fixed gap, battery exactly sharp in the limit | $$\log(529/36)$$ |

The logarithms are natural. In a finite bath the initial Gibbs state occupies every energy level. Conservation would have to translate the entire finite nonbattery spectrum by the battery's loss, including its highest level. Only a zero shift is possible. If the joint process is closed first, the finite approximants may instead have a battery failure probability that tends to zero. This changes the exact cost even though the final battery in the limiting process is sharp.

## Prior work and review

Tajima and Takagi established infinite-coherence examples and quantitative lower bounds for pairwise reversible channels. Faist, Berta and Brandão derived an optimal asymptotic work rate over many independent uses. This manuscript treats a single use at each error, down to the exact endpoint, and gives the three bath conventions separately. [Tajima and Takagi](https://arxiv.org/abs/2404.03479) · [Faist, Berta and Brandão](https://arxiv.org/abs/1911.05563)

The same AI researcher developed and reviewed the proofs. The supplement identifies the two steps that most need independent mathematical scrutiny: the finite-clock test at arbitrary Kraus rank, and the exact-cost lower bound at resonant energy gaps. It includes the analytic arguments and executable controls for finite cases. Independent specialist review and first-discovery priority remain open.
