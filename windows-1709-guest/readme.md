# Windows 10 Guest

Although Windows 10 version 1709 was not released as a Long-Term Servicing Branch/Channel (LTSB/LTSC), it is widely regarded as one of the most stable mainstream builds of Windows 10. Windows 10 Version 1709 was the last Windows 10 build that officially supported a wide range of legacy hardware. Subsequent builds of Windows 10 had elevated system requirements, became more resource heavy and ran poorly on legacy hardware. Windows 10 Version 1709 was also regarded as the best Windows 10 32 Bit Build because the hardware resources for 32 Bit is limited (32 Bit Windows can only handle a maximum of 4 GB of RAM).

## Download Windows 10

### Windows 10 Builds

Windows 10 is a 10 year old series of Windows Operating System that had multiple versions. Initially each version was named YYMM corresponding to the year and month respectively however this gave the expectation for a build to be released to RTM on the Month. Often it was delayed slightly in order for Microsoft to improve stability and as a consequence they switched to the naming convention YYHX correponding to the year and year half respectively.

A major version is essentially a full OS swap refreshing the Windows Kernel, while the minor version builds on the previous versions Windows Kernel.

|Version|Date|Notes|Long Term|
|---|---|---|---|
|1507|Half 2 2015|Initial Release|LTSB|
|1511|Half 2 2015|Minor: Fixed Product Activation||
|1607|Half 2 2016|Major|LTSB|
|1703|Half 1 2017|Major||
|1709|Half 2 2017|Major: Best Performance on Old Hardware||
|1803|Half 1 2018|Major||
|1809|Half 2 2018|Major|LTSC|
|1903|Half 1 2019|Major||
|1909|Half 2 2019|Minor||
|2004|Half 1 2020|Major||
|20H2|Half 2 2020|Minor||
|21H1|Half 1 2021|Minor||
|21H2|Half 2 2021|Minor|LTSC|
|22H2|Half 2 2022|Major||

## Windows 10 Media Creation Tool (All Builds)

Microsoft used to host all the ISOs as direct download links however as Windows 10 approaches end of life many of the ISO download links are removed. The GitHub Repository Windows 10 Media Creation Tool.bat is a Universal Media Creation Tool wrapper script for all Windows 10/11 versions from 1507 to 22H2!

