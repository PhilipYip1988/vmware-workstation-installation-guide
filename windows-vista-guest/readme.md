# Windows Vista

## YouTube Video

* [YouTube](https://www.youtube.com/watch?v=oysZWd6vPhA)

## Notes

VMware Workstation Player 17.6.4 has Windows Vista as an option for a Virtual Machine. However Windows Vista is regarded as a legacy Operating System and isn't tested by Broadcom. Moreover the VMware Tools 12.5.3 which comes with VMware workstation player doesn't support Windows Vista.

VMware Tools 11.0.6 is the last version of VMware Tools to support Windows Vista and should be downloaded seperately as an ISO. This ISO should be mounted in the VM so they can be installed manually.

On modern hardware, with a 11th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

The first setting allows the CPU to optimise the VM performance, the VM may be very slow without this setting. The second setting prevents use of a memory management unit that Windows Vista doesn't understand and can lead to a Blue Screen of Death (BSOD). The third setting prevents VMware from using Vulkan for rendering, which isn't supported by Windows Vista and often leads to black screens. The last two settings prevent Windows Vista from seeing unsupported CPU features which Windows XP doesn't understand and can lead to a Blue Screen of Death (BSOD).

## Installation Media

The Website Archive.org hosts multi-lingual Dell Windows Vista Reinstallation ISOs. These are likely ripped by the uploader from physical DVDs as Dell did not provide download. The ISO Checksums can be used to ensure a complete download:

|ISO|SHA256 ISO Checksum|
|---|---|
|[Dell Vista Business SP1 (x64)](https://archive.org/details/Reinstallation_DVD_Windows_Vista_Business_64Bit_SP1_H207H_Dell_2008)|AE468896767B27F9F53441AC09865872AE546449AC1F406BA9C1DF409DE85F7F|
|[Dell Vista Business SP1 (x86)](https://archive.org/details/windows-vista-business-sp-1-dell-oem-32bit)|B0898DA188B90C40C47A231B8A8A1A8EC761EFD5C6C4F39A3B01BD8AAA743DB0|

Other editions (untested):

* [Dell Windows Vista Home Premium 64 Bit SP1](https://archive.org/details/vistasp1homepremiumn069h)
* [Dell Windows Vista Home Premium 32 Bit SP1](https://archive.org/details/Dell_OEM_Windows_Vista_Home_Premium_32Bit_Reinstall_DVD_2007_Eng)
* [Dell Windows Vista Home Basic 32 Bit SP1](https://archive.org/details/WindowsVistaHomeBasicwithServicePack1x86DellOEM)
* [Dell Windows Vista Ultimate 32 Bit SP1](https://archive.org/details/vista-sp-1-ultimate)

To check the SHA256, in the downloads folder, right click the ISO file and select copy as path:

<img src="https://github.com/user-attachments/assets/26c843c2-d75c-4481-aa20-1f17b670d5e8" width="600"/>

Then open up the Windows Terminal and type in:


```
Get-FileHash "C:\Users\Philip\Downloads\Reinstallation DVD Windows Vista Business 64Bit SP1 (H207H)(Dell)(2008).ISO"
```

<img src="https://github.com/user-attachments/assets/c4178ecd-cb15-457e-8732-35c4a8923ea3" width="600"/>

### Creating a Installation ISO from a DVD

Dell Systems came with a Windows Vista Reinstallation DVD which can be converted into an ISO using NTLite:

* [Using NTLite to Create a Windows Vista Reinstallation ISO from a Dell Windows Reinstallation CD/DVD](./integration/readme.md)

This works on a Windows 11 Host to convert a Windows Vista folder to a ISO. Windows Vista is otherwise unsupported by NTLite.

### WSUS Offline Update

The Website Archive.org hosts the ISO created from WSUS Offline Update before Microsoft removed Windows Vista downloads from their download servers:

* [WSUS Offline Update for Windows Vista](https://archive.org/details/windowsvistaupdates24)

Select `wou-w60-x64 [2023-v1].iso` for Windows Vista 64 Bit or `wou-w60-x86 [2023-v1].iso`for Windows Vista 32 Bit respectively.

|ISO|SHA256 ISO Checksum|
|---|---|
|wou-w60-x64 [2023-v1].iso (x64)|-|
|wou-w60-x64 [2023-v1].iso (x86)|-|

### Download VMware Tools ISO

The Windows Vista drivers for the Windows Vista Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

* [VMware Tools Version 11.0.6](https://archive.org/details/vmware-tools-windows-11.0.6-15940789)

|ISO|SHA256 ISO Checksum|
|---|---|
|VMware-tools-windows-11.0.6-15940789.iso|8F1CC3181055891B98672F715E0CA7BBE4018960EAE945D7A4B9F640C44C3D79|

## Configuring Virtual Hardware for a Windows Vista Guest

Select Player → File → New Virtual machine...

<img src="https://github.com/user-attachments/assets/befb1aa8-4e63-4263-b3d8-fc6d1220fcf5" width="600"/>

It is recommended to instead use "I Will Install this Operating System Later":

<img src="https://github.com/user-attachments/assets/9108e5a6-1396-49d9-919d-ac6e2121982d" width="600"/>

Select Microsoft Windows and Windows Vista x64 Edition (64 Bit) or Windows Vista x86 Edition (32 Bit) and select Next:

<img src="https://github.com/user-attachments/assets/395bd386-6f95-4860-9c22-0fd91ee2dc72" width="600"/>

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive, you may want to move this to a local only location) and select next:

<img src="https://github.com/user-attachments/assets/3ab6bcce-a878-4662-b904-ff0c742196db" width="600"/>

The default maximum size of the Windows XP Guest is 40 GB which is too small, I recommend increasing this to 256 GB. Note the files on the Windows 11 Host won't be 256 GB but can be up to 256 GB if the Windows Vista Guests Virtual Drive is fully occupied with files:

<img src="https://github.com/user-attachments/assets/d088ebd2-7976-4bda-b995-8a51adee2ecb" width="600"/>

Select Customise Hardware:

<img src="https://github.com/user-attachments/assets/05531677-fcd6-4b7c-8115-1e4fdba60653" width="600"/>

The default memory used by the Windows Vista Guest is 1024 MB (1.0 GB). If the Windows 11 Host PC has ≥16 GB RAM, this can be upped to 4096 MB (4 GB) for increased performance of the VM. Note if the Windows 11 Host PC has ≤8 GB of RAM, setting the RAM to 4096 MB (4 GB) may throttle the Host PC leading to decreased performance and 2048 MB (2 GB) may be more approprate:

<img src="https://github.com/user-attachments/assets/c4cd37a7-87b9-430d-b621-880781ebf9a5" width="600"/>

The default number of processors cores used by the Windows Vista Guest is 1. This can be upped to 2 if the Windows 11 Host has a processor with ≥ 16 cores. If the Windows 11 Host PC has ≤16 cores, setting this to a higher value may throttle the Host PC leading to an decreased performance:

<img src="https://github.com/user-attachments/assets/557d9d13-0d42-4c1b-b469-ef7dc7ee709f" width="600"/>

Under CD/DVD select browse:

<img src="https://github.com/user-attachments/assets/222ff72a-80ac-452c-91f2-46a9ab35648c" width="600"/>

Load the Dell Windows Vista Business SP1 Reinstallation x64 (64 Bit) or x86 (32 Bit) ISO:

<img src="https://github.com/user-attachments/assets/51dfad4b-62c1-443f-ab79-731c99b99865" width="600"/>

Ensure connected at power on is enabled:

<img src="https://github.com/user-attachments/assets/b0b02e7d-ead9-4c1b-95b1-3ffc6b02b1eb" width="600" />

Uncheck Connect at Power On for Network Adaptor:

<img src="https://github.com/user-attachments/assets/26fa1975-8ab6-41fa-af9e-3cec5f950e05" width="600"/>

The default USB Controller for Windows Vista is USB 2.0 and Windows Vista does not have any drivers for USB 3.0:

<img src="https://github.com/user-attachments/assets/32ab6de5-9617-474f-9f4d-e2034fce2ae5" width="600"/>

The default Sound Card can be used for the Windows Vista Guest:

<img src="https://github.com/user-attachments/assets/19b13527-b9c9-46f1-a2b3-94d3804fcea8" width="600"/>

Use the default settings for Display and select Close:

<img src="https://github.com/user-attachments/assets/09452ec0-4a4f-4892-980a-159fed80be5f" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/2070dc1e-f069-4511-a5fd-11f2e17b0254" width="600"/>

## Windows Vista  Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows Vista Guest is installed:

<img src="https://github.com/user-attachments/assets/41c8ec62-7eaf-41f2-b3d0-d2e919e94b8a" width="600"/>

Look for the `Windows Vista x64 Edition.vmx` file:

<img src="https://github.com/user-attachments/assets/1e51bb32-8aa1-4aac-a64d-c741509eeb30" width="600"/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/22f01ca1-55eb-414e-8299-988eac9fa5ee" width="600"/>

Press `Ctrl+f` to begin a search for an option for example `bios.bootDelay`:

<img src="https://github.com/user-attachments/assets/d551f360-c771-496b-8be8-e8e97891b57d" width="600"/>

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/9c2dcc39-eeda-468c-b34f-326dcb72c469" width="600"/>

The command above will change the time the Windows Vista Guest Virtual BIOS displays before selecting the default boot option giving more time to select the option to boot from CD/DVD. This line can be removed post-installation.

### Modern Generation Processors (11-14th Generation)

Certain legacy settings may need to be configured to run older guest operating systems such as Windows Vista:

<img src="https://github.com/user-attachments/assets/4c2dc230-fb75-4476-b56d-b3b28d6a6fdb" width="600"/>

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

These settings ensure proper CPU and MMU handling for legacy guests.

### OEM SLP

OEM SLP is not applied by default:

<details>
  <summary>Modded ROMs</summary>

The my digital life forums has a post about a modded Virtual BIOS which includes a Dell SLIC 2.1 compatible with Dell Windows Vista Business OEM SLP. These ROMs are not supported by Microsoft or Dell (but then neither is Windows Vista). You will need to log into their forums to view the files:

* [My Digital Life: SLIC 1.0, 2.1 Mod](https://forums.mydigitallife.net/threads/vmware-workstation-esxi-bios-efi-slic-mod.64693/#post-1132133)

Extract the downloaded file and navigate to the `17.6.0 Modded ROMs` folder. Rename `WORKSTATION_17.6.0_DELL2.7_SLIC_BIOS.440_(497).ROM` `WORKSTATION_17.6.0_DELL2.7_SLIC_BIOS.440_(497).ROM` to `modded_BIOS.440.ROM` and copy the modded ROM to the directory of the Windows Vista Guest. 

Update the Virtual Machine Configuration file to include the line:

```
bios440.filename = "modded_BIOS.440.ROM"
```

Note if the corresponding ROM is not found in the directory the above line of code will prevent the Windows Vista Guest from booting.

</details>

## Installing the Windows Vista Guest OS

Select the Windows Vista Guest and select Play:

<img src="https://github.com/user-attachments/assets/e3a8f769-bd23-4e20-b92d-225319100726" width="600"/>

The Windows Vista VM will boot from the Dell Windows Vista Business Reinstallation ISO:

<img src="https://github.com/user-attachments/assets/cf959629-5d75-465a-a7da-293d4424f505" width="600"/>

Select your language:

<img src="https://github.com/user-attachments/assets/37a7ad10-efdf-4df1-83a0-e634be8397d3" width="600"/>

And keyboard layout and select next:

<img src="https://github.com/user-attachments/assets/5f1ff368-98a6-4393-a770-ea52c4b6f159" width="600"/>

Select Install Now:

<img src="https://github.com/user-attachments/assets/0f9b2573-6919-4377-a73d-8c98b0aa2ae3" width="600"/>

Accept the license agreement and select next:

<img src="https://github.com/user-attachments/assets/ea6506fb-0aab-4749-a1e6-ecfba705da77" width="600"/>

Select Custom (Advanced):

<img src="https://github.com/user-attachments/assets/dbe7e26b-944f-437c-87ec-bcc5a091b35a" width="600"/>

Select Disk 0 (Unallocated Space) and select next:

<img src="https://github.com/user-attachments/assets/d8c585e8-03df-41a4-b967-0c926f7330c8" width="600"/>

Input your user name and select next:

<img src="https://github.com/user-attachments/assets/d40aebf3-8146-48ad-831b-846a9747dc6b" width="600"/>

Input the computer name and select next:

<img src="https://github.com/user-attachments/assets/fbacee92-40ad-4626-add6-f79dc576a9e2" width="600"/>

Select Ask me later:

<img src="https://github.com/user-attachments/assets/4f7f097d-49c2-4f3a-9f50-f65b2ee6e083" width="600"/>

Select your timezone and then select next:

<img src="https://github.com/user-attachments/assets/fd6f8a3b-5f1c-4510-8b66-b1049f877d9c" width="600"/>

Select Start:

<img src="https://github.com/user-attachments/assets/4f0eb7d2-a384-4572-ba91-f8951c821dc4" width="600"/>

You will be taken to the Windows Vista Desktop:

<img src="https://github.com/user-attachments/assets/9f79f6d2-ae17-48d0-bb56-9f53d6819df8" width="600"/>

Uncheck run at startup and close the welcome centre.

## Backing up the VM

Shut down the Windows Vista VM and then create a copy of the VM folder. Should you encounter problems with your VM after installing software, you can delete the original folder and rename the copied folder to the original folders name. Essentially this will give you a VM to roll back to:

<img src="https://github.com/user-attachments/assets/0e1b6187-febd-485e-9e5f-ffc737707880" width="600"/>

## Installing Windows Updates

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/0526c4c9-5730-4359-b226-edc0d09dedbc" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/5de80434-bd93-4fa2-8fa6-665cfcf7fcdd" width="600"/>

Select `wou-w60-x64 [2023-v1].iso` or `wou-w60-x86 [2023-v1].iso` and select open:

<img src="https://github.com/user-attachments/assets/98949438-3cbe-4f4a-b53f-e0e85d4ed13c" width="600"/>

Select the DVD drive:

<img src="https://github.com/user-attachments/assets/fed5c2a6-f022-4752-ba9c-3afe12083bf2" width="600"/>

Select allow:

<img src="https://github.com/user-attachments/assets/3b64e684-ea53-4d5d-9d59-124c9d4cd95e" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/dc1ff938-6fb4-4222-8e37-065fb230f15b" width="600"/>

Select Start:

<img src="https://github.com/user-attachments/assets/edd81857-0173-420d-851a-37f3b7026175" width="600"/>

WSUS Offline Update will install a very large number of updates unattended, and reboot the VM after installing updates. This will take a few hours and should not be interrupted. If it is interrupted, the VM may blue screens, you may need to close the VM, then delete the VM folder. Then you can rename the copy of the unpatched Windows Vista back to the original (and create another copy) and retry.

After installation, the updates installed can be seen by going to Control Panel:

<img src="https://github.com/user-attachments/assets/0ebf8ed9-a8ce-448c-9a09-eb8892ca3d68" width="600"/>

Programs:

<img src="https://github.com/user-attachments/assets/edbe61aa-227e-49ac-a076-f7e3d09f7c31" width="600"/>

Here the .NET Framework,Camera Codec Pack, C++ Resdistributables installed will be listed. The updates installed can be seen by selecting view installed updates:

<img src="https://github.com/user-attachments/assets/9fc5ca04-1666-4074-b5bc-0707ccfd3025" width="600"/>

The updates installed are listed:

<img src="https://github.com/user-attachments/assets/e8bd739b-0f73-42fc-a59b-947f7cd13f5d" width="600"/>

<img src="https://github.com/user-attachments/assets/88249bb3-d423-4ca8-976a-f3ab94aa971e" width="600"/>

## Installing VMware Tools

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/193e2b35-a22a-4e96-92c9-fffa43d9bed6" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/36d04f0f-530b-4184-b60b-6dc5c1bb8387" width="600"/>

Select the `VMware-tools-windows-11.0.6-15940789.iso` and select open:

<img src="https://github.com/user-attachments/assets/b9cf0c9f-fd99-40b7-bec6-c0e2290df0a2" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/e72db2f6-ca52-46fb-a4b2-6be0a2c767ce" width="600"/>

Open the DVD drive:

<img src="https://github.com/user-attachments/assets/710abcb1-ba1b-47f8-9b28-a934346a2b4d" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/55210eb1-3af7-4b71-9f9f-73eee3eba58b" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/d1a07c6d-9352-4f63-9458-487878d1176d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/3c2bf105-d1e5-4403-9c28-eb7fd06a6365" width="600"/>

Select install:

<img src="https://github.com/user-attachments/assets/b326b546-62f0-4a93-bfbd-a383b9e286dc" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/7c70fb0e-80f1-4b73-8c8e-57870cd85b2e" width="600"/>

Select yes to restart the VM:

<img src="https://github.com/user-attachments/assets/edf804fe-4a68-46fa-9cf2-5b022f4e6552" width="600"/>

## Enabling Aero

**Enabling Windows Aero on the Windows Vista VM is not recommended as the performance is reduced.**

Select Computer and then select Properties:

<img src="https://github.com/user-attachments/assets/0aca88f8-c722-4c5d-a0b6-bacfe1d42c2a" width="600"/>

The Windows Experience Index (WEI) Assessment in this VMware Vista virtual machine reports a score of 1.0 because Windows Vista is using the VMware SVGA driver based on the Windows XP Display Driver Model (XPDM). This driver does not implement all features of the Windows Display Driver Model (WDDM) 1.0 introduced in Vista, so the WEI graphics assessment cannot run. VMware provides a WDDM 1.1 driver for Windows 7 and later that fully supports GPU-accelerated Aero and WEI, but this driver is incompatible with Windows Vista. Since Vista is less commonly virtualized and is generally considered an intermediate release between Windows XP and Windows 7, VMware did not create a dedicated WDDM driver for Vista.

<img src="https://github.com/user-attachments/assets/1c9b6009-ce45-4af8-8c26-ff967b095699" width="600"/>

If the Windows Assessment Tool is used, it will hang:

<details open>
<summary>Windows System Assessment Tool - NOT RECOMMENDED</summary>

When efresh now is selected:

<img src="https://github.com/user-attachments/assets/ab867898-cf02-4e21-a489-ae7edf4e19db" width="600"/>

And continue is selected:

<img src="https://github.com/user-attachments/assets/6ff245ed-b1a4-4d02-9d83-d3761ac372fb" width="600"/>

The Windows Assessment Tool will hang here because it cannot access the graphics driver fully to flash the screen:

<img src="https://github.com/user-attachments/assets/972eb9c6-6392-426c-8759-e47061624179" width="600"/>

Press `Ctrl`, `⇧` + `Esc` to bring up the Task Manager. Right click Performance Information and Tools and select End Task:

<img src="https://github.com/user-attachments/assets/0b54f2e8-c3c4-4256-bc71-273c71664da3" width="600"/>

Select End Now:

<img src="https://github.com/user-attachments/assets/333b537f-a519-4e14-ac7f-7b559539d5c3" width="600"/>

</details>

Windows Aero can be enabled using the registry editor but the performance is noticably slower than the basic display mode. Press `⊞` + `r` and type in:

```
regedit
```

<img src="https://github.com/user-attachments/assets/fc2fab31-6c10-4871-8ad3-5bde5c409e31" width="600"/>

Accept the User Account Control:

<img src="https://github.com/user-attachments/assets/da507a88-bdb4-4e95-a055-3421f1dd93a5" width="600"/>

Navigate to:

```
HKEY_CURRENT_USER\Software\Microsoft\Windows\DWM
```

<img src="https://github.com/user-attachments/assets/10730789-c59d-4e86-80ef-5a0231720d9d" width="600"/>

<img src="https://github.com/user-attachments/assets/e66efa9b-5aba-40d5-83b2-10cf6a54156b" width="600"/>

In this folder are two DWORD values `Composition` and `CompositionPolicy` which are set to `1` and `0` respectively. Double click `CompositionPolicy` and update the value to `1` (Aero Lite) or `2` (Aero) and select OK:

<img src="https://github.com/user-attachments/assets/cf88a147-4d38-47ce-8a63-bb1656ed6624" width="600"/>

Close the registry editor. Go to Start and search for cmd and right click cmd and select run as administrator:

<img src="https://github.com/user-attachments/assets/669a5a1a-7b8e-4405-96b6-653076348273" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/4afba59e-aff3-4292-b04a-f7a136e29b54" width="600"/>

Stop the Desktop Windows Manager by inputting:

```
net stop uxsms
```

<img src="https://github.com/user-attachments/assets/183bf783-572f-4a8f-809a-a9612b065812" width="600"/>

Start the Desktop Windows Manager by inputting:

```
net start uxsms
```

<img src="https://github.com/user-attachments/assets/e0c35a10-d165-486e-a09d-683fb8e77471" width="600"/>

## Disable Security Centre Icon

The Window Security Centre Notification will display in the notifcation tray. This can be disabled by selecting it and selecting Change the way Security Centre Alerts Me:

<img src="https://github.com/user-attachments/assets/5ca43a32-7453-4fa0-bd59-104af4ef4326" width="600"/>

Then selecting Don't, Notify Me and Don't Display the Icon:

<img src="https://github.com/user-attachments/assets/c199c14d-3459-4594-a193-640c3a81fa68" width="600"/>

## Installing Python

Python will be used as an example of installing a program on Windows Vista. [python-3.7.0-amd64.exe](https://www.python.org/downloads/release/python-344](https://www.python.org/downloads/release/python-370/#files) is the latest version of Python to work on Windows Vista. The installer can be downloaded on the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/5514decd-033c-472e-8b33-fe3d7ff1ab57" width="600"/>

And dragged and dropped over to the VM:

<img src="https://github.com/user-attachments/assets/16a167a5-6ebd-4178-baea-019d560392e5" width="600"/>

Launch the setup:

<img src="https://github.com/user-attachments/assets/ee2e3a23-c988-4c4e-bd7d-ebf7b78e9198" width="600"/>

Select add to path and then select install now:

<img src="https://github.com/user-attachments/assets/20574682-b39e-4a87-b62c-fdb414df2d07" width="600"/>

Select close:

<img src="https://github.com/user-attachments/assets/962e8789-22d1-42a1-ab23-9cd1a5d26a25" width="600"/>

Open the Command Prompt:

<img src="https://github.com/user-attachments/assets/f7237b7d-5038-4244-9e5a-5a591fa19e32" width="600"/>

To launch Python input:

```powershell
python
```

Notice the change to the Python prompt `>>>`:

<img src="https://github.com/user-attachments/assets/f8656803-9ed8-4f64-adac-3abc6f6a534c" width="600"/>

Python code can now be used:

```python
print('Hello World!')
```

<img src="https://github.com/user-attachments/assets/a442aaae-c6a8-4f0b-96a3-c28b65dc54af" width="600"/>

To exit python input the function:

```python
exit()
```

<img src="https://github.com/user-attachments/assets/21783ba4-8d15-4854-a2a9-c2ecba769a2d" width="600"/>

Notice the return to the CMD prompt. 

To use the package manager requires Internet Connectivity. Select Player → File → Network Adaptor → Connect:

<img src="https://github.com/user-attachments/assets/a1ba09e2-8446-4fee-88ad-c1442af323d5" width="600"/>

Recall however that Windows Vista is past end of life and is not safe to use online for general web use.

The globe icon will appear to the bottom right corner:

<img src="https://github.com/user-attachments/assets/9edfc037-a41c-4939-8245-c2cf055b7150" width="600"/>

The Python package can be installed using:

```powershell
pip install pyserial==3.0.1
```

<img src="https://github.com/user-attachments/assets/b54222f2-79ef-436a-8246-ab728974555c" width="600"/>

And can be imported into a Python program:

<img src="https://github.com/user-attachments/assets/1b7631fd-fb08-421b-aa76-556aef2f38e1" width="600"/>

## USB Passthrough

## Serial Passthrough

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
