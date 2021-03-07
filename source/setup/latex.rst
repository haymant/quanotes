============================================================
``Latex For Math``
============================================================

In the notes, latex would be used to populate math formulas. 

Install Latex
==============

Here is basic install for Ubuntu

.. code-block:: bash

   sudo apt install texlive-latex-base texlive-latex-extra dvipng

Once latex is installed on your machine, add the following line to 

.. code-block:: bash

    'sphinx.ext.imgmath', 

Write Your Formula
==================

Let's see a basic math formula example:

.. code-block:: bash

    .. math::
        F = G \left( \frac{m_1 m_2}{r^2} \right)
      
And the generated image is:

.. math::
  F = G \left( \frac{m_1 m_2}{r^2} \right)