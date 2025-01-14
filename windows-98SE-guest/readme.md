# Windows 98SE

## Windows 98SE ISO

Windows 98SE is considered abandonware and the Windows 98SE ISO and Product Key can be obtained from WinWorld:

* [WinWorld](https://winworldpc.com/product/windows-98/98-second-edition)

Use the OEM Full ISO as the Retail Full ISO doesn't boot in VMware Player without use of a floppy disk and use the provided Product Key. For this version of Windows there was only a Product Key and there was no concept of Product Activation.

## VMware Tools ISO

Windows 98SE requires the Pre2k version of VMware Tools which installs some of the System Drivers such as the virtual display driver and also allows dragging and dropping files to the Windows 98 Guest:

* [VMware Tools Pre2k](https://packages-prod.broadcom.com/tools/frozen/windows/winPre2k.iso)

## Patcher9x

The Windows 98SE installation errors out on a VM on a modern computer:

> This program has performed an illegal operation and will be shut down.

> If the problem persists, contact the program vendor

<img src='./images/img_001.png' alt='img_001' width='600'/>

Essentially the processor is too fast and windows 98SE expects to wait more than "zero seconds" for an operation.

Download the `patcher9x.ima` from the assets of the latest release:

* [patcher9x](https://github.com/JHRobotics/patcher9x/releases/)

Right click the downloaded file and select rename: 

<img src='./images/img_002.png' alt='img_002' width='600'/>

Change the file extension from `.ima` to `.img`:

<img src='./images/img_003.png' alt='img_003' width='600'/>

Select Yes:

<img src='./images/img_004.png' alt='img_004' width='600'/>

The virtual floppy disk is now compatible with VMware:

<img src='./images/img_005.png' alt='img_005' width='600'/>

## Intel Chipset Installation Utility

VMware tools is missing the Intel Chipset driver:

* [6.3.0.1007](https://www.philscomputerlab.com/intel-chipset-drivers.html)

## NUSB Storage Driver

VMware tools is missing the NUSB Storage driver

* [NUSB36e](https://www.philscomputerlab.com/windows-98-usb-storage-driver.html)

## Creative SoundBlaster

VMware tools is missing the Creative SoundBlaster driver:

* [Creative SBPCI_WebDrvsV5_12_01.exe](https://support.creative.com/downloads/download.aspx?nDownloadId=1843)

* [Creative eapci8m.ecw](https://support.creative.com/downloads/download.aspx?nDownloadId=1825)

## Windows 98SE Service Pack

An unofficial Service pack for Windows 98 is available:

* [Windows 98SE Unofficial Service Pack](https://www.majorgeeks.com/files/details/unofficial_windows98_se_service_pack.html)

## Configuring the Windows 98 Guest

Select File → New Virtual Machine:

<img src='./images/img_006.png' alt='img_006' width='600'/>

It is recommended to instead use "I Will Install this Operating System Later":

<img src='./images/img_007.png' alt='img_007' width='600'/>

Select Microsoft Windows and Windows 98 and select Next:

<img src='./images/img_008.png' alt='img_008' width='600'/>

The VM Name and Location will be shown. Note when used on a Windows 11 Host which is signed in with a Microsoft Account and integrated with OneDrive, the default location will be on OneDrive. The VM can be quite large and the location can be changed to local Documents by removing the OneDrive folder:

<img src='./images/img_009.png' alt='img_009' width='600'/>

Note the name and location as these will be used later.

The default maximum size of the Windows 98 Guest is 8 GB which is a bit too restrictive. I recommend increasing this to 32 GB. Note the files on the Windows 11 Host won't be 32 GB but can be up to 32 GB if the Windows 98 Guests Virtual Drive is fully occupied with files. Windows 98 may struggle with a Virtual Drive > 32 GB:

<img src='./images/img_010.png' alt='img_010' width='600'/>

Select Customise Hardware:

<img src='./images/img_011.png' alt='img_011' width='600'/>

Change the memory to 512 MB (Windows 98 has issues with larger memory sizes):

<img src='./images/img_012.png' alt='img_012' width='600'/>

Leave the processor options to their default. Windows 98 does not support any of the unticked technologies and only supports 1 processor. A modern processor may be too fast for it and the patcher9x will need to later be used to address this:

<img src='./images/img_013.png' alt='img_013' width='600'/>

In CD/DVD select the Windows 98 SE OEM ISO:

<img src='./images/img_014.png' alt='img_014' width='600'/>

Leave Network Adaptor at the default setting:

<img src='./images/img_015.png' alt='img_015' width='600'/>

Leave the USB Controller at the default setting. NUSB will need to be installed later to access USB Devices:

<img src='./images/img_016.png' alt='img_016' width='600'/>

Leave the Sound Card at the default setting:

<img src='./images/img_017.png' alt='img_017' width='600'/>

Leave display at the default setting and select Close:

<img src='./images/img_018.png' alt='img_018' width='600'/>

Select Finish:

<img src='./images/img_019.png' alt='img_019' width='600'/>

## Installing the Windows 98 Guest

Select the Windows 98 Guest and select Play:

<img src='./images/img_020.png' alt='img_020' width='600'/>

Select Boot from CD-ROM:

<img src='./images/img_021.png' alt='img_021' width='600'/>

Select Start Windows 98 Setup from CD-ROM:

<img src='./images/img_022.png' alt='img_022' width='600'/>

Press `↵`:

<img src='./images/img_023.png' alt='img_023' width='600'/>

Select Configure Allocated SPace (Recommended):

<img src='./images/img_024.png' alt='img_024' width='600'/>

Select Yes Enable Large Disk Support:

<img src='./images/img_025.png' alt='img_025' width='600'/>

Press `↵`:

<img src='./images/img_026.png' alt='img_026' width='600'/>

Select Boot from CD-ROM:

<img src='./images/img_027.png' alt='img_027' width='600'/>

Select Start Windows 98 Setup from CD-ROM:

<img src='./images/img_028.png' alt='img_028' width='600'/>

The Windows Setup will format the Virtual Drive:

<img src='./images/img_029.png' alt='img_029' width='600'/>

Press `↵`:

<img src='./images/img_030.png' alt='img_030' width='600'/>

Select Continue:

<img src='./images/img_031.png' alt='img_031' width='600'/>

Select the default `C:/Windows` and select Next:

<img src='./images/img_032.png' alt='img_032' width='600'/>

Select Typical and press Next:

<img src='./images/img_033.png' alt='img_033' width='600'/>

Select Install the most common components (recommended):

<img src='./images/img_034.png' alt='img_034' width='600'/>

Use the default computer name or amend as desired and select next:

<img src='./images/img_035.png' alt='img_035' width='600'/>

Select your location and select next:

<img src='./images/img_036.png' alt='img_036' width='600'/>

Select next:

<img src='./images/img_037.png' alt='img_037' width='600'/>

Input your user name and select next:

<img src='./images/img_038.png' alt='img_038' width='600'/>

Accept the License Agreement and select Next:

<img src='./images/img_039.png' alt='img_039' width='600'/>

Input the provided Product Key and select next:

<img src='./images/img_040.png' alt='img_040' width='600'/>

Select Finish:

<img src='./images/img_041.png' alt='img_041' width='600'/>

On a Windows 11 Host or Ubuntu 24.10 Host with a modern processor. The Windows 98SE installation errors out on a VM on a modern computer:

> This program has performed an illegal operation and will be shut down.

> If the problem persists, contact the program vendor

<img src='./images/img_042.png' alt='img_042' width='600'/>

Essentially the processor is too fast and windows 98SE expects to wait more than "zero seconds" for an operation.

## Patcher 9x

Select Power → Shut Down Guest:

<img src='./images/img_043.png' alt='img_043' width='600'/>

Select Yes:

<img src='./images/img_044.png' alt='img_044' width='600'/>

Select the Windows 98 Guest and select Edit Virtual Machine Settings:

<img src='./images/img_045.png' alt='img_045' width='600'/>

Under Hardware select Add:

<img src='./images/img_046.png' alt='img_046' width='600'/>

Select Floppy Drive and Finish:

<img src='./images/img_047.png' alt='img_047' width='600'/>

Select Use Floppy Drive and select the `patcher9x-0.8.50-boot.img`:

<img src='./images/img_048.png' alt='img_048' width='600'/>

Select the Windows 98 Guest and select Play:

<img src='./images/img_049.png' alt='img_049' width='600'/>

The Windows 98 Guest will boot to the floppy drive, select FreeDOS/XMS with CD-ROM (default):

<img src='./images/img_050.png' alt='img_050' width='600'/>

Input:

```
patch9x
```

<img src='./images/img_051.png' alt='img_051' width='600'/>

Press `↵`:

<img src='./images/img_052.png' alt='img_052' width='600'/>

Input 

```
2
``` 

to select VMM32.VXB will be patched directly (default):

<img src='./images/img_053.png' alt='img_053' width='600'/>

Input:

```
y
```

<img src='./images/img_054.png' alt='img_054' width='600'/>


The Windows 98 Guest is patched press `↵` to exit:

<img src='./images/img_055.png' alt='img_055' width='600'/>

A new DOS prompt will display:

<img src='./images/img_056.png' alt='img_056' width='600'/>

Select Removable Devices → Floppy Settings:

<img src='./images/img_057.png' alt='img_057' width='600'/>

Select Floppy and uncheck Connected and Connect at Power On. Select OK:

<img src='./images/img_058.png' alt='img_058' width='600'/>

Select Power → Restart Guest:

<img src='./images/img_059.png' alt='img_059' width='600'/>

Select Yes:

<img src='./images/img_060.png' alt='img_060' width='600'/>

The Windows 98 setup will proceed:

<img src='./images/img_061.png' alt='img_061' width='600'/>

Log in:

<img src='./images/img_062.png' alt='img_062' width='600'/>

Select your Time Zone and select apply and close:

<img src='./images/img_063.png' alt='img_063' width='600'/>

Select restart now:

<img src='./images/img_064.png' alt='img_064' width='600'/>

Log in:

<img src='./images/img_065.png' alt='img_065' width='600'/>

You are now on the Windows 98 Desktop:

<img src='./images/img_066.png' alt='img_066' width='600'/>

Select Start → Shut Down:

<img src='./images/img_067.png' alt='img_067' width='600'/>

Select Shut Down and then OK:

<img src='./images/img_068.png' alt='img_068' width='600'/>

## Installing VMware Tools

Installing VMware tools will install some of the Windows 98 System Drivers. Installation of drivers also uses the Windows 98 Installation CD, so it is recommended to use a second virtual drive for VMware Tools.

Select the Windows 98 Guest and select Edit Virtual Machine Settings:

<img src='./images/img_069.png' alt='img_069' width='600'/>

Under Hardware select Add:

<img src='./images/img_070.png' alt='img_070' width='600'/>

Select CD/DVD Drive and select Finish:

<img src='./images/img_071.png' alt='img_071' width='600'/>

Select use ISO Image and select the `winPre2k.iso`:

<img src='./images/img_072.png' alt='img_072' width='600'/>

Select the Windows 98 Guest and select Play:

<img src='./images/img_073.png' alt='img_073' width='600'/>

In the Windows 98 Guest, navigate to My Computer:

<img src='./images/img_074.png' alt='img_074' width='600'/>

Select VMware Tools:

<img src='./images/img_075.png' alt='img_075' width='600'/>

Select Next:

<img src='./images/img_076.png' alt='img_076' width='600'/>

Select Typical (I select Complete and the same number of drivers were installed, some system drivers are missing and need to be manually installed) and Next:

<img src='./images/img_077.png' alt='img_077' width='600'/>

Select Install:

<img src='./images/img_078.png' alt='img_078' width='600'/>

Select Finish:

<img src='./images/img_079.png' alt='img_079' width='600'/>

Select Yes:

<img src='./images/img_080.png' alt='img_080' width='600'/>

The Windows 98 Guest will restart. Select My Computer:

<img src='./images/img_081.png' alt='img_081' width='600'/>

Select Control Panel:

<img src='./images/img_082.png' alt='img_082' width='600'/>

Select Display:

<img src='./images/img_083.png' alt='img_083' width='600'/>

Select Settings and change the resolution to the maximum value and select apply:

<img src='./images/img_084.png' alt='img_084' width='600'/>

Select OK:

<img src='./images/img_085.png' alt='img_085' width='600'/>

Select Yes:

<img src='./images/img_086.png' alt='img_086' width='600'/>

Select the Windows 98 Guest window in the Windows 11 Host or Ubuntu 24.10 Host and resize it, the Windows 98 Guest will automatically update its resolution to match the window size:

<img src='./images/img_087.png' alt='img_087' width='600'/>

Select System:

<img src='./images/img_088.png' alt='img_088' width='600'/>

Select Device Manager:

<img src='./images/img_089.png' alt='img_089' width='600'/>

Notice that the:

* Multimedia Audio Device
* System Peripheral
* PCI Universal Serial Bus

do not have driver.

## Backing Up the Windows 98 Guest

Select Start → Shut Down:

<img src='./images/img_090.png' alt='img_090' width='600'/>

Select Shut Down and then OK:

<img src='./images/img_091.png' alt='img_091' width='600'/>

On the Windows 11 Host or Ubuntu 24.10 Host, navigate to Documents and the Virtual Machines folder:

<img src='./images/img_092.png' alt='img_092' width='600'/>

Copy the Windows 98 folder to back it up:

<img src='./images/img_093.png' alt='img_093' width='600'/>

This will give you a working state to revert back to if you encounter an issue during driver installation or use of the Unofficial Service Pack.

## Intel Chipset Device Software

VMware Tools is installed meaning drag and drop to the Virtual Machine works bi-directionally on a Windows 11 Host and on a Ubuntu 24.10 only from the Ubuntu 24.10 Host to the Windows 98 Guest:

Extract the `6.3.0.1007.zip` folder:

<img src='./images/img_094.png' alt='img_094' width='600'/>

View the extracted folder and drag the `infinst_enu.exe` for the Intel Chipset Software Installation Utility to the Windows 98 Guest:

<img src='./images/img_095.png' alt='img_095' width='600'/>

Launch the `infinst_enu.exe`:

<img src='./images/img_096.png' alt='img_096' width='600'/>

Select next:

<img src='./images/img_097.png' alt='img_097' width='600'/>

Select yes:

<img src='./images/img_098.png' alt='img_098' width='600'/>

Select next:

<img src='./images/img_099.png' alt='img_099' width='600'/>

Select next to restart the Windows 98 Guest:

<img src='./images/img_100.png' alt='img_100' width='600'/>

Select next:

<img src='./images/img_101.png' alt='img_101' width='600'/>

Select next:

<img src='./images/img_102.png' alt='img_102' width='600'/>

Select next:

<img src='./images/img_103.png' alt='img_103' width='600'/>

Select next:

<img src='./images/img_104.png' alt='img_104' width='600'/>

Select finish:

<img src='./images/img_105.png' alt='img_105' width='600'/>

This process repeats for a number of other drivers. Select yes to restart the Windows 98 Guest:

<img src='./images/img_106.png' alt='img_106' width='600'/>

## NUSB - USB Mass Storage

<img src='./images/img_107.png' alt='img_107' width='600'/>
<img src='./images/img_108.png' alt='img_108' width='600'/>
<img src='./images/img_109.png' alt='img_109' width='600'/>
<img src='./images/img_110.png' alt='img_110' width='600'/>
<img src='./images/img_111.png' alt='img_111' width='600'/>
<img src='./images/img_112.png' alt='img_112' width='600'/>
<img src='./images/img_113.png' alt='img_113' width='600'/>
<img src='./images/img_114.png' alt='img_114' width='600'/>
<img src='./images/img_115.png' alt='img_115' width='600'/>
<img src='./images/img_116.png' alt='img_116' width='600'/>
<img src='./images/img_117.png' alt='img_117' width='600'/>
<img src='./images/img_118.png' alt='img_118' width='600'/>









Drag driver across and install...

Update for new version...

Update in Device Manager

## Crucial Soundblaster

<img src='./images/img_119.png' alt='img_119' width='600'/>
<img src='./images/img_120.png' alt='img_120' width='600'/>
<img src='./images/img_121.png' alt='img_121' width='600'/>
<img src='./images/img_122.png' alt='img_122' width='600'/>
<img src='./images/img_123.png' alt='img_123' width='600'/>
<img src='./images/img_124.png' alt='img_124' width='600'/>




Insert Windows 98 SE Disk into D:



Launch Setup


Do the other file...


## Hardware IDs

Start Run


```
hwinfo /ui
```


```
HKEY_LOCAL_MACHINE\enum\PCI\VEN_15AD&DEV_0740&SUBSYS_074015AD&REV_10\BUS_00&DEV_07&FUNC_07
```


VMware VMCI Bus

For Windows 98 and Windows 98SE, there is no support for the VMCI device in VMware Tools. One workaround is to disable the VMCI device using the Device Manager so that it is ignored by Windows, and diagnostic tools stop reporting errors. 

https://knowledge.broadcom.com/external/article?legacyId=1023129



## Installing Unofficial Service Pack


* Install Main Updates/System Core Files

* Install latest DirectX 9C


## Drivers

https://www.conceptworks.io/en/knowledge-base/289/


* [Logitech Mouse](https://download.cnet.com/mw980enu-exe/3000-2108_4-157438.html)


https://startup.retropc.se/win98.html
