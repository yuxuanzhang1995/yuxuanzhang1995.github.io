---
layout: page
title: Open Problem 1 of Alhejji–Knill is false
description: An exact diagonal counterexample, with a complete all-word proof and minimal dimension three.
date: 2026-06-17
last_revised: 2026-09-22
status: solved (negative)
target: Section VI, question 1 of Alhejji–Knill, arXiv:2307.06894
pdf: op1-schatten.pdf
author: Yuxuan Zhang
archive_doi: 10.5281/zenodo.22969546
archive_pdf: https://zenodo.org/records/22969546/files/op1-schatten.pdf
---

**Yuxuan Zhang** · Revised 22 September 2026

<p style="margin:0 0 1.6rem;font-size:.92rem"><a href="{{ '/assets/pdf/agentic/op1-schatten.pdf' | relative_url }}">Complete proof (PDF, 3 pages)</a> &middot; <a href="{{ '/assets/code/agentic/op1-schatten-source.zip' | relative_url }}">LaTeX source, exact checker and results (ZIP)</a></p>

**Archival source:** [Manuscript PDF on Zenodo](https://zenodo.org/records/22969546/files/op1-schatten.pdf), preserved in [*Agentic Proofs for QIQC: Collected Manuscripts*, version 1.0](https://doi.org/10.5281/zenodo.22969546) (26 September 2026).

**The proposed implication is false, already for commuting 3 × 3 matrices.** The proof below covers words of every length. Independent expert review and historical priority remain unverified; this page's status is the author's research-log label.

## The precise question

In [Section VI, question 1 of *Towards a resolution of the spin alignment problem*](https://arxiv.org/html/2307.06894v3#S6), Alhejji and Knill consider positive semidefinite matrices $$A_0,A_1,B_0,B_1$$ with $$\lambda(A_i)=\lambda(B_i)$$ for $$i=0,1$$. Write $$\Pi_s(A)$$ for the ordered product selected by a finite binary word $$s$$. If

$$
\operatorname{tr}\Pi_s(A)\geq\left|\operatorname{tr}\Pi_s(B)\right|
\qquad\text{for every word }s,
$$

must $$\lVert A_0+A_1\rVert_p\geq\lVert B_0+B_1\rVert_p$$ for every $$1\leq p<\infty$$? Here $$\lVert X\rVert_p=(\operatorname{tr}\lvert X\rvert^p)^{1/p}$$. This is the paper's proposed bridge from word traces to fractional Schatten norms.

## A small witness, and the whole proof

Take

$$
\begin{aligned}
A_0&=\operatorname{diag}(2,0,1),& A_1&=\operatorname{diag}(2,1,0),\\
B_0&=\operatorname{diag}(1,2,0),& B_1&=\operatorname{diag}(2,1,0).
\end{aligned}
$$

All four matrices have spectrum $$(2,1,0)$$. Pure words give equal traces, as does the empty word. A mixed word containing $$k\geq1$$ zeros and $$m\geq1$$ ones has traces

$$
\operatorname{tr}\Pi_s(A)=2^{k+m},\qquad
\operatorname{tr}\Pi_s(B)=2^k+2^m\leq2^{k+m},
$$

because $$2^{-k}+2^{-m}\leq1$$. All traces are nonnegative. This verifies the hypothesis for every word, without an assumption on its length.

The two sums have spectra $$(4,1,1)$$ and $$(3,3,0)$$. At $$p=3/2$$, their power traces are $$10$$ and $$6\sqrt3$$. The strict comparison follows from **$$100<108$$** after squaring two positive numbers.

In fact, the inequality fails for **every $$1<p<2$$**. Divide the difference of the power traces by $$3^p$$ and obtain

$$
g(p)=(4/3)^p+2(1/3)^p-2.
$$

The function is strictly convex and vanishes at $$p=1,2$$, so it is negative between those endpoints. It is positive for $$p>2$$. Thus the failure interval, within the question's domain, is exactly $$(1,2)$$.

## Why dimension three is minimal

This part also permits noncommuting matrices. In dimension two, the sums have the same trace $$T$$. The word $$01$$ and matched individual spectra imply

$$
\operatorname{tr}(A_0+A_1)^2\geq\operatorname{tr}(B_0+B_1)^2.
$$

Write their eigenvalues as $$T/2\pm a$$ and $$T/2\pm b$$, with $$a,b\geq0$$. The squared-trace inequality says $$a\geq b$$. For every $$p\geq1$$, the sum $$(T/2+x)^p+(T/2-x)^p$$ is nondecreasing for $$0\leq x\leq T/2$$. The required norm dominance therefore holds in dimension two. Dimension one is immediate. The displayed three-dimensional example is minimal.

## The earlier integer witness also checks exactly

The original page displayed

$$
\begin{aligned}
A_0&=\operatorname{diag}(176,0,64),&A_1&=\operatorname{diag}(80,49,0),\\
B_0&=\operatorname{diag}(64,176,0),&B_1&=A_1.
\end{aligned}
$$

For any mixed word, the trace ratio is

$$
\frac{\operatorname{tr}\Pi_s(B)}{\operatorname{tr}\Pi_s(A)}
=\left(\frac{64}{176}\right)^k+\left(\frac{49}{80}\right)^m
\leq\frac{859}{880}<1.
$$

Pure words again give equality. At $$p=3/2$$, the power traces are exactly **4951 and 5103**, a strict gap of **152**. No floating-point tolerance enters this comparison.

## Verification and scope

The accompanying checker uses only integers and exact rational arithmetic. It verifies the individual spectra, the uniform ratio bounds, and both decisive strict inequalities. As additional diagnostics, it checks all 8,191 binary words of length at most 12, including the empty word, for each witness. The analytic argument above supplies the conclusion for every length.

Both witnesses appeared in the earlier PDF dated 17 June 2026. This revision makes the all-word, interval, and minimal-dimension arguments explicit. It supersedes the earlier statement that a kernel lemma was still needed for the displayed diagonal construction. The result does not depend on the earlier, incompletely documented noncommuting example or on a general diagonal-family claim.

This answers the bridge question. It does **not** refute the spin-alignment conjecture or establish a quantum-capacity formula. The construction, revision, and checks involved substantial AI assistance; the present revision does not claim independent human mathematical review. [Scientific Agent Skills](https://arxiv.org/abs/2609.00065) guided evidence tracking and exposition and is cited in the PDF.

## Source

M. A. Alhejji and E. Knill, *Towards a resolution of the spin alignment problem*, **Communications in Mathematical Physics 405**, 119 (2024). [Journal](https://doi.org/10.1007/s00220-024-04980-1) · [arXiv](https://arxiv.org/abs/2307.06894). Exact source statement: Section VI, question 1 of arXiv version 3.
