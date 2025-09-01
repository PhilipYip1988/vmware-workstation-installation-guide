# Windows 2000

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

## Configuring Virtual Hardware for a Windows 2000 Guest

Select Playser → File → New Virtual machine...

<img hsrc="https://github.com/user-attachments/assets/9f228229-2d40-4682-9e37-fae103f60410" width="600"/>

Select I will install this operating system later and then next:

<img src="https://github.com/user-attachments/assets/580444bd-cb3d-41a2-8fad-3e434c248bab" width="600"/>

Select Windows 2000 Professional and then next:

<img src="https://github.com/user-attachments/assets/15133c99-2dba-4ef2-87d8-e319a19e1f03" width="600"/>

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive. you may want to move this to a loal only location) and select next:

<img src="https://github.com/user-attachments/assets/d1b95fda-74a1-4730-a05d-5ef8b1159ab0" width="600"/>

Select 20 GB and select enxt:

<img src="https://github.com/user-attachments/assets/24dd4b12-5717-4265-a185-09ca82041a2c" width="600"/>

Select customise hardware:

<img src="https://github.com/user-attachments/assets/2fd1b7c9-c122-430b-9fab-0307fe2fb325" width="600"/>

Set the memory to 512 MB:

<img src="https://github.com/user-attachments/assets/67232df2-7094-48e7-8289-b2280ee6fd98" width="600"/>

Set the number of processors to 1:

<img src="https://github.com/user-attachments/assets/19602989-7bee-4685-b05c-9877ccc89f65" width="600"/>

Under CD/DVD ensure connected at power on is checked and select browse to browse for the Windows 2000 Professional ISO:

<img src="https://github.com/user-attachments/assets/94f3f417-cc69-4d9a-99a0-92565da23117" width="600"/>

Select the Windows 2000 Professional ISO:

<img src="https://github.com/user-attachments/assets/2e4ea6ac-1a57-4424-b160-dd87f2c609f1" width="600"/>

<img src="https://github.com/user-attachments/assets/11877ead-169f-4cf3-883a-5a024d6e458e" width="600"/>

<img src="https://github.com/user-attachments/assets/6381c218-4692-45d5-91a7-9b3a33555ab1" width="600"/>

<img src="https://github.com/user-attachments/assets/2a969d3f-a3cb-408b-9103-d697b5baf44b" width="600"/>

Uncheck Connect at Power On for Network Adaptor:

<img src="https://github.com/user-attachments/assets/cac9fc38-ba76-4710-90c1-7367616a79b5" width="600"/>

Under USB Controller, select USB 2.0:

<img src="https://github.com/user-attachments/assets/e6d01ffb-2694-47b1-8018-c917d45f130a" width="600"/>

Under Sound Card, use the default settings:

<img src="https://github.com/user-attachments/assets/b65b5f79-16e8-49f9-8f7f-161345489d72" width="600"/>

Under display uncheck accelerate 3d Graphics:

<img src="https://github.com/user-attachments/assets/c21bbe05-3e1d-42e7-b699-911e62109ecb" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/128a6d37-4c68-4708-a6bb-06aee806a56f" width="600"/>

## Windows 2000 Guest Virtual Machine Configuration File




## Windows 2000 ISO


Windows 2000 is considered abandonware and the Windows 2000 ISO and Product Key can be obtained from WinWorld:

* [WinWorld](https://winworldpc.com/library/operating-systems)

## Windows 2000 SP4

* [Windows 2000 SP4](https://winworldpc.com/download/41c38361-6518-c39a-11c3-a4e284a2c3a5)

##

* [KB891861](https://www.catalog.update.microsoft.com/Search.aspx?q=KB891861)
* [KB893803](https://www.catalog.update.microsoft.com/Search.aspx?q=KB893803)
* [KB973544](https://www.catalog.update.microsoft.com/Search.aspx?q=KB973544)
* [KB2538242](https://www.catalog.update.microsoft.com/Search.aspx?q=KB2538242)

## nLite

* [nLite](https://www.nliteos.com/download.html)

## VMware Tools ISO

The Windows XP drivers for the Windows XP Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

* [VMware Tools 6.5.5](https://archive.org/details/vmware-tools-collectio](https://archive.org/details/vmware-tools-collection)

## WSUS Offline Update

The last version of WSUS Offline Update to support Windows 2000:

* ~~[WSUS Offline Update](https://download.wsusoffline.net/)~~

This no longer works as Microsoft removed the downloads WSUS Offline updates uses from their servers.

<details>
  <summary>Archive.org</summary>

The Website Archive.org appears to host the ISO created from WSUS Offline Update before Microsoft removed Windows Vista downloads from their download servers:

* [WSUS Offline Update Windows 2000](https://archive.org/details/wsusoffline-w2k-enu)

Install manually from `w2k\enu`:

* KB817701 Windows 2000 SP4
* KB891861 Update Rollup 1 for Windows 2000 SP4
* KB835732 Security Update for Windows 2000 SP4 

Install manually from `w2k\glb`:

* KB893803 Windows Installer 3.1

Install manually from `w2k\enu`:

* KB926247 Root Certificates Update

Install the 2005 and 2008:

* [Microsoft Visual C++ Redistributable](https://archive.org/details/microsoftvisualcredistributable_202004)

Install:

* [Microsoft .NET Framework Version 2.0](https://archive.org/details/dotnetfx2_202301)

Install:

* [Direct X 9.0C](https://archive.org/details/directx9-dec2006-redist)


WSUS offline update fails at installing direct x June 2010 SDK "is not a valid win32 application" and reboots. Access is denied Infinite loop.

</details>

Additional Windows 98 software can be found in:

* [Retro PC installation files](https://startup.retropc.se/win2k.html)

### 12th-14 Generation Processors

On a 12th–14th Generation Intel processor, certain legacy settings may need to be configured to run older guest operating systems such as Windows XP.

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
