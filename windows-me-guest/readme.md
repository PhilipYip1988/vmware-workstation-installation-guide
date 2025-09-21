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

### Windows ME Update CD ISO

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

## Configuring the Windows ME Guest

Select File → New Virtual Machine:

<img src="https://github.com/user-attachments/assets/abe6751d-74c2-4787-8da4-45a845aa8070" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/cf0e3ff0-ac1f-4407-833c-3e9a8e903c78" width="600"/>

Select the `Windows ME.iso` and select Open:

<img src="https://github.com/user-attachments/assets/60b08e22-70bb-4b8b-a506-8d72a84d7fc7" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/ad2c5bd4-3b9a-4c7a-a184-4b7f0507cf3c" width="600"/>

The VM Name and Location will be shown. Note when used on a Windows 11 Host which is signed in with a Microsoft Account and integrated with OneDrive, the default location will be on OneDrive. The VM can be quite large and the location can be changed to local Documents by removing the OneDrive folder:

<img src="https://github.com/user-attachments/assets/6727a1f4-71d2-4f10-b2d4-14a7cf426bf9" width="600"/>

Note the name and location as these will be used later.

The default maximum size of the Windows ME Guest is 8 GB which is a bit too restrictive. I recommend increasing this to 32 GB. Note the files on the Windows 11 Host won't be 32 GB but can be up to 32 GB if the Windows ME Guests Virtual Drive is fully occupied with files. Windows ME may struggle with a Virtual Drive > 32 GB:

<img src="https://github.com/user-attachments/assets/fee60872-d124-4353-8d66-706c6be27215" width="600"/>

Select Customise Hardware:

<img src="https://github.com/user-attachments/assets/87ccf584-4e00-4ef8-9c27-b4e7dcc1064f" width="600"/>

Change the memory to 512 MB (Windows 98 has issues with larger memory sizes):

<img src="https://github.com/user-attachments/assets/a8ff7db6-75d4-4b41-a0f3-6793b02281dc" width="600"/>

Leave the processor options to their default. Windows ME does not support any of the unticked technologies and only supports 1 processor. A modern processor may be too fast for it and the patcher9x will need to later be used to address this:

<img src="https://github.com/user-attachments/assets/793858cb-ae4f-452b-a571-88b2cf92caaa" width="600"/>

In CD/DVD the Windows ME OEM ISO will be selected. Ensure Connect at Power On is checked:

<img src="https://github.com/user-attachments/assets/a3fe2b98-e29f-4fc2-b3a4-951d4a293205" width="600"/>

Under Network Adaptor uncheck Connect at Power On. Windows ME has reached end of life and is unsafe to use on the internet:

<img src="https://github.com/user-attachments/assets/a5370562-1ccc-455d-be85-4700c01bafda" width="600"/>

Leave the USB Controller at the default setting:

<img src="https://github.com/user-attachments/assets/f1c2bfa5-a820-4ce1-ba6e-7a6964a38fa5" width="600"/>

Leave the Sound Card at the default setting:

<img src="https://github.com/user-attachments/assets/a81448f2-68cf-4f7b-956d-d3d64af76c12" width="600"/>

Leave display at the default setting and select Close:

<img src="https://github.com/user-attachments/assets/21c24564-3dc8-45b8-8915-af1c19c20a11" width="600"/>

Some changes will be made in the Virtual Machine Configuration Files and select Uncheck Power on this Virtual Machine After Creation. Then select Finish:

<img src="https://github.com/user-attachments/assets/b271bb95-5ae2-40fe-818d-502e6856581a" width="600"/>

## Windows ME Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows ME Guest is installed: 

<img src="https://github.com/user-attachments/assets/dcb38b68-bb31-48a5-8d55-93e271deface" width="600"/>

<img src="https://github.com/user-attachments/assets/bdf62619-1647-4f6e-8fb3-075ee6fd4490" width="600"/>

Look for the `Windows ME.vmx` file:

<img src="https://github.com/user-attachments/assets/5839b518-72fd-4181-b7d5-e03d646292ac" width="600"/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/e9aa158f-2ebe-4a9c-8a18-afa4b0b73c15" width="600"/>

