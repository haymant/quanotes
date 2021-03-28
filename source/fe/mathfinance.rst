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

