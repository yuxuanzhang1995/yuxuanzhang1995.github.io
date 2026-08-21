---
layout: page
permalink: /research/
title: research
description: Quantum information, quantum many-body physics, and machine learning.
nav: true
nav_order: 1
---

<p>
My work sits at the interface of quantum information, quantum many-body physics, and artificial
intelligence, with one organising goal: identifying quantum computations that are both
<em>verifiable</em> and <em>practically useful</em>. It runs along three lines.
</p>

<style>
.rfig{margin:1.6rem 0 .6rem;border:1px solid var(--global-divider-color);border-radius:6px;overflow:hidden}
.rfig img{display:block;width:100%;height:auto}
.rfig.rfig-wide{margin-left:max(-9vw,-120px);margin-right:max(-9vw,-120px)}
.rfig-ph{display:flex;align-items:center;justify-content:center;min-height:230px;
  background:rgba(128,128,128,.06);color:var(--global-text-color-light);font-size:.9rem;text-align:center;padding:1rem}
.rcap{color:var(--global-text-color-light);font-size:.85rem;margin:.1rem 0 2rem}
.rpapers{list-style:none;padding:0;margin:.6rem 0 0}
.rpapers li{padding:.4rem 0;border-bottom:1px solid var(--global-divider-color)}
.rpapers li:last-child{border-bottom:0}
.rvenue{color:var(--global-text-color-light);font-size:.92rem}
.newdir{border-left:3px solid var(--global-theme-color);background:rgba(128,128,128,.05);
  padding:.6rem .9rem;border-radius:3px;margin:1.2rem 0}
</style>

## Quantum advantage and its classical boundary

<div class="rfig"><img src="{{ 'assets/img/research/advantage-boundary.webp' | relative_url }}" alt="A quantum circuit with a “magic” T gate above; below, the cost of the best classical simulation growing from manageable to intractable, with a marked crossover to quantum advantage." loading="lazy"></div>
<div class="rcap">Adding non-Clifford “magic” drives the cost of the best classical simulation from manageable to intractable; the crossover is where quantum advantage begins.</div>

Sampling experiments have demonstrated quantum advantage, but their outputs are hard to check. I
study circuit families — such as *peaked circuits* — whose outputs can be verified efficiently on a
classical computer, together with the complexity-theoretic evidence for their hardness. The flip
side is knowing exactly what classical algorithms cannot do: I develop tensor-network and
Pauli-path methods that push classical simulation as far as it will go, and prove structural
results that map the boundary between the classically tractable and the genuinely quantum.

<ul class="rpapers">
<li>Classical simulability of quantum circuits with shallow magic depth
    <span class="rvenue">— <a href="https://doi.org/10.1103/PRXQuantum.6.010337">PRX Quantum</a> <b>6</b>, 010337 (2025)</span></li>
<li>On verifiable quantum advantage with peaked circuit sampling
    <span class="rvenue">— <a href="https://arxiv.org/abs/2404.14493">arXiv:2404.14493</a>, with S. Aaronson</span></li>
<li>Complexity and hardness of random peaked circuits
    <span class="rvenue">— <a href="https://arxiv.org/abs/2510.00132">arXiv:2510.00132</a></span></li>
<li>Heuristic quantum advantage with peaked circuits
    <span class="rvenue">— <a href="https://arxiv.org/abs/2510.25838">arXiv:2510.25838</a></span></li>
<li>Straddling-gates problem in multipartite quantum systems
    <span class="rvenue">— <a href="https://doi.org/10.1103/PhysRevA.105.062430">Phys. Rev. A</a> <b>105</b>, 062430 (2022)</span></li>
</ul>

## Quantum simulation of many-body and open systems

<div class="rfig"><img src="{{ 'assets/img/research/simulation-states.webp' | relative_url }}" alt="One quantum circuit whose measurements reveal different outcomes — ground state, excited state, and dynamics — drawn as three cats." loading="lazy"></div>
<div class="rcap">One circuit, many accessible states: ground state, excited states, and real-time dynamics.</div>

