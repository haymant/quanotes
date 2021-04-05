============================================================
``Finance Formula``
============================================================

Math Search Engine
==================

Given an example, if we want to find derivative of Normal Distribution's Cumulative distribution function (CDF), we can search
"derivative of 1/sqrt(2 \pi)* e^{-(x^2)/2)" in `wolframalpha
<https://www.wolframalpha.com/>`_.

Compound Interest
=================

:math:`r` is normalised annual interest rate, :math:`n` is compound frequency, then $1 will become:

.. math::
  (1+\frac{r}{n})^n \\
  \lim_{x \to \infty} (1+\frac{r}{n})^n = e^r

Binominal Distribution
======================

:math:`p` is probability of individual event, :math:`n` is number of obervations and :math:`x` are number of events oberved. 

.. math::
  Density\ f(x) &= \binom{n}{x}p^x (1-p)^{n-x} \\
  \binom{n}{x} &= \frac{n!}{(n-x)!x!} \\
  CDF \mathcal{N}(f) &= Pr(x<k) = \sum_{x=0}^{k}f(x)

Normal Distribution
===================

.. math::
  Density\ f(x) &=\frac{1}{\sqrt{2\pi}}e^{-\frac{x^2}{2}}  \\
  Derivative\ fn'(x) &=-xf(x) \\
  CDF\ \mathcal{N}(f) &=\int^x_{-\infty}f(t)d_t


Vanilla Option
==============

Put-Call Parity: call - put = forward or call plus strike equals to put plus a share.

With Strik K, spot price x, maturity :math:`\tau`, risk free rate :math:`r_f` and dividend rate :math:`r_d` 

.. math::
    call(K) - put(K) &= xe^{-r_f\tau} - Ke^{-r_d\tau}

Option Structure
================

Call: __/ Put: \\__

Call (Bull) Spread: __/‾‾ Put (Bear) Spread: ‾‾\\__ Calendar Spread: vanilla(T) - vanilla(t) for t<T

Strangle: \\____/ Condor: ‾\\____/‾ Seagull: ,--’‾

Risk Reversal (vanna): ,---’ Staddle (vega): \\/  Butterfly (volga): ‾‾\\/‾‾

Digital call and put _|‾ and ‾|_

Volatility Estimation
=====================

.. math::
  time\ series\ prices\ S_0, S_1, ..., S_n \big\vert total\ days\ t\\
  returns\ r_i &= \ln(S_i/S_{i-1}) \\
  average\ return\ \tilde{r} &= \frac{1}{n}\sum_{i=1}^n r_i \\
  estimated\ standard\ deviation\ _k &= \sqrt{\frac{k}{n-1}\sum_{i=1}^n(r_i-\tilde{r})^2}\Bigg\vert k=\frac{n}{t}252


Annual Vol to Daily Vol	Divide by √252 ( Use 15.8745 or 16)

Annual Vol to Weekly Vol	Divide by √50 ( Use 7.071 or 7)

Annual Vol to Monthly Vol	Divide by √12 ( Use 3.464 or 3.5)
  