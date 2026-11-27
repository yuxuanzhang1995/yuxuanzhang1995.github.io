---
layout: page
title: A permutation-orbit criterion for the advantage of limited entanglement assistance
description: A single block input can witness a strict gain over endpoint time sharing at the channel's regularized threshold.
date: 2026-11-27
status: Complete proof candidate · regularized criterion · internal review
target: QIQCOP Zoo · Structural criterion for classical–entanglement trade-off advantage
pdf: permutation-orbit-entanglement-tradeoff-v1.pdf
author: Yuxuan Zhang
---

**Yuxuan Zhang<sup>1,2</sup>** · Version 1.0 · 27 November 2026

<sup>1</sup> École Polytechnique Fédérale de Lausanne  
<sup>2</sup> Princeton University

[Manuscript (PDF)]({{ '/assets/pdf/agentic/permutation-orbit-entanglement-tradeoff-v1.pdf' | relative_url }}) · [Paper source, review and checks (ZIP)]({{ '/assets/code/agentic/permutation-orbit-entanglement-tradeoff-v1.zip' | relative_url }}) · [Original problem](https://qiqc-op.com/problem/op_ad12295d8fdfb02a/)

Alice has a noisy quantum channel to Bob and a limited supply of shared entanglement. She can spend it on a fraction of the transmissions and use the rest without assistance. When can a single coding strategy transmit strictly more classical information than this time-sharing strategy?

Take one state on a block of channel inputs. Average its output over all reorderings of the channel uses, and compute the entropy of that average. The manuscript combines this entropy with the input and environment entropies. At a slope fixed by the channel's unassisted capacity, fully assisted capacity, and least cost of attaining full assistance, a strict inequality for one such state is necessary and sufficient for an advantage. The slope is itself defined by regularized channel invariants. Evaluating them can require arbitrarily long blocks.

## Why one input suffices

All permutations of a single input form a legitimate coding ensemble. A positive witness therefore has an operational interpretation at its actual finite block length. Conversely, a symmetric reference state bounds how much a general ensemble can improve the support function over the best orbit. At fixed output dimension that difference is at most logarithmic in the block length. Its contribution per use vanishes.

For a qubit with phase-flip probability one quarter, the supplement evaluates a fixed family of inputs. Its excess above the supporting line is −0.000141 bits per use at 64 uses and +0.002039 at 128 uses. The latter is a finite positive witness. Other inputs can behave differently. The dephasing channel's advantage was already known from its exact trade-off curve. [Brádler et al.](https://arxiv.org/abs/1001.1732)

## Evidence and prior work

Shor and Hsieh–Wilde supply the coding theorem. The manuscript uses it to obtain the single-input strict test and gives two proofs that permutation orbits recover the regularized support. Wang and Hayashi also used permutations for a distinct coding model with prescribed shared states and encoding restrictions. [Shor](https://www.rintonpress.com/xqic4/qic-4-67/537-545.pdf) · [Hsieh and Wilde](https://arxiv.org/abs/0901.3038) · [Wang and Hayashi](https://arxiv.org/abs/2001.01845)

Internal review covered the initial entanglement budget, singular output states, both directions of the finite-witness test, and the right derivative that gives the least saturation cost. The computational controls include a noiseless channel and the published dephasing example. Independent specialist review and priority remain open.
