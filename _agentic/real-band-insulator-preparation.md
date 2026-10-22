---
layout: "page"
title: "Rapid dissipative preparation of weakly interacting real band insulators"
description: "A volume-independent weak-interaction threshold and logarithmic mixing for a fixed energy-lowering dissipator with a filled negative band."
date: "2026-10-22"
status: "proof candidate"
target: "Real gapped fermionic band insulators with weak even interactions"
pdf: "real-band-insulator-preparation.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 7 pages)]({{ '/assets/pdf/agentic/real-band-insulator-preparation.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/real-band-insulator-preparation-source.zip' | relative_url }})

Can the positive-hopping rapid-preparation argument survive a filled negative band, when the interaction becomes quasi-local after exchanging particles and holes?

## Result

For a real symmetric finite-range hopping matrix with a fixed gap around zero and both bands nonempty, sufficiently weak bounded finite-range even interactions preserve a unique pure ground-state fixed point of the specified filtered Lindblad dynamics. From every even initial state, the trace distance is at most $$4N e^{-t/4}$$ after choosing a volume-independent coupling threshold.

## What the argument adds

The particle–hole transform is followed through the interaction and the physical jump list. Exponential projector locality and a summable oscillator estimate control the resulting tails. This supplies the perturbative closure beyond the positive-definite one-particle reference.

[Zhan and coauthors, Theorem 11 and Appendix I](https://arxiv.org/html/2503.15827v3). [Fermionic locality estimates of Nachtergaele, Sims and Young](https://arxiv.org/abs/1705.08553v3).

## Scope and checks

The theorem retains real hopping, a fixed spectral gap and filter, the paired physical creation/annihilation couplings, and even initial states. It does not assert the complex-hopping extension.

The analytic locality, perturbation and stationary-state arguments received fresh independent agent review. Finite CAR controls were replayed twice in isolated processes; those controls check the algebra and do not prove the uniform theorem by themselves.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
