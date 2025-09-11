
## Windows 95 Setup

Select option `1` and press `↵`:



Input:

```powershell
FDISK
```



Input `Y` and press `↵`:



Select option `1` and press `↵`:



Select option `1` and press `↵`:



Input `Y` and press `↵`:



Press `Esc`:



Select Player → Send `Ctrl`, `Alt` + `Del`:




Select option `1` and press `↵`:



Input:

```powershell
FORMAT C: /S
```



Input `Y` and press `↵`:




Press `↵`:




To change to the `C:` drive input:

```powershell
C:
```




To make a directory called `win95` input:

```powershell
MD win95
```



To copy the files input from the CD `D:` to the virtual hard drive `C:` inputwin95:

```powershell
COPY D:\WIN95\*.* C:\WIN95
```



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