The option `bios.bootDelay` for example will change the time the Windows98 SE Guest Virtual BIOS displays before selecting the default boot option giving more time to select the option to boot from CD/DVD. This line can be removed post-installation, returning to the default value.

Press `Ctrl+f` to begin a search for an option for example `bios.bootDelay`:

<img src="https://github.com/user-attachments/assets/69dbb5b5-ca06-48b6-89de-71fb01facad3" width="600"/>

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/0ba88aab-7e00-4c61-b715-dd1dade3d397" width="600"/>

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

<img src="https://github.com/user-attachments/assets/270e0c3b-3b22-4f86-a728-a4417461df64" width="600"/>

## Installing the Windows ME Guest

Select the Windows ME Guest and select Play:

<img src="https://github.com/user-attachments/assets/180d514e-a40f-48d8-b358-105bb99c6be5" width="600"/>

Click into the VM and select option 2 Boot from CD-ROM:

<img src="https://github.com/user-attachments/assets/c5b3d2e5-95de-4b6d-abd3-09796a5012b4" width="600"/>

Select option 1 Start Windows Setup from CD-ROM:

<img src="https://github.com/user-attachments/assets/b258633f-0854-4007-8dfb-3931541cc53d" width="600"/>

Press `↵`:

<img src="https://github.com/user-attachments/assets/229cfa9c-2cfb-4aba-8c50-b9a3609173e0" width="600"/>

Select Configure Unallocated Disk Space (Recommended):

<img src="https://github.com/user-attachments/assets/e0ff4d94-96e2-4008-9d52-9ece313ac22a" width="600"/>

Select Yes, Enable Large Disk Support:

<img src="https://github.com/user-attachments/assets/fac33f5e-109d-42a0-b0d2-a2c428fff175" width="600"/>

Press `↵`:

<img src="https://github.com/user-attachments/assets/2a43933e-122b-4d43-9ebc-e33b7a228593" width="600"/>

Click into the VM and select option 2 Boot from CD-ROM:

<img src="https://github.com/user-attachments/assets/c5b3d2e5-95de-4b6d-abd3-09796a5012b4" width="600"/>

Select option 1 Start Windows Setup from CD-ROM:

<img src="https://github.com/user-attachments/assets/b258633f-0854-4007-8dfb-3931541cc53d" width="600"/>

Press `↵`:

<img src="https://github.com/user-attachments/assets/b700f26e-6ec2-4886-8018-034cc615bd27" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/0afc8fea-6f26-4b68-90dd-c4f6cf902320" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/4f2d4bf3-ff55-4b87-842a-801659363388" width="600"/>

Select Typical and select Next:

<img src="https://github.com/user-attachments/assets/8df77e6b-cb61-4319-b67a-9a5af1fb0f27" width="600"/>

Select Install the Most Common COmponents and select Next:

<img src="https://github.com/user-attachments/assets/c2db842c-3ea2-49c9-b2a9-1f4e8b504119" width="600"/>

Input the computer anme and select Next:

<img src="https://github.com/user-attachments/assets/7e3d8153-4855-4d57-9be6-6a22074ac94b" width="600"/>

Select your Country/Region and select Next:

<img src="https://github.com/user-attachments/assets/17f886c5-e2ab-4837-9fd3-925337df02d2" width="600"/>

Select yout Time Zone and select Next:

<img src="https://github.com/user-attachments/assets/26c3c7d0-d610-4a21-890b-5f0679e3ed32" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/d93940ba-1234-431e-a013-c19f772e533d" width="600"/>

Input your User Name and select Next:

<img src="https://github.com/user-attachments/assets/00b3e2ee-17cf-4903-9b02-c1c601908590" width="600"/>

Accept the License Agreement and select Next:

<img src="https://github.com/user-attachments/assets/368e18c7-2d09-4146-b83d-77b21d8edd28" width="600"/>

Input the product key supplied by WinWorld and select next:

<img src="https://github.com/user-attachments/assets/a4a5ab47-f706-4af2-bd90-aac4c8c11a65" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/0cd43dcc-c420-44ab-ac77-74174c8ec63e" width="600"/>

Input your User Name and log in to the Windows ME Desktop:

<img src="https://github.com/user-attachments/assets/337a8c19-cffc-400e-b3e8-294fb9b05a74" width="600"/>

