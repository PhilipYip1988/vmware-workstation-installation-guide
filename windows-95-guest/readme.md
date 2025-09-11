

## Configuring the Windows 95 Guest

Select File → New Virtual Machine:

<img src="https://github.com/user-attachments/assets/d8857004-a04f-49c6-9768-4d874b222734" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/81385eb4-a74e-4983-8ba7-c528bfcebb76" width="600"/>

Select the `Win95_OSR25_Patcher9x.iso` and select Open:

<img src="https://github.com/user-attachments/assets/8f82fa3b-d1a7-4f3d-9e2b-43ceb64de961" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/49af4614-c69d-490d-93c8-d2e93e6874fb" width="600"/>

The VM Name and Location will be shown. Note when used on a Windows 11 Host which is signed in with a Microsoft Account and integrated with OneDrive, the default location will be on OneDrive. The VM can be quite large and the location can be changed to local Documents by removing the OneDrive folder:

<img src="https://github.com/user-attachments/assets/35d0e326-43f0-4515-b967-194cecdc2071" width="600"/>

Note the name and location as these will be used later.

The default maximum size of the Windows 95 Guest is 8 GB which is a bit too restrictive. I recommend increasing this to 32 GB. Note the files on the Windows 11 Host won't be 32 GB but can be up to 32 GB if the Windows 98 Guests Virtual Drive is fully occupied with files. Windows 95 may struggle with a Virtual Drive >32 GB:

<img src="https://github.com/user-attachments/assets/d527249d-b092-441b-9c14-137b50cab396" width="600"/>

Select Customise Hardware:

<img src="https://github.com/user-attachments/assets/b87bb276-3cf7-4f67-81a7-d5b010924a42" width="600"/>

Change the memory to 256 GB:

<img src="https://github.com/user-attachments/assets/8e985def-698a-4930-8905-851f98aeb6a1" width="600"/>

Leave the number of processor cores at 1:

<img src="https://github.com/user-attachments/assets/ccc5d5de-c1f9-4014-ad97-4d299004a946" width="600"/>

Under CD/DVD, connect at power on should be checked and `Win95_OSR25_Patcher9x.iso` should already be selected:

<img src="https://github.com/user-attachments/assets/ba06e003-1d86-4241-9a97-df46a685942c" width="600"/>

Under Network Adaptor uncheck Connect at Power On. Windows 95 has reached end of life and is unsafe to use on the internet:

<img src="https://github.com/user-attachments/assets/d70a50f3-15bb-4c9b-a788-d2ea315c17a6" width="600"/>

Leave the Sound Card at the default setting:

<img src="https://github.com/user-attachments/assets/2155f89e-f283-4895-a10d-19a408563d98" width="600"/>

Leave display at the default setting:

<img src="https://github.com/user-attachments/assets/cf3f27df-526b-43da-920c-e6656b5f150e" width="600"/>

The bootable floppy disk needs to be added select Add:

<img src="https://github.com/user-attachments/assets/0610a23f-43ee-4e04-8f3c-169ebcad5f49" width="600"/>

Select Floppy Drive and Finish:

<img src="https://github.com/user-attachments/assets/30e02e44-0d4d-4179-924a-07253c75cc27" width="600"/>

Select Connect at Power On, Use Floppy Image File and Browse:

<img src="https://github.com/user-attachments/assets/d736989b-03e0-49ca-a502-ba326d5540e5" width="600"/>

Select `Boot Disk Windows 95.img` and select open:

<img src="https://github.com/user-attachments/assets/6f7bfa24-c7de-42f2-bff8-32736cb689d2" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/6ad3f877-18fc-4953-b5e9-8009da542535" width="600"/>

Some changes to the Virtual Machine COnfiguration file are recommended before beginning the installation. Uncheck Power on this Virtual Machine After Creation and select Finish:

<img src="https://github.com/user-attachments/assets/1100a495-2368-4730-a2c7-bae0675fc287" width="600"/>

## Windows 95 Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows 98 SE Guest is installed:

<img src="https://github.com/user-attachments/assets/c8cef617-546e-4c02-b68f-8b96653b45b0" width="600"/>

<img src="https://github.com/user-attachments/assets/d9938ca8-5f52-4a6e-b724-214071653905" width="600"/>

Look for the Windows 95.vmx file:

<img src="https://github.com/user-attachments/assets/3660a826-e295-475c-a298-36c397c769c9" width="600"/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/9a517f86-9c33-4abd-889c-b71f3ed7e021" width="600"/>

The option `bios.bootDelay` for example will change the time the Windows98 SE Guest Virtual BIOS displays before selecting the default boot option giving more time to select the option to boot from CD/DVD. This line can be removed post-installation, returning to the default value.

Press Ctrl+f to begin a search for an option for example bios.bootDelay:

<img src="https://github.com/user-attachments/assets/5981482a-b3b1-430c-8966-96a7a14b1982" width="600"/>

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/ac7a3851-452e-481c-a7bb-5ae4db89a13d" width="600"/>

### 12th-14 Generation Processors

On a 12th–14th Generation Intel processor, certain legacy settings may need to be configured to run older guest operating systems such as Windows 95.

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

<img src="https://github.com/user-attachments/assets/8a0eb120-62ae-4fef-b5cc-70aec7e91e00" width="600"/>

## Windows 95 Setup

Select the Windows 95 Guest and select Play. Windows 95 will boot from the floppy disk:

<img src="https://github.com/user-attachments/assets/e34d47a3-099e-43e1-990a-d6728a811014" width="600"/>

Select option `1` Load NEC IDE CDROM driver and press `↵`:

<img src="https://github.com/user-attachments/assets/042e9c67-79a5-41cf-b15f-cc0a2928885e" width="600"/>

The DOS prompt will display:

<img src="https://github.com/user-attachments/assets/03b54b34-2053-483f-b940-6d8df5c565b8" width="600"/>

The DOS command `FDISK` creates a partition on the Drive, it can be started by inputting:

```powershell
FDISK
```

and press `↵`:

<img src="https://github.com/user-attachments/assets/b982e6fc-d647-4d21-99fd-b6c0b85289fe" width="600"/>

Input `Y` to enable large disk support and press `↵`:

<img src="https://github.com/user-attachments/assets/1b60f026-ba87-48be-bbbe-c8124d54f10a" width="600"/>

Select option `1` Create DOS Partition or Logical DOS Drive and press `↵`:

<img src="https://github.com/user-attachments/assets/2c1fb6f2-8269-4019-9d5d-51206445c3d8" width="600"/>

Select option `1` Create Primary DOS Partition and press `↵`:

<img src="https://github.com/user-attachments/assets/47e14e6e-8521-4723-9ae4-70810cd7059a" width="600"/>

To make a partition the maximum available size input `Y` and press `↵`:

<img src="https://github.com/user-attachments/assets/dd573535-2a93-4c9c-85b3-b9ff1c9a66ed" width="600"/>

To exit the DOS program `FDISK` press `Esc`:

<img src="https://github.com/user-attachments/assets/4a018c84-e555-4ff3-846d-349baaaa8625" width="600"/>

A new prompt from the bootable floppy disk will display:

<img src="https://github.com/user-attachments/assets/658af53e-3424-4d94-8ac0-1c3b323be95d" width="600"/>

Select Player → Send `Ctrl`, `Alt` + `Del`:

<img src="https://github.com/user-attachments/assets/cb21bb37-0ad6-4243-a504-bb5ebb175d1e" width="600"/>

Windows 95 will boot from the floppy disk again. Select option `1` Load NEC IDE CDROM driver and press `↵`:

<img src="https://github.com/user-attachments/assets/ce7fcc2a-85af-4961-abb1-4350ad706d6e" width="600"/>

The DOS prompt will display:

