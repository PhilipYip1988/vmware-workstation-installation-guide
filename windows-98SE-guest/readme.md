# Windows 98SE

## Windows 98SE ISO

Windows 98SE is considered abandonware and the Windows 98SE ISO and Product Key can be obtained from WinWorld:

* [WinWorld](https://winworldpc.com/product/windows-98/98-second-edition)

Use the OEM Full ISO (the Retail Full ISO doesn't boot in VMware Player) and the provided product key. For this version of Windows there was only a Product Key and there was no concept of Product Activation.

## Windows 98SE Service Pack

* [Windows 98SE Unofficial Service Pack](https://www.softpedia.com/get/System/OS-Enhancements/Unofficial-Windows-SE-Service-Pack.shtml)

## VMware Tools ISO

* [VMware Tools Pre2k](https://packages-prod.broadcom.com/tools/frozen/windows/winPre2k.iso)

## Drivers

* [Intel USB 2.0 Drivers for Windows 98 ISO](https://archive.org/details/usb-20-driver-win-98)
* [Intel Chipset Software Installation Utility (5.0.1.1015)](https://archive.org/details/Intel_Chipset_Software_Installation_Utility_5.0.1.1015)
* [Creative SBPCI_WebDrvsV5_12_01.exe](https://support.creative.com/downloads/download.aspx?nDownloadId=1843)
* [Direct X 9.0c](https://archive.org/details/directx9-dec2006-redist)
* [Logitech Mouse](https://download.cnet.com/mw980enu-exe/3000-2108_4-157438.html)

With VMWare tools you can drag and drop files from the host to the VM or vice versa from folder to folder or folder to desktop. Dragging all these updates across:

## Content from Old Guide

Setup of Windows 98SE on a VM
The most difficult thing about setting a Windows 98SE VM up is obtaining the installation media and Retail Product Key in the first place. For one installing this OS for legacy hardware/software this guide assumes you have a Retail or Volume License of Windows 98SE and have Converted the installation CD into a .iso and installed VMWare Player.
Select player File → File → New Virtual machine:

Then load the .iso:

Select your Windows 98SE .iso and select open:

VMWare should detect that its Windows 98SE and set up the conditions appropriately. Select next:

Name your VM and select its storage location on your host HDD/SSD select next:

You may change the size of the virtual HDD if you want when ready select next. I advise leaving the default option to split the disk into multiple files:

Select customise hardware:

Select the network adapter and I advise ensuring that connect at power on is disabled. Windows 98SE has reached end of life and is very insecure. It should not be connected to the internet:

Then select ok. Then Finish:

The Windows 98SE VM will launch:

You may get some notifications select Ok to change to the recommended settings:

You will get a warning about removable devices, select Do not show me this hint again and select ok:

Select Download and Install:

VMWare Tools for 95, 98, ME and NT will download and install:

Select yes at the UAC:

Unfortunately during the time it took to install these tools you lost the 10 seconds to select the boot device and the VM automatically booted to the HDD which has no OS. You will therefore have a black screen.

Select player → "Send Ctrl, Alt and Delete":

The VM will restart and you'll see the VMWare BIOS screen:

Left click in the VM and select option 2. Boot from the CD-Rom:

Select option 1. Start Windows 98 Setup from CD-Rom:

The setup will load:

Press Enter at this screen:

Highlight configure unallocated disk space and press Enter:

Select Yes Enable Large Disk Support and press Enter:

Ignore the message about the floppy boot drive and press Enter:

You will see the VMWare BIOS screen:

Again select option 1. Boot from CD-Rom (the virtual HDD is still blank):

Again select option 1 Start Windows setup from CD-Rom:

Again the setup will load:

The setup will now format the Virtual HDD:

After the format you will need to press Enter to continue the setup:

The Windows setup will then begin to copy the files across:

The setup will then initialise:

Select continue:

The setup will prepare:

Select C:\Windows as the directory and select Next:

Select Next:

Select typical and select Next:

Opt to install the most common components and then select next:

Input the computers name, workgroup and the computer's description and then select next:

Select your language and then select next:

Select next again:

The setup will then copy over the Windows 98 files to the virtual HDD:

Select restart now when prompted:

You will see the VMWare virtual BIOS again:

You will see the Windows 98 SE logo:

Input your name and select next:

Now accept the license agreement and select next:

Input your retail product key and select next:

Select Finish:

Windows 98SE will now detect and install drivers for some of the hardware:

You will be prompted to restart again, select restart now:

You will see the Windows 98SE is shutting down screen, the VMWare virtual BIOS and the Windows 98SE is starting screen:

More hardware will be setup:

Windows setup will continue:

You will be prompted for your date and time settings:

I will select the English UK time zone:

Then apply it:

Then select ok:

The control panel and other items will now install:

Again you will be prompted to restart so select restart now:

You will see the Windows 98SE is shutting down screen, the VMWare virtual BIOS and the Windows 98SE is starting screen:

You will be prompted to login, input your password if set and then press ok:

Windows will install drivers for more devices:

The welcome to Windows 98SE screen will take an age to load. Ensure you uncheck Show this screen each time Windows 98 starts and then select close:

Installation of the Unofficial Service Pack
The unofficial service pack can be downloaded from Softpedia:
http://www.softpedia.com/get/System/OS-Enhancements/Unofficial-Windows-SE-Service-Pack.shtml
It is unfortunately only available as a .exe and not a .iso files so can't be loaded to the VM until its part of a .iso:

I use ImgBurn to make it a .iso. Be careful with installation of ImgBurn as it preinstalls some junk if you don't opt to install only ImgBurn see my instructions here. Once ImgBurn is installed launch it:

Select create image file from files/folders:

Select to browse for a file:

Select the unofficial service pack then select open:

Select the folders to image button:

Select a location for the .iso and select save:

Change the volume label and then select yes:

You will be told the .iso is made:

Select ok and then close ImgBurn:

Now select the player menu → Removable Devices → CD-DVD Drive → Settings:

Select Browse and load the .iso you just created with the Unofficial Service Pack Update:

Select the .iso and select open:

Select ok:

This annoying error message comes up just select yes (whenever you see it after changing CD-DVD .iso):

Go to computer:

Open the .iso:

Launch the unofficial Service Pack:

Select yes:

I advise selecting most the options however I unchecked the new boot and shut down logos. When ready select ok:

Select ok and then yes:

You will see the Windows 98SEshutting down screen, VMWare virtual BIOS and then the Windows 98SE Starting screen:

You will be prompted to login. If you have set a password input it and then select ok:

It will continue to install:

You'll reach the Windows 98SE Desktop:

Installation of VMWare Tools
In order to get a decent resolution (video) and be able to drag and drop files over to the VM you will need to install VMWare tools. Select player → manage → install VMWare Tools:

This will load the VMWare Tools .iso in the optical drive. Select yes at the annoying error message.

The VMWare tools installation should autorun if not go to computer and launch it from the optical drive.

Select next:

Select typical and then next:

Select install:

Select okay, yes and ok for the annoying error messages (again to do with the virtual optical drive):

Select Finish:

Select yes to restart:

You will see the Windows is shutting down screen, the VMWare BIOS and the Windows is starting screen:  
Input your password if you've set one and select ok:

To get a decent resolution, right click the desktop and select properties:

Select settings:

Maximise the resolution and then select apply and then ok, then yes:

 
The resolution will be too much. Left click the top of the VMWare Window in the host. Hold down the left click and drag the Window around.

It will then get smaller. Then just snap it to the top again:

The resolution of the VM should now resize automatically to fit the VM Window within the host machine.

Installation of Missing Drivers
Although VMWare tools installs the display driver and allows bidirectional drag and drop it is missing some of the drivers in particular the audio. Looking at the device manager gives 3 unknown devices. Go to start → settings → Control Panel:

Select System:

The main missing device is the audio:

As far as I can tell there are not any system drivers for the 2 additional devices and they are not necessary for the function of the VM. If someone has installed drivers let me know so I can update the guide.
Download the following on your host PC.
Intel Chipset
http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8178&ProdId=816&lang=eng
Intel USB 2.0:
http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=5829&ProdId=950&lang=eng
NUSB:
http://www.mdgx.com/spx/NUSB.EXE
Creative Sound Driver:
http://ccftp.creative.com/manualdn/Drivers/Others/1843/SBPCI_WebDrvsV5_12_01.exe
Direct X 9.0c:
http://www.oldapps.com/directx.php?system=Windows_98
Logitech Mouse
http://affiliates.digitalriver.com/z/140280/CD133407/ihgvhd38gd010nwu00jmo&lnkurl=http://www.logitech.com/pub/techsupport/mouse/mw980enu.exe
With VMWare tools you can drag and drop files from the host to the VM or vice versa from folder to folder or folder to desktop. Dragging all these updates across:
 
As some of these drivers will refer to the Windows 98SE installation CD so its best to load the Windows 98 SE .iso. Go to player → Removable Devices → CD/DVD and then settings:

Browse for the Windows 98SE .iso:

Load the .iso:

Select yes at the annoying warnings:

Close the Windows 98SE setup if automatically runs:

Installing the drivers is fairly straightforward but some additional notes.
Intel Chipset - The find new hardware wizard will show select Next, Check Search for the best driver for your device then select Next. Check Specify a Location and the default as C:\Windows\CATROOT and then select next. Repeat several times.
Creative Sound Driver - Wait for al the New Hardware Found Windows to show and disappear before restarting.
Direct X 9.0c - Make a folder on the Desktop and extract the files to it. In the folder launch the DirectX Setup.
Logitech Mouse - Install this and then configure your mouse cursor to suit a speed you are comfortable with.
Addition of Legacy Devices
You can add more hardware such as a floppy drive (virtual floppy drive with .flp images or an onboard/USB floppy drive), serial port (onboard or USB serial port) and parallel port (onboard or USB serial port). Power off the VM and right click your VM and select settings:

Select Add Hardware:

Select yes at the User Account Control:

You may add a floppy drive, parallel port and/or serial port depending on the legacy hardware you wish to connect to:

I advise not setting the Floppy to Connect at Power on otherwise the system will try to boot from the Floppy Disk before the HDD> This can be amended in the BIOS setup however:

 

These and USB devices can be accessed via the Player Menu. Each optical drive, floppy drive, network adapter, serial port, parallel port and soundcard will be listed separately. Below these any USB device are listed. If the USB devices have a tick they are connected to the VM (and removed from the Host OS). The Ability to connect to all of these Removable Devices and the installation of legacy Windows OS make the VM very powerful: