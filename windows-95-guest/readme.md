# Windows 95 Guest

Step-by-step guides for VMware Workstation 17.6.4, focused on running Windows 95 in a virtual environment. Due to the operating system’s age, shared folders and USB passthrough are not functional, and serial port passthrough is limited, typically restricted to COM1. Windows 95 support is highly limited, so users often prefer Windows 98 SE for better hardware compatibility and device support. These guides are useful for researchers, lab technicians, and IT staff needing to run legacy software and control older laboratory instruments on modern systems.

## Notes

VMware Workstation Player 17.6.4 has Windows 95 as an option for a Virtual Machine. However Windows 95 is regarded as an ancient legacy Operating System and isn't tested by Broadcom. Modern processors are significantly faster than the processers available when WIndows 98 SE was released. As a consequence the timing for some operations is divided by 0 and there is a divide-by-zero error that needs to be addressed using patcher9x.

A Windows 95 bootable floppy disk needs to be used with DOS commands to partition and format the hard drive and start the setup from CD. Usually the installation is smoother if the setup files are copied from the CD to the hard drive and the setup is invoked from these setup files. This overcomes problems when the setup reboots from the hard drive and the cannot view the CD because the CD driver which is on the floppy drive is not available. Starting the setup file from DOS invokes the Windows Setup as a GUI.

VMware Tools 12.5.3 which comes with VMware workstation player doesn't support Windows 95. VMware Tools WinPre2k is the last version of VMware Tools to support Windows 98SE and should be downloaded seperately as an ISO. This ISO should be mounted in the VM so they can be installed manually.

On modern hardware with a 12th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

The first setting allows the CPU to optimise the VM performance, the VM may be very slow without this setting. The second setting prevents use of a memory management unit that Windows 95 doesn't understand and can lead to a Blue Screen of Death (BSOD). The third setting prevents VMware from using Vulkan for rendering, which isn't supported by Windows 95 and often leads to black screens. The last two settings prevent Windows 95 from seeing unsupported CPU features which Windows 95 doesn't understand and can lead to a Blue Screen of Death (BSOD).

## Downloads

### Windows 95 Floppy IMG and CD ISO

Note the Windows 95 floppy disk hosted by WinWorld lacks the CD driver required to install Windows 95 OSR 2.5. They recommend using a Windows 98 Floppy Disk but I had a better experience using the floppy disk from Archive.org:

