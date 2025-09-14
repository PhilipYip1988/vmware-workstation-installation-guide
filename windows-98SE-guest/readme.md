# Windows 98SE

## YouTube Video

* [YouTube](https://www.youtube.com/watch?v=cxW57znmmu8)

## Notes

VMware Workstation Player 17.6.4 has Windows 98 SE as an option for a Virtual Machine. However Windows 98 SE is regarded as an ancient legacy Operating System and isn't tested by Broadcom. Modern processors are significantly faster than the processers available when WIndows 98 SE was released. As a consequence the timing for some operations is divided by 0 and there is a divide-by-zero error that needs to be addressed using patcher9x.

VMware Tools 12.5.3 which comes with VMware workstation player doesn't support Windows 98SE. VMware Tools WinPre2k is the last version of VMware Tools to support Windows 98SE and should be downloaded seperately as an ISO. This ISO should be mounted in the VM so they can be installed manually.

On modern hardware with a 12th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

The first setting allows the CPU to optimise the VM performance, the VM may be very slow without this setting. The second setting prevents use of a memory management unit that Windows 98SE doesn't understand and can lead to a Blue Screen of Death (BSOD). The third setting prevents VMware from using Vulkan for rendering, which isn't supported by Windows 98SE and often leads to black screens. The last two settings prevent Windows 98SE from seeing unsupported CPU features which Windows 98SE doesn't understand and can lead to a Blue Screen of Death (BSOD).

## Downloads

### Windows 98SE ISO

Windows 98SE is considered abandonware and the Windows 98SE ISO and Product Key can be obtained from WinWorld:

* [WinWorld](https://winworldpc.com/product/windows-98/98-second-edition)

Use the OEM Full ISO as the Retail Full ISO doesn't boot in VMware Player without use of a floppy disk and use the provided Product Key. For this version of Windows there was only a Product Key. Windows 98 SE was too primitive for Product Activation and a high proportion of Windows 98 SE computers were offline meaning internet activation mechanisms were unfeasible during this version fo Windows lifecycle.

### VMware Tools ISO

The Windows 98SE drivers for the Windows 98SE Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

* [VMware Tools Pre2k](https://archive.org/details/winPre2k)

### Patcher9x

Download the `patcher9x-win64.zip` from the assets of the latest release:

* [patcher9x](https://github.com/JHRobotics/patcher9x/releases/)

### 7-zip

Download and install on the Windows 11 Guest:

* [7-zip](https://7-zip.org/download.html)

### ImgBurn

Download and install on the Windows 11 Guest:

* [ImgBurn](https://www.imgburn.com/)

### Patching the Installation ISO

The Windows 98SE installation errors out on a VM on a modern computer:

> This program has performed an illegal operation and will be shut down.

> If the problem persists, contact the program vendor

<img src='./images/img_001.png' alt='img_001' width='600'/>

Essentially the processor is too fast and windows 98SE expects to wait more than "zero seconds" for an operation. Therefore the WIndows 98SE installation media needs to be patched with patcher9x. Extract patcher9x:

<img src='./images/img_002.png' alt='img_002' width='600'/>

<img src='./images/img_003.png' alt='img_003' width='600'/>

<img src='./images/img_004.png' alt='img_004' width='600'/>

Now extract the WIdnows 98 SE ISO:

<img src='./images/img_005.png' alt='img_005' width='600'/>

<img src='./images/img_006.png' alt='img_006' width='600'/>

The files from the ISO need to be extracted, to do this right click the ISO and select Show More Options:

<img src='./images/img_007.png' alt='img_007' width='600'/>

<img src='./images/img_008.png' alt='img_008' width='600'/>

Select 7zip and then extract to:

<img src='./images/img_009.png' alt='img_009' width='600'/>

<img src='./images/img_010.png' alt='img_010' width='600'/>

Cut the extracted folder and paste to Downloads:

<img src='./images/img_011.png' alt='img_011' width='600'/>

<img src='./images/img_012.png' alt='img_012' width='600'/>

Rename the folder WIN98_SE and delete the old ISO and zip files:

<img src='./images/img_013.png' alt='img_013' width='600'/>

<img src='./images/img_014.png' alt='img_014' width='600'/>

Navigate to the extracted `patcher-win64` folder:

<img src='./images/img_015.png' alt='img_015' width='600'/>

Launch `patcher9x.exe`:

<img src='./images/img_016.png' alt='img_016' width='600'/>

Select More Info and Run Anyway:

<img src='./images/img_017.png' alt='img_017' width='300'/>

<img src='./images/img_018.png' alt='img_018' width='300'/>

In file explorer navigate to `WIN98_SE` and then `win98` which is the folder that contains the `.cab` files:

<img src='./images/img_019.png' alt='img_019' width='600'/>

Copy the file path:

<img src='./images/img_020.png' alt='img_020' width='600'/>

And paste it into the terminal (note the file path should be entered without quotes):

<img src='./images/img_021.png' alt='img_021' width='600'/>

Input `4` scan \*.CAB archives and patch them directly. Input:

<img src='./images/img_022.png' alt='img_022' width='600'/>

Input `y`:

<img src='./images/img_023.png' alt='img_023' width='600'/>

The \*.CAB files will now be patched. Press `↵` to exit:

<img src='./images/img_024.png' alt='img_024' width='600'/>

The following folder now needs to be converted back into an .iso and this .iso needs to be bootable:

<img src='./images/img_025.png' alt='img_025' width='600'/>

Launch ImgBurn and select Create Image File from Files/Folders:

<img src='./images/img_026.png' alt='img_026' width='600'/>

Load a folder:

<img src='./images/img_027.png' alt='img_027' width='600'/>

Select `WIN98_SE`:

<img src='./images/img_028.png' alt='img_028' width='600'/>

Select, select folder:

<img src='./images/img_029.png' alt='img_029' width='600'/>

Select options and change the data type to MODE1/2048 and the file system to ISO9660 + Joliet. Ensure Recurse subdirectories is checked:

<img src='./images/img_030.png' alt='img_030' width='600'/>

Select Labels and under ISO9660 input WIN98_SE and under Joliet input WIN98_SE:

<img src='./images/img_031.png' alt='img_031' width='600'/>

Under Advanced, select Bootable Disc. In Bootable Disc select Make Image Bootable and change the emulation type to Floppy Disk 1.44 MB. Change the Platform ID to 80x86 and set the Developer ID as Microsoft Corporation:

<img src='./images/img_032.png' alt='img_032' width='600'/>

Under Boot image select load folder:

<img src='./images/img_033.png' alt='img_033' width='600'/>

Go to the \[Boot\] folder and select the Boot-1.44M.img:

<img src='./images/img_034.png' alt='img_034' width='600'/>

<img src='./images/img_035.png' alt='img_035' width='600'/>

Under destination select the folder icon:

<img src='./images/img_036.png' alt='img_036' width='600'/>

Navigate to Downloads and save the .iso as WIN98_SE_PATCHER9X:

<img src='./images/img_037.png' alt='img_037' width='600'/>

Select the Create Image File from Files/Folder icon:

<img src='./images/img_038.png' alt='img_038' width='600'/>

Select Yes and Ok:

<img src='./images/img_039.png' alt='img_039' width='300'/>

<img src='./images/img_040.png' alt='img_040' width='200'/>

The patched .iso will now be created, select OK:

<img src='./images/img_041.png' alt='img_041' width='300'/>

Delete the previous files:

<img src='./images/img_042.png' alt='img_042' width='600'/>

There should now be the patched .iso and the vmware tools .iso:

<img src='./images/img_043.png' alt='img_043' width='600'/>

## System Drivers

Download the following drivers

### Intel Chipset Installation Utility

VMware tools is missing the Intel Chipset driver (use the latest at the bottom):

* [6.3.0.1007](https://www.philscomputerlab.com/intel-chipset-drivers.html)

### NUSB Storage Driver

VMware tools is missing the NUSB Storage driver (use the 33 version, it reported works better with Windows 98 SE and the 36 version reportedly works better with Windows ME)

* [NUSB33e](https://www.philscomputerlab.com/windows-98-usb-storage-driver.html)

### Creative SoundBlaster

VMware tools is missing the Creative SoundBlaster driver:

* [Creative SBPCI_WebDrvsV5_12_01.exe](https://support.creative.com/downloads/download.aspx?nDownloadId=1843)

* [Creative eapci8m.ecw](https://support.creative.com/downloads/download.aspx?nDownloadId=1825)

### Windows 98SE Autopatcher

* [Windows 98SE Autopatcher](https://download.cnet.com/auto-patcher-for-windows-98se-english/3000-2094_4-10653137.html)

Extract the Intel Chipset driver:

<img src='./images/img_044.png' alt='img_044' width='600'/>

You should have the following and are now ready to create a Windows 98SE Guest Virtual Machine:

<img src='./images/img_045.png' alt='img_045' width='600'/>

## Configuring the Windows 98 Guest

Select File → New Virtual Machine:

<img src='./images/img_046.png' alt='img_046' width='600'/>

It is recommended to instead use "I Will Install this Operating System Later":

<img src='./images/img_047.png' alt='img_047' width='600'/>

Select Microsoft Windows and Windows 98 and select Next:

<img src='./images/img_048.png' alt='img_048' width='600'/>

The VM Name and Location will be shown. Note when used on a Windows 11 Host which is signed in with a Microsoft Account and integrated with OneDrive, the default location will be on OneDrive. The VM can be quite large and the location can be changed to local Documents by removing the OneDrive folder:

<img src='./images/img_049.png' alt='img_049' width='600'/>

Note the name and location as these will be used later.

The default maximum size of the Windows 98 Guest is 8 GB which is a bit too restrictive. I recommend increasing this to 32 GB. Note the files on the Windows 11 Host won't be 32 GB but can be up to 32 GB if the Windows 98 Guests Virtual Drive is fully occupied with files. Windows 98 may struggle with a Virtual Drive > 32 GB:

<img src='./images/img_050.png' alt='img_050' width='600'/>

Select Customise Hardware:

<img src='./images/img_051.png' alt='img_051' width='600'/>

Change the memory to 512 MB (Windows 98 has issues with larger memory sizes):

<img src='./images/img_052.png' alt='img_052' width='600'/>

Leave the processor options to their default. Windows 98 does not support any of the unticked technologies and only supports 1 processor. A modern processor may be too fast for it and the patcher9x will need to later be used to address this:

<img src='./images/img_053.png' alt='img_053' width='600'/>

In CD/DVD select the Windows 98 SE OEM ISO:

<img src='./images/img_054.png' alt='img_054' width='600'/>

Under Network Adaptor uncheck Connect at Power On. Windows 98 SE has reached end of life and is unsafe to use on the internet:

<img src='./images/img_055.png' alt='img_055' width='600'/>

Leave the USB Controller at the default setting. NUSB will need to be installed later to access USB Devices:

<img src='./images/img_056.png' alt='img_056' width='600'/>

Leave the Sound Card at the default setting:

<img src='./images/img_057.png' alt='img_057' width='600'/>

Leave display at the default setting and select Close:

<img src='./images/img_058.png' alt='img_058' width='600'/>

Select Finish:

<img src='./images/img_059.png' alt='img_059' width='600'/>

## Windows 98 SE Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows 98 SE Guest is installed: 

<img src="https://github.com/user-attachments/assets/0ef95099-1ab9-42a0-bc4e-fc09e03dbff1" width='600'/>

Look for the `Windows 98 SE.vmx` file:

<img src="https://github.com/user-attachments/assets/84da345f-cb0d-4d7b-ab89-d231fd9d3a7a" width='600'/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/b9735045-7549-42f3-8333-c4ca3007288f" width='600'/>

The option `bios.bootDelay` for example will change the time the Windows98 SE Guest Virtual BIOS displays before selecting the default boot option giving more time to select the option to boot from CD/DVD. This line can be removed post-installation, returning to the default value.

Press `Ctrl+f` to begin a search for an option for example `bios.bootDelay`:

<img src="https://github.com/user-attachments/assets/accae0e7-da9f-4077-93a9-9491d77f3f6b" width='600' />

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/0e82afed-fe7e-4718-a315-5d85c6898436" width='600'/>

### 12th-14 Generation Processors

On a 12th–14th Generation Intel processor, certain legacy settings may need to be configured to run older guest operating systems such as Windows 98 SE.

Legacy CPU settings:

```
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

These settings help emulate older CPU instructions that Windows 98 SE (patched) expects.

Legacy monitor / virtualization settings

```
mks.enableVulkanRenderer = "FALSE"
```

This disables the Vulkan renderer, forcing VMware to use a more compatible DirectX/software renderer.

Legacy monitor / virtualization settings:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
```

These settings ensure proper CPU and MMU handling for legacy guests.

<img src="https://github.com/user-attachments/assets/1176ef78-a6fb-49a7-8def-96b679d54309" width='600'/>


## Installing the Windows 98 Guest

Select the Windows 98 Guest and select Play:

<img src='./images/img_060.png' alt='img_060' width='600'/>

Select Boot from CD-ROM:

<img src='./images/img_061.png' alt='img_061' width='600'/>

Select Start Windows 98 Setup from CD-ROM:

<img src='./images/img_062.png' alt='img_062' width='600'/>

Press `↵`:

<img src='./images/img_063.png' alt='img_063' width='600'/>

Select Configure Allocated Space (Recommended):

<img src='./images/img_064.png' alt='img_064' width='600'/>

Select Yes Enable Large Disk Support:

<img src='./images/img_065.png' alt='img_065' width='600'/>

Press `↵`:

<img src='./images/img_066.png' alt='img_066' width='600'/>

Select Boot from CD-ROM:

<img src='./images/img_067.png' alt='img_067' width='600'/>

Select Start Windows 98 Setup from CD-ROM:

<img src='./images/img_068.png' alt='img_068' width='600'/>

The Windows Setup will format the Virtual Drive:

<img src='./images/img_069.png' alt='img_069' width='600'/>

Press `↵`:

<img src='./images/img_070.png' alt='img_070' width='600'/>

Select Continue:

<img src='./images/img_071.png' alt='img_071' width='600'/>

Select the default `C:/Windows` and select Next:

<img src='./images/img_072.png' alt='img_072' width='600'/>

Select Typical and press Next:

<img src='./images/img_073.png' alt='img_073' width='600'/>

Select Install the most common components (recommended):

<img src='./images/img_074.png' alt='img_074' width='600'/>

Use the default computer name or amend as desired and select next:

<img src='./images/img_075.png' alt='img_075' width='600'/>

Select your location and select next:

<img src='./images/img_076.png' alt='img_076' width='600'/>

Select next:

<img src='./images/img_077.png' alt='img_077' width='600'/>

Input your user name and select next:

<img src='./images/img_078.png' alt='img_078' width='600'/>

Accept the License Agreement and select Next:

<img src='./images/img_079.png' alt='img_079' width='600'/>

Input the provided Product Key and select next:

<img src='./images/img_080.png' alt='img_080' width='600'/>

Select Finish:

<img src='./images/img_081.png' alt='img_081' width='600'/>

Log in:

<img src='./images/img_082.png' alt='img_082' width='600'/>

Select your Time Zone and select apply and close:

<img src='./images/img_083.png' alt='img_083' width='600'/>

Select restart now:

<img src='./images/img_084.png' alt='img_084' width='600'/>

Log in:

<img src='./images/img_085.png' alt='img_085' width='600'/>

You are now on the Windows 98 Desktop:

<img src='./images/img_086.png' alt='img_086' width='600'/>

Select Start → Shut Down:

<img src='./images/img_087.png' alt='img_087' width='600'/>

Select Shut Down and then OK:

<img src='./images/img_088.png' alt='img_088' width='600'/>

## Installing VMware Tools

Installing VMware tools will install some of the Windows 98 System Drivers. Installation of drivers also uses the Windows 98 Installation CD, so it is recommended to use a second virtual drive for VMware Tools.

Select the Windows 98 Guest and select Edit Virtual Machine Settings:

<img src='./images/img_089.png' alt='img_089' width='600'/>

Under Hardware select Add:

<img src='./images/img_090.png' alt='img_090' width='600'/>

Select CD/DVD Drive and select Finish:

<img src='./images/img_091.png' alt='img_091' width='600'/>

Select use ISO Image and select the `winPre2k.iso`:

<img src='./images/img_092.png' alt='img_092' width='600'/>

Select the Windows 98 Guest and select Play:

<img src='./images/img_093.png' alt='img_093' width='600'/>

In the Windows 98 Guest, navigate to My Computer:

<img src='./images/img_094.png' alt='img_094' width='600'/>

Select VMware Tools:

<img src='./images/img_095.png' alt='img_095' width='600'/>

Select Next:

<img src='./images/img_096.png' alt='img_096' width='600'/>

Select Typical (I select Complete and the same number of drivers were installed, some system drivers are missing and need to be manually installed) and Next:

<img src='./images/img_097.png' alt='img_097' width='600'/>

Select Install:

<img src='./images/img_098.png' alt='img_098' width='600'/>

Select Finish:

<img src='./images/img_099.png' alt='img_099' width='600'/>

Select Yes:

<img src='./images/img_100.png' alt='img_100' width='600'/>

The Windows 98 Guest will restart. Select My Computer:

<img src='./images/img_101.png' alt='img_101' width='600'/>

Select Control Panel:

<img src='./images/img_102.png' alt='img_102' width='600'/>

Select Display:

<img src='./images/img_103.png' alt='img_103' width='600'/>

Select Settings and change the resolution to the maximum value and select apply:

<img src='./images/img_104.png' alt='img_104' width='600'/>

Select OK:

<img src='./images/img_105.png' alt='img_105' width='600'/>

Select Yes:

<img src='./images/img_106.png' alt='img_106' width='600'/>

Select the Windows 98 Guest window in the Windows 11 Host or Ubuntu 24.10 Host and resize it, the Windows 98 Guest will automatically update its resolution to match the window size:

<img src='./images/img_107.png' alt='img_107' width='600'/>

Select System:

<img src='./images/img_108.png' alt='img_108' width='600'/>

Select Device Manager:

<img src='./images/img_109.png' alt='img_109' width='600'/>

Notice that the:

* Multimedia Audio Device
* System Peripheral
* PCI Universal Serial Bus

do not have driver.

## Backing Up the Windows 98 Guest

Select Start → Shut Down:

<img src='./images/img_110.png' alt='img_110' width='600'/>

Select Shut Down and then OK:

<img src='./images/img_111.png' alt='img_111' width='600'/>

On the Windows 11 Host or Ubuntu 24.10 Host, navigate to Documents and the Virtual Machines folder:

<img src='./images/img_112.png' alt='img_112' width='600'/>

Copy the Windows 98 folder to back it up:

<img src='./images/img_113.png' alt='img_113' width='600'/>

This will give you a working state to revert back to if you encounter an issue during driver installation (to revert, delete the WIndows 98 folder and rename the backup Windows 98).

## Intel Chipset Device Software

VMware Tools is installed meaning drag and drop to the Virtual Machine works bi-directionally on a Windows 11 Host and on a Ubuntu 24.10 only from the Ubuntu 24.10 Host to the Windows 98 Guest:

Extract the `6.3.0.1007.zip` folder:

<img src='./images/img_114.png' alt='img_114' width='600'/>

View the extracted folder and drag the `infinst_enu.exe` for the Intel Chipset Software Installation Utility to the Windows 98 Guest:

<img src='./images/img_115.png' alt='img_115' width='600'/>

Launch the `infinst_enu.exe`:

<img src='./images/img_116.png' alt='img_116' width='600'/>

Select next:

<img src='./images/img_117.png' alt='img_117' width='600'/>

Select yes:

<img src='./images/img_118.png' alt='img_118' width='600'/>

Select next:

<img src='./images/img_119.png' alt='img_119' width='600'/>

Select next to restart the Windows 98 Guest:

<img src='./images/img_120.png' alt='img_120' width='600'/>

Select next:

<img src='./images/img_121.png' alt='img_121' width='600'/>

Select next:

<img src='./images/img_122.png' alt='img_122' width='600'/>

Select next:

<img src='./images/img_123.png' alt='img_123' width='600'/>

Select next:

<img src='./images/img_124.png' alt='img_124' width='600'/>

Select finish:

<img src='./images/img_125.png' alt='img_125' width='600'/>

This process repeats for a number of other drivers. Select yes to restart the Windows 98 Guest:

<img src='./images/img_126.png' alt='img_126' width='600'/>

## NUSB - USB Mass Storage

Drag the `nusb33e.exe` to the WIndows 98 Guest desktop and launch the application:

<img src='./images/img_127.png' alt='img_127' width='600'/>

Select yes:

<img src='./images/img_128.png' alt='img_128' width='600'/>

Select yes:

<img src='./images/img_129.png' alt='img_129' width='600'/>

Select My Computer:

<img src='./images/img_130.png' alt='img_130' width='600'/>

Select Control Panel:

<img src='./images/img_131.png' alt='img_131' width='600'/>

Select System:

<img src='./images/img_132.png' alt='img_132' width='600'/>

Select Device Manager:

<img src='./images/img_133.png' alt='img_133' width='600'/>

Select PCI Universal Serial BUS and select properties:

<img src='./images/img_134.png' alt='img_134' width='600'/>

Select Driver → Update Driver:

<img src='./images/img_135.png' alt='img_135' width='600'/>

Select next:

<img src='./images/img_136.png' alt='img_136' width='600'/>

Select finish:

<img src='./images/img_137.png' alt='img_137' width='600'/>

The PCI Universal Serial BUS is no longer listed under Other devices because it has its driver installed:

<img src='./images/img_138.png' alt='img_138' width='600'/>

## Crucial Soundblaster

Drag `SBPCI_WebDrvsV5_12_01.exe` to the Windows 98 Guest Desktop and launch the setup:

<img src='./images/img_139.png' alt='img_139' width='600'/>

Select yes:

<img src='./images/img_140.png' alt='img_140' width='600'/>

If the following error displays, check the Windows 98 Installation Disk is mounted in `D:` (just mount it on both optical drives). Select Removable Devices → CD/DVD → Settings:

<img src='./images/img_141.png' alt='img_141' width='600'/>

Under Use ISO file image, select the Windows 98 Installation Disk. Repeat for CD/DVD and select OK:

<img src='./images/img_142.png' alt='img_142' width='600'/>

Select OK:

<img src='./images/img_143.png' alt='img_143' width='600'/>

Select finish:

<img src='./images/img_144.png' alt='img_144' width='600'/>

Open the Device Manager, the PCI Multimedia Audio Device listed under Other Device is gone because the driver is installed:

<img src='./images/img_145.png' alt='img_145' width='600'/>

Drag the `eapci8m.ecw` waveset to `C:\WINDOWS\SYSTEM`:

<img src='./images/img_146.png' alt='img_146' width='600'/>

Expand Sound, video and game controllers. Select SB PCI(WDM) and select Properties:

<img src='./images/img_147.png' alt='img_147' width='600'/>

Select Settings and select Add WaveSet:

<img src='./images/img_148.png' alt='img_148' width='600'/>

Select the `system` folder:

<img src='./images/img_149.png' alt='img_149' width='600'/>

Select the `eapci8m.ecw` waveset and select Ok:

<img src='./images/img_150.png' alt='img_150' width='600'/>

Select Ok:

<img src='./images/img_151.png' alt='img_151' width='600'/>

Restart the Windows 98 SE Guest.

## Hardware IDs

There is still a PCI System Peripheral in the Device Manager without a driver. To get the Hardware IDs press Start and select Run:

<img src='./images/img_152.png' alt='img_152' width='600'/>

Input the following command:

```
hwinfo /ui
```

<img src='./images/img_153.png' alt='img_153' width='600'/>

In the output file, press `Ctrl+f` and search for PCI System Peripheral:

<img src='./images/img_154.png' alt='img_154' width='600'/>

This is:

```
HKEY_LOCAL_MACHINE\enum\PCI\VEN_15AD&DEV_0740&SUBSYS_074015AD&REV_10\BUS_00&DEV_07&FUNC_07
```

which is the VMware VMCI Bus which is used by VMware for folder sharing and dragging and dropping files:

<img src='./images/img_155.png' alt='img_155' width='600'/>

According to Broadcom there is no Windows 98 driver for this device:

> For Windows 98 and Windows 98SE, there is no support for the VMCI device in VMware Tools. 

[Broadcom Legacy Article 1023129](https://knowledge.broadcom.com/external/article?legacyId=1023129)

## Autopatcher for Windows 98 SE

It is recommended to backup the Virtual Machine by copying the Windows 98 folder on the Windows 11 Host before attempting to patch Windows 98 SE.

Drag `Auto-Patcher_for_Win98se_August_2007_FULL.EXE` to the Windows 98 Guest Desktop and launch the application:

<img src='./images/img_156.png' alt='img_156' width='600'/>

Select next:

<img src='./images/img_157.png' alt='img_157' width='600'/>

Select next:

<img src='./images/img_158.png' alt='img_158' width='600'/>

Select next:

<img src='./images/img_159.png' alt='img_159' width='600'/>

Select next:

<img src='./images/img_160.png' alt='img_160' width='600'/>

Select install:

<img src='./images/img_161.png' alt='img_161' width='600'/>

Select finish:

<img src='./images/img_162.png' alt='img_162' width='600'/>

The autopatcher will launch, input:

```
a
```

<img src='./images/img_163.png' alt='img_163' width='600'/>

Then:

```
i
```

<img src='./images/img_164.png' alt='img_164' width='600'/>

The autopatcher will begin installing updates:

<img src='./images/img_165.png' alt='img_165' width='600'/>

Restart the Windows 98 Guest:

<img src='./images/img_166.png' alt='img_166' width='600'/>

When you login back in, the autopatcher will display as a blank screen. Click into the terminal:

<img src='./images/img_167.png' alt='img_167' width='600'/>

Press:

```
f
```

<img src='./images/img_168.png' alt='img_168' width='600'/>

Updates will proceed:

<img src='./images/img_169.png' alt='img_169' width='600'/>

Multiple restart cycles will be required. Eventually all the updates will be installed, press:

```
h
```

<img src='./images/img_170.png' alt='img_170' width='600'/>

The log file will display the updates installed:

<img src='./images/img_171.png' alt='img_171' width='600'/>

## Shared Folders

Although the options for shared folders shows up for the Windows 95 Guest. The map as a network drive in Windows guests does not do anything. Therefore you cannot view the shared folder:

<img src="https://github.com/user-attachments/assets/1129bd5e-c16b-4492-89f7-d70c3abf52d8" width="600"/>

This is likely because VMware tools did not include a driver for the PCI System Peripheral which controls the behaviour of Shared Folders for this Operating System.

## Installing Python

Python will be used as an example of installing a program on Windows 98 SE. The installer is available here:

* [Python 2.5.4](https://www.python.org/downloads/release/python-254/)
* [pyserial 2.1](https://sourceforge.net/projects/pyserial/files/pyserial/2.1/)
* [pywin32 2.18](https://sourceforge.net/projects/pywin32/files/pywin32/Build%20218/)

The pywin32, version 2.18 installer for Python 2.5 needs to be downloaded.

Drag and drop the applications to the Windows 98 Desktop:

<img src="https://github.com/user-attachments/assets/47f707f2-6fd1-462b-a6a3-157acb9e8cff" width="600"/>

Launch the `Python-2.5.4.exe`:

<img src="https://github.com/user-attachments/assets/ba86324c-d6cd-4f1f-b6d2-3370b46a63f4" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/fd43709c-25b2-4127-a97c-911a49391aab" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/57063334-5a5c-49a1-9932-3d0b392c6249" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/cc2f8fdf-754f-4fc6-a161-e372c2b4bf95" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/79a2b06f-bd74-4e36-bf91-5033d684d32f" width="600"/>

Go to Computer:

<img src="https://github.com/user-attachments/assets/f72b7b27-ec54-4a45-9708-4cfd69ece4d1" width="600"/>

Navigate to `C:`:

<img src="https://github.com/user-attachments/assets/3871357b-df55-4058-94d3-b9a1f5520b84" width="600"/>

Python is installed in the `Python25` folder:

<img src="https://github.com/user-attachments/assets/9fddd0da-f8f8-46b1-8b2b-d0848dbcf6a3" width="600"/>

Python is installed in this folder as a single environment:

<img src="https://github.com/user-attachments/assets/ae17f35b-0df4-4a9c-b5ec-d5156ab01697" width="600"/>

This version of Python did not support Python environments.

Standard libraries are found in the `lib` folder:

<img src="https://github.com/user-attachments/assets/8df884f8-5e85-4187-b1ef-f3594d0574cb" width="600"/>

Third-party libraries are installed to the `site-packages` folder:

<img src="https://github.com/user-attachments/assets/6a93e106-b08a-48f0-ad2f-377d4aad010b" width="600"/>

Note the absense of `pip`, the Python package manager which wasn't created yet.

<img src="https://github.com/user-attachments/assets/1f72ce4b-bb2a-496b-b087-9cb56c5cd8c6" width="600"/>

Packages were typically available in `.exe` format. Many packages relied on `pywin32` which can be installed:

<img src="https://github.com/user-attachments/assets/07c681e7-f34d-4b7b-8e11-fbbd6a68fa2a" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/e829323e-0e5c-41ec-87a5-28f05ec81c26" width="600"/>

The Python directory and corresponding `site-packages` directory is found. Select next:

<img src="https://github.com/user-attachments/assets/a2b6898d-44fa-4fd7-bd2b-451e9e5921e0" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/58af89b1-504c-449d-8078-1e960e7b474c" width="600"/>

Select finish:

<img src="https://github.com/user-attachments/assets/fb6fdf9c-1fa0-49a4-a10c-1188f4c283ff" width="600"/>

Repeat the same process for pyserial. The `serial` folder is now in `site-packages`:

<img src="https://github.com/user-attachments/assets/862379b8-5338-4d6d-87cd-e5a06dae1057" width="600"/>

This folder also contains the dependencies based up pywin.

The MSDOS prompt can be used to launch Python. Select Start → Programs → MS-DOS Prompt:

<img src="https://github.com/user-attachments/assets/d4d272f5-0e19-4e3c-8113-68ce0f76d485" width="600"/>

Launch Python using:

```powershell
C:\python25\python
```

Notice the prompt changes to `>>>`, the Python prompt. Test Python code can be input such as:

```python
print 'Hello World!'
```

<img src="https://github.com/user-attachments/assets/9bde7559-b34e-47d6-8917-1daeb0c230a2" width="600"/>

The pyserial library can be imported using:

```python
pyserial
```

<img src="https://github.com/user-attachments/assets/e43a2348-7121-4c33-9141-384827b163aa" width="600"/>

This works without any errors. To exit type in:

```python
exit()
```

<img src="https://github.com/user-attachments/assets/478c5514-3053-4e15-bf6f-6b287863eff5" width="600"/>

## USB Passthrough

Windows 98 had very limited support for a small subset of USB 1.1 devices, which consistent of a limited number of keyboard/mouse input devices and low capacity storage devices. DAQ devices were typically attached via Serial port.

## Serial Port Passthrough

Close the Windows 2000 VM. Attach a USB to Serial Port to the Window 11 Host PC:

<img src="https://github.com/user-attachments/assets/0ef84622-10c0-4bff-8cf1-9edf492137ba" width="600"/>

On the Windows 11 Host PC, right click the Start Button and select Device Manager:

<img src="https://github.com/user-attachments/assets/622bcb44-367d-42b6-aaf8-fea04bf18ebd" width="400"/>

Expand ports (COM & LPT). In this example, the USB Serial COM Port is COM3:

<img src="https://github.com/user-attachments/assets/7a133968-f0fc-4b26-9d75-2e4233f0dc1e" width="600"/>

Right click it and select properties:

<img src="https://github.com/user-attachments/assets/530c8c0b-ac42-4ad8-8ef4-7d1dbbe75aa5" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects:

<img src="https://github.com/user-attachments/assets/60686db0-b415-4ea7-a82e-a758329f4fb0" width="600"/>

The port number can be changed by selecting Advanced:

<img src="https://github.com/user-attachments/assets/3ac282d1-9dbc-4a17-b42f-bb3c9aab24f2" width="600"/>

In this case it will be left at port 3:

<img src="https://github.com/user-attachments/assets/04cd83bf-c91f-4ca1-84ae-f93b09257e10" width="600"/>

Open VMware Player and select Edit Virtual Machine Settings:

<img src="https://github.com/user-attachments/assets/e4594fd4-1464-41bb-90a2-4b37caea7c0b" width="600"/>

Under CD/DVD make sure the Windows 98SE Installation ISO is mounted and conencted at power on:

<img src="https://github.com/user-attachments/assets/2055cc9c-6200-4528-a7d7-c676021dced6" width="600"/>

Select Add...:

<img src="https://github.com/user-attachments/assets/efaab223-c358-4c2e-bb9e-834af426eec3" width="600"/>

Select Serial Port and Finish:

<img src="https://github.com/user-attachments/assets/df4ab69c-66be-4a2f-aa81-b1935fd80a48" width="600"/>

Select Connect at Power On. Autodetect is useful for a single port, but for multiple ports, it is more useful to select the serial Port indiviually. In this example COM3 will be used:

<img src="https://github.com/user-attachments/assets/c9873078-9dda-4388-a145-ec209840919c" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/47ce415a-ec42-4ab7-a7ab-eb2b37c83fa9" width="600"/>

Launch the Windows 98 SE Guest:

<img src="https://github.com/user-attachments/assets/229e7559-e75a-4391-bb87-c8b453012726" width="600"/>

The driver will install for the Serial Port will automatically install from the Windows 98 SE CD and prompt for a reboot.

Right click My Computer and select Properties:

<img src="https://github.com/user-attachments/assets/ecc86b14-82e8-4d2a-9605-296a376c4f1f" width="600"/>


<img width="960" height="899" alt="image" src="https://github.com/user-attachments/assets/3a77fa94-bc65-4c6b-9a70-b04818f154a0" />

Expand ports, note the Windows 11 COM3 is passed through to the Windows 2000 98 SE as COM1. COM1 is the expected port number for a number of legacy applications. Select Properties:

<img src="https://github.com/user-attachments/assets/6e02a387-82ff-4ea0-a263-1c047ad0db21" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects (consistent with the settings on the Windows 11 Host):

<img src="https://github.com/user-attachments/assets/a6bfdfb9-f723-4833-9ac2-626134b6911c" width="600"/>

Select Advanced:

<img src="https://github.com/user-attachments/assets/af09de9d-872a-475e-b6f5-cf6e1bebcbe0" width="600"/>

There is no way to change the port number in Advanced in this legacy version of Windows:

<img src="https://github.com/user-attachments/assets/388e72dc-0daf-417d-831a-542b9d668e68" width="600"/>

The Serial Port COM3 is now ready for use in the Windows 98 SE Guest VM. I don't have a device that connects via Serial Port, so will test the Serial Port using Python with pyserial. The Serial Port looks like the following:

<img src="https://github.com/user-attachments/assets/3e4d4398-1bfc-420e-8aa5-d5492f80402b" width="600"/>

|Pin Number|Name|
|---|---|
|1|Data Carrier Detect (CDC)|
|2|Received Data (RXD)|
|3|Transmit Data (TXD)|
|4|Data Terminal Ready (DTR)|
|5|Ground (GND)|
|6|Data Set Ready (DSR)|
|7|Request to Send (RTS)|
|8|Clear To Send (CTS)|
|9|Ring Indicator (RI)|

A Python script will be used which essentially transmits the data using pin 3 and then reads it back using pin 2. A Serial port can only read low `0` and high `1` signals, so any data sent via the Serial Port has to be in the form of a byte. In the basic American Standard for Information Interchange (ASCII), each ASCII character is an 8 bit binary sequence:

| Char | Decimal | Hex  | Binary    |
|------|---------|------|-----------|
| H    | 72      | 0x48 | 01001000  |
| e    | 101     | 0x65 | 01100101  |
| l    | 108     | 0x6C | 01101100  |
| l    | 108     | 0x6C | 01101100  |
| o    | 111     | 0x6F | 01101111  |
| (space) | 32   | 0x20 | 00100000  |
| S    | 83      | 0x53 | 01010011  |
| e    | 101     | 0x65 | 01100101  |
| r    | 114     | 0x72 | 01110010  |
| i    | 105     | 0x69 | 01101001  |
| a    | 97      | 0x61 | 01100001  |
| l    | 108     | 0x6C | 01101100  |
| \n   | 10      | 0x0A | 00001010  |

Open notepad:

<img src="https://github.com/user-attachments/assets/9eea59de-b12a-43dd-af57-f0d6888821c0" width="600"/>

Paste in the following code:

```python
import time
import serial

# Replace COM3 with your serial port
port = 'COM1'
baudrate = 9600

# Open the serial port
ser = serial.Serial(port, baudrate, timeout=1)

# Give the port some time to initialize
time.sleep(2)

# Test data
test_data = 'Hello Serial\r\n'

# Write data
ser.write(test_data)
print('Sent: %s' % test_data)

# Read back data
received = ser.read(len(test_data))
print('Received: %s' % received)

# Check if the loopback worked
if received == test_data:
    print('Serial loopback test passed!')
else:
    print('Serial loopback test failed!')

ser.close()
```

<img src="https://github.com/user-attachments/assets/00d59b12-307a-4474-9d6c-fb68ba3abcc9" width="600"/>

Select file → save as:

<img src="https://github.com/user-attachments/assets/647748b1-5212-44a3-b22b-4d84ff3fd7c5" width="600"/>

Save the file as `script.py` ensuring that save as type is All Files:

<img src="https://github.com/user-attachments/assets/ffe8b069-30ec-45e1-86db-979644bdafe3" width="600"/>

The script file is in Documents. Right click the script file and select Properties:

<img src="https://github.com/user-attachments/assets/7b98fc18-897a-4725-b13c-60e0de77d949" width="600"/>

<img src="https://github.com/user-attachments/assets/23c8da2f-acef-48fb-a4f0-a3a98dcb6b32" width="600"/>

Copy the file location:

<img src="https://github.com/user-attachments/assets/959b5afa-a733-4767-80a8-8edc1a77c27a" width="600"/>

The file path contains spaces:

```powershell
C:\My Documents\script.py
```

To prevent CMD from taking `C: My` and `Documents\script.py` as seperate command line arguments, double quotations much be used:

```powershell
"C:\My Documents\script.py"
```

Because this is a long path name, the DOS path is often more convenient:

```powershell
C:\MYDOCU~1\SCRIPT.PY
```

The Python script can be launched using:

```powershell
C:\Python25\python C:\MYDOCU~1\SCRIPT.PY\
```

With no pins connected, the following shows:

<img src="https://github.com/user-attachments/assets/e0842283-bc24-4526-a8e9-e92c91a986fe" width="600"/>

<img src="https://github.com/user-attachments/assets/41aa400b-4b09-48fc-98ca-ca7e4a47afc3" width="600"/>

With pins 2 and 3 connected, the following shows:

<img src="https://github.com/user-attachments/assets/0ec50a62-e408-469d-ae8f-493599320523" width="600"/>

<img src="https://github.com/user-attachments/assets/5e10b591-3e3a-45c1-9310-1fb46effbbb4" width="600"/>

The code works as expected and interfaces with the Serial Port which is passed through to the Windows 98 SE Guest VM from the Windows 11 Host PC.

## Parallel Port Passthrough

VMware can theoretically passthrough a physical parallel port. However, USB-to-parallel adapters are designed exclusively for printers and do not provide true parallel port functionality for other hardware. I do not have a parallel port printer available to test passthrough functionality.

## PCI/PCIe Card Passthrough

VMware does not support direct passthrough of PCI or PCIe cards to a guest virtual machine. Additionally, there are no USB adapters that replicate the functionality of PCI/PCIe expansion cards.

## Physical Media

The procedure to copy a CD/DVD to ISO has been examined already using ImgBurn. However most installation media does not need to be bootable and there is therefore no requirement to use the Advanced Bootable settings.

For a floppy disk. It can be converted into an image using WinImage:

* [WinImage](https://www.winimage.com/download.htm)

The USB to Floppy Drive driver should be installed on a Windows 11 Host however may not display as a drive in Computer:

<img src='./images/img_186.png' alt='img_186' width='600'/>

<img src='./images/img_187.png' alt='img_187' width='600'/>

If it doesn't input:

```
A:\
```

into the address bar:

<img src='./images/img_188.png' alt='img_188' width='600'/>

<img src='./images/img_189.png' alt='img_189' width='600'/>

<img src='./images/img_190.png' alt='img_190' width='600'/>

Select Disk and make sure Use Floppy A:\ is selected then select Read Disk:

<img src='./images/img_191.png' alt='img_191' width='600'/>

Select save:

<img src='./images/img_192.png' alt='img_192' width='600'/>

WinImage uses the format `.ima`:

<img src='./images/img_193.png' alt='img_193' width='600'/>

However VMware requires the file extension `.img`, rename the file and change the file extension:

<img src='./images/img_194.png' alt='img_194' width='600'/>

<img src='./images/img_195.png' alt='img_195' width='600'/>

Select ok:

<img src='./images/img_196.png' alt='img_196' width='200'/>

## Reapplying Patcher9x from a Bootable Floppy Drive

Patching Windows 98SE removed some of the patches made by patcher9x. 

The floppy disk created above is a copy of the `patcher9x-0.8.50-boot.ima` from the assets of the latest release. Download this floppy image and change the file extensions from `.ima` to `.img`:

* [patcher9x](https://github.com/JHRobotics/patcher9x/releases/)

Edit the Windows 98SE Guest Virtual Machine Settings:

<img src='./images/img_197.png' alt='img_197' width='600'/>

Select Add:

<img src='./images/img_198.png' alt='img_198' width='600'/>

Then Floppy Drive:

<img src='./images/img_199.png' alt='img_199' width='600'/>

And select this floppy drive image and then select ok:

<img src='./images/img_200.png' alt='img_200' width='600'/>

When the Windows 98SE Guest launches:

<img src='./images/img_201.png' alt='img_201' width='600'/>

It will boot to the Floppy Disk DOS program:

<img src='./images/img_202.png' alt='img_202' width='600'/>

Input:

```
patch9x
```

<img src='./images/img_203.png' alt='img_203' width='600'/>

Press `↵` to select the default Widnows system path:

<img src='./images/img_204.png' alt='img_204' width='600'/>

Input:

```
2
```

<img src='./images/img_205.png' alt='img_205' width='600'/>

and input:

```
y
```

<img src='./images/img_206.png' alt='img_206' width='600'/>

Press `↵` to exit:

<img src='./images/img_207.png' alt='img_207' width='600'/>

The next DOS prompt will display:

<img src='./images/img_208.png' alt='img_208' width='600'/>

The floppy disk image needs to be disconnected to prevent the WIndows 98SE from booting to the DOS program. Select Player → Removable Devices → Floppy → Settings:

<img src='./images/img_209.png' alt='img_209' width='600'/>

Uncheck Connected and Connected at Power On:

<img src='./images/img_210.png' alt='img_210' width='600'/>

Select Player → Power → Restart Guest:

<img src='./images/img_211.png' alt='img_211' width='600'/>

Select yes:

<img src='./images/img_212.png' alt='img_212' width='200'/>

When the Windows 98SE Guest boots, it will install the floppy drive driver using drive D:\ hich contains the Windows 98SE CD:

<img src='./images/img_213.png' alt='img_213' width='600'/>

The floppy drive image can be reselected now that Windows 98SE has booted:

<img src='./images/img_214.png' alt='img_214' width='600'/>

The floppy drive now shows up as `A:\` and can be selected:

<img src='./images/img_215.png' alt='img_215' width='600'/>

The DOS program can be launched:

<img src='./images/img_216.png' alt='img_216' width='600'/>

There is no need to run the program as Windows 98SE is already patched:

<img src='./images/img_217.png' alt='img_217' width='600'/>

Return to [VMware Installation Guide](../readme.md).

Python is just used as an example of a legacy program to run in a Windows 98 SE VM and not covered in detail in this tutorial. For details about using Python, see my other GitHub repository [Python Tutorials](https://github.com/PhilipYip1988/python-tutorials). Note Windows 98 SE is using Python 2 which has a significant number of changes from modern Python.
