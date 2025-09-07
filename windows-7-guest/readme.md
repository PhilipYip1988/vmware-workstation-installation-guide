# Windows 7 Guest

Setting up a Windows 7 Guest using VMware Workstation Player.

## YouTube Video

* [YouTube](https://www.youtube.com/watch?v=rZ8DaVV_skk)

## Notes

VMware Workstation Player 17.6.4 has Windows 7 as an option for a Virtual Machine. However Windows 7 is regarded as a legacy Operating System and isn't tested by Broadcom. Moreover the VMware Tools 12.5.3 which comes with VMware workstation player doesn't support Windows 7 and the following errors will display if they are attempted to be installed in the Windows 7 VM:

<img width="802" height="711" alt="Screenshot 2025-09-01 043806" src="https://github.com/user-attachments/assets/cf5f06b6-8ff1-4404-b869-264c1f16af25" width='600'/>

VMware Tools 11.0.6 is the last version of VMware Tools to support Windows 7 and should be downloaded seperately as an ISO. This ISO should be mounted in the VM so they can be installed manually.

On modern hardware, with a 12th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
firmware = "efi"
```

The first setting allows the CPU to optimise the VM performance, the VM may be very slow without this setting. The second setting prevents use of a memory management unit that Windows 7 doesn't understand and can lead to a Blue Screen of Death (BSOD). The third setting prevents VMware from using Vulkan for rendering, which isn't supported by Windows 7 and often leads to black screens. The last two settings prevent Windows 7 from seeing unsupported CPU features which Windows 7 doesn't understand and can lead to a Blue Screen of Death (BSOD).

## Installation Media

### Dell Windows 7 Reinstallation ISO

To download the Dell Windows 7 Professional Reinstallation ISO Media Refresh 2016 (`GDXKK_X8V66A00_W7SP1PRO64_ROW.iso`). Use the Windows ISO Download Tool which downloads the ISO from Dell's servers:

* [Windows ISO Download Tool](https://www.heidoc.net/joomla/technology-science/microsoft/67-microsoft-windows-and-office-iso-download-tool)

Launch the Windows ISO Download Tool:

<img src='./images/img_001.png' alt='img_001' width='600'/>

To the right hand side select Dell, then select Dell OptiPlex 7040, Windows 7 Professional 64 Bit (or 32 Bit) and then Download:

<img src='./images/img_002.png' alt='img_002' width='600'/>

Alternatively the Website Archive.org hosts the ISO file:

|Edition|Architecture|ISO|SHA256|
|---|---|---|---|
|Professional|x64|[GDXKK_X8V66A00_W7SP1PRO64_ROW.iso](https://archive.org/details/dell-windows)|5CCD8F03C950AC590F01125E17090DF3D75E71B3B7BF14FC64B8493BBCB4A4FC|
|Professional|x86|[MT5KY_N6N9GA00_W7SP1PRO32_ROW(DL).iso](https://archive.org/details/dell-windows)|B33B6B5A5C98AD33729741B2F2FE4C74BC7A8677F7C13D0C4966FD9AE5ED2C14|

To check the SHA256, right click the ISO file and select copy as path:

<img src="https://github.com/user-attachments/assets/352a0bad-1698-4819-81e1-604fb73b0fb9" width="600"/>

Open up the Windows Terminal and use the command:

```powershell
Get-FileHash "C:\Users\Philip\Downloads\GDXKK_X8V66A00_W7SP1PRO64_ROW.iso"
```

<img src="https://github.com/user-attachments/assets/b31ebe0e-2bfa-44c7-af7c-0abfb359f2c9" width="600"/>

### WSUS Offline Update

The Website Archive.org hosts the ISO created from WSUS Offline Update before Microsoft removed Windows 7 downloads from their download servers. Select `wou-w61-x64 [2023-v1].iso` for Windows 7 64 Bit or `wou-w61-x86 [2023-v1].iso` for Windows 7 Bit respectively.

|ISO|SHA256|
|---|---|
|[wou-w61-x64 \[2023-v1\].iso](https://archive.org/details/windows7updates24)|Unavailable|
|[wou-w61-x86 \[2023-v1\].iso](https://archive.org/details/windows7updates24)|Unavailable|

### VMware Tools ISO

The Windows 7 drivers for the Windows 7 Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

|ISO|SHA256|
|---|---|
|[VMware Tools Version 11.0.6](https://archive.org/details/vmware-tools-windows-11.0.6-15940789)|8F1CC3181055891B98672F715E0CA7BBE4018960EAE945D7A4B9F640C44C3D79 |

<img src='./images/img_004.png' alt='img_004' width='600'/>

## Windows 11 Host or Ubuntu 24.10 Host System Requirements

Your Windows 11 Host PC or Ubuntu Host PC should satisfy the minimum system the system requirements of Windows 11 and have additional overhead to run a Virtual Machine in addition to these requirements. It is recommended to have a Host PC with at least:

* i5 or i7 11th Generation Intel Processor or Newer
* 16 GB RAM
* 1 TB SSD

## Configuring Virtual Hardware for a Windows 7 Guest

Select File → New Virtual Machine:

<img src='./images/img_005.png' alt='img_005' width='600'/>

Select I will Isntall the Operating System Later:

<img src="https://github.com/user-attachments/assets/9b3f5b1b-99bb-4a39-a75c-a8d06275529d" width="600"/>

**Note do not select Isntaller Disc Image File (ISO) in this screen because VMware will use the asy install which will override the `sources/$OEM$` folder and the `sources/ei.cfg` file, essentially converting the OEM ISO to retail and prompt for a Retail Product Key.**

Select Microsoft Windows and Windows 7 x64 or Windows 7 x86 and select Next:

<img src='./images/img_009.png' alt='img_009' width='600'/>

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive, you may want to move this to a local only location) and select next:

<img src="https://github.com/user-attachments/assets/8fc9ba02-e49f-436a-bc78-64499762367e" width="600"/>

Note the name and location as these will be used later.

The default maximum size of the Windows 7 Guest is 40 GB which is too small, I recommend increasing this to 256 GB. Note the files on the Windows 11 Host won't be 256 GB but can be up to 256 GB if the Windows Vista Guests Virtual Drive is fully occupied with files:

<img src="https://github.com/user-attachments/assets/2f002035-a952-4bcc-8ba3-195a087b468c" width="600"/>

Select customise hardware...

<img src="https://github.com/user-attachments/assets/baad016d-9d3d-4507-bee1-b5bfe85f72bc" width="600"/>

The default memory used by the Windows 7 Guest is 2048 MB (2.0 GB). If the Windows 11 Host PC has ≥16 GB RAM, this can be upped to 4096 MB (4 GB) for increased performance of the VM. Note if the Windows 11 Host PC has ≤8 GB of RAM, setting the RAM to 4096 MB (4 GB) may throttle the Host PC leading to decreased performance and 2048 MB (2 GB) may be more approprate:

<img src="https://github.com/user-attachments/assets/b60d5599-2f5c-41f4-a35c-d0a220b1d13a" width="600"/>

The default number of processors cores used by the Windows 7 Guest is 1. This can be upped to 2 or 4 if the Windows 11 Host has a processor with ≥ 16 cores. If the Windows 11 Host PC has ≤16 cores, setting this to a higher value may throttle the Host PC leading to an overall decreased performance:

<img src="https://github.com/user-attachments/assets/264d69b4-1cc6-4338-9578-21fefad91d01" width="600"/>

Under CD/DVD select browse:

<img src="https://github.com/user-attachments/assets/dccb48ec-4ac6-4f64-832e-3d759d20d74c" width="600"/>

Load the Dell Windows 7 Professional Media Refresh 2016 Reinstallation x64 (64 Bit) or x86 (32 Bit) ISO:

<img src="https://github.com/user-attachments/assets/c91ff09b-12f6-4032-b1c3-b3f6be2356c4" width="600"/>

Ensure connected at power on is enabled:

<img src="https://github.com/user-attachments/assets/a48eb1ec-85dd-4c4a-82cf-58b42624482d" width="600"/>

Windows 7 has reached end of life and should be deemed unsafe to use online. The virtual network adaptor is connected by default and can optionally be disabled:

<img src='./images/img_018.png' alt='img_018' width='600'/>

The default USB Controller for Windows 7 is USB 2.0 as the Windows 7 SP1 Installation ISO provided in 2011 lacked the storage controller for newer hardware preventing the mouse and keyboard from working during the Windows Setup when attached to a USB 3.0 port:

<img src='./images/img_019.png' alt='img_019' width='600'/>

The Windows 7 Professional Index of the Dell Windows Windows 7 ISO was updated in 2016 to contain USB 3.0 drivers so this can be changed to USB 3.0:

<img src='./images/img_020.png' alt='img_020' width='600'/>

The default Sound Card can be used for the Windows 7 Guest:

<img src='./images/img_021.png' alt='img_021' width='600'/>

The default Display can be used for the Windows 7 Guest:

<img src='./images/img_022.png' alt='img_022' width='600'/>

Select Close and Finish:

<img src='./images/img_023.png' alt='img_023' width='600'/>

## Windows 7 Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows 7 Guest is installed: 

<img src="https://github.com/user-attachments/assets/33f615b5-08b3-48cf-a11b-5e51e3baecd7" width="600"/>

Look for the `Windows 7 x64.vmx` file:

<img src="https://github.com/user-attachments/assets/b8ca905f-ea8c-4966-83a8-f9791465e2b4" width="600"/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/cfa16b5c-56c8-4355-80bb-6e92d2fb383a" width="600"/>

<img src="https://github.com/user-attachments/assets/613e55e4-278c-4377-b624-afe947a23f64" width="600"/>

Press `Ctrl+f` to begin a search for an option for example `bios.bootDelay`:

<img src="https://github.com/user-attachments/assets/752bef46-4a2c-4730-9870-910dccaa632a" width="600"/>

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/2b4f24c6-6ca6-45b9-9239-4f5714797372" width="600"/>

The command above will change the time the Windows 7 Guest Virtual BIOS displays before selecting the default boot option giving more time to select the option to boot from CD/DVD. This line can be removed post-installation.

### Modern Generation Processors (11-14th Generation)

Certain legacy settings may need to be configured to run older guest operating systems such as Windows 7:

<img src="https://github.com/user-attachments/assets/337869a0-b646-4462-912d-7111bb8f2b0f" width="600"/>

Legacy CPU settings:

```
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

These settings help emulate older CPU instructions that XP expects.

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

The firmware should be EFI for Windows 7 64 Bit:

```
firmware = "efi"
```

These settings ensure proper CPU and MMU handling for legacy guests.

### OEM SLP

OEM SLP is not applied by default:

<details>
  <summary>SLIC 2.1 Passthrough</summary>

If the Windows 11 Host PC came with a Windows 10 Professional OEM License, it has upgrade rights to Windows 11 Professional and downgrade right to Windows 7 Professional. The downgrade rights to Windows 7 Professional can be used by passing through the SLIC 2.1 to the Virtual Machine by adding the line to the Virtual Machines Configuration File:

```
acpi.passthru.slic = "TRUE"
acpi.passthru.slicvendor = "TRUE"
SMBIOS.reflecthost = "TRUE"
```

Note if the Windows 11 Host PC doesn't have a SLIC 2.1, the above lines of code will prevent the Windows 7 Guest from booting and should be removed.

</details>

<details>
  <summary>Modded ROMs</summary>

The my digital life forums has a post about a modded Virtual BIOS which includes a Dell SLIC 2.1 compatible with Dell Windows 7 Professional OEM SLP. These ROMs are not supported by Microsoft or Dell (but then neither is Windows 7). You will need to log into their forums to view the files:

* [My Digital Life: SLIC 2.1 Mod](https://forums.mydigitallife.net/threads/vmware-workstation-esxi-bios-efi-slic-mod.64693/#post-1132133)

Extract the downloaded file and navigate to the `17.6.0 Modded ROMs` folder. Rename `WORKSTATION_17.6.0_DELL2.7_SLIC_EFI20-64.ROM` to `EFI20-64.ROM` and copy the modded ROM to the directory of the Windows 7 64 Bit Guest (with UEFI). Update the Virtual Machine Configuration file to:

```
efi20-64.filename = "modded_EFI20-64.ROM"
```

Extract the downloaded file and navigate to the `17.6.0 Modded ROMs` folder. Rename `WORKSTATION_17.6.0_DELL2.7_SLIC_BIOS.440_(497).ROM` `WORKSTATION_17.6.0_DELL2.7_SLIC_BIOS.440_(497).ROM` to `modded_BIOS.440.ROM` and copy the modded ROM to the directory of the Windows 7 32 Bit Guest or Windows 7 64 Bit Guest (without UEFI). 

```
bios440.filename = "modded_BIOS.440.ROM"
```

Note if the corresponding ROM is not found in the directory the above line of code will prevent the Windows 7 Guest from booting.

</details>

## Installing the Windows 7 Guest OS

Select the Windows 7 Virtual Machine and select Play:

<img src="https://github.com/user-attachments/assets/963e7326-4604-4e52-b482-0ec2baae00e6" width="600"/>

Loading files will display:

<img src='./images/img_031.png' alt='img_031' width='600'/>

Starting Windows will display:

<img src='./images/img_032.png' alt='img_032' width='600'/>

The Dell Windows 7 Reinstallation .iso is multi-lingual, select your language:

<img src="https://github.com/user-attachments/assets/7f22615d-7900-47ea-baec-cfc1a2df912b" width="600"/>

Select your Time and Currency Format and select Next:

<img src="https://github.com/user-attachments/assets/049b27ec-b172-42fc-8ae0-c0c6eba4c663" width="600"/>

Select Install Now:

<img src="https://github.com/user-attachments/assets/c20e2205-ba12-4c2e-89d0-6aeffd112095" width="600"/>

Accept the License Agreement and select Next:

<img src="https://github.com/user-attachments/assets/f913a2c6-a359-4969-8248-9bced948a22c" width="600"/>

Select Custom Advanced:

<img src="https://github.com/user-attachments/assets/048d18e1-3190-41ca-b5f3-355a5c459b14" width="600"/>

Select Disc 0: Unallocated Space and select Next:

<img src="https://github.com/user-attachments/assets/eb458453-0b7a-4eff-98f1-0962bd450155" width="600"/>

Input your User Name and PC Name:

<img src='./images/img_039.png' alt='img_039' width='600'/>

Leave the password blank. A blank password is required to update Windows 7 unattended. Select Next:

<img src='./images/img_040.png' alt='img_040' width='600'/>

Select Next:

<img src='./images/img_041.png' alt='img_041' width='600'/>

Select Home Network, or use the Virtual Machine Settings to disconnect the Virtual Network Adaptor:

<img src='./images/img_042.png' alt='img_042' width='600'/>

## Backing up the VM

Shut down the Windows 7 VM and then create a copy of the VM folder. Should you encounter problems with your VM after installing software, you can delete the original folder and rename the copied folder to the original folders name. Essentially this will give you a VM to roll back to:

<img src="https://github.com/user-attachments/assets/b3af2149-7e37-4fa1-b7e2-22406fc4586c" width="600"/>

## Installing Windows Updates

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/11475c45-f02e-4a57-b553-39e0d4fd839e" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/d3823f67-032f-480f-8e62-06602d8d9941" width="600"/>

Select `wou-w61-x64 [2023-v1].iso` or `wou-w61-x86 [2023-v1].iso` and select open:

<img src="https://github.com/user-attachments/assets/7de2ea4a-a101-4d18-af4c-11373d580935" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/c827282b-9512-429e-83c3-c0df979a0edd" width="600"/>

Select WSUS Offline Udpate:

<img src="https://github.com/user-attachments/assets/3154f248-3c31-46c7-9a6e-a86b4ac054b9" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/c743be1b-0815-4a58-a607-6fd328823f59" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/dd83cfce-a5a3-4373-91e6-b03082c99dcd" width="600"/>

Select Fully Automated Process (Reboot, Recall and Shut Down) and select Start:

<img src="https://github.com/user-attachments/assets/0e0703d9-ec5c-4c28-90de-eb424a009806" width="600"/>

The WSUS Offline Udpate will begin installing Microsoft Frameworks and Updates:

<img src="https://github.com/user-attachments/assets/9fc86e5f-c325-426a-9c48-dbaa4607868f" width="600"/>

WSUS Offline Update will install a very large number of updates unattended, and reboot the VM after installing updates. This will take a few hours and should not be interrupted. If it is interrupted, the VM may blue screen and you may need to close the VM, then delete the VM folder. Then you can rename the copy of the unpatched Windows 7 back to the original (and create another copy) and retry.

<img src="https://github.com/user-attachments/assets/f611d976-39ab-40dc-b691-6a4c17e7f639" width="600"/>

After installing updates the VM will shut down. Relaunch the VM and go to Computer:

<img src="https://github.com/user-attachments/assets/947777fe-89a5-4671-948d-3f581fbbfa70" width="600" />

Select Uninstall of Change a Program:

<img src="https://github.com/user-attachments/assets/84a49943-1ac0-44d7-9f73-e44a048c5c29" width="600"/>

The Microsoft Frameworks are installed, select View Installed Updates:

<img src="https://github.com/user-attachments/assets/89fd3205-840b-46b8-b5e4-7f49e8d6fdec" width="600"/>

Al the updates required for Windows 7 are installed:

<img src="https://github.com/user-attachments/assets/a6304b00-cd5d-4dfa-bd3f-c19f1ea3cf58" width="600"/>

It is recommended to back up the VM by creating another copy of the folder.

## Installing VMware Tools

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/8002c7b0-8396-4b82-b152-98be887bd63e" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/eb7ff352-6cdb-45e8-beab-1c343de52868" width="600"/>

Load the `VMware-tools-windows-11.0.6-15940789.iso`:

<img src="https://github.com/user-attachments/assets/49f1374e-521f-4e61-a996-352ca6677e9b" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/25019f6f-37dc-4446-9c3a-4f0651916dca" width="600"/>

On Windows 7 64 Bit select Run `setup64.exe`, on Windows 7 32 Bit select Run `setup.exe`:

<img src="https://github.com/user-attachments/assets/8a589ff5-5862-4169-a8e8-107e5c3983c3" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/3688a960-ed0d-4d80-9160-bc262ad30251" width="600"/>

Select Next:

<img src='./images/img_048.png' alt='img_048' width='600'/>

Select Next:

<img src='./images/img_049.png' alt='img_049' width='600'/>

Select Next:

<img src='./images/img_050.png' alt='img_050' width='600'/>

Select Install:

<img src='./images/img_051.png' alt='img_051' width='600'/>

Select Finish:

<img src='./images/img_052.png' alt='img_052' width='600'/>

Select Yes:

<img src='./images/img_053.png' alt='img_053' width='600'/>

## Shared Folders

Create a new folder on the Windows 11 Host or Ubuntu 24.10 Host PC called `vmshared`:

<img src="https://github.com/user-attachments/assets/2c6992d8-2956-4ed3-82c3-40d31a9652c1" width="600"/>

<img src="https://github.com/user-attachments/assets/00f073e9-a589-4bdb-b114-22f1c5e69986" width="600"/>

Select Player → Manage → Virtual Machine Settings:

<img src="https://github.com/user-attachments/assets/597b51d9-9b5a-465f-abf7-a97613899d28" width="600"/>

Select Options → Shared Folders and change the setting to Always Enabled and check Map Network Drive in Windows Guests. Then select Add:

<img src="https://github.com/user-attachments/assets/dd44fdf8-20fb-4a5c-9285-d68dcb9ef532" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/d14fac4b-150c-4c8c-a4c0-ac7ce002947c" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/cb5ee26c-a8a1-4610-8488-f3292e22c4a0" width="600"/>

Select the `vmshared` folder and select OK:

<img src="https://github.com/user-attachments/assets/d52c89f1-0cc4-4e7f-b52a-660ef3af9ee4" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/eb4cd9da-7465-4b6c-8ba2-cb2ff09ce534" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/4b249dbc-a92d-4281-92e4-4fcc85c1084c" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/63d4b01e-8738-437c-8b83-b52cfeea32a6" width="600"/>

Select Computer:

<img src="https://github.com/user-attachments/assets/77f90bcc-9f91-4d5f-8074-ed4444bd6824" width="600"/>

Select Shared Folders:

<img src="https://github.com/user-attachments/assets/5b2900d6-11a3-4f9d-85ad-3f5bb1371076" width="600"/>

Select `vmshared`:

<img src="https://github.com/user-attachments/assets/ac2e50b6-b314-4a7d-909b-3eff1d6ef9b4" width="600"/>

This is empty just now:

<img src="https://github.com/user-attachments/assets/9c0ecf86-4cab-4af4-bd7e-6cb63a464ce7" width="600"/>

## Installing Python

Python will be used as an example of installing a program on Windows 7. [python-3.8.10-amd64.exe](https://www.python.org/downloads/release/python-3810/) is the latest version of Python to work on Windows 7. The installer can be downloaded on the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/53b12abd-f0dd-4462-9a56-b25ca63bc681" width="600"/>

When using a Windows 11 Host, the file can be dragged and dropped over to the VM. On a Linux host, the most commonly used Desktop Environment GNOME (and less common Desktop Environments) are not supported and shared folders have to be configured:

<img src="https://github.com/user-attachments/assets/17b57ab0-0ce2-4ed9-928c-c96f04e3d3f2" width="600"/>

Launch the setup:

<img src="https://github.com/user-attachments/assets/1dc52846-f321-43fb-a4d8-6f807a5561b6" width="600"/>

Select add to path and then select install now:

<img src="https://github.com/user-attachments/assets/96666f6f-4d57-4a4b-9b3e-8e3e09f35e0b" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/4f9083e0-8cda-483b-bcf3-efc5479854ee" width="600"/>

Select Close:

<img src="https://github.com/user-attachments/assets/eda83226-d680-44da-9ab9-083c847208e2" width="600"/>

Open the Command Prompt:

<img src="https://github.com/user-attachments/assets/fe14b967-3977-4c6e-9f2d-5a7630cdcebb" width="600"/>

To launch Python input:

```powershell
python
```

Notice the change to the Python prompt `>>>`:

<img src="https://github.com/user-attachments/assets/23ae902a-41bf-45c6-8be0-77988f8f4882" width="600"/>

Python code can now be used:

```python
print('Hello World!')
```

<img src="https://github.com/user-attachments/assets/57eef803-e6ab-4eb9-be91-8aff13b08cf5" width="600"/>

To exit python input the function:

```python
exit()
```

<img src="https://github.com/user-attachments/assets/155f7a9c-50d9-459e-9924-2687fa5934be" width="600"/>

Notice the return to the CMD prompt. 

To use the package manager requires Internet Connectivity. Select Player → File → Network Adaptor → Connect:

<img src="https://github.com/user-attachments/assets/49c2014c-6e37-4564-897f-55d937b0e64d" width="600"/>

Recall however that Windows 7 is past end of life and is not safe to use online for general web use.

Select Home Network or Work Network:

<img src="https://github.com/user-attachments/assets/32652067-ccd7-442d-a816-b7b9f6ba60da" width="600"/>

<img src="https://github.com/user-attachments/assets/1d8c5273-d8d8-41d9-a4fd-774795b2d539" width="600"/>

The Python package can be installed using:

```powershell
pip install pyserial==3.5
```

<img src="https://github.com/user-attachments/assets/3bc9dfc5-796c-46f2-84d5-00e97df33aff" width="600"/>

And can be imported into a Python program:

<img src="https://github.com/user-attachments/assets/6e674756-696b-4e83-aa54-dc911454a2b8" width="600"/>

## USB Passthrough

A legacy USB Device can be passed through from the Windows 11 Host or Ubuntu 24.10 to the Windows Vista Guest. In this example a Logitech Pro 9000 webcam will be used. The Logitech Pro 9000 is a USB 2.0 camera which had HD 720p (1280×720 pixels) and 30 fps which is effectively at the limit of USB 2.0. The Windows XP driver and software can be downloaded on the Windows 11 Host:

<img src="https://github.com/user-attachments/assets/4c18a4c9-04b7-4eff-94ad-4adab6ba11e5" width="600"/>

The installer can be copied to `vmshared` or directly dragged and dropped from the Windows 11 Host to the Windows 7 Guest:

<img src="https://github.com/user-attachments/assets/f81de79f-908e-49f1-809a-6f85e0cf7479" width="600"/>

Select Computer:

<img src="https://github.com/user-attachments/assets/910245b0-a70c-40a8-b60a-e89cf385d6d1" width="600"/>

Shared Folders:

<img src="https://github.com/user-attachments/assets/1743161a-8a8a-42cc-8843-b184689ce513" width="600"/>

And the `vmshared` folder:

<img src="https://github.com/user-attachments/assets/90df7f28-d50d-4d33-8f3e-06c4d0c5dcb3" width="600"/>

If the application does not show, the shared folder may need to be refreshed, right click the folder and select refresh:

<img src="https://github.com/user-attachments/assets/f79a61c0-0aeb-42b4-94f5-95613beb4c7e" width="600"/>

Launch the installer:

<img src="https://github.com/user-attachments/assets/3611dd3b-d971-41f1-b291-d9fc4d203d4b" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/1db5b764-bb9b-41fb-b541-3a08a8892288" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/f9e241d1-d00b-4006-aa71-da0ce3c9c4a6" width="600"/>

Attach the USB Device, in this case the Logitech Pro 9000 to the USB Port. VMware will show the New USB Device Detectd Dialog which will allow you to connect the USB either to the Host or the VM:

<img src="https://github.com/user-attachments/assets/ffd6c573-98d0-4be2-b7bd-5cd1e4f39d01" width="600"/>

When prompted to connect the webcam, pass through the USB device from the Windows 11 Host to the VM using Player → Removable Devices → Logitech USB Device → Connect:

<img src="https://github.com/user-attachments/assets/15e11094-0f9e-42ad-9817-afd254332055" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/fe2c34a2-f7fc-4bbc-95ae-750c54c365bc" width="600"/>

The found new hardware wizard will show:

<img src="https://github.com/user-attachments/assets/d0a622ec-b251-4886-80a6-280692debc0f" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/0720abaa-2445-4ed2-a99b-43f438484b07" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/f8f5e50e-776d-4dee-83a9-ad646e137b96" width="600"/>

The video from the webcam should display, although it doesn't in this case select next:

<img src="https://github.com/user-attachments/assets/86006e33-25d3-49cc-b6ea-ec78e3ff1ff9" width="600"/>

Select check out my webcam:

<img src="https://github.com/user-attachments/assets/d3ba0e1c-fb63-4a4d-a6c6-1d1a445c1ff3" width="600"/>

Select Quick Capture:

<img src="https://github.com/user-attachments/assets/57f3ec3b-8480-49bb-a5a6-c5b36d980172" width="600"/>

The webcam software can be used in the Windows Vista Guest to control the Logitech Pro 9000 which has been passed through from the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/578e5164-7242-4f9c-b243-4de53df123cc" width="600"/>

Again the video from the webcam should display but doesn't in this case. This may be because the USB 3.1 passthrough is used.

Power down the Windows 7 VM and select Edit Machine Settings:

<img src="https://github.com/user-attachments/assets/9a2a185c-dc81-45d1-8b88-c148230738d2" width="600"/>

Select USB Controllerand change the USB compatibility from USB 3.1 to USB 2.0:

<img src="https://github.com/user-attachments/assets/334f8d0e-77e5-4efd-9074-a537f817c392" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/e717b0ae-442c-4e10-8f55-d227e03a23ef" width="600"/>

Select Play Virtual Machine:

<img src="https://github.com/user-attachments/assets/b8c3845b-d6ae-4f7c-9562-dd2383f15bff" width="600"/>

Select Quick Capture:

<img src="https://github.com/user-attachments/assets/c252fb0b-6a09-432b-8876-de7ee697b4b3" width="600"/>

The webcam software can be used in the Windows 7 Guest to control the Logitech Pro 9000 which has been passed through from the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/50a4d57f-d50a-4a5d-8f6a-d1363f3dbd39" width="600"/>

## Serial Port Passthrough

Close the Windows Vista VM. Attach a USB to Serial Port to the Window 11 Host PC:

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

<img src="https://github.com/user-attachments/assets/43253763-ae7c-484e-a2f3-57be52a9e178" width="600"/>

Select Add...:

<img src="https://github.com/user-attachments/assets/6c0f92f2-7484-425a-b83d-7153c4ae9095" width="600"/>

Select Serial Port and Finish:

<img src="https://github.com/user-attachments/assets/93fc8640-0137-4e91-b473-e2acecd3416d" width="600"/>

Select Connect at Power On. Autodetect is useful for a single port, but for multipe ports, it is more useful to select the serial Port indiviually. In this example COM3 will be used:

<img src="https://github.com/user-attachments/assets/733582a8-1935-4b7a-996c-e4a05d54c556" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/3e9e87b7-a969-4e22-bb14-ccfa3eda9b6c" width="600"/>

Launch the VM:

<img src="https://github.com/user-attachments/assets/04a359b2-003a-495e-8153-d768fadf41d8" width="600"/>

Right click computer and select properties:

<img src="https://github.com/user-attachments/assets/f17aaf59-a2f9-4530-bd33-0eadfc7f7762" width="600"/>

Select Device Manager:

<img src="https://github.com/user-attachments/assets/5c1ca82c-9225-4956-983d-a6385f00d384" width="600"/>

Select Continue:

<img src="https://github.com/user-attachments/assets/e6b5cc9b-3173-4557-92de-70048a82c237" width="600"/>

Expand ports, note the Windows 11 COM3 is passed through to the Windows 2000 VM as COM1:

<img src="https://github.com/user-attachments/assets/536792bc-3c84-44d3-82ec-415f042c1cb2" width="600"/>

Right click the communication port and select properties:

<img src="https://github.com/user-attachments/assets/e436a1f5-8a59-4a83-a33a-95ebd414cbe6" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects (consistent with the settings on the Windows 11 Host):

<img src="https://github.com/user-attachments/assets/1f54b213-3e96-4066-ac1e-830601eca734" width="600"/>

Select Advanced:

<img src="https://github.com/user-attachments/assets/ee0d1939-586d-46b1-a46c-9644f70f414b" width="600"/>

Update the COM Port Number to be consistent with the Windows 11 Host. In this case COM3. Select OK:

<img src="https://github.com/user-attachments/assets/b7ac9e19-febb-49ef-b26a-2b67d5411d4d" width="600"/>

The Serial Port COM3 now displays correctly in the device manager but is not available for use in other programs until the Windows Vista VM is restarted:

<img src="https://github.com/user-attachments/assets/2d72397b-fe58-49c4-9924-9c417e97407a" width="600"/>

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

<img src="https://github.com/user-attachments/assets/c5978ef9-c00a-46d4-8322-006a7249fd93" width="600"/>

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
print(f"Sent: {test_data}")

# Read back data
received = ser.read(len(test_data))
print(f'Received: {received}')

# Check if the loopback worked
if received == test_data:
    print('✅ Serial loopback test passed!')
else:
    print('❌ Serial loopback test failed!')

ser.close()
```

<img src="https://github.com/user-attachments/assets/91967ab2-9838-4b65-aeca-0eb3b1cd6074" width="600"/>

Select file → save as:

<img src="https://github.com/user-attachments/assets/1db3cc28-ed92-4a3e-a603-5ec3bd2d9708" width="600"/>

Save the file as `script.py` ensuring that save as type is All Files and Encoding is UTF-8:

<img src="https://github.com/user-attachments/assets/ff4f227a-575e-442b-a4c8-1ce119678ffc" width="600"/>

The script file is in Documents, copy the path:

<img src="https://github.com/user-attachments/assets/1caa01ad-85aa-44c1-8299-30981fde4598" width="600"/>

Launch the script file in the command prompt:

<img src="https://github.com/user-attachments/assets/62052024-7877-4c4f-811f-c1a79e7aaecb" width="600"/>

With no pins connected, the following shows:

<img src="https://github.com/user-attachments/assets/e0842283-bc24-4526-a8e9-e92c91a986fe" width="600"/>

<img src="https://github.com/user-attachments/assets/f7c02ce1-58fd-4717-b667-1d080d61c5a9" width="600"/>

With pins 2 and 3 connected, the following shows:

<img src="https://github.com/user-attachments/assets/0ec50a62-e408-469d-ae8f-493599320523" width="600"/>

<img src="https://github.com/user-attachments/assets/b8fe5ab6-7f7d-4cca-a028-c36327d66672" width="600"/>

The code works as expected and interfaces with the Serial Port which is passed through to the Windows Vista VM from the Windows 11 Host PC.

## Parallel Port Passthrough

VMware can theoretically passthrough a physical parallel port. However, USB-to-parallel adapters are designed exclusively for printers and do not provide true parallel port functionality for other hardware. By the time of Windows Vista, parallel ports were already considered legacy and were rarely included on new PCs. I do not have a parallel port printer available to test passthrough functionality.

## PCI/PCIe Card Passthrough

VMware does not support direct passthrough of PCI or PCIe cards to a guest virtual machine. Additionally, there are no USB adapters that replicate the functionality of PCI/PCIe expansion cards.

Return to [VMware Installation Guide](../readme.md).

Python is just used as an example of a legacy program to run in a Windows Vista VM and not covered in detail in this tutorial. For details about using Python, see my other GitHub repository [Python Tutorials](https://github.com/PhilipYip1988/python-tutorials).
