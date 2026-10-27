---
layout: page
title: "A small collective cooling advantage in a four-collision model"
description: "A finite-budget proof candidate comparing normalized collective and independent couplings, with its explicit protocol, proof outline and verification limits."
date: "2026-10-27"
permalink: /agentic-research/collective-collision-cooling/
status: "research note · proof candidate"
target: "Supplied problem P12 · Two thermal oscillators and at most four non-Gaussian collisions"
---

**Research note, version 1.0 · 27 October 2026.** The argument covers the complete supplied problem and has undergone sequential analytic checks and two computational implementations. **Independent review and confirmation of novelty remain outstanding.** P12 is an identifier in the supplied question set, not a verified QIQCOP catalog number.

The candidate result is a small, explicit separation. With the same total action budget and at most four collisions, a protocol that can address normalized combinations of two oscillator modes has lower final mean excitation than every protocol restricted to addressing those modes separately:

$$
E_{\mathrm{coll}}(3)\le 0.390028802
<0.3902\le E_{\mathrm{ind}}(3).
$$

The comparison uses the same nonlinear interaction on both sides. Its extra resource is the choice of mode combination. It does not compare strong coupling with weak coupling.

## What is being compared

Set ℏ = ωS = ωM = β = 1. Each target and each fresh machine begins in the thermal state

$$
\tau=(1-q)\sum_{n=0}^{\infty}q^n|n\rangle\langle n|,
\qquad q=e^{-1}.
$$

There are two target modes, initially in the product state τ ⊗ τ. A collision couples a chosen target mode combination to a fresh machine mode b through

$$
U(s,v,\phi)=\exp\!\left[-is\left(
e^{i\phi}a_vb^{\dagger 2}+e^{-i\phi}a_v^\dagger b^2
\right)\right],\qquad
a_v=v_1a_1+v_2a_2,\quad \|v\|_2=1.
$$

After the collision the machine is discarded. Each s is nonnegative, the sum of the s values is at most T, and at most four collisions are allowed. The objective is the final expectation of N₁ + N₂, with Nⱼ = aⱼ†aⱼ. Initially it is 2/(e − 1), approximately 1.163953414.

The independent class allows only v = e₁ or v = e₂. The collective class allows any normalized complex direction v. Both allow arbitrary phases and durations subject to the same budget. No extra control operations, measurements, feedback or postselection are available. The displayed equation specifies the interaction-picture dynamics; a bare-Hamiltonian drift is not added.

Normalization matters. For example, coupling to (a₁ + a₂)/√2 changes the addressed mode without increasing the norm of its coefficient vector. The conserved quantity for one collision is 2N + B, where B is the machine occupation. This charge is a symmetry of the specified generator; it is not the physical total bare energy N + B. The result is therefore a statement about this action-constrained control model, not a work-cost or autonomous-refrigerator performance theorem.

## An explicit protocol

Use zero phase in every collision and take the following sequence:

| Collision | Addressed mode | Action s |
|:--|:--|:--|
| 1 | a₁ | 79/125 = 0.632 |
| 2 | a₂ | 79/125 = 0.632 |
| 3 | (a₁ + a₂)/√2 | 337/500 = 0.674 |
| 4 | (−a₁ + a₂)/√2 | 337/500 = 0.674 |

The total action is 653/250 = 2.612, within the budget T = 3. The last two collisions directly address the allowed combinations. A change of basis in the calculation does not insert a physical beam splitter into the protocol.

The initial pair of identical thermal states is invariant under a passive change of mode basis. The useful change of basis comes after two nonlinear cooling steps. To evaluate it, the calculation retains the complete occupation distributions produced by those steps, rather than assigning each output an effective temperature. This provides an exact route to the witness energy; it does not establish entanglement as the necessary resource for the advantage.

## How the comparison is certified

There are two distinct requirements: an upper bound for the displayed collective protocol and a lower bound for the entire independent class. Numerical optimization alone would not establish the second requirement.

### Collective upper bound

For one target and one machine, the charge sector ℓ = 2n + m is finite. The generator in that sector is a real symmetric tridiagonal matrix with entries

$$
(G_\ell)_{n-1,n}
=\sqrt{n(\ell-2n+1)(\ell-2n+2)}.
$$

The direct sum of these finite self-adjoint blocks defines the collision unitary. The exact one-mode transition kernel is

$$
K_s(h,n)=\sum_{m\ge0}(1-q)q^m
\left|\left[e^{-isG_{2n+m}}\right]_{h,n}\right|^2.
$$

A thermal machine makes the channel covariant under number rotations, so diagonal target states remain diagonal. Conjugating the machine by its number rotation removes φ without changing its thermal state or the partial trace. The phase freedom therefore does not invalidate the independent bound below.

Write t = 79/125, u = 337/500, pₙ = (1 − q)qⁿ, f = Kₜp, and eᵤ(j) = ∑ₕ hKᵤ(h,j). After the first two collisions the state is σₜ ⊗ σₜ. The last two orthogonal-mode channels commute. Their total final energy depends only on the two marginal occupation distributions in that basis, giving the positive sum

$$
F=2\sum_{n,m\ge0}f(n)f(m)
\sum_{j=0}^{n+m}B_{j,n,m}\,e_u(j),
$$

where the exact basis-change probabilities are

$$
B_{j,n,m}=\frac{j!(n+m-j)!}{2^{n+m}n!m!}
\left[\sum_a(-1)^{j-a}\binom{n}{a}\binom{m}{j-a}\right]^2.
$$

Out-of-range binomial coefficients vanish. These probabilities follow by expanding the two creation operators in the rotated basis.

For the finite sum, retain initial and first-stage target occupations through 16 and machine occupations through 32, while keeping complete charge sectors in every exponential and every allowed final occupation. Introduce all four machines at the start. The full protocol conserves

