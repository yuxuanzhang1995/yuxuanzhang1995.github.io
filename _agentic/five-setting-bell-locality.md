---
layout: page
title: Five settings suffice opposite three binary measurements
description: A finite-setting locality criterion and a classification of Bell facets with three binary measurements on one side and arbitrarily many on the other.
date: 2026-11-19
status: Complete proof candidate · independent AI review
target: Jesus–Zambrini Cruzeiro conjecture for every (N,3,2,2), N ≥ 5
pdf: five-setting-bell-locality-v1.1.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang · Version 1.1, 19 November 2026**

[Manuscript (PDF)]({{ '/assets/pdf/agentic/five-setting-bell-locality-v1.1.pdf' | relative_url }}) · [Source, exact checks and review (ZIP)]({{ '/assets/code/agentic/five-setting-bell-locality-v1.1.zip' | relative_url }}) · [Release metadata]({{ '/assets/code/agentic/five-setting-bell-locality-v1.1.json' | relative_url }})

Suppose Alice can choose between three binary measurements, while Bob has any finite number of measurements. How many of Bob's settings must be examined together to decide whether their statistics admit a local hidden-variable model?

This manuscript proves that **five settings suffice**. Every restriction to at most five Bob settings is local if and only if the full behavior is local. Bob's measurements may have different finite outcome sets. The theorem concerns the full conditional probabilities, including the one-party marginals.

For binary outcomes on both sides, this reduction and an existing finite enumeration give a complete facet classification for every $$(N,3,2,2)$$ scenario with $$N\geq5$$. The classes are positivity and setting liftings and relabelings of

$$
\mathrm{CHSH},\qquad I_{3322},\qquad I_{4322}^{1},\ I_{4322}^{2},\ I_{4322}^{3},\qquad I_{5322}.
$$

This is the arbitrary-$$N$$ conjecture stated in Section IV.B of [Jesus and Zambrini Cruzeiro, *Tight Bell inequalities from polytope slices*](https://arxiv.org/abs/2212.03212v3). The finite facet list is their result; the manuscript supplies the reduction from unbounded $$N$$ to five settings. It does not classify Bell scenarios with unrestricted measurement counts on both sides.

## Why five appears

Alice's three binary measurements have eight deterministic assignments. A probability distribution over those assignments has four free affine coordinates after fixing normalization and Alice's three observed marginals. Each Bob setting imposes a convex set of compatible distributions in that four-dimensional affine space.

The common-distribution characterization of locality is already known, in particular from Lemma 5 of [Pironio, *All CHSH polytopes*](https://arxiv.org/abs/1402.6914v2). Finite Helly's theorem says that a finite family of convex sets in four dimensions has a common point whenever every five members do. Combining these facts gives the setting bound. The manuscript proves the additional polyhedral step needed to turn the locality criterion into a statement about every facet.

More generally, if Alice's measurement $$x$$ has $$a_x$$ outcomes, the same argument gives

$$
t=\prod_x a_x-\sum_x(a_x-1)
$$

as a sufficient number of Bob settings. Zero-probability hidden assignments and degenerate observed marginals are included. The bound need not be optimal for every outcome pattern.

[Budroni and Cabello](https://arxiv.org/abs/1112.5876v2) previously gave a sixteen-setting bound in the three-binary case through variable elimination. The contribution here is a short convex-geometric strengthening of that reduction and its classification consequence. The compatibility interface, Helly's theorem, the finite facet list and setting lifting are established ingredients.

## Five cannot be replaced by four

The supplementary package gives an exact rational no-signalling behavior that violates a genuine five-setting facet, while each of its five four-setting restrictions has an explicit local decomposition. The facet is a relabeling of the known $$I_{5322}$$ inequality; its source coefficients appear in Table A.4 of [José Diogo da Costa Jesus's 2022 thesis](https://fenix.tecnico.ulisboa.pt/downloadFile/1970719973970056/Thesis_JJ.pdf).

The example has violation $$-11/5000$$ in the manuscript's lower-bound convention and minimum conditional probability $$99/2000$$. Each deletion model uses twenty nonnegative rational weights. No quantum realization of this particular no-signalling example is asserted.

## Proof review and reproducibility

A separate AI reviewer received the frozen manuscript in fresh context, reconstructed the decisive proof steps and compared primary sources. The review found no unresolved load-bearing proof gap. It identified missing attribution to Pironio's 2014 compatibility lemma; version 1.1 incorporates that correction and more precise finite-source references. This is internal verification by a separate AI reviewer, not external specialist peer review. First-discovery priority remains unconfirmed.

Run `python3 reproduce.py` from the extracted package. The checks use exact arithmetic and Python's standard library, without network access or an optimization solver. They include:

- All 256 deterministic vertices, the 40 vertices saturating the witness, and its facet rank.
- All five local deletion models, independently reconstructed in the full conditional probabilities.
- Gluing examples with null hidden weights and unequal finite outcome sets.
- The six source-facet relabeling orbits and the witness's exact identification with $$I_{5322}$$.
- Deliberately damaged controls that must fail.

The source-orbit checks recover 71,280 nontrivial inequalities, or 71,340 including positivity. They verify those orbits, **not completeness of an independent enumeration**. Completeness of the finite base case remains a cited input. The arbitrary-setting theorem follows from the analytic proof, not from testing finitely many setting counts.

The package includes the manuscript source, rational certificate, author and reviewer checks, the proof review, and the primary-source comparison.
