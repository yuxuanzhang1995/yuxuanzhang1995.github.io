---
layout: "page"
title: "Classical counterexamples to monotonicity of noninteger Rényi reflected entropy"
description: "Actual classical probability laws and ordinary partial traces violate monotonicity at every finite noninteger order above one."
date: "2026-10-22"
status: "counterexample"
target: "Universal monotonicity of finite noninteger Rényi reflected entropy"
pdf: "noninteger-reflected-entropy-counterexamples.pdf"
author: "Yuxuan Zhang"
---

**Yuxuan Zhang**

[Manuscript, version 1, 22 October 2026 (PDF, 6 pages)]({{ '/assets/pdf/agentic/noninteger-reflected-entropy-counterexamples.pdf' | relative_url }}) · [LaTeX source, proof, checkers and review records (ZIP)]({{ '/assets/code/agentic/noninteger-reflected-entropy-counterexamples-source.zip' | relative_url }})

Does the reflected-entropy monotonicity statement extend from integer replicas to finite noninteger orders above two?

## Result

For every finite noninteger $$\alpha>1$$, the paper constructs a classical tripartite density operator whose ordinary partial trace reverses the proposed inequality. A separate twelve-entry rational probability law gives a certified witness at $$\alpha=5/2$$.

## What the argument adds

Noninteger matrix powers losing entrywise positivity are an inherited mechanism. The additional bridge realizes that mechanism as one physical probability law and its ordinary partial trace. The new range relative to the checked Hayden–Lemm–Sorce result is finite noninteger orders above two.

[Hayden, Lemm and Sorce, the previous failure range](https://arxiv.org/html/2302.10208v2). [Guillot, Khare and Rajaratnam, matrix-power background](https://arxiv.org/abs/1303.4701v2). [Dutta and Faulkner, established integer-order monotonicity](https://arxiv.org/html/1905.00577).

## Scope and checks

The construction depends on the order and does not give one universal state or a uniform gap near integers. Integer orders at least two obey the known monotonicity theorem and lie outside this construction; the infinity-order result is also distinct.

The rational witness and a separate Arb eigensystem implementation were replayed twice. The all-order statement rests on the analytic construction, not on the finite list of numerical controls.

The proof and primary-source comparisons were reviewed independently within the AI-assisted research workflow. No specific unresolved proof gap or covering result was found in the checked sources through 22 October 2026. This is internal review, not external peer review, formal certification or an exhaustive priority guarantee.

This paper is part of the [22 October 2026 ten-paper release]({{ '/agentic-research/2026-10-22/' | relative_url }}). Its PDF and source package are posted here; the release does not add an archival DOI or claim a catalog's acceptance.

**Human and AI contributions.** The work was developed in an author-directed research workflow. AI systems assisted mathematical derivation, primary-source comparison, computational checks and scientific writing. The broader [research log]({{ '/agentic-research/' | relative_url }}) describes the author's direction and the research harness.