## Backing up the Windows ME Guest

When the Windows ME Guest is powered down the Windows ME Guest VM can be backed up by copying the folder Windows Me found in Documents → Virtual Machines on the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/bb312563-14ec-41c7-9251-a4c0b6709996" width="600"/>

## Installing Windows ME Updates

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/489ae5e3-a3be-4a29-8af4-4a71e15f0062" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/9cc3e8e5-7b32-42c4-81c2-c226a01fcb20" width="600"/>

Select the Windows ME Update CD and select Open:

<img src="https://github.com/user-attachments/assets/74a737ce-0272-49df-b020-abcb04d28af8" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/b9066d9f-d165-4ab2-9a3a-1ee8b3dcf7bb" width="600"/>

Select Yes:

<img src="https://github.com/user-attachments/assets/ad76b8d7-1f02-41ce-83be-49efd6d756b5" width="600"/>

The Windows ME Update CD will display using Autorun. Select Update Windows:

<img src="https://github.com/user-attachments/assets/d5b79a24-8317-4823-b4f3-c36275bfb9b9" width="600"/>

To proceed input `Y`:

<img src="https://github.com/user-attachments/assets/96465cd4-482b-4496-ae69-996ab8e8176c" width="600"/>

And then `h`:

<img src="https://github.com/user-attachments/assets/518a35eb-50c5-45b3-9f0c-45bb70ddb0b9" width="600"/>

Select option 1 Internet Explorer 5.5 Service Pack 1:

<img src="https://github.com/user-attachments/assets/c01ba2c2-74a3-4fb0-b54a-c185f20cacea" width="600"/>

And then `h`:

<img src="https://github.com/user-attachments/assets/f1252924-0f7d-499d-8f13-e62a927f4d89" width="600"/>

Select option 1 Windows Media Player 7.1:

<img src="https://github.com/user-attachments/assets/2bd15d2b-e7b3-4a31-9e8b-b1ebe5b2241d" width="600"/>

And then `h`:

<img src="https://github.com/user-attachments/assets/46b9bf99-c226-498c-bfa2-6b113ce3d95f" width="600"/>

Windows ME will install updates and restart the Windows ME Guest multiple times:

<img src="https://github.com/user-attachments/assets/443ecd96-d931-41ae-b93b-26ac08b60b58" width="600"/>

If error messages display:

<img src="https://github.com/user-attachments/assets/4dfecf3e-95df-4b1a-b565-cbb6c10e66a2" width="600"/>

Select Player → Send Ctrl+Alt+Del:

<img src="https://github.com/user-attachments/assets/1f5c941a-2577-43a5-88f6-140c5ff04201" width="600"/>

Then select Shut Down:

<img src="https://github.com/user-attachments/assets/348e8592-5e37-4e9b-a44c-11219428a6d4" width="600"/>

Installation of Updates will proceed once rebooted:

<img src="https://github.com/user-attachments/assets/988eec74-6012-4dae-9a94-78c374f42e48" width="600"/>

You will be informed that all updates are complete. Press `h` to restart the Windows ME Guest:

<img src="https://github.com/user-attachments/assets/558ca6f9-5448-4344-a27f-c43894a0b544" width="600"/>

## Installing Optional Updates

Install the following optional updates:

* DirectX 9.0c (w/ updates)
  * Components → DurectX → 9.0c → DXSetup.exe
  * Components → DirectX → 9.0c Updates → WindowsME.Windows98SE-KB904706-DX9-x86-ENU.exe
* Microsoft .NET Framework 1.0, 1.1 and 2.0 (w/ updates)
  * Components → Microsoft .NET Framework → 1.0 → dotnetfx.exe
  * Components → Microsoft .NET Framework → 1.0 → Updates → NDP1.0sp3-KB867461-X86-Enu.exe
  * Components → Microsoft .NET Framework → 1.0 → Updates → NDP1.0sp3-KB886906-X86-Enu.exe
  * Components → Microsoft .NET Framework → 1.1 → dotnetfx.exe
  * Components → Microsoft .NET Framework → 1.1 → Updates → NDP1.1sp1-KB867460-X86.exe
  * Components → Microsoft .NET Framework → 1.1 → Updates → NDP1.1sp1-KB886903-X86.exe
  * Components → Microsoft .NET Framework → 2.0 → dotnetfx.exe
