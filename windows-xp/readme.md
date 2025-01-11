# Windows XP

## Requirements

To install Windows XP in a Virtual Machine, a Volume License ISO is required:

* Windows XP SP3 Volume License ISO\*
* [VMware Tools Version 10.0.12 ISO](https://packages.vmware.com/tools/releases/)
* [GitHub: Windows XP All Keys Universal Product Key Collection All Keys](https://github.com/Fuwn/xp)
* [GitHub: XP keyGen](https://github.com/Endermanch/XPKeygen/releases)

\* The Windows XP SP3 Volume License ISO is not yet available to download on [WinWorld](https://winworldpc.com/library/operating-systems) which has Windows 1 through to Windows ME. It appears to be available on Archive dot org.

## XP Mode Notes (Not Recommended)

* [Windows XP Mode](https://download.cnet.com/windows-xp-mode/3000-18513_4-77683344.html)

Rename the file `WindowsXPMode_en-us.exe` to `WindowsXPMode_en-us.zip`. Extract the zip file and go to the sources folder. Rename `xpm` to `xpm.zip`. Rename `VirtualXPVHD` to `VirtualXP.VHD`. Use of `VirtualXP.VHD` as a Virtual Drive in VMware Workstation Player results in a VM where the mouse doesn't work. Installation of VMware tools gives a black screen.












XP Mode was a free Windows XP Virtual Machine available for Windows 7 Pro, Windows 7 Ultimate and Windows Enterprise Licenses. Unfortunately it required Windows Virtual PC which is far inferior to VMware Workstation Player. This guide will look at downloading the XP Mode Installer from Microsoft and creating a XP Mode Virtual Machine within VMware Workstation Player.






If this is grayed out. Manually download the ISO:












Note this by default will give a virtual machine that lasts for only 30 Days if carried out on Windows 8.1 Pro or Windows 10 Pro. If carried out on Windows 7 Pro, Windows 7 Ultimate or Windows Enterprise there is an official line of code that can be added to the Virtual machines Configuration File to allow Product Activation.