Today's processors are good enough to probe physics that is otherwise hard to reach. Using
holographic (qubit-efficient) tensor-network circuits and trapped-ion hardware, I study
non-Hermitian dynamics, thermal states, and *mixed-state phases of matter* — phases that exist only
in the presence of noise, and whose order parameters turn out to be tied to quantum error
correction.

<ul class="rpapers">
<li>Probing mixed-state phases on a quantum computer via Rényi correlators and variational decoding
    <span class="rvenue">— <a href="https://doi.org/10.1038/s41467-026-73814-6">Nature Communications</a> (2026)</span></li>
<li>Observation of a non-Hermitian supersonic mode on a trapped-ion quantum computer
    <span class="rvenue">— <a href="https://doi.org/10.1038/s41467-025-57930-3">Nature Communications</a> <b>16</b>, 3286 (2025)</span></li>
<li>Holographic simulation of correlated electrons on a trapped-ion quantum processor
    <span class="rvenue">— <a href="https://doi.org/10.1103/PRXQuantum.3.030317">PRX Quantum</a> <b>3</b>, 030317 (2022)</span></li>
<li>Holographic quantum simulation of entanglement renormalization circuits
    <span class="rvenue">— <a href="https://doi.org/10.1103/PRXQuantum.4.030334">PRX Quantum</a> <b>4</b>, 030334 (2023)</span></li>
</ul>

## Machine learning for quantum computing

<div class="rfig rfig-wide"><img src="{{ 'assets/img/research/ml-for-quantum.webp' | relative_url }}" alt="Three roles for machine learning in quantum computing: compiling long dynamics into short circuits, discovering new phases from learned representations, and adapting to hardware feedback." loading="lazy"></div>
<div class="rcap">Three ways learning enters: compiling long dynamics into short circuits, discovering phases from learned representations, and adapting to hardware feedback.</div>

Learning enters quantum computing in three places. I use machine learning to *compile* long
many-body dynamics into much shorter, hardware-friendly circuits; to *discover* phases and phase
boundaries from learned representations of quantum states, including systems where conventional
methods struggle; and — more recently — to *adapt* to real devices, learning noise models and
control strategies from hardware feedback.

<ul class="rpapers">
<li>Scalable quantum dynamics compilation via quantum machine learning
    <span class="rvenue">— <a href="https://doi.org/10.1103/wswv-nq6d">Phys. Rev. Research</a> <b>8</b>, 023128 (2026)</span></li>
<li>Biorthogonal neural network approach to two-dimensional non-Hermitian systems
    <span class="rvenue">— <a href="https://doi.org/10.1103/3kk2-3fsj">Phys. Rev. Lett.</a> <b>136</b>, 126501 (2026)</span></li>
<li>Circuit compression for 2D quantum dynamics
    <span class="rvenue">— <a href="https://arxiv.org/abs/2507.01883">arXiv:2507.01883</a></span></li>
</ul>

<div class="newdir">
<strong>Newer directions.</strong> The <em>discover</em> and <em>adapt</em> strands above are just
getting started — autonomous exploration of phase diagrams, and learning noise and control directly
from device data. Both are wide open, with room for students to shape them.
</div>

<hr style="margin:2.4rem 0 1.2rem">

<p class="rvenue">
<em>Earlier work.</em> Benchmarking and architecture for photonic quantum processors — quantum
volume for photonic processors (<a href="https://doi.org/10.1103/PhysRevLett.130.110602">Phys. Rev. Lett. <b>130</b>, 110602</a>),
all-photonic one-way quantum repeaters (<a href="https://doi.org/10.1038/s41534-023-00775-9">npj Quantum Information <b>9</b>, 106</a>),
and quantum algorithms for network-flow optimisation (<a href="https://doi.org/10.22331/q-2021-07-27-510">Quantum <b>5</b>, 510</a>).
Full list on the <a href="/publications/">publications</a> page.
</p>
