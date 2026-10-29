---
layout: page
title: "A strict quantum work advantage in three-round cooling"
description: "A complete internally checked solution candidate with equal memory, exact product return, a universal population converse and a reproducible computational certificate."
date: "2026-10-29"
permalink: /agentic-research/three-round-quantum-cooling-work/
status: "complete solution candidate · internally checked"
target: "Supplied problem P11 · Three-round cooling with equal retained memory"
---

**Research note, version 1.0 · 29 October 2026.** This note presents a complete solution candidate for the finite model stated below. Its analytic reductions, exhaustive computational certificate and exact feasible protocols have passed internal checks. A second arithmetic implementation checks the feasible protocols and strict gap. **These checks were performed by the same agent; independent expert review and broader novelty confirmation remain outstanding.** P11 is an identifier in the supplied question set, not a verified public problem-catalog number.

At the inverse temperature

$$
\gamma=1.00001,
$$

the candidate establishes

$$
W_Q(\gamma)+6\times10^{-9}\leq W_C(\gamma),
\qquad W_Q(\gamma),W_C(\gamma)<\infty.
$$

The comparison allows the same retained qubit memory and the same three bath molecules in both classes. The memory must be returned in its original thermal state, exactly uncorrelated with the cooled target in the unconditional output. The population lower bound covers every permitted permutation protocol and every externally randomized mixture of such protocols.

The guaranteed improvement is small: the certified gap between bounds is greater than \(6.26982680365\times10^{-9}\), about 0.217% of the population lower bound. The result does not identify either optimum or establish a scaling advantage. It separates unrestricted quantum control from the specific population-permutation class defined here; it does not isolate which intermediate coherences are necessary for the advantage.

## Model and precise claim

Set \(\hbar=k_{\mathrm B}=\beta=1\). The target \(S\) and each fresh bath molecule \(R_j\) are qutrits, while the retained memory \(M\) is a qubit:

$$
H_S=H_R=\operatorname{diag}(0,1,2),\qquad
H_M=\operatorname{diag}(0,1),\qquad
\tau_\eta(H)=\frac{e^{-\eta H}}{\operatorname{Tr}e^{-\eta H}}.
$$

Initially \(SM\) is \(\tau_1(H_S)\otimes\tau_1(H_M)\). In each of exactly three rounds:

1. A recharge unitary \(V_j\) acts on \(SM\).
2. A fresh, independent \(R_j\) in \(\tau_1(H_R)\) is introduced. A unitary \(U_j\) satisfying \([U_j,H_S+H_M+H_R]=0\) acts, and \(R_j\) is discarded.

Each of these six stages has time \(\pi\) and interaction-picture control norm at most one. There is no additional stage, bath molecule, ancilla, measurement, feedback or postselection. The memory is kept between rounds.

If \(\rho_j\) is the recharge input, define

$$
w_j=\operatorname{Tr}\!\left[(H_S+H_M)
(V_j\rho_jV_j^\dagger-\rho_j)\right],\qquad
W_+=\sum_{j=1}^3[w_j]_+.
$$

Thus extracted work is not credited against positive supplied work. The **quantum class** permits arbitrary allowed unitaries. In the **population class**, every \(V_j\) is a computational-basis permutation and every \(U_j\) is a permutation within total-energy eigenspaces. Both classes allow externally randomized open-loop choices. For such mixtures, the positive parts are taken within each classical branch before averaging.

For \(1<\gamma\leq2\), let \(W_Q(\gamma)\) and \(W_C(\gamma)\) be the infima of this averaged gross work under the exact unconditional target

$$
\rho'_{SM}=\tau_\gamma(H_S)\otimes\tau_1(H_M).
$$

**Candidate theorem.** In this model, at \(\gamma=1.00001\), directed arithmetic gives

| Quantity | Certified bound |
|:--|--:|
| Quantum feasible work, hence an upper bound on \(W_Q\) | \(0.000002877311260917970\) |
| Universal population lower bound on \(W_C\) | \(0.000002883581087721625\) |
| Population feasible work, hence an upper bound on \(W_C\) | \(0.000002895623849635827\) |

The last row establishes finite population cost. Subtracting the quantum upper bound from the population lower bound proves the claimed separation with \(\delta=6\times10^{-9}\). Feasible quantum and population mixtures, exact rational controls, and the complete converse checker are included in the [reproducibility supplement]({{ '/assets/code/agentic/three-round-quantum-cooling-work-v1.zip' | relative_url }}).

## Proof strategy

Write the six \(SM\) basis states as \(s=2a+m\), where \(a=0,1,2\) and \(m=0,1\). Their energies are

