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

## Windows Vista Standalone Updates

WSUS Offline update may hang, the following updates should be installed manually before using WSUS Offline Update:

<details>
  <summary>Windows Vista Standalone Updates Microsoft Update Catalog</summary>

* [KB948465](https://catalog.update.microsoft.com/Search.aspx?q=KB948465)
* [KB3205638](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3205638)
* [KB4012583](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4012583)
* [KB4015195](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4015195)
* [KB4015380](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4015380)

</details>

## WSUS Offline Update

The last version of WSUS Offline Update to support Windows Vista was 10.9.2:

* ~~[WSUS Offline Update](https://download.wsusoffline.net/)~~

This no longer works as Microsoft removed the downloads WSUS Offline updates uses from their servers.

<details>
  <summary>Archive.org</summary>

The Website Archive.org appears to host the ISO created from WSUS Offline Update before Microsoft removed Windows Vista downloads from their download servers:

* [WSUS Offline Update Windows Vista (Windows Vista 32 Bit=w60 and Windows Vista 64 Bit=w60-x64)](https://archive.org/details/wsusoffline-eol-windows)

I have tested installation of the ISO in a Virtual Machine but as this is an unofficial source and should be used with caution. 

The following updates should be installed manually before using the WSUS Offline Update ISO as Windows Vista has a bug and enters an infinite loop when checking for updates. This issue is addressed if the following 5 updates are manually installed:

* [KB948465](https://catalog.update.microsoft.com/Search.aspx?q=KB948465)
* [KB3205638](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3205638)
* [KB4012583](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4012583)
* [KB4015195](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4015195)
* [KB4015380](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4015380)

Copy the following 5 updates to a folder and convert the folder to an ISO using [ImgBurn](https://www.imgburn.com/). Mount this ISO and install these updates immediately after installing Windows Vista. Then mount the WSUS Offline Update ISO and use it to patch Windows Vista fully until end of life. 

</details>

## Download VMware Tools ISO

The Windows Vista drivers for the Windows Vista Guest are contained in the VMware Tools Installation ISO. VMware tools for legacy versions of Windows needs to be downloaded from VMware separately:

* [VMware Tools Version 11.0.6](https://packages.vmware.com/tools/releases/11.0.6/windows/)

Windows Vista setup is very similar to Windows 7 setup confer with:

* [VMware Installation Guide](../windows-7-guest/readme.md)