* Microsoft XML Core Services 2.6 SP3, 3.0 SP7 and 4.0 SP2 (w/ updates)
  * Components → Microsoft XML Core Services → 2.6 SP3 → msxml2.msi
  * Components → Microsoft XML Core Services → 2.6 SP3 → Updates → kb887606_msxml2.6_x86.exe
  * Components → Microsoft XML Core Services → 3.0 SP7 → msxml3.msi
  * Components → Microsoft XML Core Services → 4.0 SP2 → msxml4.msi
  * Components → Microsoft XML Core Services → 4.0 SP2 → Updates → kb887606_msxml4.0_x86.exe
* Visual Basic Runtimes
  * Components → Visual Basic Runtime → 6.0 SP6 → vbrun60sp6.exe
* Visual C++ Runtimes (6.0 and 2005 SP1 w/ MFC Security Update)
  * Components → Visual C++ Runtime → 6.0 SP6 → INSTALL.BAT
* Windows Script 5.6
  * Components → Windows Script → 5.6 → Windows9x-Script56-KB917344-x86-enu.exe

## Installing VMware Tools

Select Player → Manage → Install VMware Tools:

<img src="https://github.com/user-attachments/assets/243fbaf8-d042-4911-b9c7-bc2fb811b583" width="600"/>

This will give a download link to the `winPre2k.iso`:

<img src="https://github.com/user-attachments/assets/b2f73a6b-930b-42ea-8dbf-6b2bcacf9e13" width="600"/>

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/94c7ddfc-1209-4420-8a2a-f5538aac5596" width="600"/>

Then Browse:

<img src="https://github.com/user-attachments/assets/e5200d16-e399-4e22-a0a0-9b9e9758a3b7" width="600"/>

Select the `winPre2K.iso` and select Open:

<img src="https://github.com/user-attachments/assets/a00e80f8-c166-4a15-b0fa-2386ec3ca650" width="600"/>

Select Yes:

<img src="https://github.com/user-attachments/assets/9f3efcb6-c087-4567-ad77-748fc39802cb" width="300"/>

Select Next:

<img src="https://github.com/user-attachments/assets/78020d99-1454-4088-8c44-3ff90e82ba9c" width="600"/>

Select Complete and select Next:

<img src="https://github.com/user-attachments/assets/0f1b5398-fe67-4c19-84fb-11828bb1d07a" width="600"/>

Select Install:

<img src="https://github.com/user-attachments/assets/d47c5552-b462-4c3b-a8eb-2ef68883d4b7" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/f82e8bd9-933a-4c60-ad54-e54981f7a965" width="600"/>

Select Yes:

<img src="https://github.com/user-attachments/assets/1f9fd25e-db3a-4824-be0f-ee41a872a5d8" width="600"/>

After rebooting, right click the Desktop and select Properties::

<img src="https://github.com/user-attachments/assets/a6c541cf-cd26-4b45-846f-8e961348c999" width="600"/>

Go to settings and maximise the resolution slider and select Apply:

<img src="https://github.com/user-attachments/assets/baed7789-f51b-462c-b62a-e4c65b77f66a" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/9e04993a-7ecb-48cf-a5cb-2b0d2d22ab52" width="600"/>

Select Yes:

<img src="https://github.com/user-attachments/assets/bfd622d1-2f96-4e2f-bb59-67a99565d521" width="600"/>

Right click Computer and select Properties:

<img src="https://github.com/user-attachments/assets/d6db889d-6a53-4e2f-9042-1d637c4708df" width="600"/>

Under display adaptors the VMware SVGA II displays and under Sound, Audio and Game Controllers, the Creative AudioPCI displays:

<img src="https://github.com/user-attachments/assets/f043f9de-6cf9-41c2-969c-5772df2709b0" width="600"/>

Under Other Devices, there are two devices without a driver. PCI System Peripheral and PCI Universal Serial Bus. More details about these can be seen by going to Start → Run and inputting

```
hwinfo /ui
```

<img src="https://github.com/user-attachments/assets/52938231-8aa3-4c02-8f6f-97bf2512119c" width="600"/>

