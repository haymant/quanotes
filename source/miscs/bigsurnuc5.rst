============================================================
``Big Sur on Intel NUC5``
============================================================

Install Big Sur in VMWare
=========================

Follow this `guide
<https://www.wikigain.com/install-macos-big-sur-on-vmware-windows-pc/>`_ to install BigSur with VMWare on Windows.

Please be noted, the following codes should be appended to the .vmx file. Sometimes, double quote symbols will change when you copy-paste,
which will cause some errors. Please double check.

.. code-block:: bash

  smc.version = "0"
  cpuid.0.eax = "0000:0000:0000:0000:0000:0000:0000:1011"
  cpuid.0.ebx = "0111:0101:0110:1110:0110:0101:0100:0111"
  cpuid.0.ecx = "0110:1100:0110:0101:0111:0100:0110:1110"
  cpuid.0.edx = "0100:1001:0110:0101:0110:1110:0110:1001"
  cpuid.1.eax = "0000:0000:0000:0001:0000:0110:0111:0001"
  cpuid.1.ebx = "0000:0010:0000:0001:0000:1000:0000:0000"
  cpuid.1.ecx = "1000:0010:1001:1000:0010:0010:0000:0011"
  cpuid.1.edx = "0000:0111:1000:1011:1111:1011:1111:1111"
  smbios.reflectHost = "TRUE"
  hw.model = "MacBookPro14,3"
  board-id = "Mac-551B86E5744E2388"

Make Big Sur USB Installer
==========================

There are guides for 11.0.1. I directly downloaded 11.2.3 from App Store and seems it works.

Prepare USB
===========

Before burn USB installer, please format it with EFI partition, which is important.

- Insert Flash Drive
- Open Disk Utility
- Select the Flash Drive on the left column
- Click Erase
- Set the following settings:
- Name: BigSurInstaller
- Format: Mac OS Extended (Journaled)
- Scheme: GUID Partition Map
- Click Erase
- Click Done upon finish

Install Big Sur
===============

This section are mostly copied from `Hervé guide
<https://osxlatitude.com/forums/topic/8883-dell-latitude-e6230-with-i5-3340mi7-3540m-hd4000-and-1366x768-lcd-el-capitansierrahigh-sierramojavecatalinabig-sur/page/2/#comments>`_
, which is for Dell E6230. But the steps to burn USB and install basically are the same, especiall when there is EFI pack for your model already.

Install from USB
-----------------

- boot the Big Sur USB installer
- at the OpenCore main menu, select the "Install macOS Big Sur" partition and press [ENTER]
- at Big Sur main installation screen, select Disk Utility to create & format APFS the target Big Sur partition/disk. Note that installation won't work if target partition/disk is formatted HFS+
- exit DU and return to Big Sur main installation screen, then proceed with installation
- the installation process will twice reboot a temporary macOS installer partition to complete the installation. This overall installation process takes much longer (~1hr) than what was experienced with previous macOS versions so be patient. Don't be frightened by the 2nd reboot which show things never seen with previous macOS versions
- a 3rd reboot will boot your target named Big Sur partition/disk and will be quickly followed by a 4th and final reboot of that same target Big Sur partition/disk 
- each time, reboot via your USB installer. Please note that your USB installer will probably register as an OpenCore entry in the E6230 UEFI list displayed after pressing [F12]
 

Post-installation tuning
------------------------

- Once the finalised Big Sur installation has booted, complete the 1st boot configuration tuning
- Once at the desktop, mount the EFI partition of your Big Sur disk
- Copy the EFI folder of the `haymant's Big Sur OpenCore pack <https://www.tonymacx86.com/threads/guide-intel-broadwell-nuc5-using-clover-uefi-nuc5i5mhye-nuc5i3myhe-etc.261712/page-15>`_ to the mounted EFI partition
- You may then reboot and verify that Big Sur boots off your disk through OpenCore
- You may then disable verbose mode by removing -v flag from NVRAM->7C436110-AB2A-4BBB-A880-FE41995C9F82->boot-args in the OpenCore config file.
- You may then modify your SMBIOS info under PlatformInfo->Generic section and ensure you have unique numbers or unique combination of numbers. Use `GenSMBIOS <https://github.com/corpnewt/GenSMBIOS>`_ tool to generate new MLB, ROM, SystemSerialNumber and SystemUUID. Refer to Dortania's documentation for further info and guidance