<img src="https://github.com/user-attachments/assets/03b54b34-2053-483f-b940-6d8df5c565b8" width="600"/>

The DOS command `FORMAT` formats the drive, and the option `/S` copies the commands MSDOS.SYS and COMMAND.COM making the hard drive bootable:

```powershell
FORMAT C: /S
```

<img src="https://github.com/user-attachments/assets/617cb524-4185-4e5f-bce9-12e0e9111772" width="600"/>

To proceed with the format input `Y` and press `↵`:

<img src="https://github.com/user-attachments/assets/d1e9fa27-5d17-45a0-b86a-482858a82763" width="600"/>

Press `↵`:

<img src="https://github.com/user-attachments/assets/2f31bd0b-1a31-4f58-8fd7-556850c13b73" width="600"/>

A new prompt from the bootable floppy disk will display:

<img src="https://github.com/user-attachments/assets/4835aecd-8a00-4e87-afd3-95b52edb24b0" width="600"/>

Currently `A:` is a DOS bootable floppy drive and has drivers to view the CD drive `D:` which contains the Windows 95 Installation Files. Installation is onto the HDD `C:` which becomes the OS Boot Drive. During installation there is a prompt for a restart and an instruction to remove the floppy drive. This boots from the OS boot drive which doesn't have the driver for the CD drive `D:`. Unfortunately by default the setup continues to look for the optical drive and fails to install fails leading to an incomplete/faulty installation.

To rectify this, the setup files should be copied to the `C:` drive from `D:` and the setup should be launched from `C:`. To change to the `C:` drive input:

```powershell
C:
```

<img src="https://github.com/user-attachments/assets/a9d9b6ad-a2ae-4b38-8572-195a8970e1de" width="600"/>

The DOS command `MD` will make a directory called `win95`:

```powershell
MD win95
```

<img src="https://github.com/user-attachments/assets/8cea10d7-2925-4bef-9847-33ed029d8088" width="600"/>

Since currently we are on `C` this is `C:\win95`. The DOS command `COPY` can be used to copy files from the CD `D:\win95` to destination  `C:\win95`. `*.*` is a wildcard where the first `*` essentially means any file name and the second `*` is the file extension:

```powershell
COPY D:\win95\*.* C:\win95
```

<img src="https://github.com/user-attachments/assets/27d7a55b-d11f-439a-8635-a2506740b089" width="600"/>

225 files should be copied:

<img src="https://github.com/user-attachments/assets/5cfd416d-e148-4328-9748-64d059b0dea5" width="600"/>

The `setup` program can be launched from the CD with the flag `IS` meaning install:

```powershell
C:\win95\setup /IS
```




Press `↵`:



Select Continue:



Select Yes:



Select next:



Select next:



Select custom:



Input the product key and select next:



Input your username and select next:



Under components, leave the defaults and select next:



Under Network Configuration, select Add:



Select Adaptor and select Add:



To the right select Advanced Micro Devices (AMD) and to the left select AMD PCNET Family Ethernet Adapter (PCI&ISA). Then select OK:



Then select next:



Then enter the Computer Name, Workgroup Name and Computer Description and select next:



Select next:



Select No, I do not want a startup disk and select next:



Select next:



Select finish:



Select player → removable devices → floppy → settings:


Uncheck Connected and Connect at Power On and select OK:



Select OK:



Input a user name and select ok:



Press ok and ok:



Select the time zone and select apply and then ok:



Select cancel:



Select OK:



Select OK:



Select next:



Select your language and select next:



The install will stall at Installing RealPlayer at 78 %. Select Player → Send `Ctrl`, `Alt` + `Del`:



Select R32msie4 and select End Task:



Select End task:



Right click the desktop and select properties:



Select the web tab and uncheck View my Active Desktop as a Web Page:



Select apply, ok and no. Select ok and no:


Right click Computer and select Properties:



Select Device Manager:




Expand Other Devices:




Remove Other Devices:



Scan Add New Hardware Wizard:



PCI Bridge
PCI Multimedia Devices
PCI System Peripheral
Other Devices



Install VMware Tools 

Select complete




Select Advanced Properties:



Select Change:



Standard Display Type will be checked to the left and to the right Standard PCI Graphics Adaptor (VGA) will be checked:




Select Have Disk:



Input:

```
C:\Program Files\VMware\VMware Tools\Drivers\video
```

Select VMware SVGA II and select OK:




The Windows 95 Setup will say insert disk. Select OK and then select the `vmx_svga.drv`:



Select OK. Select Apply and then OK:



After restarting, right click the desktop and select Properties. Increase the resolution. To the left select standard monitor type, to the right select Plug and Play Monitor:



Select apply, ok and yes:



Drag and drop works, the soun blaster driver can be dragged over and installed:









### USB Storage Driver Win95 OSR 2 - Unofficial Bundle

* [VOGONS: USB Storage Driver Win95 OSR 2 - Unofficial Bundle](https://vogonsdrivers.com/getfile.php?fileid=1813&menustate=0&utm_source=chatgpt.com) 

### Windows 95B/95C OSR 2.0/2.1/2.5 Service Pack 1 (SP1) Version 1.05 

Go to [MDGX](https://www.mdgx.com/). Press `Ctrl` + `f` and search for: 

```
Unofficial Windows 95B/95C OSR 2.0/2.1/2.5 Service Pack 1 (SP1) 1.05 
```

### VMware Tools

[VMware Tools 3.5.0](https://archive.org/details/VMwareToolsforWin95RTM_OSR1?utm_source=chatgpt.com)


### Creative Labs SB-PCI64v Sound Card Version 5.13d

[Cnet: Creative Labs SB-PCI64v Sound Card Version 5.13d](https://download.cnet.com/creative-labs-sb-pci64v-sound-card-version-5-13d/3000-2110_4-107804.html)






https://github.com/joncampbell123/dosbox-x/wiki/Guide:Installing-Windows-95/c6894fd3c687213e3466603941f4b0490c42b898

https://retrosystemsrevival.blogspot.com/2018/05/windows-95-osr2x-service-pack-10x.html

https://winworldpc.com/product/windows-95/patches

* Win95 Comctl32 Leak Fix
* Winsock 2 update
* DCOM95 OLE Update
* Microsoft Direct 8.0

https://winworldpc.com/product/internet-explorer/ie-55

* Internet Explorer 5.51.4807.2300

DirectX 8.0

https://winworldpc.com/product/windows-95/patches

Windows Media Player 7.1

https://archive.org/details/mp71_20191017





https://www.vogons.org/viewtopic.php?t=36770














QuickTime 4.1.2 (optional, for old media)

💻 Runtimes

Visual Basic runtimes (VB4, VB5, VB6)

Visual C++ runtimes (MFC42, MSVCP60, etc.)

🔧 Drivers (VMware)

VMware Tools for Win9x (gives you SVGA graphics + mouse integration)

Sound Blaster 16 driver (Creative’s official Win95 SB16 driver)

AMD PCnet Ethernet driver (usually included, but install AMD’s NDIS driver if needed)
















System Patches (must-have)




Windows Installer 2.0

Internet Explorer 5.5 SP2 (last IE for Win95, brings modern system DLLs)

🎮 Graphics / Multimedia

DirectX 8.0a (last official for Win95, covers everything from earlier versions)

Windows Media Player 7.1

QuickTime 4.1.2 (optional, for old media)

💻 Runtimes

Visual Basic runtimes (VB4, VB5, VB6)

Visual C++ runtimes (MFC42, MSVCP60, etc.)

🔧 Drivers (VMware)

VMware Tools for Win9x (gives you SVGA graphics + mouse integration)

Sound Blaster 16 driver (Creative’s official Win95 SB16 driver)

AMD PCnet Ethernet driver (usually included, but install AMD’s NDIS driver if needed)
