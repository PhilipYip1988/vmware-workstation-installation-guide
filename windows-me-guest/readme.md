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




## Installing Python

Python will be used as an example of installing a program on Windows ME. The installer is available here:

* [Python 2.5.4](https://www.python.org/downloads/release/python-254/)
* [pyserial 2.1](https://sourceforge.net/projects/pyserial/files/pyserial/2.1/)
* [pywin32 2.18](https://sourceforge.net/projects/pywin32/files/pywin32/Build%20218/)

The pywin32, version 2.18 installer for Python 2.5 needs to be downloaded.