Then pressing `Ctrl`+`f` to search for the two devices:

<img src="https://github.com/user-attachments/assets/f47e8b3b-df81-46aa-b6e7-316080645830" width="600"/>

The hardware ID for the PCI System Peripheral is:

`HKEY_LOCAL_MACHINE\enum\PCI\VEN_15AD&DEV_0740&SUBSYS_074015AD&REV_10\BUS_00&DEV_07&FUNC_07`

<img src="https://github.com/user-attachments/assets/fe0131e5-5cfe-4679-82d1-ca8a1e187b5f" width="600"/>

Which is the VMware VMCI Bus which is used by VMware for folder sharing and dragging and dropping files:

According to Broadcom there is no Windows 98 driver for this device:

> For Windows 98 and Windows 98SE, there is no support for the VMCI device in VMware Tools. 

[Broadcom Legacy Article 1023129](https://knowledge.broadcom.com/external/article?legacyId=1023129)

The hardware ID for the PCI Universal Serial Bus is:

`HKEY_LOCAL_MACHINE\enum\PCI\VEN_15AD&DEV_0770&SUBSYS_077015AD&REV_00\188800`

<img src="https://github.com/user-attachments/assets/cb7a95f5-bcd3-4089-be2c-a8c6fa5d4540" width="600"/>

## Installing Python

Python will be used as an example of installing a program on Windows ME. The installer is available here:

* [Python 2.5.4](https://www.python.org/downloads/release/python-254/)
* [pyserial 2.1](https://sourceforge.net/projects/pyserial/files/pyserial/2.1/)
* [pywin32 2.18](https://sourceforge.net/projects/pywin32/files/pywin32/Build%20218/)

The pywin32, version 2.18 installer for Python 2.5 needs to be downloaded.

These installers can be dragged from the Windows 11 Host to the Windows ME Guest:

<img src="https://github.com/user-attachments/assets/9a854c50-075a-40f6-90a5-7ce9e6cea3b1" width="600"/>

The Python installer can be launched:

<img src="https://github.com/user-attachments/assets/656a7155-f866-4681-b10b-e9711100f884" width="600"/>

Select Install for All Users and select Next:

<img src="https://github.com/user-attachments/assets/a2ccb7a6-8ece-4aea-8a7f-1486c80c9793" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/cf176dac-0366-49cf-bacb-e11234b8b88c" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/5a4d40c3-89b0-4120-9bac-651221967500" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/4afc633c-07b3-4740-90e5-18e53ad2dc1d" width="600"/>

Open My Computer:

<img src="https://github.com/user-attachments/assets/e9fb3f4d-f1bb-40e5-9d8b-0d60bcd93199" width="600"/>

Navigate to the `C:` Drive:

<img src="https://github.com/user-attachments/assets/87943090-e906-403f-aa1e-7d51475365a5" width="600"/>

Select View the Entire Contents of this Drive:

<img src="https://github.com/user-attachments/assets/572d26cf-05c4-4518-9a36-3c901afa13bb" width="600"/>

Python 2.5 is installed in the `Python25` folder:

<img src="https://github.com/user-attachments/assets/f596e3cc-5d3d-4413-899f-3176a42fef79" width="600"/>

In this folder there is the `python.exe`:

<img src="https://github.com/user-attachments/assets/e7194cf0-c328-423b-be2b-22aacc3787b5" width="600"/>

There is no `Scripts` folder or Python Package Manager `pip` in this version of Python. The `Lib` folder contains Python's standard libraries:

<img src="https://github.com/user-attachments/assets/f0a7317d-c897-4091-810c-e98853b73a53" width="600"/>

In this folder is a subfolder called `site-packages`, where third-party libraries are installed:

<img src="https://github.com/user-attachments/assets/01ed1808-ef4f-4174-bb6d-a6c0e9a60871" width="600"/>

Currently it is empty:

<img src="https://github.com/user-attachments/assets/779c698b-04bd-40c3-9243-5e225450e570" width="600"/>

Packages were typically available in `.exe` format. Many packages relied on `pywin32` which can be installed:

<img src="https://github.com/user-attachments/assets/a1e67705-8277-4233-952c-875de1052c15" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/216a541c-06a7-4264-930c-9b09b0f3e52e" width="600"/>

The Python directory and corresponding `site-packages` directory is found. Select next:

<img src="https://github.com/user-attachments/assets/9164df32-4ee5-4908-8db0-d97c36a4296a" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/8da4bc06-0706-4d79-a7b9-45f5c513ab23" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/a58692df-8c6b-4818-b013-4bbdf2653d6b" width="600"/>

These dependencies are now found in `site-packages`:

<img src="https://github.com/user-attachments/assets/5f882b1e-822e-47c5-be83-c23d1db3e73a" width="600"/>

Repeat the same process for `pyserial`. The serial folder is now in `site-packages`:

<img src="https://github.com/user-attachments/assets/44e322e6-6c90-4e73-a7c8-37ef6d32235e" width="600"/>

The MSDOS prompt can be used to launch Python. Select Start → Programs → MS-DOS Prompt:

<img src="https://github.com/user-attachments/assets/1fd689ce-07dd-48c6-89b4-c14d461e9d70" width="600"/>

Launch Python using:

```powershell
C:\Python25\python
```

<img src="https://github.com/user-attachments/assets/aee46067-8036-4228-9e26-47b777ede8ed" width="600"/>

Notice the prompt changes to `>>>`, the Python prompt. Test Python code can be input such as:

```python
print 'Hello World!'
```

<img src="https://github.com/user-attachments/assets/4ddf366d-1712-4bb0-a216-5da5bbd19003" width="600"/>

The pyserial library can be imported using:

```python
import serial
```

<img src="https://github.com/user-attachments/assets/4947462d-3931-440d-bed6-e247a1363cfc" width="600"/>

To exit type in:

```python
exit()
```

<img src="https://github.com/user-attachments/assets/81d8b3df-2eae-49f3-b66a-b594c695410c" width="600"/>

## USB Device Passthrough

A Brother QL-570 label printer will be used as an example of a USB Device that can be connected to the Windows 2000 VM. The [Brother QL-570 Windows 2000](https://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=lpql570eas&os=43) Driver can be downloaded from from the Brother website using the Windows 11 Hst PC and copied over to the Windows 2000 VM Desktop:

<img src="https://github.com/user-attachments/assets/23de78d9-4710-43c4-bd88-26296cf46a4d" width="600"/>

The driver can be installed:

<img src="https://github.com/user-attachments/assets/5d65733a-7301-4df4-8293-024db6afe83c" width="600"/>

Select unzip:

<img src="https://github.com/user-attachments/assets/88b090fa-0773-46ed-b9c2-c33503008e3f" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/ba47ea42-3bc0-490f-a03b-6142d69ecf43" width="600"/>

Select close:

<img src="https://github.com/user-attachments/assets/4972149e-56e8-4297-a681-68c55c66c559" width="600"/>

Go to the extracted folder:

<img src="https://github.com/user-attachments/assets/8efcc74e-874b-45c7-8193-ea19c6ab3c47" width="600"/>

Launch the setup:

<img src="https://github.com/user-attachments/assets/ef8b20f1-9beb-4e2a-b8cb-937cd5b8399b" width="600"/>

Select Start:

<img src="https://github.com/user-attachments/assets/f2d0c8a5-017a-4a3e-b8bd-cde4a32d506a" width="600"/>

The driver install will prompt for connection to the printer:

<img src="https://github.com/user-attachments/assets/5076eb5d-cf36-4c82-8237-d775351b3b27" width="600"/>

When a USB device is connected to the Windows 11 Host PC and the Windows 2000 VM is launched, there will be a prompt to connect it to the Windows 11 Host PC or the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/c96f66a3-ffad-4a80-8256-a604c2103eb4" width="600"/>

Alternatively the USB device can be connected by going to Player → Removable Devices → Brother QL-570 and selecting Connect:

<img src="https://github.com/user-attachments/assets/b82aee5b-9757-4821-8ace-8e2540336a16" width="600"/>

Sellect OK:

<img src="https://github.com/user-attachments/assets/fefa2ae7-28c1-4579-a620-15b28b50fd70" width="600"/>

The Brother QL-570 passes through to the Windows 2000 VM via the Windows 11 host USB port is detected:

<img src="https://github.com/user-attachments/assets/a751ce38-4394-4d4f-af9a-9a5097031185" width="600"/>

To complete the printer driver installation the Windows 2000 VM needs to be restarted:

<img src="https://github.com/user-attachments/assets/92c00a06-aa10-489d-a400-bceb47b2b63d" width="600"/>

The p-touch editor can now be installed:

<img src="https://github.com/user-attachments/assets/5141a7c1-5976-46f6-b588-78f534f3bbf8" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/7697e79d-44e9-4faa-8c9c-b915d2d3a615" width="600"/>

Input your user name and select next:

<img src="https://github.com/user-attachments/assets/5344cafa-9245-46d6-a60b-60a2002dcc69" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/0b38c79d-a95b-4153-b6a1-eeb5e9a93f9d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/e855638a-50ae-479c-a5d7-81b43e6340b5" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/d805eb43-e690-48c7-94da-b3dde348806e" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/0bda3352-56a4-4898-8ace-245f65483348" width="600"/>

Select finish and restart the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/e3a40afd-3db8-40ce-8513-f917f8d689c4" width="600"/>

Launch the p-touch editor:

<img src="https://github.com/user-attachments/assets/9b640093-b1c5-49b0-8db8-6838ddd00868" width="600"/>

Select the BrotherQL-570 printer:

<img src="https://github.com/user-attachments/assets/66d489bc-5998-415f-be5b-f71375db8787" width="600"/>

Create a test label:

<img src="https://github.com/user-attachments/assets/7e17576e-63de-404a-a01b-5370cff561cd" width="600"/>

Select print:

<img src="https://github.com/user-attachments/assets/d3f090f4-587e-4ecb-a011-bc3a83a02220" width="600"/>

The ptouch editor on the Windows 2000 VM prints to the QL-570 attached to the host PC using VMwares USB passthrough:

<img src="https://github.com/user-attachments/assets/cd119cbf-51b5-4274-9715-b4646a5d361c" width="600"/>

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

<img src="https://github.com/user-attachments/assets/865199af-f476-4d3a-b821-41d5568a7058" width="600"/>

Select Add...:

<img src="https://github.com/user-attachments/assets/8ed534f3-f9a8-4c54-b5fc-2103d640e700" width="600"/>

Select Serial Port and Finish:

<img src="https://github.com/user-attachments/assets/3b4c2dc4-84e5-4f27-91df-773f3a9bb67b" width="600"/>

Select Connect at Power On. Autodetect is useful for a single port, but for multipe ports, it is more useful to select the serial Port indiviually. In this example COM3 will be used:

<img src="https://github.com/user-attachments/assets/98fc0369-8b8a-4299-b7d6-3eed19bf55dc" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/47ce415a-ec42-4ab7-a7ab-eb2b37c83fa9" width="600"/>

Launch the VM:

<img src="https://github.com/user-attachments/assets/c37f2fdb-e39b-46e1-83ac-59fdbabc3d14" width="600"/>

Right click My Computer and select Properties:

<img src="https://github.com/user-attachments/assets/30514a5d-70f4-4bf0-bc5c-245734a565d8" width="600"/>

Select the hardware tab and then device manager:

<img src="https://github.com/user-attachments/assets/fc66c338-8512-4b06-b982-2a7165b15acd" width="600"/>

Expand ports, note the Windows 11 COM3 is passed through to the Windows 2000 VM as COM1:

<img src="https://github.com/user-attachments/assets/072cbe90-58c4-4f9b-8cbe-a8c90480afde" width="600"/>

Right click the communication port and select properties:

<img src="https://github.com/user-attachments/assets/e85d671c-7b30-45c1-9016-fa6b55da28da" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects (consistent with the settings on the Windows 11 Host):

<img src="https://github.com/user-attachments/assets/af4fa0e1-acdc-481f-a1d6-be3e1799c5ab" width="600"/>

Select Advanced:

<img src="https://github.com/user-attachments/assets/b25ca227-6356-4da1-ad17-8c4b40ff92f5" width="600"/>

Update the COM Port Number to be consistent with the Windows 11 Host:

<img src="https://github.com/user-attachments/assets/dd217523-f84b-415e-a9f7-5730f57ff293" width="600"/>

In this case COM3. Select OK:

<img src="https://github.com/user-attachments/assets/8b395e07-919e-4b87-8acb-07e98dd2fc88" width="600"/>

The Serial Port COM3 is now ready for use in the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/a2fa4051-045f-4861-9aa4-d8c613e4db07" width="600"/>

I don't have a device that connects via Serial Port, so will test the Serial Port using Python with pyserial. The Serial Port looks like the following:

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

<img src="https://github.com/user-attachments/assets/d2e87382-eeb1-489c-a455-14fa06bc202b" width="600"/>

Paste in the following code:

```python
import time
import serial

# Replace 'COM3' with your serial port
port = 'COM3'
baudrate = 9600

# Open the serial port
ser = serial.Serial(port, baudrate, timeout=1)

time.sleep(2)  # give the port some time to initialize

# Test data
test_data = b'Hello Serial\n'

# Write data
ser.write(test_data)
print('Sent: {}'.format(test_data))

# Read back data
received = ser.read(len(test_data))
print('Received: {}'.format(received))

# Check if the loopback worked
if received == test_data:
    print('Serial loopback test passed!')
else:
    print('Serial loopback test failed!')

ser.close()
```

<img src="https://github.com/user-attachments/assets/f33acf19-c285-45df-b15e-257079e4cb5a" width="600"/>

Select file → save as:

<img src="https://github.com/user-attachments/assets/f3806b60-0495-4784-874f-dc410702b960" width="600"/>

Save the file as `script.py` ensuring that save as type is All Files and Encoding is UTF-8:

<img src="https://github.com/user-attachments/assets/59be9405-9cb5-416c-a0be-e3219a93a1ca" width="600"/>

The script file is in Documents. Right click the script file and select Properties:

<img src="https://github.com/user-attachments/assets/324ae497-9dae-42f7-9862-c1544cdade63" width="600"/>

Copy the file location:

<img src="https://github.com/user-attachments/assets/2952ccc1-a0c8-45eb-a84e-8e96d08e4a47" width="600"/>

The file path contains spaces:

```powershell
C:\Documents and Settings\Philip\My Documents\script.py
```

To prevent CMD from taking `C:\Documents`, `and`, `Settings\Philip\My` and `Documents\script.py` as seperate command line arguments, double quotations much be used:

```powershell
"C:\Documents and Settings\Philip\My Documents\script.py"
```

Because this is a long path name, the DOS path is often more convenient:

```powershell
C:\DOCUME~1\Philip\MYDOCU~1\script.py
```

The Python script can be launched using:

```powershell
python C:\DOCUME~1\Philip\MYDOCU~1\script.py
```

With no pins connected, the following shows:

<img src="https://github.com/user-attachments/assets/e0842283-bc24-4526-a8e9-e92c91a986fe" width="600"/>

<img src="https://github.com/user-attachments/assets/b439d546-ebef-403c-b24b-f5ecbd9d1ef8" width="600"/>

With pins 2 and 3 connected, the following shows:

<img src="https://github.com/user-attachments/assets/0ec50a62-e408-469d-ae8f-493599320523" width="600"/>

<img src="https://github.com/user-attachments/assets/80a262c7-1f01-43dc-b989-479977dbdbf5" width="600"/>

The code works as expected and interfaces with the Serial Port which is passed through to the Windows 2000 Guest VM from the Windows 11 Host PC.

## Parallel Port Passthrough

VMware can theoretically passthrough a physical parallel port. However, USB-to-parallel adapters are designed exclusively for printers and do not provide true parallel port functionality for other hardware. By the time of Windows 2000, parallel ports were already considered legacy and were rarely included on new PCs. I do not have a parallel port printer available to test passthrough functionality.

## PCI/PCIe Card Passthrough

VMware does not support direct passthrough of PCI or PCIe cards to a guest virtual machine. Additionally, there are no USB adapters that replicate the functionality of PCI/PCIe expansion cards.

Return to [VMware Installation Guide](../readme.md).

Python is just used as an example of a legacy program to run in a Windows 2000 VM and not covered in detail in this tutorial. For details about using Python, see my other GitHub repository [Python Tutorials](https://github.com/PhilipYip1988/python-tutorials).