$$
Q=2(N_1+N_2)+B_1+B_2+B_3+B_4.
$$

Every history with initial Q ≤ 32 survives the cutoffs. On the complement the final target energy is at most Q/2. Since the summands are nonnegative, the omitted contribution is bounded by

$$
\frac12\mathbb E[Q\,\mathbf 1_{Q>32}]
\le 0.000060722719941275.
$$

This tail is evaluated from the exact initial generating function

$$
\mathbb E[z^Q]=
\left(\frac{1-q}{1-qz^2}\right)^2
\left(\frac{1-q}{1-qz}\right)^4.
$$

The spectral implementation, with verified residuals and directed rounding, gives a full energy upper bound of 0.390028801307254. A second implementation uses direct matrix Taylor expansions and norm-controlled squaring, without an eigensolver; its upper bound is 0.3900288013064348. Both support the deliberately rounded bound 0.390028802 stated above. These are different arithmetic methods implemented by the same agent.

### Lower bound for all independent protocols

Let mᵣ(3) be the infimum one-target energy after at most r collisions, with total action at most 3. Zero-duration collisions include shorter protocols. The certificate establishes

$$
m_1(3)\ge 0.274,\qquad m_2(3)\ge 0.1951.
$$

Here the finite kernels retain target occupations through 10 and machine occupations through 20. They are unnormalized positive partial sums of the exact dynamics, hence lower bounds. No tail subtraction is needed for this direction of the inequality.

The entire one-time interval and two-time simplex are covered by dyadic boxes. Each feasible box receives a Taylor lower bound from outward-enclosed values, gradients and Hessians, together with uniform third-derivative bounds of 684 and 1434. Exact rational endpoints exclude only boxes wholly outside the action constraint. Prefix-free leaf paths with exact Kraft sum one certify complete coverage. The corrected calculation uses 22 one-dimensional leaves and 1,918 two-dimensional leaves; 97 of the latter are wholly infeasible. The smallest accepted lower bounds are respectively 0.28130411092203716 and 0.1951309933896756, above the quoted thresholds.

For three collisions, a time-independent relaxation supplies

$$
m_3(T)\ge 0.1163648821387783442\qquad\text{for every }T.
$$

Retain the three machines and allow every unitary preserving 2N + B₁ + B₂ + B₃. In charge sector ℓ, target occupation n has multiplicity binom(ℓ − 2n + 2, 2), and each initial basis eigenvalue is (1 − q)⁴q^(ℓ − n). Pairing decreasing input eigenvalues with increasing target energies gives a lower bound by the rearrangement inequality. Summing only the nonnegative sector minima through ℓ = 40, with downward rounding, gives the displayed bound. The enlarged unitary class is used for a converse, not claimed reachable by sequential collisions.

Independent operations on separate targets commute and preserve a product state. With at most four collisions, either a target is untouched, each gets at most two, or the allocation is (3, 1) up to exchange. Giving each target the full budget 3 enlarges the independent feasible set and therefore preserves a lower bound. Thus

$$
\begin{aligned}
E_{\mathrm{ind}}(3)
&\ge\min\left\{\frac1{e-1},\;2(0.1951),\;
0.274+0.1163648821387783442\right\}\\
&=0.3902.
\end{aligned}
$$

This covers every allowed assignment, ordering, phase, continuous choice of durations, shorter protocol and unused budget. The collective witness and monotonicity of the independent infimum also give the same separation for every T between 2.612 and 3.

## Scale, context and limits

The conservative separation is 0.000171198 in total mean excitation, about 0.044% of the independent lower-bound benchmark. This is a guaranteed margin between bounds, not the exact optimum gap. The collective protocol is not claimed optimal. The conclusion is an existence result in one explicitly constrained model; there is no demonstrated scaling advantage, broad robustness region, experimental benefit or general thermodynamic efficiency advantage.

The closest supplied reference is Png, Hu and Scarani, [*Sub-Bath Cooling in Bosonic Systems: Gaussian Constraints and Non-Gaussian Enhancements*, arXiv:2512.10703v2](https://arxiv.org/html/2512.10703v2). Its Section IV studies non-Gaussian p-excitation exchange for a single target and machine, with a bare Hamiltonian included; its conclusion identifies collective advantage as future work. The present note treats the specific four-collision, fixed-action interaction-picture comparison above. That distinction is narrower than resolving the paper's entire proposed research direction. The source comparison does not establish publication priority.

The substantive point is the lower bound over **all** admissible independent histories, together with an explicit collective witness. It is best viewed at present as a concrete, modest separation supported by a reproducible proof candidate. Whether it leads to a more general principle remains open.

## Verification record and reproducibility

An earlier interval implementation accidentally shared storage between its lower and upper endpoints. That version was invalidated. The corrected version owns separate endpoint arrays and reran the complete box certificate. The correction is preserved in the research record; the invalid certificate is not evidence for this note.

Further checks compare values, gradients and Hessians at ten decisive box centers, compare transition kernels and derivatives at four additional times, and exercise 823 exact-rational arithmetic containment cases plus endpoint independence. These checks support the argument without constituting independent review or formal proof-assistant verification.

Before posting this note, the six numerical programs were rerun sequentially from an isolated copy, and all reproduced the stated bounds and checks. The complete proof record P12-R40-v1, detailed dependencies, computational certificates, code and file hashes are retained locally. Those underlying files are not attached to this page, so this webpage alone is not a standalone reproducibility package. The current review status is the one stated at the beginning of this note.

The mathematical derivation, computation and drafting were carried out with AI assistance under human direction. This note records the checks actually performed in this run; it does not imply an independent human proof review, catalog acceptance or an archival deposit.

[Back to the research log]({{ '/agentic-research/' | relative_url }}).
