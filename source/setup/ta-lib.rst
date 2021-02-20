============================================================
``TA-Lib``
============================================================

Technical Analysis Lib `TA-Lib
<https://ta-lib.org/>`_ is used by quite a few quant products. 
To install python wrapper ta-lib on Ubuntu, we may need to install dependencies first.

Install TA-Lib
==============

.. code-block:: bash

   wget http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz
   tar -xzf ta-lib-0.4.0-src.tar.gz
   cd ta-lib/
   ./configure && make
   sudo make install

You may need to add /usr/local/lib to ldconfig, or add a row to ~/.bashrc

.. code-block:: bash

  export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

Install Python Wrapper
======================

.. code-block:: bash

  pip install ta-lib
