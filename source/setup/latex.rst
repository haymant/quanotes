============================================================
``Latex For Math``
============================================================

In the notes, latex would be used to populate math formulas. 

Install Latex
==============

Here is basic install for Ubuntu

.. code-block:: bash

   sudo apt install texlive-latex-base texlive-latex-extra

Once latex is installed on your machine, add the following line to conf.py

.. code-block:: bash

    # extensions = [
      'sphinx.ext.imgmath',
    # ]
    # using svg seems generate fonts better than png
    imgmath_image_format = 'svg'


Write Your Formula
==================

Let's see a basic math formula example:

.. code-block:: bash

    .. math::
        F = G \left( \frac{m_1 m_2}{r^2} \right)
      
And the generated image is:

.. math::
  F = G \left( \frac{m_1 m_2}{r^2} \right)


Plot
====

Install Latex
--------------

.. code-block:: bash

   sudo apt install dvipng
   pip install matplotlib sphinxcontrib-needs sphinxcontrib-plantuml

.. code-block:: bash

   # extensions = [
    'sphinxcontrib.needs',
    'matplotlib.sphinxext.plot_directive', 
   # ]

.. plot::

   # Load matplotlib
   import matplotlib.pyplot as plt

   import numpy as np
   x = np.random.randn(1000)
   plt.hist( x, 20)
   plt.grid()
   plt.title(r'Normal: $\mu=%.2f, \sigma=%.2f$'%(x.mean(), x.std()))
   plt.show()