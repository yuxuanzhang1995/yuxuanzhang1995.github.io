---
layout: page
title: "Thermal mutual information of order beta to the one-quarter power in one dimension"
description: "A bounded-local one-dimensional Hamiltonian whose full Gibbs state has middle-cut mutual information at least c beta^(1/4), including all charge and spin sectors."
date: "2026-11-13"
permalink: /agentic-research/thermal-mutual-information-quarter-power/
status: "Complete proof candidate · sequential internal review"
target: "Thermal correlations · one-dimensional Gibbs states"
pdf: "thermal-mutual-information-quarter-power-v1.pdf"
---

Yuxuan Zhang · 13 November 2026 · Version 1.0

How quickly can correlations across a single cut grow as a one-dimensional
quantum system is cooled? This construction gives an explicit family whose
thermal mutual information grows at least as the one-quarter power of
inverse temperature:

$$
I(L:R)_{ho_{eta_N}}ge c,eta_N^{1/4},
qquad ho_{eta_N}=rac{e^{-eta_NH_N}}{operatorname{Tr}e^{-eta_NH_N}}.
$$

The Hamiltonian has fixed local dimension, nearest-neighbor interactions
and uniformly bounded local terms. The bound concerns the full Gibbs state,
including every particle-number and spin sector. This is a complete proof
candidate with sequential internal analytical review; independent expert
review and comprehensive priority assessment remain outstanding.

[Full paper (PDF)]({{ '/assets/pdf/agentic/thermal-mutual-information-quarter-power-v1.pdf' | relative_url }})
· [Source, checks and review (ZIP)]({{ '/assets/code/agentic/thermal-mutual-information-quarter-power-v1.zip' | relative_url }})
· [Version and SHA-256 metadata]({{ '/assets/code/agentic/thermal-mutual-information-quarter-power-v1.json' | relative_url }})

## The precise result

For every $$Nge2^{30}$$ divisible by four, the construction gives an open
chain of $$N$$ sites of dimension nine. At

$$
eta_N=2^{44}N^4,qquad
I(L:R)_{ho_{eta_N}}gerac{log 2}{8}N.
$$

Logarithms here are natural. Thus one can take
$$c=(log2)/(8cdot2^{11})$$. The small local potential depends on the chain
length; its coefficients remain uniformly bounded. The theorem is an
asymptotic existence result along this sequence, with conservative constants.
It does not claim practical temperatures, translation invariance or an
efficient preparation algorithm.

## Why a finite density of holes helps

Each of two rings carries holes and spin-one-half particles. Neighboring
particles can exchange places with holes, while a boundary interaction lets
a hole cross the endpoint only when both rings do so together. A contact
term favors a singlet between the first particles on the two rings.
Folding each ring produces the two halves of a one-dimensional chain.

Synchronized motion aligns the ordered spins into singlet pairs. The new
boundary rule requires a genuine particle-hole exchange on each ring, which
keeps that alignment intact when there are many holes. Endpoint transport
and an overlapping-singlet constraint separate all unwanted spin states
by an energy of order $$N^{-3}$$.

A weak local potential favors a central density band. Its effect is handled
with a pointwise scalar ground-state transform, so it does not overwhelm
the small spin separation. The proof then controls every charge sector.
At the stated temperature, the full thermal weight outside the useful
subspace is less than $$e^{-13N}$$. Local operations extract $$N/4$$ nearly
perfect singlet pairs, giving the mutual-information bound by data processing.

## Relation to earlier work

[Gottesman and Hastings](https://arxiv.org/html/0901.1108v2) introduced the
two-ring architecture, singlet contact and folding. Their ground-state
entanglement-gap relation has a one-quarter exponent. That exponent alone
does not give the same temperature dependence for a thermal state.

[Kuwahara, Alhambra and Anshu](https://arxiv.org/html/2007.11174v2), Section
III.2, obtain a thermal lower bound of order
$$(eta/logeta)^{1/5}$$. The proposed advance here is the finite-density
construction and its full-sector thermal estimate, which replace that
exponent by $$1/4$$. The path-exclusion spectral gap is inherited from
[Caputo, Liggett and Richthammer](https://arxiv.org/html/0906.1238v4).

The source package compares the exact statements and also checks the
recent Gibbs-mixture representation result of
[Bakshi, Choi and Pilatowsky-Cameo](https://arxiv.org/html/2602.13386v2).
The distinction from these inspected papers is supported by the comparison;
it is not a claim that every concurrent or equivalent result has been ruled out.

## Evidence and review

The original checker passes 22,113 exact comparisons between the physical
Hamiltonian and its charge-spin representation, together with 50 charge
means and four deliberately incorrect operator controls. New exact code
checks the ground-state transform with nonconstant rational weights and
detects an incorrect edge factor. Numerical endpoint and spin checks are
included as diagnostics.

The all-size proof rests on the written argument, especially the endpoint
transport estimate, unequal-count spin inequality and uniform comparison
across sectors. The review examined those steps rather than relying only on
the finite tests. The source package distinguishes the proof, exact controls,
numerical diagnostics and review limits.

The author directed the research and workflow. AI systems assisted with
derivation, source comparison, computation and drafting. This release records
an internally reviewed candidate; it is separate from external refereeing
or acceptance by a problem catalogue.
