
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

To change to the `C:` drive input:

```powershell
C:
```

<img src="https://github.com/user-attachments/assets/a9d9b6ad-a2ae-4b38-8572-195a8970e1de" width="600"/>






To make a directory called `win95` use the DOS command `MD`:

```powershell
MD win95
```

<img src="https://github.com/user-attachments/assets/8cea10d7-2925-4bef-9847-33ed029d8088" width="600"/>





To copy the files input from the CD `D:` to the virtual hard drive `C:` input:

```powershell
COPY D:\WIN95\*.* C:\WIN95
```

<img width="722" height="457" alt="image" src="https://github.com/user-attachments/assets/27d7a55b-d11f-439a-8635-a2506740b089" />


To begin the setup input:

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