$$
E=(0,1,1,2,2,3).
$$

Put \(q=e^{-1}\), \(Z_R=1+q+q^2\), \(Z_{SM}=Z_R(1+q)\),

$$
p_s=\frac{q^{E_s}}{Z_{SM}},\qquad b_r=\frac{q^r}{Z_R}.
$$

The main task is a lower bound for the entire population class. A few good quantum protocols alone would not establish a separation. We use the following exact terminating-decimal price vector:

$$
\begin{split}
y=(&1.0534853791937386,\;1.0534853791937449,\\
&0.06636892168045987,\;0.06636892168045924,\;0,\;0).
\end{split}
$$

The nearly equal entries are retained as distinct exact numbers. For every deterministic population history, with output population \(z\) and gross paid work \(g\), the certificate proves

$$
y\cdot(z-p)-g\leq0. \tag{1}
$$

Any externally randomized open-loop policy is a probability mixture of complete deterministic histories: its correlated random choices can be sampled at the beginning. Averaging (1) therefore gives

$$
W_C(\gamma)\geq y\cdot(t_\gamma-p),\qquad
(t_\gamma)_{2a+m}=\frac{e^{-\gamma a}q^m}
{(1+e^{-\gamma}+e^{-2\gamma})(1+q)}. \tag{2}
$$

This argument uses branchwise gross work, including all random mixtures allowed in the question. It never replaces the average of positive parts by the positive part of averaged work.

## The universal population converse

### 1. Complete first-round reduction

There are \(6!/(2!2!)=180\) distinct permutations of the initial energy profile. A recharge that leaves \(p\) unchanged is followed by a collision that also leaves it unchanged, since \(p\otimes b\) is Gibbs for the total bare Hamiltonian. A leading idle pair may therefore be removed and an identity pair appended at the end. After this reduction, every nonidentity history starts with an active recharge of strictly positive work. No allowed stage count is changed.

The first filtering price \(y_0\), included in the supplement, differs slightly from \(y\). At \(y_0\), a global spectral reward cap excludes 165 of the 179 active profiles: their first work exceeds even the maximum final reward when all three bath molecules are retained and an arbitrary global unitary is allowed. This enlargement of the feasible set is valid for an upper bound on reward.

For the remaining 14 profiles, enumerate the assignments of incoming exponents to destination indices in every collision energy block. The blocks have sizes \(1,3,5,5,3,1\). After discarding the bath, each probability is an exact integer-coefficient polynomial in \(q\) with a common denominator. Equal incoming exponents can be exchanged without affecting the output, and identical reduced coefficient matrices have identical future possibilities. Keeping one legal representative of each matrix gives 58,424 states.

A directed two-bath relaxation excludes 57,832 states. The 592 remaining prefixes reduce to 35 representatives through equal population spectra and the following cost dominance relation. Suppose prefixes \(A,B\) have the same population spectrum, energies \(h_A,h_B\), and paid costs \(c_A,c_B\). If

$$
c_A\leq c_B,\qquad c_A-h_A\leq c_B-h_B,
$$

then \(A\) can simulate any suffix of \(B\) at no greater cost. Absorb the permutation matching their spectra into the next recharge. For a common recharged energy \(x\), the cumulative costs become

$$
\max(c_A,c_A-h_A+x),\qquad
\max(c_B,c_B-h_B+x),
$$

respectively, proving the comparison even when that recharge extracts work. Keeping only \(c\) would not suffice; both quantities are needed.

The change of price must also be justified. Let \(d=y-0.999y_0\). Exact decimal arithmetic gives

$$
\operatorname{osc}(d)=1.062\times10^{-16},\qquad
g\geq0.04160467253998552
$$

for every active history. Since the difference of two probability distributions pairs with \(d\) to at most \(\operatorname{osc}(d)\), every history with a nonpositive old score has new score at most

$$
-0.001g+\operatorname{osc}(d)<-0.0000416046725398793.
$$

This transfers both old exclusion steps. The spectrum/cost dominance relation is itself independent of the price. Identifying the two prices, or treating the scaling as exact without its decimal correction, would leave a gap in the proof.

### 2. All second recharges and second collisions

For each of the 35 representatives, enumerate all 720 second recharges and charge the actual positive part of their signed work. A directed two-bath relaxation excludes 24,656 of the 25,200 choices. The 544 survivors reduce to 88 families after matching coefficient rows within equal \(SM\) energies and retaining a representative of no greater paid cost.

This last matching may be absorbed into the next collision: if \(W\) permutes only equal \(SM\) energies, then \(U_2(W\otimes I_R)\) still preserves total bare energy. An arbitrary energy-changing permutation could not be absorbed this way.

