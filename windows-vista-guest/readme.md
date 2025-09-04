# Windows Vista

## YouTube Video

* [YouTube](https://www.youtube.com/watch?v=oysZWd6vPhA)

## Installation Media

The biggest difficulty to setting up a Windows Vista Virtual Machine is obtaining the installation as Microsoft nor its OEMs provided official download links to an Installation ISO. Windows Vista Setup Files were available from Microsoft and the ISO needed to manually be created from them but these download links have long been removed:

* [WinWorld OS](https://winworldpc.com/library/operating-systems) 

<details>
  <summary>Archive.org</summary>

The Website Archive.org hosts each Unofficial Dell Windows Vista Reinstallation ISO which are multi-lingual:

* [Dell Windows Vista Business 64 Bit SP1](https://archive.org/details/Reinstallation_DVD_Windows_Vista_Business_64Bit_SP1_H207H_Dell_2008)
* [Dell Windows Vista Home Premium 64 Bit SP1](https://archive.org/details/vistasp1homepremiumn069h)

* [Dell Windows Vista Business 32 Bit SP1](https://archive.org/details/windows-vista-business-sp-1-dell-oem-32bit)
* [Dell Windows Vista Home Basic 32 Bit SP1](https://archive.org/details/WindowsVistaHomeBasicwithServicePack1x86DellOEM)
* [Dell Windows Vista Home Premium 32 Bit SP1](https://archive.org/details/Dell_OEM_Windows_Vista_Home_Premium_32Bit_Reinstall_DVD_2007_Eng)
* [Dell Windows Vista Ultimate 32 Bit SP1](https://archive.org/details/vista-sp-1-ultimate)

I have tested installation of the the following ISOs in a Virtual Machine but as this is an unofficial source and should be used with caution. 

The ISO Checksums can be used to ensure a complete download but these do not match official Dell or Microsoft records as they would have been created from a CD/DVD by an end user:

|ISO|sha256 ISO Checksum|
|---|---|
|Business (x64)|ae468896767b27f9f53441ac09865872ae546449ac1f406ba9c1df409de85f7f|
|Business (x86)|b0898da188b90c40c47a231b8a8a1a8ec761efd5c6c4f39a3b01bd8aaa743db0|

</details>

### Creating a Installation ISO from a DVD

Dell Systems came with a Windows Vista Reinstallation DVD which can be converted into an ISO using NTLite:

* [Using NTLite to Create a Windows Vista Reinstallation ISO from a Dell Windows Reinstallation CD/DVD](./integration/readme.md)

This works on a Windows 11 Host to convert a Windows Vista folder to a ISO. Windows Vista is otherwise unsupported by NTLite.

## WSUS Offline Update

The Website Archive.org hosts the ISO created from WSUS Offline Update before Microsoft removed Windows Vista downloads from their download servers:

* [WSUS Offline Update for Windows Vista](https://archive.org/details/wsusoffline-eol-windows)

Select w60-x64 for Windows Vista 64 Bit or w60 for Windows Vista 32 Bit respectively.

The following updates should be installed manually before using the WSUS Offline Update ISO as Windows Vista has a bug and enters an infinite loop when checking for updates. This issue is addressed if the following 5 updates are manually installed:

* [KB948465](https://catalog.update.microsoft.com/Search.aspx?q=KB948465)
* [KB3205638](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3205638)
* [KB4012583](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4012583)
* [KB4015195](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4015195)
* [KB4015380](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4015380)

Copy the following 5 updates to a folder and convert the folder to an ISO using [ImgBurn](https://www.imgburn.com/). Mount this ISO and install these updates immediately after installing Windows Vista. Then mount the WSUS Offline Update ISO and use it to patch Windows Vista fully until end of life. 

### Download VMware Tools ISO

The Windows Vista drivers for the Windows Vista Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

* [VMware Tools Version 11.0.6](https://archive.org/details/vmware-tools-windows-11.0.6-15940789)

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

Certain legacy settings may need to be configured to run older guest operating systems such as Windows Vista.









Windows Vista setup is very similar to Windows 7 setup confer with:

* [VMware Installation Guide](../windows-7-guest/readme.md)