* [WinWorld: Windows 95 OSR 2.5 and Microsoft Plus](https://winworldpc.com/product/windows-95/osr-3)
* [Archive.org: Windows 95 OSR 2.5 Boot Disk](https://archive.org/details/win-95-osr-25_202103)

### Windows 95 Updates

* [Intel Chipset INF Software v 2.80](https://www.dell.com/support/home/en-uk/drivers/driversdetails?driverid=r26343)
* [VOGONS: USB Storage Driver Win95 OSR 2 - Unofficial Bundle](https://vogonsdrivers.com/getfile.php?fileid=1813&menustate=0&utm_source=chatgpt.com) 
* [AMDK6 Update](https://winworldpc.com/product/windows-95/patches)
* [Osr2sp: Unofficial Service Pack](https://www.mdgx.com/spx/OSR2SP1.EXE)
* [Internet Explorer 5.5](https://winworldpc.com/product/internet-explorer/ie-55)
* [Creative Labs SB-PCI64v Sound Card Version 5.13d](https://www.dell.com/support/home/en-uk/drivers/driversdetails?driverid=r20634)

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

## Patching the Installation ISO

The Windows 95 installation errors out on a VM on a modern computer:

> This program has performed an illegal operation and will be shut down.

> If the problem persists, contact the program vendor

Essentially the processor is too fast and windows 95 expects to wait more than "zero seconds" for an operation. Therefore the WIndows 95 installation media needs to be patched with patcher9x. Extract patcher9x:

<img src="https://github.com/user-attachments/assets/ea0c757a-24e6-409a-b3e7-b1bcfc15cf28" width="600"/>

Extract the Windows 95 OSR 2.5 ISO:

<img src="https://github.com/user-attachments/assets/8df9a596-5c30-4620-82ab-7d7de8ae39d5" width="600"/>

Select Extract:

<img src="https://github.com/user-attachments/assets/e768cf02-1057-4e72-a5d5-3e4c4bb6c4b2" width="600"/>

Navigate to the extracted ISO:

<img src="https://github.com/user-attachments/assets/34a02c5a-96ba-4cb9-999b-30f693bb346a" width="600"/>

Open the ISO file in Windows Explorer:

<img src="https://github.com/user-attachments/assets/7fcc0933-8795-4e26-96e9-d6971b3ac58b" width="600"/>

Select Open:

<img src="https://github.com/user-attachments/assets/295d79e3-fb5f-4fb7-94d6-ebd78038613f" width="600"/>

Select all the files and select Copy:

<img src="https://github.com/user-attachments/assets/c2de2269-e07a-4fbb-8642-f560599e9181" width="600"/>

Create a new folder called CD:

<img src="https://github.com/user-attachments/assets/89dee5cb-5703-4b63-9edd-b0ed35df8dfa" width="600"/>

Select Paste:

<img src="https://github.com/user-attachments/assets/8ec24841-d88b-4f36-b266-d69f0102fe76" width="600"/>

Delete the old folders:

<img src="https://github.com/user-attachments/assets/25b01e28-3287-4ecb-8570-956192a07b46" width="600"/>

Right click the patcher9x and select Extract:

<img src="https://github.com/user-attachments/assets/a430f3e5-96db-47e9-93ef-f98622a1e728" width="600"/>

Select Extract:

<img src="https://github.com/user-attachments/assets/39cc98c2-640b-4986-8c0f-5f6e47c68894" width="600"/>

Launch `patcher9x`:

<img src="https://github.com/user-attachments/assets/fc7e0858-140f-4a14-bfab-f321e22a1c53" width="600"/>

Select More Info:

<img src="https://github.com/user-attachments/assets/ffd3d1fb-6a3a-4479-a481-7cfa4624dfa2" width="600"/>

Select Run Anyway:

<img src="https://github.com/user-attachments/assets/4ba5972d-48a3-4e4e-af4f-75b56217680f" width="600"/>

Go to the copy of the extracted CD and look at the win95 folder:

<img src="https://github.com/user-attachments/assets/103259f2-5acc-42bd-b498-9c6f432feed2" width="600"/>

Select copy as path:

<img src="https://github.com/user-attachments/assets/3137f2bd-cb96-42b1-837e-f9ec51b8ac4d" width="600"/>

Paste in the path:

<img src="https://github.com/user-attachments/assets/f8a0fb44-d1bb-4a3f-99b9-7c1ce24ce8c6" width="600"/>

And remove the quotations:

<img src="https://github.com/user-attachments/assets/ce4b1def-b0d8-4c99-a254-c8409fb9c6b1" width="600"/>

Select `4`:

<img src="https://github.com/user-attachments/assets/713267d2-d306-4a3c-897c-e345ba652bcf" width="600"/>

Select `Y`:

<img src="https://github.com/user-attachments/assets/6ae83e6d-9d0c-4057-9bf5-0206eba88f13" width="600"/>

Press `↵` to exit:

<img src="https://github.com/user-attachments/assets/62d25de8-c1de-409b-8946-60c87efb35c1" width="600"/>

The `patcher9x` folder can be deleted:

<img src="https://github.com/user-attachments/assets/4614d2e1-eec9-4cab-9e3a-d5814a6c8f99" width="600"/>

Select create image from files/folder:

<img src="https://github.com/user-attachments/assets/91b909ce-6b29-4d09-8c0e-132b61dc90b0" width="600"/>

Select the open folder icon:

<img src="https://github.com/user-attachments/assets/7d225a3c-1e40-43c5-936a-92df0c9744f9" width="600"/>

Select the CD folder:

<img src="https://github.com/user-attachments/assets/c506ba61-602d-4d63-a8c5-a8330cc576ef" width="600"/>

Select the destination filder:

<img src="https://github.com/user-attachments/assets/2da8c47a-9fa7-41ba-a8bb-db060b87fb1c" width="600"/>

Name the ISO and select save:

<img src="https://github.com/user-attachments/assets/affca1bc-b7b3-403b-a467-0933689ff097" width="600"/>

Select the folder to Image button:

<img src="https://github.com/user-attachments/assets/e5c24d75-aa39-4c33-8d53-058f042d33c7" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/3e257d20-c88c-4401-9281-aa7eaee1a452" width="300"/>

Select yes:

<img src="https://github.com/user-attachments/assets/68a22136-1c72-41c0-b1e3-e6f2c3fe5ca0" width="300"/>

Select ok:

<img src="https://github.com/user-attachments/assets/356e2c8f-c376-433a-807c-579ecb2eff7a" width="300"/>

Select ok:

<img src="https://github.com/user-attachments/assets/e845484e-16c1-45d4-a178-9a597617a2d2" width="300"/>

Delete old folders:

<img src="https://github.com/user-attachments/assets/60a8ab75-5826-4c56-ab68-19eb46534420" width="600"/>

The Boot Floppy Disk and Installation CD are now ready:

<img src="https://github.com/user-attachments/assets/3d6eaf25-b873-4df4-b726-9493f88be762" width="600"/>

## Creating an Update ISO

Download the Updates:

<img src="https://github.com/user-attachments/assets/5fdee15c-7fb3-44de-9408-536203f117a2" width="600"/>

Extract all the files and delete old zipped files:

<img src="https://github.com/user-attachments/assets/2c1b9013-3076-47e7-bcbb-524affafae89" width="600"/>

Use ImgBurn to create an ISO of the Update folder as instructed above. Delete old files:

<img src="https://github.com/user-attachments/assets/a3a64186-f6f7-441c-a8c5-5d4e8f07de48" width="600"/>

You should have the following 3 ISOs and boot disk:

<img src="https://github.com/user-attachments/assets/12137ea9-17c1-4478-849e-1423e725ea00" width="600"/>

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

<img src="https://github.com/user-attachments/assets/7e5ca2a4-0d41-4592-b423-b130e6fd8d2a" width="600"/>


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

<img src="https://github.com/user-attachments/assets/9710439b-6649-4c24-9aa4-7fe1ebfc1cda" width="600"/>

Since currently we are on `C` this is `C:\win95`. The DOS command `COPY` can be used to copy files from the CD `D:\win95` to destination  `C:\win95`. `*.*` is a wildcard where the first `*` essentially means any file name and the second `*` is the file extension:

```powershell
COPY D:\win95\*.* C:\win95
```

<img src="https://github.com/user-attachments/assets/7d65613b-b761-4a7a-abab-4a01655426b7" width="600"/>


225 files should be copied:

<img src="https://github.com/user-attachments/assets/927efb0a-8612-4b8c-b567-d28067697be7" width="600"/>


The `setup` program can be launched from the CD with the flag `IS` meaning install:

```powershell
C:\win95\setup /IS
```

<img src="https://github.com/user-attachments/assets/c322dffa-7095-4196-aefc-f41f106c5431" width="600"/>

Select Continue:

<img src="https://github.com/user-attachments/assets/7c6d8346-de50-499a-a26d-b4fc3f39e478" width="600"/>

Select Yes:

<img src="https://github.com/user-attachments/assets/69345071-1916-465e-b6f3-8e20da67214d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/ee1c31b7-a942-4404-9597-c5409987ef78" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/ffe9b4dc-0f25-422c-82d5-056d772435d1" width="600"/>

Select custom and enxt:

<img src="https://github.com/user-attachments/assets/f2a96bfd-4d2b-42d7-a5b4-1aa038a69c95" width="600"/>

Input the product key and select next:

<img src="https://github.com/user-attachments/assets/af04f5af-2699-4983-8488-476dadc5f53d" width="600"/>

Input your username and select next:

<img src="https://github.com/user-attachments/assets/7b1ba322-7172-4b64-8264-732483cbb1b4" width="600"/>

Select Yes and next:

<img src="https://github.com/user-attachments/assets/abdc09a1-3352-4489-a3e6-6d49214bf2fc" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/1d4ab32e-cb9e-45fc-a3a4-6ed3c4efd6ab" width="600"/>

Under components, leave the defaults and select next:

<img src="https://github.com/user-attachments/assets/70945477-8478-4ff3-b183-084f7e661678" width="600"/>

Under Network Configuration, select Add:

<img src="https://github.com/user-attachments/assets/3cd954d3-7974-447b-abb0-93c8ae0d6358" width="600"/>

Select Adaptor and select Add:

<img src="https://github.com/user-attachments/assets/9764dcbd-e3f1-4230-be20-c010552b5822" width="600"/>

To the right select Advanced Micro Devices (AMD) and to the left select AMD PCNET Family Ethernet Adapter (PCI&ISA). Then select OK:

<img src="https://github.com/user-attachments/assets/19601514-37bc-4530-8029-09c008d3b1b4" width="600"/>

Select Add:

<img src="https://github.com/user-attachments/assets/e146cf87-032c-4e19-b668-dd6bf811da42" width="600"/>

Select Protocol and select Add:

<img src="https://github.com/user-attachments/assets/e9ea7414-a348-42f7-bee3-047c8910c445" width="600"/>

To the right select Microsoft and to the left select TCP/IP:

<img src="https://github.com/user-attachments/assets/a75ddc22-0bfd-4d03-9000-aef42fa2cc61" width="600"/>

Then select next:

<img src="https://github.com/user-attachments/assets/c5d9779f-43d9-4252-a097-6adee922884a" width="600"/>

Then enter the Computer Name, Workgroup Name and Computer Description and select next:

<img src="https://github.com/user-attachments/assets/f3cdf280-bf2d-4e70-948f-be0eeeeec6f3" width="600"/>

Select the keyboard layout and select change:

<img src="https://github.com/user-attachments/assets/4e30a81c-914a-466b-b21e-11edebc965bd" width="600"/>

Select your keyboard layout and select ok:

<img src="https://github.com/user-attachments/assets/46ba977c-4b5e-45ed-97d4-58c4658fc93d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/9b8b8e68-e064-4472-aed6-cb41c2b618a0" width="600"/>

Select No, I do not want a startup disk and select next:

<img src="https://github.com/user-attachments/assets/a3cfd3e9-073a-42f7-a0ba-81f33458b8c0" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/3a2259d1-d1b6-4047-ac3c-a0e0094f2815" width="600"/>

Select finish:

<img src="https://github.com/user-attachments/assets/77b0e385-6ae6-4bba-b1d3-e51f59fdd650" width="600"/>

An instruction will display to remove the floppy disk:

<img src="https://github.com/user-attachments/assets/f652321c-8fa1-46f2-8ce4-708a182a1d09" width="600"/>

Select player → removable devices → floppy → settings:

<img src="https://github.com/user-attachments/assets/56fee8cd-8c11-4662-affb-4a8618d066aa" width="600"/>

Uncheck Connected and Connect at Power On and select OK:

<img src="https://github.com/user-attachments/assets/2162666c-ba20-4676-afd0-671481d66bef" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/4aa7ff82-72f5-4bd6-b24f-34cd4d4db76a" width="600"/>

Input a user name and select ok:

<img src="https://github.com/user-attachments/assets/de4d70b4-8191-4c84-b542-05ef8da8d615" width="600"/>

Press ok:

<img src="https://github.com/user-attachments/assets/79c606d7-68d2-4ff5-b7db-3711b7661cd5" width="600"/>

Select the time zone and select apply:

<img src="https://github.com/user-attachments/assets/67f34815-0ac8-41ca-bbb9-701f110ea734" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/cb6f8c8e-672c-4fc3-960a-888a1aa11d6c" width="600"/>

Select cancel:

<img src="https://github.com/user-attachments/assets/11f3aa32-13fc-40fa-b7a9-5d8130b14ac6" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/2d7f8775-4c12-4bb9-b6e2-f947adc4d91f" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/eb214191-1abd-48dc-b84c-badfbd27935f" width="600"/>

The following warning displays because Windows 95 is offline, select No:

<img src="https://github.com/user-attachments/assets/555c9892-e073-49a9-a81d-e4f074d1cb42" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/d64e0bb5-4a53-481b-9a64-6fbef6667642" width="600"/>

Select your language and select next:

<img src="https://github.com/user-attachments/assets/29c94ecb-fe16-4790-8b12-87fbdb1b4c5d" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/3f94572c-f61f-470f-943e-e25c5d0343a9" width="600"/>

## Backing up the Windows 95 Guest

Select Start → Shut Down:

<img src="https://github.com/user-attachments/assets/4da41325-fd44-4036-a082-6990a950ccf5" width="600"/>

Select Shut Down and then OK:

<img src="https://github.com/user-attachments/assets/250b676d-adc6-42ba-a1c1-6a399435114d" width="600"/>

On the Windows 11 Host or Ubuntu 24.10 Host, navigate to Documents and the Virtual Machines folder. Copy the Windows 95 folder to back it up:

<img src="https://github.com/user-attachments/assets/eb042994-e9f4-4c26-80d7-62a165eb6b63" width="600"/>

## Installing Windows 95 Updates and Drivers

Right click Computer and select Properties:

<img src="https://github.com/user-attachments/assets/6f8d912d-c739-4791-8020-c314151ffed9" width="600"/>

Select Device Manager:

<img src="https://github.com/user-attachments/assets/9e645c5a-8424-4505-befb-51aced3eda9b" width="600"/>

The Device Manager has:

* Standard PCI Graphics Adaptor
* PCI Bridge
* PCI Multimedia Devices
* PCI System Peripheral
* Other Devices

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/3e6b2f86-85ae-49a8-911e-558f5b5827f0" width="600" />

Select Browse:

<img src="https://github.com/user-attachments/assets/72050d17-7778-4b3d-8472-09d719c35f70" width="600"/>

Select the `Updates.iso` and select Open:

<img src="https://github.com/user-attachments/assets/28622c07-b9c3-44e6-831f-da66aca1feaa" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/ab39cd6d-f5af-47fc-9ae4-04bba3b7eddf" width="600"/>

Open the Updates CD:

<img src="https://github.com/user-attachments/assets/2c9603c3-5a07-4090-a644-8fd72c0029fc" width="600"/>

Select the `infinst_280_win32` folder:

<img src="https://github.com/user-attachments/assets/d63f1dbb-b70b-42a1-8cef-d59156645b85" width="600"/>

And `Disk1`:

<img src="https://github.com/user-attachments/assets/432f805a-5e20-4adf-9900-145b201696a7" width="600"/>

Select the `Setup`:

<img src="https://github.com/user-attachments/assets/00acc772-28b3-43c0-a048-8f9ce84ef7a8" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/d635af41-d5f4-46ba-a046-58ff2dec79fa" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/7a2b60a5-9b51-43f8-8fe8-ca665c3723ee" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/f8ae77d9-8b12-4554-97cd-7b6dd8acae09" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/1ad40702-dada-4c39-b731-1e9f1cb2f734" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/a2b8d65f-6303-4208-bdfc-1202addc69c5" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/a8718d16-4615-4b12-ab7a-bd7d4652c342" width="600"/>

Select finish:

<img src="https://github.com/user-attachments/assets/3c1774b1-f6c4-4f0d-af96-42c39ee330b7" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/d658afb1-93b0-4bea-a702-5b5573d06e0a" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/2c618e93-3da2-4f57-95f9-9cac5b42966a" width="600"/>

Select the `xusbsupp` folder:

<img src="https://github.com/user-attachments/assets/4b2c5af1-f8a0-4ca2-b445-bba42c34409b" width="600"/>

Install the `Xusbsupp` application:

<img src="https://github.com/user-attachments/assets/435060a7-e3a1-4655-a9c7-39a12be33d46" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/825acb1f-fefd-4729-8aed-c5da31e71a4f" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/3a5acd48-14d7-4b94-bdeb-8e57e56cebb7" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/e990480f-796a-47b0-b95b-672469d1ce16" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/2e6b0dfc-9ce8-48bd-888a-029f4b56cb61" width="600"/>

Go to the `AMDK6 Update` folder:

<img src="https://github.com/user-attachments/assets/1118e2ee-4acd-42fd-9d49-de17cbc0c8ae" width="600"/>

Launch the `amdk6upd` application:

<img src="https://github.com/user-attachments/assets/365f0add-a10a-43bb-bb7a-ec923069653a" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/77195094-5ab8-4041-a113-ef5e0d6bf612" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/9ba931fa-1cfb-4ab6-b12d-7fc7d425e9b5" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/ec1e9a0d-5153-4fa6-b667-6b8f0ae143d6" width="600" />

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/47890bb9-07a4-411e-8d16-039c785b3841" width="600"/>

Launch the unofficial service pack `Osr2sp1`:

<img src="https://github.com/user-attachments/assets/202db583-a072-42b0-9516-5cdb0cc53764" width="600" />

Select Main Updates only:

<img src="https://github.com/user-attachments/assets/76bceda2-ebdb-47df-b99a-21306977efe1" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/32c1d0f9-0322-49c7-b91a-95485ef2e3dd" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/60df8657-64fb-4ef5-8269-2d6ea63937da" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/22f8675e-8e66-4783-842a-ae1225c347c5" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/359c8308-db18-42cc-9355-82bc28796f24" width="600"/>

Launch the unofficial service pack `Osr2sp1` again and now select the following:

* Adaptec ASPI Drivers
* Unimodem Drivers
* Windows Management Instrumentation 1.3
* MS System Information 4.0 & System Tools

<img src="https://github.com/user-attachments/assets/c35c07bf-f233-4898-b1d5-320c068b36c5" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/599d1016-39a1-4b5c-a559-435c60e54ecc" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/0d19bffb-2644-40b8-97a2-f3b0422857ed" width="600"/>

Launch the unofficial service pack `Osr2sp1` again and now select the following:

* Winsock

<img src="https://github.com/user-attachments/assets/baadbf98-bea6-4985-9827-b742e96fa8bd" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/86833285-9b53-4dc2-acba-37a7d7d2f748" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/feaaa686-de30-4dec-80ff-d064d3ff6342" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/84e71de6-8a31-4dbe-b61c-b9667d92d458" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/359c8308-db18-42cc-9355-82bc28796f24" width="600"/>

The Internet Explorer setup `ie5setup` extracts files in the current directory and therefore cannot be ran from the CD which is read only. Copy and paste the `ie5setup` to the desktop:

<img src="https://github.com/user-attachments/assets/a9cad703-6e0c-4e99-aea1-ea901958625b" width="600"/>

<img src="https://github.com/user-attachments/assets/5cfd8732-58e1-4bf0-bf13-fcc0b7c5111b" width="600"/>

To extract launch the `ie5setup`:

<img src="https://github.com/user-attachments/assets/bfe432b8-a933-4332-9d5c-97c6c285dd20" width="600"/>

This extracts the setup files:

<img src="https://github.com/user-attachments/assets/18ece26e-b808-46d4-8994-e85fc03975e2" width="600"/>

To the folder `IE 5.5 SP2 Full`:

<img src="https://github.com/user-attachments/assets/0fb9668f-3ce7-461a-89f1-44d0e68a430e" width="600"/>

Launch `ie5setup`:

<img src="https://github.com/user-attachments/assets/744fd666-5bdb-4a2f-a3e2-daae453df818" width="600"/>

Accept the License Agreement:

<img src="https://github.com/user-attachments/assets/35f398ca-a627-4546-8a22-b29c46eda783" width="600"/>

Select Install Now and next:

<img src="https://github.com/user-attachments/assets/896c5863-7838-4e99-bd2c-da2b5835d0be" width="600"/>

Select Finish to restart:

<img src="https://github.com/user-attachments/assets/bdef44b3-a9e1-4493-a7b4-f03efcaef929" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/63a85d70-b33a-4762-b95d-28a6c347ccfc" width="600"/>

Select Player → Removable Devices → CD/DVD and Settings:

<img src="https://github.com/user-attachments/assets/eac363f7-cab0-44d0-87e9-1d73dc63909a" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/36d8274e-4609-4df8-8575-c00c18cef367" width="600"/>

Select `winPre2k.iso` and select Open:

<img src="https://github.com/user-attachments/assets/75d9d3a1-2942-4241-8de4-d48dc4b396df" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/836ec68b-4b5f-435f-adad-0b0a9ba5d9c6" width="600"/>

VMtware Tools will begin to install. Select next:

<img src="https://github.com/user-attachments/assets/4a1e5fd2-e761-4758-8428-91d0eb298145" width="600"/>

Select Complete and Next:

<img src="https://github.com/user-attachments/assets/f1cb2b7f-490c-4d87-9343-612e72494144" width="600"/>

Select Install:

<img src="https://github.com/user-attachments/assets/c712fcb9-9f69-4d31-8820-9e492c743fa9" width="600"/>

You will be informed that the setup failed to install the Standard Video Graphics Adaptor (SVGA) driver automatically. Select OK:

<img src="https://github.com/user-attachments/assets/84e54a0f-f6f3-4636-bc30-301c6ec21350" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/d9c0ddb8-700e-492e-9dfb-910eee0111ff" width="600"/>

Installation instructions display in notepad, these can be closed since you are following the more detailed instructions here:

<img src="https://github.com/user-attachments/assets/75a234f7-f6db-4aba-aac3-df119eac2d49" width="600"/>

Select Advanced Properties:

<img src="https://github.com/user-attachments/assets/d7dd892c-2e9e-4a05-9ae0-f2e5a7ea1d8e" width="600"/>

Select Change:

<img src="https://github.com/user-attachments/assets/6135695f-8e74-4aa2-8ef2-125130a40fe6" width="600"/>

To the left select Standard Display Type and to the right select Standard PCI Graphics Adaptor (VGA) and then select Have Disk:

<img src="https://github.com/user-attachments/assets/ebe31505-96da-4519-845a-fc1a049ae2da" width="600"/>

In the file path input:

```
C:\Program Files\VMware\VMware Tools\Drivers\video
```

Then select OK:

<img src="https://github.com/user-attachments/assets/6b325a37-16fb-4c5e-a260-60dd16855cc7" width="600"/>

If an error displays, retype the above checking you haven't made a typo. Select VMware SVGA II and select OK:

<img src="https://github.com/user-attachments/assets/d3ce110c-052e-4923-8425-66ea9954fe23" width="600"/>

The following error message displays, please insert the disk labeled VMware Tools and then select OK. Likely Windows 95 is expecting a floppy disk with the driver, there is no need to insert the disk. Select OK:

<img src="https://github.com/user-attachments/assets/bdc4ded1-cecd-448d-9251-a4c5ce12a206" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/b4ca3aa4-21f9-4b21-9966-9d9c590a79ba" width="600"/>

To the right navigate change to `C:`:

<img src="https://github.com/user-attachments/assets/4b8210b8-4719-468e-8ada-d5ad4d491392" width="600"/>

Then navigate to the same folder:

<img src="https://github.com/user-attachments/assets/0cfd9d7c-d000-45d8-8dd6-ef623c1f0928" width="600"/>

To the left select the `vmx_svga.drv` should display, select it:

<img src="https://github.com/user-attachments/assets/933e2818-acc1-434c-b656-cbbe5d27e825" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/13aaabed-569e-492a-a629-a07689cbbd92" width="600"/>

This changes the path to the DOS file name which has a limit of 8 characters per folder:

```
C:\PROGA~1\VMWARE\VMWARE~1\DRIVERS\VIDEO
```

Select OK:

<img src="https://github.com/user-attachments/assets/9217cff0-1218-47d4-8ec5-82f4ea5b85b6" width="600"/>

Select apply:

<img src="https://github.com/user-attachments/assets/309fe6ce-eb0a-41cf-ae35-164710c95f75" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/c77e89d0-1ad2-41d4-9330-51c556f0d7a4" width="600"/>

Select Close:

<img src="https://github.com/user-attachments/assets/10461290-956d-4451-864f-b95f61e2ac2f" width="600"/>

At the prompt to restart select yes:

<img src="https://github.com/user-attachments/assets/34604990-133e-45a8-9f95-c43919d20a0d" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/63a85d70-b33a-4762-b95d-28a6c347ccfc" width="600"/>

Right click the desktop and select Properties:

<img src="https://github.com/user-attachments/assets/e0c5bd00-12fd-45d7-a54d-5c9ccce503c0" width="600"/>

Move the resolution slider to the right and select apply:

<img src="https://github.com/user-attachments/assets/609554d5-58f3-401c-80c0-af32959aa660" width="600"/>

You will be asked to specify a monitor, select yes:

<img src="https://github.com/user-attachments/assets/e2171e70-eed9-4104-8d39-8ee714863572" width="600"/>

To the left select Standard Monitor Types and to the right select Plug and Play Monitor and then select OK:

<img src="https://github.com/user-attachments/assets/b12575be-bba8-485a-bf4e-99bad482ac2b" width="600"/>

Move the resolution slider to the right and select apply:

<img src="https://github.com/user-attachments/assets/10785af4-715c-42f7-9ba8-d3136fabd346" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/26334f2e-f063-44e1-a75c-8a025cc970c7" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/54f3a659-a041-4308-adec-4249918731de" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/b3c70eda-1033-4e6d-9219-0eaa908691c9" width="600"/>

Now on the WIndows 11 Guest, the Window containing the Windows 98 VM can be aerosnapped or resized. The resolution of the VM will then automatically adjust to the size of the window.

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/214b29b2-22af-4929-9389-4c20d3be9f87" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/89ae14d0-f938-4d90-ae7b-640dcac32f52" width="600"/>

Select the  `Updates.iso` and select Open:

<img src="https://github.com/user-attachments/assets/62e5e75f-f0cd-435e-9c30-ebc6feb8a3e6" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/6d814963-54c5-4d9a-9135-4c9b92e598b9" width="600"/>

Run the Creative Labs SB-PCI64v Sound Card Version 5.13 driver `sb-9xeng`:

<img src="https://github.com/user-attachments/assets/f9307c30-2611-4958-a42f-e91e1fb85dde" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/09b22005-16ed-4889-9931-171d4533aab9" width="600"/>

Select unzip:

<img src="https://github.com/user-attachments/assets/2af3d931-8c57-4bc0-8ce0-b1ac5b3e33cb" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/bc2f4683-9924-48cb-a81f-cd466668525c" width="600"/>

Select Install Now:

<img src="https://github.com/user-attachments/assets/b5ab183a-f7e0-4d93-a856-e7200f7e29fa" width="600"/>

Select Run this Program from its Current Location and select OK:

<img src="https://github.com/user-attachments/assets/fbc869bf-4e6f-4a32-957e-fa19c800c7d2" width="600"/>

Select Yes:

<img src="https://github.com/user-attachments/assets/926675a5-4638-4b1c-bdab-50df60d18183" width="600"/>

Select Remove and Install Software and select Next:

<img src="https://github.com/user-attachments/assets/2a80657c-1ec8-4215-a7b7-b5cc2fc6c009" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/9301923e-02a3-4809-9ffc-1b0746dedc6d" width="600"/>

Select Yes to restart:

<img src="https://github.com/user-attachments/assets/3c48dd87-8427-420f-9bd4-9e9e546d76a3" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/c737f83f-31ee-4f48-a306-57a22654df38" width="600"/>

The driver will finish installing. Select yes to restart:

<img src="https://github.com/user-attachments/assets/fd727c09-e508-4525-8fd4-860cca16be91" width="600"/>

Press `↵` to log in:

<img src="https://github.com/user-attachments/assets/c737f83f-31ee-4f48-a306-57a22654df38" width="600"/>

You will be informed about a Settigns CHange. Select Yes to restart:

<img src="https://github.com/user-attachments/assets/ebbd90a7-1992-438e-857f-e4ae46272d22" width="600"/>

Press `↵` to log in, you will hear audio as you log in:

<img src="https://github.com/user-attachments/assets/c737f83f-31ee-4f48-a306-57a22654df38" width="600"/>

Launch the unofficial service pack `Osr2sp1` again and now select the following:

* DirectX 8.0a

<img src="https://github.com/user-attachments/assets/5a76a984-ac48-4c09-8c2d-c365cdaa0467" width="600"/>

Select OK and yes and then log back in.

<img src="https://github.com/user-attachments/assets/0d19bffb-2644-40b8-97a2-f3b0422857ed" width="600"/>

Launch the unofficial service pack `Osr2sp1` again and now select the following:

* Windows Media Player 6.4.7.1129

<img src="https://github.com/user-attachments/assets/139e89f5-ee1a-42bd-9d8e-0fd74fbcc5c6" width="600"/>

Select OK and yes and then log back in.

Launch the unofficial service pack `Osr2sp1` again and now select the following:

* TweakUI 1.33
* Command Prompt Here
* WinTop 0.95

<img src="https://github.com/user-attachments/assets/266f598e-3c1e-4c5d-8124-7026b4dd5edf" width="600"/>

Right click Computer and select Properties:

<img src="https://github.com/user-attachments/assets/3aac9292-96d7-4970-818f-e9fa56905643" width="600"/>

Select Device Manager:

<img src="https://github.com/user-attachments/assets/53925dc5-22ad-4e0f-add1-21cb6d5285b3" width="600"/>

There are two devices listed under Other Devices PCI System Peripheral and Unknown Device. For more details, select Start → Run:

<img src="https://github.com/user-attachments/assets/aae9b2b2-f952-4168-ab67-ffb5c59594cf" width="600"/>

And input:

```
hwinfo /ui
```

Press `Ctrl` + `f` and search for these devices:

<img src="https://github.com/user-attachments/assets/1644d05c-167d-402f-a5e6-d08d5e8711fc" width="600"/>

<img src="https://github.com/user-attachments/assets/dc86dad1-5c1d-44cd-8712-f7e73dfe24fb" width="600" />

This gies:

```
HKEY_LOCAL_MACHINE\enum\PCI\VEN_15AD&DEV_0740\BUS_00&DEV_07&FUNC_07
```

And:

```
HKEY_LOCAL_MACHINE\enum\ROOT\NET\0000
```

The first is the VMware VMCI Bus which is used by VMware for folder sharing and dragging and dropping files. According to Broadcom there is no Windows 95/98 driver for this device:

> For Windows 98 and Windows 98SE, there is no support for the VMCI device in VMware Tools. 

[Broadcom Legacy Article 1023129](https://knowledge.broadcom.com/external/article?legacyId=1023129)

On a Windows 11 Guest, bi-directional drag and drop appear to work but I was unable to get shared folders to work.

I was not able to find any more details about the second device.

## Shared Folders

Although the options for shared folders shows up for the Windows 95 Guest. The map as a etwork drive in Windows guests does not do anything. Therefore you cannot view the shared folder:

<img src="https://github.com/user-attachments/assets/8d58ccb5-9612-4ec4-93e9-13352635eda0" width="600"/>

## Installing Python

Python will be used as an example of installing a program on Windows 95. The isntaller is available here:

* [Python 2.3.3](https://www.python.org/downloads/release/python-233/)
* [pywin32](https://sourceforge.net/projects/pywin32/files/pywin32/Build%20214/pywin32-214.win32-py2.3.exe/download)
* [Pyserial](https://sourceforge.net/projects/pyserial/files/pyserial/2.1/)

Drag and drop the applications to the Windows 95 Desktop:

<img src="https://github.com/user-attachments/assets/7bb227d0-bddf-4353-b6eb-5d4442ef5c1e" width="600"/>

Launch the `Python-2.3.3.exe`:

<img src="https://github.com/user-attachments/assets/4c008c46-bbaf-473a-91e5-de4b2e7ef54e" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/171364ca-97c1-4fb0-8614-870ba535bb76" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/57063334-5a5c-49a1-9932-3d0b392c6249" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/6250a0f5-e5a2-4f89-bf2e-dc8263e2103d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/9d0ff044-1440-4b4f-9284-0b3f77759931" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/945fa936-1ac7-4abd-a2db-f62fb15bc451" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/a3d7249c-7c7f-4441-a73a-d318a19eef1f" width="600"/>

GGo to Computer:

<img src="https://github.com/user-attachments/assets/e33a1c2a-d6c8-4708-96b0-3e3971086487" width="600"/>

Navigate to `C:`:

<img src="https://github.com/user-attachments/assets/0cb836a6-986e-4964-bec8-f519f69aed5c" width="600"/>

Python is installed in the `Python23` folder:

<img src="https://github.com/user-attachments/assets/78bd2d2b-164c-4a03-afcd-a7d1a9cc51a0" width="600"/>

Python is installed in this folder as a single environment:

<img src="https://github.com/user-attachments/assets/450f19d6-12b8-4ae1-8e76-915f3d3d94be" width="600"/>

This version of Python did not support Python environments.

Standard libraries are found in the `lib` folder:

<img src="https://github.com/user-attachments/assets/c1197822-c758-48d8-bd0a-398ab6da5838" width="600"/>

Third-party libraries are installed to the `site-packages` folder:

<img src="https://github.com/user-attachments/assets/d54b69da-2dc1-4dc9-8ea1-dd97f13c388f" width="600"/>

Note the absense of `pip`, the Python package manager which wasn't created yet.

<img src="https://github.com/user-attachments/assets/d95c999d-c13d-4f11-88aa-488e7f36c39f" width="600"/>

Packages were typically available in `.exe` format. Many packages relied on `pywin32` which can be installed:

<img src="https://github.com/user-attachments/assets/9757fb5d-cbdf-4bf1-8467-b4346c4576b7" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/22721b82-1d2f-4f40-9a28-d5e69a8f62a2" width="600"/>

The Python directory and corresponding `site-packages` directory is found. Select next:

<img src="https://github.com/user-attachments/assets/8e679575-7a73-4dab-b78a-3d20b228fe93" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/9f2d63dc-5749-4ca0-abf2-b78e735669b1" width="600"/>

Select finish:

<img src="https://github.com/user-attachments/assets/54880bc8-1b27-45ad-b940-a1cd1a36b0be" width="600"/>

`pywin32` is installed in `site-packages`:

<img src="https://github.com/user-attachments/assets/cb73fc2a-f967-4418-91a5-cddbe534d52d" width="600"/>

Installation of pyserial is similar:

<img src="https://github.com/user-attachments/assets/bc6c9af1-9ed0-4b40-a50f-bb240df95d69" width="600"/>

<img src="https://github.com/user-attachments/assets/7d073f99-ca46-4ace-81bc-0f2d10dc0ab8" width="600"/>

<img wsrc="https://github.com/user-attachments/assets/2425c907-a0c4-4fbf-b941-1bd5330833c5" width="600"/>

<img src="https://github.com/user-attachments/assets/ec6610cb-629b-4bb2-a121-460ad31cf32d" width="600"/>

<img src="https://github.com/user-attachments/assets/94cdf958-1d0c-4d62-bf10-39627a2bb901" width="600"/>

The `pyserial` folder is found in `site-packages`:

<img src="https://github.com/user-attachments/assets/b64e44cc-0579-4721-bdff-e6a7970b05ec" width="600"/>

The MSDOS prompt can be sued to launch Python. Select Start → Programs → MS-DOS Prompt:

<img src="https://github.com/user-attachments/assets/e40aca57-45f5-4775-8d74-77d72f6e731c" width="600"/>

<img src="https://github.com/user-attachments/assets/7c842895-623b-4d43-abc2-20a0d2518dd1" width="600"/>

Change directory to the Python23 directory:

```powershell
CD C:\Python23
```

<img src="https://github.com/user-attachments/assets/3fc701a3-12f2-4350-8ad2-fc37a82a6a3f" width="600"/>

Launch Python using:

```powershell
python
```

Notice the prompt changes to `>>>`, the Python prompt. Test Python code can be input such as:

```python
print 'Hello World!'
```

<img src="https://github.com/user-attachments/assets/5dbb7229-0b23-4a64-9b97-4dc36d90fd0c" width="600"/>

The pyserial library can be imported using:

```python
pyserial
```

<img src="https://github.com/user-attachments/assets/c4c3a514-b453-40a3-b079-a77eb95c76d6" width="600"/>

This gives a traceback error. In this early version of Windows and Python it is very difficult to setup compatible libraries which work.

To exit type in:

```python
exit
```

<img src="https://github.com/user-attachments/assets/2328279f-8005-4c4f-b4b1-2376bd885223" width="600"/>

Press `Ctrl` + `z`:

<img src="https://github.com/user-attachments/assets/fd5c98ca-9602-4e4f-b18f-70a9ccb093e5" width="600"/>

A Python program can be created using notepad:

<img src="https://github.com/user-attachments/assets/43de15d2-0a22-4b1f-a8cb-d4874f368aed" width="600"/>

```python
print 'Hello World!'
```

<img src="https://github.com/user-attachments/assets/63f69495-36a4-4c57-8f10-fb20f6c81c43" width="600"/>

Select File → Save As...:

<img src="https://github.com/user-attachments/assets/d933d714-82f1-4752-a106-f4a499e5a5df" width="600"/>


When saving add the `.py` extension and select All Files:

<img src="https://github.com/user-attachments/assets/2c2c61fe-57e7-4642-8799-f60cb17dcb34" width="600"/>

In this Windows build, the Desktop was a subndirectory of the Windows folder! To run the Python script the following command can be used:

```powershell
C:\Python23\python C:\Windows\Desktop\script.py
```

<img src="https://github.com/user-attachments/assets/877d6491-4a8e-4be5-81bf-6f78a3cae183" width="600"/>

## USB Passthrough

Windows 95 had very limited support for a small subset of USB 1.0 devices and therefore USB Passthrough is not really functional.

## Serial port Passthrough

Close the Windows 95 Guest. Attach a USB to Serial Port to the Window 11 Host PC:

<img src="https://github.com/user-attachments/assets/dc02277e-d8ff-4fa1-b071-993df8f0cd7b" width="600"/>

On the Windows 11 Host PC, right click the Start Button and select Device Manager:

<img src="https://github.com/user-attachments/assets/4c5f545f-e66c-4ece-b524-10454a2397b4" width="600"/>

Expand ports (COM & LPT). In this example, the USB Serial COM Port is COM3:

<img src="https://github.com/user-attachments/assets/da226f02-457e-417d-9294-d018f54fc562" width="600"/>

Right click it and select properties:

<img src="https://github.com/user-attachments/assets/0f1768d9-c1bf-4324-8bc6-946640ba5531" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects:

<img src="https://github.com/user-attachments/assets/283e424d-9fea-448d-ab0a-874db7c018c1" width="600"/>

In this case it will be left at port 3:

<img src="https://github.com/user-attachments/assets/bf7258a0-b073-4451-ac3c-45542580d38f" width="600"/>

Open VMware Player and select Edit Virtual Machine Settings:

<img src="https://github.com/user-attachments/assets/97bce49b-5f03-4021-af0e-9e9f763eca25" width="600"/>

Under CD/DVD select Browse:

<img src="https://github.com/user-attachments/assets/8032c04b-7b68-40d4-ab2a-c48df0f653fb" width="600"/>

Select the Windows 95 CD and select open:

<img src="https://github.com/user-attachments/assets/ba500745-8421-48cf-9dca-8765c9d22a41" width="600"/>

Select Add:

<img src="https://github.com/user-attachments/assets/5807be8e-f4f0-4474-8bc0-7f26426c2db7" width="600"/>

Select Serial Port and Finish:

<img src="https://github.com/user-attachments/assets/40fba3f8-52b5-4a1e-bec2-2c8e39354e38" width="600"/>

Select the Serial Port, in this case COM3:

<img src="https://github.com/user-attachments/assets/495bd7fd-625a-458c-953e-2147ec417c2f" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/459f2261-b535-4cf9-96e5-1b327d8a9b76" width="600"/>

Launch the Windows 95 Guest:

<img src="https://github.com/user-attachments/assets/7dac7987-891f-4b1c-b0e4-74d267e55895" width="600"/>

The Serial Port driver will automatically install. Right click Computer and select Properties:

<img src="https://github.com/user-attachments/assets/d6fa23e7-12c6-43af-8124-64a44b3c6032" width="600"/>

Select the Serial Port and select Proeprties:

<img src="https://github.com/user-attachments/assets/0da14bf5-8d12-4e78-8d04-7b53bb1454c6" width="600"/>

The Baud Rate displays:

<img src="https://github.com/user-attachments/assets/9946ef05-dc2a-4600-b7e9-a3b2d3b1a756" width="600"/>

Note under Advanced, there is no way to change the Port number:

<img src="https://github.com/user-attachments/assets/29696463-c74a-491f-b341-574dd2e59938" width="600"/>

<img src="https://github.com/user-attachments/assets/2500a688-a545-46df-b7cb-441d2b96073e" width="600"/>

Many programs assume a single Serial Port on COM1.

Since pyserial isn't working, TeraTerm can be used to test the serial port:

# [TeraTerm](https://www.majorgeeks.com/mg/getmirror/tera_term_(pro),1.html)

The zip file can be extracted and copied over to the Windows 95 Guest. Launch the setup:

<img src="https://github.com/user-attachments/assets/3d8a9955-c37c-4ebf-a75e-a11edb217303" width="600"/>

Select Continue:

<img src="https://github.com/user-attachments/assets/12c91f36-e733-48ca-a626-64e7134a6719" width="600"/>

Select Continue:

<img src="https://github.com/user-attachments/assets/faf33006-75f0-484e-ac1b-10842ecfd684" width="600"/>

Select OK and launch TeraTerm:

<img src="https://github.com/user-attachments/assets/1519dd73-adae-4893-87b9-d7b5ec098577" width="600"/>

Select Serial, Com1 and OK:

<img src="https://github.com/user-attachments/assets/4392e215-11b7-4717-a1aa-5c288537d6e3" width="600"/>

Select Setup → Serial Port:

<img src="https://github.com/user-attachments/assets/3dd1996d-eefb-403e-a02d-da503eacf513" width="600"/>

Change the Transmit delay to 5 ms/char:

<img src="https://github.com/user-attachments/assets/ee947341-6110-4f11-b436-47d7065e0a46" width="600"/>

Select Setup → Terminal:

<img src="https://github.com/user-attachments/assets/6f2fb941-ef98-48a0-b12e-db2ed946dcf9" width="600"/>

Set Receive and Transmit both to Carriage Return and Line Feed. Check Local Echo:

<img src="https://github.com/user-attachments/assets/aceeb4af-1b81-4bc5-a952-e25d860b1669" width="600"/>

The Serial Port looks like the following:

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

Now with no pins connected:

<img src="https://github.com/user-attachments/assets/e0842283-bc24-4526-a8e9-e92c91a986fe" width="600"/>

When:

```
a
```

is input the following shows:

<img src="https://github.com/user-attachments/assets/20394d49-a4fe-4bd9-a2f0-03fc8e113ae3" width="600"/>

With pins 2 and 3 connected:

<img src="https://github.com/user-attachments/assets/0ec50a62-e408-469d-ae8f-493599320523" width="600"/>

When:

```
b
```

is input the following shows:

<img src="https://github.com/user-attachments/assets/a565db65-ef32-4cd9-9bef-abfd5da6322d" width="600"/>

This `B`  has essentially been transmitted using the data pin 3 and then read back using pin 2. 

## Parallel Port Passthrough

VMware can theoretically passthrough a physical parallel port. However, USB-to-parallel adapters are designed exclusively for printers and do not provide true parallel port functionality for other hardware. I do not have a parallel port printer available to test passthrough functionality.

## PCI/PCIe Card Passthrough

VMware does not support direct passthrough of PCI or PCIe cards to a guest virtual machine. Additionally, there are no USB adapters that replicate the functionality of PCI/PCIe expansion cards.

Return to [VMware Installation Guide](../readme.md)
