============================================================
``Ubuntu 21.10+ on Lenovo T5 26amr5``
============================================================

File System
===========

It's convenient to put home directory to harddisk other than the one used
by root directory, especially when I reinstall the system.

.. code-block:: bash

  sudo vim /etc/fstab
  # add:
  # /dev/sda2 /home/lee	ext4 defaults 0 0

Network
=======

Ethernet
--------

As the Wifi card Realtek 8852 is not supported out of box in Ubuntu 21.10, 
we would either temporarily tether Bluetooth/Ethernet to a Windows machine,
assuming the Windows machine enabled mobile hotpot via Bluetooth or shared
its wifi via Ethernet. Bluetooth is quite slow to install packages though.

When I once tried to enable a new propriety driver for nvidia 3060ti, the 
kernel is updated and caused Bluetooth and Ethernet problem. To avoid the
troubles, I don't update Nvidia drivers and lock kernel version if no great
reason. 

.. code-block:: bash

  $uname -r
  5.13.0-23-generic
  $sudo apt-mark hold 5.13.0-23-generic


Wifi
----

.. code-block:: bash

  $ls-pci
  05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8852

T5 comes with Realtek M.2 Wifi card, which is not supported by default. 
We need to install driver for it.

.. code-block:: bash

  $ sudo apt-get install make gcc linux-headers-$(uname -r) build-essential git
  $ git clone git://github.com/lwfinger/rtw89.git
  $ cd rtw89/
  $ make
  $ sudo make instal
  $ sudo modprobe -v rtw89pci
  $ dmesg |grep rtw #if any problem

Above steps require Secure-Boot disabled. Alternatively, do the following:

.. code-block:: bash

  sudo make sign-install

Please remember the password input, and reboot. MOK management screen will pop up then.
At MOK screen, select "Enroll key" and enroll the key created by above sign-install.
Input the password remembered when sign-install. 
If you enter wrong password, your computer won't not bebootable. In this case, use the BOOT menu from your BIOS, to boot into your OS then do below steps:

.. code-block:: bash
  
  sudo mokutil --reset


Audio
=====

I use Wbcam microphone to capture sound. It doesn't work no matter how to 
change sound level of it, until it's adjusted via command line:

.. code-block:: bash

  alsamixer


Deep Learning Setup
===================


Cuda Install
------------


.. code-block:: bash

  wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
  sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
  sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/7fa2af80.pub
  sudo add-apt-repository "deb https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/ /"
  sudo apt-get update
  sudo apt-get -y install cuda
  nvcc -V

Conda is preferred to manage python environment. 

.. code-block:: bash

  #Download Miniconda and install, e.g., 
  $ bash Miniconda3-py39_4.10.3-Linux-x86_64.sh

  #Install pytorch using Conda
  $ conda install pytorch cudatoolkit=11.3 -c pytorch
  $ python

  >>> import torch
  >>> torch.cuda.is_available()