In each of these 88 families, write the post-recharge state as

$$
\rho_s=\frac{\sum_{k=0}^5N_{sk}q^k}{Z_{SM}Z_R},
\qquad N_{sk}\in\mathbb Z_{\geq0}.
$$

Introducing the next bath shifts the coefficient vector in incoming state \((s,r)\) by \(r\). Enumerate all distinct assignments of these vectors inside each total-energy block, sum over outgoing bath indices, and deduplicate identical six-by-eight coefficient matrices. Each has a stored legal collision representative. Since the collision has zero work cost and the bath is discarded, this quotient preserves every possible continuation.

The complete enumeration covers \(88\times518{,}400=45{,}619{,}200\) formal second-collision choices and yields **12,434,168** family/state records. Every reconstructed state is checked against its legal control. A separately written destination-to-source enumeration of all 518,400 permutations for one family yields the same 503,930 distinct states as the quotient construction; this is a completeness control, not a replacement for the general enumeration argument.

### 3. Directed one-bath bound

Fix a post-collision state \(\rho\) and the cost \(c\) already paid. For any \(0\leq\lambda\leq1\),

$$
[w_3]_+\geq\lambda w_3.
$$

The final collision conserves bare energy, so \(w_3\) is the total energy change on \(SM\) and its final bath over the recharge/collision pair. Allowing an arbitrary joint unitary and applying spectral rearrangement gives the upper bound

$$
\begin{split}
B_\lambda(\rho,c)={}&
\sum_i\operatorname{sort}(\rho\otimes b)_i
\operatorname{sort}\!\big(y_s-\lambda(E_s+r)\big)_i\\
&+\lambda(E\cdot\rho+E_R\cdot b)-c-y\cdot p.
\end{split} \tag{3}
$$

Both sorts are in the same order. The relaxed joint unitary need not be implementable by the original final pair; only its upper-bound property is used. The earlier two-bath filters use the identical argument with two fresh bath spectra and total bath energy \(r+t\).

Floating calculations choose a decimal \(\lambda\in[0,1]\). Its optimality is unnecessary. All exclusions are then recomputed outward, using 80-digit directed intervals to enclose \(q\) and other scalar constants and fixed-point integers at scale \(2^{28}\). Nonnegative polynomial coefficients bound the state populations. Products round outward; sorting is coordinatewise monotone. Each upper observable bound multiplies the upper probability if nonnegative and the lower probability if negative. The energy and constant terms round upward separately. Conservative magnitude bounds keep every signed 64-bit operation within range.

The integer numerator divided by \(2^{56}\) is a rigorous upper bound on (3). A floating negative sign is never sufficient to exclude a state. This removes 12,431,254 records and leaves 2,914 states for exact treatment of the final pair.

### 4. Complete final-pair treatment

For each remaining state, enumerate all 720 final recharge permutations. If the resulting population is \(r\), its signed work is \(E\cdot(r-\rho)\). The following collision preserves total energy. In each energy block, matching the sorted incoming probabilities \(r_sb_r\) to the sorted destination rewards \(y_s\) maximizes the reward over all block permutations. Blocks are independent and no stage follows, so this is the exact optimal population collision for that recharge.

All **2,098,080** remaining state/recharge cases are evaluated outward. The reward uses upper probabilities and upper nonnegative rewards. The recharge cost uses the positive part of the lower signed-work bound; lower bounds on \(c\) and \(y\cdot p\) are subtracted. Every resulting upper score is strictly negative. The least-negative certified maximum is below

$$
-0.0001130159592.
$$

Together with the prefix exclusions, dominance reductions and identity history, this proves (1) for every allowed population history. Equation (2) then proves the population lower bound, including arbitrary permitted randomization.

## Exact feasible protocols in both classes

The supplement specifies five population histories and five quantum histories. The former use integer permutations. The latter use permutations composed with real two-level rotations specified by exact rational parameters. For a rational parameter \(t\), the rotations use

$$
\cos\theta=\frac{1-t^2}{1+t^2},\qquad
\sin\theta=\frac{2t}{1+t^2},
$$

or the recorded reciprocal convention. Unitarity is exact. Every rotation in a collision acts within an equal-energy block. These rational controls, rather than rounded floating matrices, define the actual protocols.

In either class, let \(z_j\) be the final six diagonal populations of history \(j\), and let \(g_j\) be its branchwise gross cost. Put \(A_{ij}=(z_j-p)_i\). Define the five weights \(\alpha_j\) as the exact solution of the first five equations of

$$
A\alpha=t_\gamma-p.
$$

