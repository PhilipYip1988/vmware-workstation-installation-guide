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

The Website Archive.org hosts multi-lingual Dell Windows Vista Reinstallation ISOs. These are likely ripped by the uploader from physical DVDs as Dell did not provide download:

* [Dell Windows Vista Business 64 Bit SP1](https://archive.org/details/Reinstallation_DVD_Windows_Vista_Business_64Bit_SP1_H207H_Dell_2008)
* [Dell Windows Vista Home Premium 64 Bit SP1](https://archive.org/details/vistasp1homepremiumn069h)

* [Dell Windows Vista Business 32 Bit SP1](https://archive.org/details/windows-vista-business-sp-1-dell-oem-32bit)
* [Dell Windows Vista Home Basic 32 Bit SP1](https://archive.org/details/WindowsVistaHomeBasicwithServicePack1x86DellOEM)
* [Dell Windows Vista Home Premium 32 Bit SP1](https://archive.org/details/Dell_OEM_Windows_Vista_Home_Premium_32Bit_Reinstall_DVD_2007_Eng)
* [Dell Windows Vista Ultimate 32 Bit SP1](https://archive.org/details/vista-sp-1-ultimate)

The ISO Checksums can be used to ensure a complete download:

|ISO|SHA256 ISO Checksum|
|---|---|
|Business (x64)|AE468896767B27F9F53441AC09865872AE546449AC1F406BA9C1DF409DE85F7F|
|Business (x86)|b0898da188b90c40c47a231b8a8a1a8ec761efd5c6c4f39a3b01bd8aaa743db0|

To check the SHA256, in the downloads folder, right click the ISO file and select copy as path. Then open up the Windows Terminal and type in:

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

## Modern Generation Processors (11-14th Generation)

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

Windows Service Pack 2, Internet Explorer 9, Microsoft C++ Runtime Libraries and Microsoft .Net Frameworks for Windows Vista will install. The VM will automatically restart multiple times.

On my Windows Vista VM, I encountered a bluescreen and had to select last known configuration:

<img src="https://github.com/user-attachments/assets/1e16b3e6-d3bc-4587-99e5-f2811bc2bd9e" width="600"/>

However the large number of updates were installed:

<img src="https://github.com/user-attachments/assets/ab662c55-244e-48a3-832b-748e927621d0" width="600"/>

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

# Enabling Aero

The Windows Experience Index Assessment does not work as the Virtual Display Adaptor will not flash during the assessment and the assessment therefore hangs. Aero can be enabled using the following registry edit

Go to HKCU\Software\Microsoft\Windows\DWM

Add a DWORD Composition = 1

Add a DWORD CompositionPolicy = 2

Restart Desktop Window Manager (net stop uxsms → net start uxsms).