* [GitHub: Windows 10 Media Creation Tool.bat](https://github.com/AveYo/MediaCreationTool.bat)
  * [GitHub: Windows 10 Media Creation Tool.bat lzw29107 fork](https://github.com/lzw29107/MediaCreationTool.bat)

Note Microsoft make frequent changes to the files used by the last version of the Windows 10 media Creation Tool and it takes time for developers to update the .bat file in the GitHub Repository. One of the forks maintained by lzw29107 is more up to date but in my testing didn't work with 22H2:

* [Windows 10 Media Creation Tool](https://www.microsoft.com/en-gb/software-download/windows10)

<img src="https://github.com/user-attachments/assets/c1cdedfa-5868-44f8-9a32-b3e89a0e1947" width="300"/>

In this example, I will use the Windows 10 Media Creation Tool to download Windows 10 (Version 1709). Go to the GitHub respository and select Code:

<img src="https://github.com/user-attachments/assets/f14aef6a-edc5-498a-826c-792d2ee9f451" width="600"/>

Then Download ZIP:

<img src="https://github.com/user-attachments/assets/9bc6b0fa-decd-440a-a806-b9d6e3f5355a" width="600"/>

Go to Downloads, right click the zip file and select Extract All:

<img src="https://github.com/user-attachments/assets/61bf7c75-79ac-47b3-bfcb-4a07ecfc7ad6" width="600"/>

Select Etract:

<img src="https://github.com/user-attachments/assets/e79c8c23-c3b3-4d25-ba44-0d4461a553c4" width="600"/>

Select the extracted folder:

<img src="https://github.com/user-attachments/assets/7e67b28b-afba-4090-b02c-466b9053f898" width="600"/>

Right click `MediaCreationTool.bat`:

<img src="https://github.com/user-attachments/assets/642bfe3a-b1d0-42b7-a937-84db590f00e9" width="600"/>

And select Open:

<img src="https://github.com/user-attachments/assets/85bf06f1-3b85-4522-b3ca-7a559e289a4a" width="600"/>

Select Run:

<img src="https://github.com/user-attachments/assets/0c1f8fa1-0361-4d85-bf1e-10277c02a499" width="600"/>

Select the Build, in this example 1709:

<img src="https://github.com/user-attachments/assets/5d7d840c-99ae-45f8-a87e-23754dc13f4a" width="600"/>

Then select, select:

<img src="https://github.com/user-attachments/assets/3c855bff-3965-4308-9de2-d6c09bf2edbf" width="600"/>

Details about the downloads will display:

<img src="https://github.com/user-attachments/assets/e569ef02-6501-4901-846b-5a8f80fa3f73" width="600"/>

The Media Creation Tool for that Build will display:

<img src="https://github.com/user-attachments/assets/8c0f68ec-3db8-4b09-9605-8d2e80ed58a1" width="600"/>

Select the Language, Edition and Architecture:

<img src="https://github.com/user-attachments/assets/5f0d6324-86ae-44de-8b94-30aedbf76154" width="600"/>

Select ISO file and next:

<img src="https://github.com/user-attachments/assets/951915ba-ae9b-4546-8263-b2ee750ea7ed" width="600"/>

Select the Downloads folder and save the ISO:

<img src="https://github.com/user-attachments/assets/6ec06c7d-0ff4-4045-a038-b6e79c4257f8" width="600"/>

The Media Creation Tool will download the setup files and create the IISO as requested:

<img src="https://github.com/user-attachments/assets/eddaf210-b335-42aa-a534-6293fb3e3368" width="600"/>

## WSUS Offline Update

The WSUS Offline Update is a utility that can be used to download all the updates for a Windows Build and create an ISO which can be used for offline update. The Original Developer maintained the WSUS Offline Update project until April 2020, just after Windows 7 Reached End of Life. After April 2020 it was forked into a Community Edition. The Community Edition is better for Windows 10 Builds released post-2020 and the Long Term Support Build/Channel (LTSB/LTSC) Builds 1507/1607/1809/21H2.

WSUS Offline Update Community 12.6H6:

<img src="https://github.com/user-attachments/assets/b9519a7c-4fa5-4de8-8475-d524f4f412b7" width="600"/>

* [WSUS Offline Update Community](https://gitlab.com/wsusoffline/wsusoffline/-/releases)

WSUS Offline Update 12.0:

<img src="https://github.com/user-attachments/assets/14fd73bc-c36b-46b3-b525-ac69e8b8f8e2" width="600"/>

* [WSUS Offline Update](https://download.wsusoffline.net/)

Since Windows 1709 is use, the original WSUS Offline Update will be used:

<img src="https://github.com/user-attachments/assets/62ba7f62-d75a-4bb0-8503-f07e9f7c99a8" width="600"/>

For a newer or LTSB/C build the WSUS Offline Update Community Edition would need to be used:

<img src="https://github.com/user-attachments/assets/9ad61993-609d-48c3-8d5b-6e1ace88e6e9" width="600"/>

Select Extract All...:

<img src="https://github.com/user-attachments/assets/fcd5bd52-0d9a-47b2-81d2-44e240519ecc" width="600"/>

Select Extract:

<img src="https://github.com/user-attachments/assets/3ebdba3f-627f-4ac3-9964-9ca8e9c64b7d" width="600"/>

Select the `wsusoffline` folder:

<img src="https://github.com/user-attachments/assets/c6feff61-af90-46ab-b68c-36f0426346f4" width="600"/>

Select `UpdateGenerator.exe`:

<img src="https://github.com/user-attachments/assets/8be1faee-8abe-49a2-b26f-43968ff20745" width="600"/>

Select Windows, uncheck all the builds, except the one of interest, in this case 1709 (Windows 10 x64). Under options select Verify Downloaded Updates and Include C++ Runtime Libraries and .NET Frameworks. Select Create ISO Images per Selected Product and Language and select Start:

<img src="https://github.com/user-attachments/assets/e790c329-6986-40b3-8dac-ed6d3147a8f9" width="600"/>

WSUS Offline Update will download a series of updates:

<img src="https://github.com/user-attachments/assets/d911243f-10e1-4d25-9f92-912dfc811088" width="600"/>

<img src="https://github.com/user-attachments/assets/d1c1cac7-cc8f-44af-ab2b-1f34ecf5c4d8" width="600"/>

The ISO will be created:

<img src="https://github.com/user-attachments/assets/33ca3ace-d065-4d21-9579-1a1aa9b94179" width="600"/>

Select yes to view the log file:

<img src="https://github.com/user-attachments/assets/999c05b5-08b2-4871-afa5-163b168a4096" width="200"/>

The log file will display in notepad:

<img src="https://github.com/user-attachments/assets/5216230f-be59-4fd9-8d73-444e77bbdc8e" width="600"/>

The Update ISO will be found in the iso folder:

<img src="https://github.com/user-attachments/assets/c680386d-f39e-4473-a4c9-4f688b002aad" width="600"/>

<img src="https://github.com/user-attachments/assets/4692b217-62cd-4f52-aeee-8bf45c6b3172" width="600"/>

## Windows 11 Host or Ubuntu 24.10 Host System Requirements

Your Windows 11 Host PC or Ubuntu Host PC should satisfy the minimum system the system requirements of Windows 11 and have additional overhead to run a Virtual Machine in addition to these requirements. It is recommended to have a Host PC with at least:

* i5 or i7 11th Generation Intel Processor or Newer
* 16 GB RAM
* 1 TB SSD

## Configuring Virtual Hardware for a Windows 10 Guest

Select Player → File → New Virtual Machine:

<img src="https://github.com/user-attachments/assets/8697d9e4-b7de-45a5-952b-7c627b803b6a" width="600"/>

Select Installer Disc Image File (ISO) and browse:

<img src="https://github.com/user-attachments/assets/7bd29bfe-6954-4ba0-8b5d-8fb424e494a3" width="600"/>

Select the Windows 10 Version 1709 ISO and select Open:

<img src="https://github.com/user-attachments/assets/ab79dc0d-96fd-4fbd-8eb1-70d3c5a04bfd" width="600"/>

Windows 10 is selected, however easy install is not enabled as it is an older build. Select next:

<img src="https://github.com/user-attachments/assets/10b7bab5-613f-4c9f-98d3-820afacb3f1d" width="600"/>

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive, you may want to move this to a local only location) and select next:

<img src="https://github.com/user-attachments/assets/001707c4-3a97-4d17-b625-760eca8665bb" width="600"/>

Note the name and location as these will be used later. The default maximum size of the Windows 10 Version 1709 Guest is 60 GB which is too small, I recommend increasing this to 256 GB. Note the files on the Windows 11 Host won't be 256 GB but can be up to 256 GB if the Windows10 Version 1709 Guests Virtual Drive is fully occupied with files:

<img src="https://github.com/user-attachments/assets/29adcaac-4765-42df-9e54-3477ce1e4249" width="600"/>

Select customise hardware:

<img src="https://github.com/user-attachments/assets/1f1d37bf-29fb-4ca9-b4a1-6e976ef3f1f7" width="600"/>

Increase the RAM to 16384 MB (16 GB) if your host PC has 64 GG of RAM and you are installing Windows 10 Version 1709 64 Bit as a guest. If installing Windows 10 Version 1709 32 Bit set the RAM to 4096 MB (4 GB). 

If your Windows 11 Host PC has 16 GB of RAM, limit the RAM to the Windows 10 Version 1709 Guest to 4 GB as otherwise you may cripple the Windows 11 Host leading to detrimental performance:

<img src="https://github.com/user-attachments/assets/c04268cf-0e94-4cd0-88f7-ca3faa62d9a8" width="600"/>

Change the number of cores to 4:

<img src="https://github.com/user-attachments/assets/36fa82e9-703a-4b77-ac56-62132a034772" width="600"/>

Windows 10 Version 1709 has reached end of life and should be deemed unsafe to use online. The virtual network adaptor is connected by default and can optionally be disabled:

<img src="https://github.com/user-attachments/assets/9ec5955e-580a-4518-9c57-a432d0c468a5" width="600"/>

Under Sound Card, use the default options:

<img src="https://github.com/user-attachments/assets/fc15e775-7671-4728-90f4-d9d360855b53" width="600"/>

Under Display, the default options can be selected. Select Close:

<img src="https://github.com/user-attachments/assets/82c44335-0b60-42ce-8732-e0996b485397" width="600"/>

**Uncheck Power On this Virtual Machine After Creation (as we want to make some changes to the Virtual machine's configuration file before launching it).** Select Finish:

<img src="https://github.com/user-attachments/assets/843148dc-2d71-4df3-a7cb-af343c108b15" width="600"/>

## Windows 10 Version 1709 Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows 10 Version 1709 Guest is installed:

<img src="https://github.com/user-attachments/assets/dc503308-80e8-44bb-ba54-501ceafa1851" width="600"/>

<img src="https://github.com/user-attachments/assets/560c52ad-00d2-4d2e-8dad-0c032fc5f352" width="600"/>

Look for the `Windows 10 x64.vmx` file:

<img src="https://github.com/user-attachments/assets/82bb87eb-72dc-4da0-868c-8995c1d7e58c" width="600"/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/4911d503-75e7-4286-9599-7911aee3f0cf" width="600"/>

Press `Ctrl+f` to begin a search for an option for example `bios.bootDelay`:

<img src="https://github.com/user-attachments/assets/5e62dc93-9bde-4dcb-9841-383c83306eff" width="600"/>

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/a75de770-d936-4cdd-acb9-32555fbdeb07" width="600"/>

### Modern Generation Processors (11-14th Generation)

Certain legacy settings may need to be configured to run older guest operating systems such as Windows 8.1:

<img src="https://github.com/user-attachments/assets/26dfa577-c56f-4575-acfb-58ea7263b89a" width="600"/>

Legacy monitor / virtualization settings

```
mks.enableVulkanRenderer = "FALSE"
```

Legacy monitor / virtualization settings:

```
monitor.virtual_exec = "hardware"
```

## Installing the Windows 10 Version 1709 Guest OS
Select the Windows 8.1 Virtual Machine and select Play:








VMware easy install will allow isntalaltion of each Windows 10 Build using a local account:




