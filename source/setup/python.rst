============================================================
``Python``
============================================================

For light use, miniconda is convenient, without using virtualenv.

Install MiniConda
==============

Google MiniConda to download installer pkg, such as https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh.

Frequent used commands:

- conda config --set auto_activate_base false
- conda update conda
- conda create --name {newEnvName} [python=3.x]
- conda activate {newEnvName}
- conda activate
- conda info --envs
- conda search {pkgName}
- conda list
- conda install {pkgName} [--channel conda-forge]
- conda install --file requirements.txt 