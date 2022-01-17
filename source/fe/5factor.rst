============================================================
``Five-factor APM``
============================================================

Stock returns are related to

- Book Value of a firm's historical cost or accounting value calculated from its balance sheet
- Market Value for public traded company is its market capitalization
- Profitability
- Investment

Explain market value :math:`m_t` using expected discounted dividend :math:`E(d)`, with expected average
stock return (IRR of expected dividends).

.. math::
    m_t = \sum_{\tau=1}^{\infty} \frac{E(d_{t+\tau})}{(1+r)^\tau}

This formula gives intuitive relationship that expected return of a stock should be higher (higher risk)
when its market value is lower, if dividends are same.