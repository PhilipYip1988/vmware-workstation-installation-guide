# Windows XP

Setting up a Windows XP Guest using VMware Workstation Player.

The biggest difficulty to setting up a Windows XP VM is obtaining the installation as Microsoft nor its OEMs provided official download links.

## Windows Volume License License

The Windows XP Professional SP3 Volume License ISO and associated Product Key is not yet available to download on [WinWorld](https://winworldpc.com/library/operating-systems) which lists abandoned Windows Versions from Windows 1 through to Windows ME. The Windows XP Professional SP3 Volume License ISO is preferred for a Windows XP Professional VM as it activates offline.

Unofficially Volume License Keys are listed on this GitHub repository:

* [GitHub: Windows XP All Keys Universal Product Key Collection All Keys](https://github.com/Fuwn/xp)

## Windows OEM License



To install Windows XP in a Virtual Machine, a Volume License ISO is required:

* Windows XP SP3 Volume License ISO\*


## Windows XP Mode Notes (Not Recommended)

A common question is conversion of the Windows XP Mode VM into a VMware Workstation VM:

* [Windows XP Mode](https://download.cnet.com/windows-xp-mode/3000-18513_4-77683344.html)

A VM can be created from this by renaming the file `WindowsXPMode_en-us.exe` to `WindowsXPMode_en-us.zip`. Then extracting the zip file and going to the sources folder. Then renaming the `xpm` to `xpm.zip` and renaming the `VirtualXPVHD` to `VirtualXP.VHD`. The `VirtualXP.VHD` can be used as a Virtual Drive in VMware Workstation Player but results in a VM where the mouse doesn't work. Installation of VMware tools gives a black screen.

## VMware Tools ISO

* [VMware Tools Version 10.0.12 ISO](https://packages.vmware.com/tools/releases/)
















XP Mode was a free Windows XP Virtual Machine available for Windows 7 Pro, Windows 7 Ultimate and Windows Enterprise Licenses. Unfortunately it required Windows Virtual PC which is far inferior to VMware Workstation Player. This guide will look at downloading the XP Mode Installer from Microsoft and creating a XP Mode Virtual Machine within VMware Workstation Player.






If this is grayed out. Manually download the ISO:












Note this by default will give a virtual machine that lasts for only 30 Days if carried out on Windows 8.1 Pro or Windows 10 Pro. If carried out on Windows 7 Pro, Windows 7 Ultimate or Windows Enterprise there is an official line of code that can be added to the Virtual machines Configuration File to allow Product Activation.