Directed interval Gaussian elimination encloses nonzero pivots, each \(\alpha_j>0\), and \(\sum_j\alpha_j<1\). Thus the exact solution exists and defines an allowed mixture of the five histories and an identity history of weight \(1-\sum_j\alpha_j\). The sixth equation follows **exactly** from trace preservation and normalization, not from a numerical residual near zero.

The quantum histories may leave output coherences. Uniformly average over diagonal sign matrices \(D=\operatorname{diag}(\pm1,\ldots,\pm1)\) on \(SM\), folding \(D\otimes I_R\) into the existing final collision in each random branch. Because \(D\) commutes with the bare Hamiltonian, this remains an allowed energy-preserving collision. The average removes off-diagonal entries, leaves the diagonal and every recharge cost unchanged, and introduces no additional stage. The unconditional output is therefore exactly \(\tau_\gamma(H_S)\otimes\tau_1(H_M)\).

Finally, every specified unitary fits the stage time and norm restriction. Choose a Hermitian principal logarithm of norm at most \(\pi\), and divide it by \(\pi\) to obtain the constant control generator. For a collision, take the logarithm within each energy block. The combined final collision including the sign matrix has its own such logarithm; it need not be implemented as two successive stages.

Direct interval propagation and exact mixture equations give the two feasible-work bounds stated above. The second implementation uses 192-bit dyadic intervals, a different exponential enclosure and different state propagation. It encloses the strict gap by

$$
\frac{[39356340709807515497027569615020587876879875028789,
\;39356340709807515497027569615020587876879875029732]}{2^{192}}.
$$

The lower endpoint exceeds \(6\times10^{-9}\). An identity protocol passes, and a deliberately energy-changing collision is rejected. These checks support the feasible witness and arithmetic; the universal converse still depends on the exhaustive certificate proved above.

## Relation to earlier work

Hu and Scarani's [*Thermalization of finite complexity and its application to heat bath algorithmic cooling*, arXiv:2505.10054v1](https://arxiv.org/html/2505.10054v1), especially Sections IV.2–IV.3, supplies the finite-molecule cooling context. Its explicit machine-assisted protocols compare with protocols without a machine, and its cumulative coefficient of performance uses summed signed work. The present statement instead fixes three rounds, gives both classes the same memory, charges branchwise gross work, and requires exact unconditional product return. The cited results do not directly supply this particular inequality.

Taranto et al.'s [*Exponential improvement for quantum cooling through finite-memory effects*, arXiv:2004.00323v2](https://arxiv.org/html/2004.00323v2), Theorem 1, establishes attainable asymptotic cooling bounds and an advantage of memory over a memoryless setting. Its comparison and objective differ from the equal-memory, three-round work comparison here. Its use of the term coherent control should not be identified with this note's particular permutation comparator.

Coherence-assisted cooling itself is older. For example, Mitchison et al.'s [*Coherence-assisted single-shot cooling by quantum absorption refrigerators*, arXiv:1504.01593v3](https://arxiv.org/html/1504.01593v3), studies transient cooling of a three-qubit absorption refrigerator powered by baths at different temperatures. That result makes a broad claim that coherence can help cooling inappropriate as a novelty claim for this note. The present contribution is the explicit narrow comparison with a complete population converse. These checked distinctions do not establish publication priority or exhaustive novelty clearance.

## Reproduction and review status

Download the [version 1.0 supplement]({{ '/assets/code/agentic/three-round-quantum-cooling-work-v1.zip' | relative_url }}) and [release manifest]({{ '/assets/code/agentic/three-round-quantum-cooling-work-v1.json' | relative_url }}). The supplement contains this note, exact witness controls, the certificate programs, minimal numerical proposal data, file hashes, and a runner. It rebuilds the exhaustive certificate from an empty temporary directory; the precomputed 12-million-state output archive is not needed.

With Python 3 and NumPy installed, extract the supplement and run:

```text
OPENBLAS_NUM_THREADS=1 python3 reproduce.py
```

The runner checks input hashes, executes the complete prefix and suffix verification sequentially, and runs the separate dyadic witness checker. It exits unsuccessfully if a stage fails. The packaged version was checked this way before publication. Floating proposals only select legal bound parameters; the directed checks decide all exclusions. The programs are computational evidence and do not constitute a formal proof-assistant derivation.

The derivation, computation and drafting were carried out with AI assistance under human direction. Internal proof review, different arithmetic implementations, public posting, novelty and external acceptance are separate statuses. This release has no independent expert-review claim, archival-deposit claim or external catalog-status claim.

[Back to the research log]({{ '/agentic-research/' | relative_url }}).
