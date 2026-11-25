---
layout: page
permalink: /industrial-phd/
title: Industrial PhD with BlueQubit
description: An NUS PhD with BlueQubit, through EDB's Industrial Postgraduate Programme.
nav: false
---

I'm looking for a PhD student to work with me at [NUS](https://www.comp.nus.edu.sg/cs/people/zhangyx/)
and with [BlueQubit](https://www.bluequbit.io/), through EDB's
[Industrial Postgraduate Programme (IPP)](https://www.edb.gov.sg/en/business-insights/insights/how-singapore-partners-with-global-companies-to-groom-top-local-r-d-talent.html).
You'd do an NUS PhD and be employed at BlueQubit while you do it. The IPP is open to Singapore
Citizens and Permanent Residents.

## BlueQubit

[BlueQubit](https://www.bluequbit.io/) is a quantum algorithms lab in San Francisco. They work on
applications for today's noisy quantum computers and for the fault-tolerant ones coming next. What
they're after is real quantum advantage, meaning scientific and commercial problems that the best
classical supercomputers can't handle. They write their own algorithms and simulators and run them on
the leading quantum hardware, so you can go from an idea to a real device quickly. This autumn they
also started
[Quantum Flywheel](https://thequantuminsider.com/2026/11/17/bluequbit-names-eight-research-teams-quantum-flywheel/),
a grant programme supported by IBM, AWS and NVIDIA that gives research groups AI and computing credits.
More than 160 proposals came in from 29 countries.

I've been working with them since 2025. Two things we've done together:

- [Peaked circuits on Quantinuum's H2](https://arxiv.org/abs/2510.25838). A peaked circuit hides one
  bitstring that's hard to find and easy to check. H2 finds it in a circuit with 2000 two-qubit gates
  in under two hours, and the best classical methods we tried would take years. The paper won the
  [Best Paper award](https://qce.quantum.ieee.org/2026/wp-content/uploads/sites/13/2026/08/QCE26-Best-Papers-v19.pdf)
  in the Quantum Algorithms track at IEEE Quantum Week 2026.
- [Random circuit sampling on IBM's Nighthawk](https://arxiv.org/abs/2609.28657). On 61 qubits, the
  chip collects a million samples in 19 seconds. We estimate the same job would take the Frontier
  supercomputer more than a century.

## What we could work on

There's no fixed project. We'll choose one together with BlueQubit, based on what you like and what
you're good at. Some directions:

- New algorithms on current quantum computers, aimed at advantage that anyone can check. Peaked
  circuits are one example, and the [code](https://github.com/yuxuanzhang1995/Peaked-circuits) is public.
- Algorithms for early fault-tolerant machines, where logical qubits are few and error correction is
  expensive.
- Classical simulation with tensor networks and Pauli-path methods, pushed far enough to see where
  quantum computers really win.
- AI for quantum computing, from compiling circuits and mitigating errors to agents that work on open
  problems.

My own view is that quantum computations should be verifiable and useful, and that most of the work of
running a quantum computer should be learned rather than designed by hand. If that sounds interesting,
have a look at my [research]({{ '/research/' | relative_url }}) and
[agentic research]({{ '/agentic-research/' | relative_url }}) pages. If you have your own idea, bring it.

## How the IPP works

You'd be a full-time PhD student in the
[School of Computing](https://www.comp.nus.edu.sg/programmes/pg/phdcs/industrial/), supervised by me
and by someone at BlueQubit. The company employs you during the PhD, and at least half of the project
happens there. EDB and the company cover your tuition, salary and employer CPF, and there's no bond.
We write the project proposal together, and EDB and the School have to approve it.

If you're not a Singapore Citizen or PR, have a look at the
[other PhD routes]({{ '/join/' | relative_url }}).

## How to apply

Email me at [zhangyx@comp.nus.edu.sg](mailto:zhangyx@comp.nus.edu.sg) with your CV, transcripts and a
short note on what you'd like to work on. You should have a degree in computer science, physics,
mathematics or something close, meet the School's
[admission requirements](https://www.comp.nus.edu.sg/programmes/pg/phdcs/admissions/), program well in
Python or C++, and know some quantum information. Experience with quantum hardware, tensor networks or
machine learning helps.
