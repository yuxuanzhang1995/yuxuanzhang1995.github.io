---
layout: page
title: Multi-slot virtual channel conjugation
description: An exact signed simulation of the conjugate of an unknown channel, a closed formula for the state subcase, and certified adaptive advantage at three slots.
date: 2026-09-14
status: partially solved
target: QIQCOP problem op_06e9f0c7b3b62f3b
pdf: multi-slot-conjugation.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang**<br>
Department of Physics, Princeton University, Princeton, New Jersey 08544, USA<br>
Institute of Physics, École Polytechnique Fédérale de Lausanne (EPFL), CH-1015 Lausanne, Switzerland

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/multi-slot-conjugation.pdf' | relative_url }}">Full version (PDF, 7 pp)</a></p>

## Background

Some linear maps on quantum states are useful but not physical — complex conjugation and
transposition among them. They can still be *simulated* by taking a signed combination of physical
circuits and post-processing the outcomes, at a cost: the sum of absolute coefficients, which
controls the sampling overhead. The framework for quantifying that cost is [5], and the circuit
model for querying an unknown channel several times with memory is the quantum comb [6].

For an unknown channel given as a black box, the one-query optimum is known [2]. The natural next
question — what repeated queries buy — is [QIQCOP problem op_06e9f0c7b3b62f3b](https://qiqc-op.com/problem/op_06e9f0c7b3b62f3b/) [1].

## The problem

Let Λ be an unknown CPTP map, and let a *slot* be one call to it. Each branch of the protocol is a
deterministic fixed-order *n*-slot comb with arbitrary finite quantum memory. The target is
**complex conjugation in fixed bases** — not the adjoint. The cost is the infimum of the sum of
absolute real coefficients over universal *exact* signed combinations of such branches.

Two things are being asked: how the cost behaves as *n* grows, and whether **adaptive** access —
feeding one query's output into the next — beats running the queries in **parallel**.

## What was established

**A general construction.** An explicit physical parallel comb realises the target exactly at every
finite *n*, built from unnormalised Choi matrices with swap pairs transposing the inserted channel.
Its cost is controlled by a Jucys–Murphy content bound [3], and at any fixed nontrivial pair of
dimensions the cost approaches one at the optimal order. The cost, not the channel error, is what
has a limit — the simulation is exact throughout.

**An exact formula for the state subcase.** When the input dimension is one, the optimal cost is
given in closed form by a finite sum over integer partitions with Weyl dimensions and rational
arithmetic. It optimises over freely chosen CPTP branches rather than a fixed white-noise line.

**Two queries, and where adaptivity starts.** For all dimensions the optimal two-slot adaptive and
parallel costs *coincide* — adaptivity buys nothing at two queries. At three and four qubit-channel
slots, rational primal/dual witnesses put the optimum in certified intervals whose upper endpoints
fall strictly below the corresponding parallel lower bounds. So **three slots is the first point at
which adaptive access can help at all** in this problem.

## Verification

The certificates are exact. Verification uses no optimizer, no numerical eigenvalue threshold and
no saved floating-point seed; integer products carry explicit overflow bounds. The four-slot system
is 3,330 adaptive (4,506 parallel) equations in 1,864 branch coefficients, reduced by exact
highest-weight projection to nine positivity blocks and checked by rational elimination, with a
dual witness supplying the lower bound. A separate cross-check certifies the primal's universal
action across all 1,820 channel-monomial groups without sampling channels.

Three AI reviewers worked independently — one rederiving the construction and lower bound before
reading the proof, one checking the state formula and its prior-art context, one adversarial.

**The adversarial pass found two real defects in the verifier**, and this is the part worth
dwelling on. The three-slot code converted saved rational dual equations to floating point when
checking provenance, so a tiny rational perturbation of a right-hand side could pass that check and
**forge a lower bound**. The four-slot verifier accepted misordered symmetric/skew metadata. Both
were replaced by exact checks, with regressions that reject the malformed inputs. The original
certificate rows passed independent exact provenance checks, so no endpoint moved — but a
verifier that can be fooled is worth reporting whether or not it changed an answer.

## What remains open

The broad question is **unsolved, and should stay listed as such**.

1. **No general formula** for the optimum at arbitrary finite *n*.
2. **No proof that the leading coefficient converges** for general channels; even in the qubit case
   only a range is proved.
3. **Fixed order only.** Everything here concerns fixed-order combs, not indefinite causal order.
4. **No efficient synthesis.** The constructions are not shown to compile to efficient circuits.
5. **Cost is not query count.** Sampling variance scales with squared signed cost, but each run
   consumes *n* calls, so a lower coefficient alone does not prove fewer total channel queries.

Priority is not claimed: the literature search was limited, and absence of a matching source is not
evidence of novelty. The pieces offered for scrutiny are the general-channel parallel lift, the
sector-resolved state evaluation, the two-slot statements, and the finite adaptive certificates.

## References

1. QIQCOP, *Multi-slot overhead of virtual channel conjugation*, problem [op_06e9f0c7b3b62f3b](https://qiqc-op.com/problem/op_06e9f0c7b3b62f3b/).
2. C. Zhu, Z. Tang, G. Zhen, Y. Li, G. Bai and X. Wang, *Simulation of adjoints and Petz recovery maps for unknown quantum channels*, [arXiv:2602.05828](https://arxiv.org/abs/2602.05828).
3. V. Brzić, D. Grinko, M. Studziński and M. T. Quintino, *Optimal pure state cloning and transposition are complementary channels*, [arXiv:2603.23628](https://arxiv.org/abs/2603.23628).
4. Q. Dong, M. T. Quintino, A. Soeda and M. Murao, *Implementing positive maps with multiple copies of an input state*, Phys. Rev. A **99**, 052352 (2019), [arXiv:1808.05788](https://arxiv.org/abs/1808.05788).
5. B. Regula, R. Takagi and M. Gu, *Operational applications of the diamond norm and related measures in quantifying the non-physicality of quantum maps*, [Quantum **5**, 522 (2021)](https://doi.org/10.22331/q-2021-08-09-522).
6. G. Chiribella, G. M. D'Ariano and P. Perinotti, *Theoretical framework for quantum networks*, [Phys. Rev. A **80**, 022339 (2009)](https://doi.org/10.1103/PhysRevA.80.022339).
