# Windows ME Guest

## Notes

VMware Workstation Player 17.6.4 has Windows ME as an option for a Virtual Machine. However Windows ME is regarded as an ancient legacy Operating System and isn't tested by Broadcom. Modern processors are significantly faster than the processers available when Windows ME was released. As a consequence the timing for some operations is divided by 0 and there is a divide-by-zero error that needs to be addressed using patcher9x.

VMware Tools 12.5.3 which comes with VMware workstation player doesn't support Windows ME. VMware Tools WinPre2k is the last version of VMware Tools to support Windows ME and should be downloaded seperately as an ISO. This ISO should be mounted in the VM so they can be installed manually.

On modern hardware with a 12th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

The first setting allows the CPU to optimise the VM performance, the VM may be very slow without this setting. The second setting prevents use of a memory management unit that Windows ME doesn't understand and can lead to a Blue Screen of Death (BSOD). The third setting prevents VMware from using Vulkan for rendering, which isn't supported by Windows ME and often leads to black screens. The last two settings prevent Windows ME from seeing unsupported CPU features which Windows ME doesn't understand and can lead to a Blue Screen of Death (BSOD).

## Downloads

### Windows ME ISO

Windows ME is considered abandonware and the Windows ME ISO and Product Key can be obtained from WinWorld:

* [Windows ME CD](https://winworldpc.com/product/windows-me/final)

### Windows ME Update CD

Windows ME Update CD can be used to patch a Windows ME install:

* [Windows ME Update CD](https://github.com/bricemci/wmeupd)

### VMware Tools ISO

The Windows 98SE drivers for the Windows ME Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

* [VMware Tools Pre2k](https://archive.org/details/winPre2k)

### Patcher9x

In order to install Windows ME on a VM with a modern processor, the installation files need to be patched essentially to prevent a zero-division error. Download the `patcher9x-win64.zip` from the assets of the latest release:

* [patcher9x](https://github.com/JHRobotics/patcher9x/releases/)

### 7-zip

7-zip will be used to extract the ISO. Download and install on the Windows 11 Guest:

* [7-zip](https://7-zip.org/download.html)

### ImgBurn

ImgBurn will be used to rebuild the ISO. Download and install on the Windows 11 Guest:

* [ImgBurn](https://www.imgburn.com/)

### Patching the Installation ISO

The Windows ME installation errors out on a VM on a modern computer:

> This program has performed an illegal operation and will be shut down.

> If the problem persists, contact the program vendor

Essentially the processor is too fast and windows ME expects to wait more than "zero seconds" for an operation. Therefore the Windows ME installation media needs to be patched with patcher9x. Right click zip file and select extract all and then extract:

<img src="https://github.com/user-attachments/assets/c9718304-7ab9-43a7-a5a8-2bb429d0d0d7" width="600"/>

<img src="https://github.com/user-attachments/assets/5128603b-7c60-4c74-be7e-717a31e20ad5" width="600"/>

<img src="https://github.com/user-attachments/assets/324e21d0-2f8e-41dd-b701-1135a05639bc" width="600"/>

In the extracted folder is the `patcher9x` application.

Now extract the Windows ME ISO. Right click the zip file and select extract all and then extract:

<img src="https://github.com/user-attachments/assets/1f53e0e2-4e5d-495b-b423-6f2fc21d372c" width="600"/>

<img src="https://github.com/user-attachments/assets/17bd4b63-c1f9-4fc9-a2d8-81769e4c13f9" width="600"/>

<img src="https://github.com/user-attachments/assets/1796fd5b-11ae-42ec-bfa4-7d936e1f2b3f" width="600"/>

Move the ISO to downloads:

<img src="https://github.com/user-attachments/assets/675f5b18-e9d8-45a7-b534-7311351874ec" width="600"/>

Right click the ISO and select SHow More Options and then 7zip and then extract o...:

<img src="https://github.com/user-attachments/assets/0b91ad22-74c7-4979-8676-50b99bbcc46a" width="600"/>

<img src="https://github.com/user-attachments/assets/7ce3b0fc-c553-4e9d-9fae-f3924462e72b" width="600"/>

<img src="https://github.com/user-attachments/assets/195fe925-b666-482c-a25d-23e89450f8f6" width="600"/>

In the extracted folder is the `win9x` folder which contains the Windows setup files which need to be patched:

<img src="https://github.com/user-attachments/assets/aa1fb6ad-dcc9-42f5-898d-aafdc203a85e" width="600"/>

Right click and select Copy as Path:

<img src="https://github.com/user-attachments/assets/cfbe858e-c247-4e59-902e-abbd2b6ef160" width="600"/>

Now launch `patcher9x`:

<img src="https://github.com/user-attachments/assets/e8c53a17-f377-44b3-ae0b-c486a567a9b1" width="600"/>

Select More info:

<img src="https://github.com/user-attachments/assets/114d776a-141d-4d4e-855b-a8f02f95d7e6" width="300"/>

Select Run Anyway:

<img src="https://github.com/user-attachments/assets/30978f95-379c-4910-a8a6-b49a4f8b1722" width="300"/>

Paste the path in:

<img src="https://github.com/user-attachments/assets/1a518fd2-efff-4d1e-8828-71b8ee73c41d" width="600"/>

Remove the quotations around the path:

<img src="https://github.com/user-attachments/assets/5d0859be-c924-406b-a461-f8c4283b4a72" width="600"/>

Select option `4`:

<img src="https://github.com/user-attachments/assets/c639332d-ecc9-4956-905a-dc8858d56d71" width="600"/>

Select `Y` to proceed:

<img src="https://github.com/user-attachments/assets/c6733a27-83ce-460a-8991-687f894c4a9a" width="600"/>

Now press `↵` to exit the program:

<img src="https://github.com/user-attachments/assets/5c5df07f-f238-48b8-bfc1-37522c3f8248" width="600"/>

The following folder now needs to be converted back into an .ISO file and needs to be bootable:

<img src="https://github.com/user-attachments/assets/f520dbd0-e62a-4889-9ccc-88f119d5444d" width="600"/>

Launch ImgBurn and select Create Image File from Files/Folders:

<img src="https://github.com/user-attachments/assets/3999fa2a-9c92-44d0-8c1a-270c17fd719a" width="600"/>

Load a folder:

<img src="https://github.com/user-attachments/assets/140fd84c-b68a-463b-846c-5a3f89596322" width="600"/>

Select the Windows ME folder:

<img src="https://github.com/user-attachments/assets/8ae6f3b5-145c-46d3-8a1d-d2c9c4e7d3e7" width="600"/>

Select options and change the data type to MODE1/2048 and the file system to ISO9660 + Joliet. Ensure Recurse subdirectories is checked:

<img src="https://github.com/user-attachments/assets/8a0b5205-059e-4995-8b16-f9cf299019f0" width="600"/>

Select Labels and under ISO9660 input WIN98_SE and under Joliet input WINME:

<img src="https://github.com/user-attachments/assets/59f86429-c0ab-4361-9689-017cd32f42bd" width="600"/>

Under Advanced, select Bootable Disc. In Bootable Disc select Make Image Bootable and change the emulation type to Floppy Disk 1.44 MB. Change the Platform ID to 80x86 and set the Developer ID as Microsoft Corporation:

<img src="https://github.com/user-attachments/assets/8592416b-a680-4592-919b-5a5aab752e93" width="600"/>

Under Boot image select load folder, select the Windows ME folder, the \[Boot\] subfolder and then the `Boot-1.44.img` file:

<img src="https://github.com/user-attachments/assets/b11c4e99-6c30-4f5e-a0ef-53d0a761e73d" width="600"/>

<img src="https://github.com/user-attachments/assets/1665c430-360d-4705-a7c7-5c0ca8b34251" width="600"/>

<img src="https://github.com/user-attachments/assets/b9ed8774-8519-4b8d-85ee-ba5a61e07ad8" width="600"/>

Under destination select the folder icon:

<img src="https://github.com/user-attachments/assets/983f3a91-fbd4-4c32-baea-25f7a445cb64" width="600"/>

Navigate to Downloads and save as `Windows ME.iso`:

<img src="https://github.com/user-attachments/assets/92317313-97cc-4f78-8cc6-f4db211c846a" width="600"/>

Select the Create Image File from Files/Folder icon:

<img src="https://github.com/user-attachments/assets/ff5d93d7-082d-42e1-bfec-186b3e30f78f" width="600"/>

Select Yes, OK and Ok:

<img src="https://github.com/user-attachments/assets/a5078552-96d0-4cbc-81b7-d39a2c1c0536" width="300"/>

<img src="https://github.com/user-attachments/assets/8a94e31e-6b58-4976-a4d8-cfc9dea26156" width="300"/>

<img src="https://github.com/user-attachments/assets/fa54ba60-8f56-4795-af84-709916e50da9" width="300"/>

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










## Installing Python

Python will be used as an example of installing a program on Windows ME. The installer is available here:

* [Python 2.5.4](https://www.python.org/downloads/release/python-254/)
* [pyserial 2.1](https://sourceforge.net/projects/pyserial/files/pyserial/2.1/)
* [pywin32 2.18](https://sourceforge.net/projects/pywin32/files/pywin32/Build%20218/)

The pywin32, version 2.18 installer for Python 2.5 needs to be downloaded.

