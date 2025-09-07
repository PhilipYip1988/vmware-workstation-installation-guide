# Windows 8.1 Guest

## Notes

On modern hardware, with a 12th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
mks.enableVulkanRenderer = "FALSE"
```

The first setting prevents use of a memory management unit that Windows 8.1 doesn't understand and can lead to a Blue Screen of Death (BSOD). The second setting prevents VMware from using Vulkan for rendering, which isn't supported by Windows 8.1 and often leads to black screens. 

## Downloads

### Windows 8.1 ISO

The Website Archive.org hosts the ISO created from Microsoft before Microsoft removed Windows 8.1 downloads from their download servers. The ISO Checksums should match the ISOs I downloaded from Microsoft's servers before the downloads got removed:

|Language|Name|SHA256|Architecture|Editions|
|---|---|---|---|---|
|English (UK)|[Win8.1_EnglishInternational_x64](https://archive.org/details/win8.1x32x64)|DE3D15AFBDA350F77C27AAD76844477E396E947302D7402C09A16F3FA7254C68|64|Home<br>Pro|
|English (UK)|[Win8.1_EnglishInternational_x32](https://archive.org/details/win8.1x32x64)|777D22B51326697A8227741D4565AD5A52376BD295862C0DD96BA53E47514137|32|Home<br>Pro|
|English (UK)|[Win8.1_SingleLang_EnglishInternational_x64](https://archive.org/details/win8.1x32x64)|FCE8ECD85C4443521A2658421F6AD371255971632D7AD6CF935233D61B91588F|64|HomeSL|
|English (UK)|[Win8.1_SingleLang_EnglishInternational_x32](https://archive.org/details/win8.1x32x64)|2ECA572129838E29C60103B2800C3EA094478D272EC72D9AB1369788246655D0|32|HomeSL|
|English (UK)|Win8.1_Pro_N_EnglishInternational_x64|6676DC2301A8C5DFB046C33EB4D34DE29BA1E8193CB3259116247D35D56587B7|64|HomeN<br>ProN|
|English (UK)|Win8.1_Pro_N_EnglishInternational_x32|3EAB61937D6337FAA01925F0398279F9151D6C87EED58719156BAADCDA809902|32|HomeN<br>ProN|
|English (US)|[Win8.1_English_x64](https://archive.org/details/win-8.1-english-x-64\_20240121)|D8333CF427EB3318FF6AB755EB1DD9D433F0E2AE43745312C1CD23E83CA1CE51|64|Home<br>Pro|
|English (US)|Win8.1_English_x32|A569191631A41A260CD180B0D6B926CD2064235F0AC0E3E4CCC387F440E0827A|32|Home<br>Pro|
|English (US)|[Win8.1_SingleLang_English_x64](https://archive.org/details/win-8.1-single-lang-english-x-64\_202301)|28BB2FCF46DB2B8C31A0ADA8E405D71170EE3CBE5772FDD2DA64B6500BE93097|64|HomeSL|
|English (US)|[Win8.1_SingleLang_English_x32](https://archive.org/details/win-8.1-single-lang-english-x-32\_202301)|29B4AF02988EB768F2D01EC6991CAD84AD87B4453C0C7365160D36E95CC1C1CF |32|HomeSL|
|English (US)|Win8.1_Pro_N_English_x64|BCFAAFA3A370BEA1C3A9991784D1D2534B42F09AAE55AE7CAA59FBB0168324A1|64|HomeN<br>ProN|
|English (US)|Win8.1_Pro_N_English_x32|C4A4BA7FBC1928AF7A4C462CE40FFB481697EA37BD3C85C627600FE79B3EC902|32|HomeN<br>ProN|

### WSUS Offline Update

The WSUS Offline Update still supports Windows 8.1:

* [WSUS Offline Update](https://download.wsusoffline.net/)

Download the most recent version:

<img src="https://github.com/user-attachments/assets/98096a2d-c2e6-4a3c-930c-2d2cc8d0214d" width="600"/>

Right click WSUS Offline 120:

<img src="https://github.com/user-attachments/assets/f05fcea4-bef6-4d41-9cdb-0487d7133133" width="600"/>

Select Extract All...:

<img src="https://github.com/user-attachments/assets/5221527c-cd34-454a-ab4f-1c3cbc428440" width="600"/>

Select Extract:

<img src="https://github.com/user-attachments/assets/d63b6d13-bce1-4f0b-a273-b25de25392e0" width="600"/>

Go to the `wsusoffline` folder:

<img src="https://github.com/user-attachments/assets/bb3aa358-5dfb-4cc7-828f-259ec73f9261" width="600"/>

Run `UpdateGenerator.exe`:

<img src="https://github.com/user-attachments/assets/7238080e-2def-4125-8438-a54245bf9489" width="600"/>

Uncheck all Windows 10 Versions:

<img src="https://github.com/user-attachments/assets/6a74f132-a4dc-4813-9b65-fa304e60d8a9" width="600"/>

Select Windows 8.1 x64 (64 Bit) or Windows 8.1 x86 (32 Bit). Under options select verify downloaded updates and include C++ Runtime Libraries and .NET Frrameworks. Under ISO image(s) select per selected produt and language/ Select Start:

<img src="https://github.com/user-attachments/assets/de0b3b61-a706-40b2-a212-4f693e429e76" width="600"/>

The updates will download:

<img src="https://github.com/user-attachments/assets/d10d7bd2-b3d1-4e7c-b6ff-59f4028905da" width="600"/>

And the ISO will be created:

<img src="https://github.com/user-attachments/assets/dfebf033-7f03-4e43-afca-4dbb0a494b0c" width="600"/>

Select Yes to view the log file:

<img src="https://github.com/user-attachments/assets/2c1b6195-a72b-4155-aae2-21ae4a4e4900" width="200"/>

It is found in the `iso` folder:

<img src="https://github.com/user-attachments/assets/acd2da1e-a11a-4394-b684-f593d6117c19" width="600"/>

<img src="https://github.com/user-attachments/assets/c7d23c1c-78a6-4146-ac11-0f7cd72c77f6" width="600"/>

## Windows 11 Host or Ubuntu 24.10 Host System Requirements

Your Windows 11 Host PC or Ubuntu Host PC should satisfy the minimum system the system requirements of Windows 11 and have additional overhead to run a Virtual Machine in addition to these requirements. It is recommended to have a Host PC with at least:

* i5 or i7 11th Generation Intel Processor or Newer
* 16 GB RAM
* 1 TB SSD

## Configuring Virtual Hardware for a Windows 8.1 Guest

Select Player → File → New Virtual Machine:

<img src="https://github.com/user-attachments/assets/19a2c964-1044-40c6-a2e3-d530c9eef01c" width="600"/>

Select Installer Disc Image File ISO and Browse:

<img src="https://github.com/user-attachments/assets/f65d85d3-d39b-4e41-93d6-e2feac91ee32" width="600"/>

Select the Windows 8.1 ISO and then Open:

<img src="https://github.com/user-attachments/assets/bdc96f2a-250e-4ad0-8ace-a211cfa6ece3" width="600"/>

Under version of Windows to Install, select Windows 8.1 Home or Windows 8.1 Pro from the drop down list and supply the corresponding generic product key:

|Edition|Generic Product Key|
|---|---|
|Windows 8.1 Home|334NH-RXG76-64THK-C7CKG-D3VPT|
|Windows 8.1 Home Single Language|Y9NXP-XT8MV-PT9TG-97CT3-9D6TC|
|Windows 8.1 Pro|XHQ8N-C3MCJ-RQXB6-WCHYG-C9WKB|
|Windows 8.1 Home N|6NPQ8-PK64X-W4WMM-MF84V-RGB89|
|Windows 8.1 Professional N|JRBBN-4Q997-H4RM2-H3B7W-Q68KC|
|Windows 8.1 Professional with Media Center|GBFNG-2X3TC-8R27F-RMKYB-JK7QT|

Input your User Name and select next:

<img src="https://github.com/user-attachments/assets/5daa03bc-e98e-4ed7-995f-9297aebae6cf" width="600"/>

The generic product keys allow product installation but not product activation. They give a 30 day trial, after the 30 day trials, the Windows Desktop and Windows Settings will be watermakred saying activate Windows and some customisation settings will be greyed out.

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive, you may want to move this to a local only location) and select next:

<img src="https://github.com/user-attachments/assets/cc35b89a-3531-4230-bc4a-994edc0652ea" width="600"/>

Note the name and location as these will be used later. The default maximum size of the Windows 8.1 Guest is 60 GB which is too small, I recommend increasing this to 256 GB. Note the files on the Windows 11 Host won't be 256 GB but can be up to 256 GB if the Windows 8.1 Guests Virtual Drive is fully occupied with files:

<img src="https://github.com/user-attachments/assets/f4ab9821-08e7-4ce8-9e68-9617f07cbf98" width="600"/>

Select customise hardware:

<img src="https://github.com/user-attachments/assets/a48697c0-9e44-427b-b2cc-4e7a0d811180" width="600"/>

Increase the RAM to 4096 MB:

<img src="https://github.com/user-attachments/assets/566ef98b-181a-494d-b945-5f791e9c0f45" width="600"/>

Increase the number of processors to 4:

<img src="https://github.com/user-attachments/assets/eead2c2b-6c9c-4520-8bd1-74f93100a2d7" width="600"/>

Windows 8.1 has reached end of life and should be deemed unsafe to use online. The virtual network adaptor is connected by default and can optionally be disabled:

<img src="https://github.com/user-attachments/assets/04645bf6-c37f-47a0-8ac4-fff1045e5774" width="600"/>

Under USB Compatabiliy, USB 3.1 should be selected:

<img src="https://github.com/user-attachments/assets/c60b957a-4ccf-4722-b36a-53125a6a6c30" width="600"/>

Under Sound Card, use the default options:

<img src="https://github.com/user-attachments/assets/71b22aeb-37e1-43c1-87a6-e6d31dab6cfe" width="600"/>

Under Display, the default options can be selected. Select Close:

<img src="https://github.com/user-attachments/assets/dada321e-4eb4-455b-b1ca-e2cd0a98e9f7" width="600"/>

**Uncheck Power On this Virtual Machine After Creation (aws we want to make some changes to the Virtual machine's configuration file before launching it).** Select Finish:

<img src="https://github.com/user-attachments/assets/4f1da4fa-c845-465a-89ef-856aeee93e0a" width="600"/>

## Windows 8.1 Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows 8.1 Guest is installed:

<img src="https://github.com/user-attachments/assets/01e35eb3-fdc0-4c94-b17e-093e97496126" width="600"/>

Look for the `Windows 8.x x64.vmx` file:

<img src="https://github.com/user-attachments/assets/17794339-a533-49aa-bb37-1ba2ccc219ba" width="600"/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/36176a99-9763-410a-9d58-9a99b0425163" width="600"/>

Press `Ctrl+f` to begin a search for an option for example `bios.bootDelay`:

<img src="https://github.com/user-attachments/assets/0e0cae81-c6fd-4de2-a99d-3388bbc2f418" width="600"/>

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/4829a77b-78a8-4f3b-8240-bc8d5100e5dc" width="600"/>

### Modern Generation Processors (11-14th Generation)

Certain legacy settings may need to be configured to run older guest operating systems such as Windows 8.1:

<img src="https://github.com/user-attachments/assets/16300bec-90fc-4d71-9883-fa6028f8b29c" width="600"/>

Legacy monitor / virtualization settings

```
mks.enableVulkanRenderer = "FALSE"
```

Legacy monitor / virtualization settings:

```
monitor.virtual_exec = "hardware"
```

## Installing the Windows 8.1 Guest OS

Select the Windows 8.1 Virtual Machine and select Play:

<img src="https://github.com/user-attachments/assets/769a90b3-c90a-4158-8919-0c01cb320522" width="600"/>

The Windows Install will be fully automated and automatically restart:

<img src="https://github.com/user-attachments/assets/33480cc5-7efd-409b-b1d9-9fafe2c645da" width="600"/>

<img src="https://github.com/user-attachments/assets/61446d6b-5fc3-4351-823e-4ed3b4c58036" width="600"/>

<img src="https://github.com/user-attachments/assets/d527fd5f-a170-4b5c-8aa1-d1a621653cb4" width="600"/>

<img src="https://github.com/user-attachments/assets/0bbaf350-ec57-427c-8ff7-59fb0e61f748" width="600"/>

VMware Tools will also automatically install:

<img src="https://github.com/user-attachments/assets/547da43a-bd94-40ec-898c-9c0e43fccc82" width="600"/>

<img src="https://github.com/user-attachments/assets/07051e47-3a08-4f41-8480-4c6ee005b749" width="600"/>

At the end of the install, select OK:

<img src="https://github.com/user-attachments/assets/abc9291a-9e16-40fa-84c2-937733eef66f" width="600"/>

Then click on your User Name to log back in:

<img src="https://github.com/user-attachments/assets/50d0860b-d590-41cd-9d13-5f1c5d7f4446" width="600"/>

## Installing Windows 8.1 Updates

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/b87027a4-0114-4742-834f-ba05f61978ee" width="600"/>

Ensure Connected and Connect at Power On are checked and select Browse:

<img src="https://github.com/user-attachments/assets/a796861d-8370-47bb-824b-97688643d948" width="600"/>

Select the `wsusoffline120` folder:

<img src="https://github.com/user-attachments/assets/3a8c31ac-4864-4c5a-ad7f-3efb04f058b6" width="600"/>

Select the `wsusoffline` folder:

<img src="https://github.com/user-attachments/assets/9b117432-4645-4094-87f2-93947171cf11" width="600"/>

Select the `iso` folder:

<img src="https://github.com/user-attachments/assets/1c4450bf-ca5f-43e6-af7e-762c99cc15dd" width="600"/>

Select the `wsusoffline-w63-x64.iso` (Windows 8.1 64 Bit) or `wsusoffline-w63-x86.iso` (Windows 8.1 32 Bit) and select Open:  

<img src="https://github.com/user-attachments/assets/c1a289be-60be-4bfb-ab30-8f694957c0e2" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/b0d096d7-444d-4ed7-8c44-888f6f2831f1" width="600"/>

Select the DVD Drive:

<img src="https://github.com/user-attachments/assets/17e321b7-f678-4bd4-9753-792c492d7735" width="600"/>

Select Run WSUS Offline Update:

<img src="https://github.com/user-attachments/assets/0fd6300f-51da-4799-aa2c-9fcec4d4fe24" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/6663561f-e108-4815-8c0d-29d10716fe55" width="600"/>

Under Installation check Update C++ Runtime Libraries, Install .NET Framework 3.5 and 4.8, Update Root Certificates and Install Management Framework 5.1. Under Control check Verify Installation Packages, Automatic Reboot and Recall and Shut Down on Completion:

<img src="https://github.com/user-attachments/assets/cb0f7a05-aafd-4824-b648-f3f2d7ab9e02" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/e24a7253-5447-4336-a7ad-771bbda1e08f" width="600"/>

Select Start:

<img src="https://github.com/user-attachments/assets/cfb2acef-5340-42a7-bf01-ce926a790e78" width="600"/>

WSUS Offline Update will patch Windows 8.1:

<img src="https://github.com/user-attachments/assets/4d09e903-47c5-441c-9ea9-84373b7eebc4" width="600"/>

To see the updates isntalled, right click the Start Button and select Control Panel:

<img src="https://github.com/user-attachments/assets/6998e71a-8d9b-414b-b1d9-67cbd4e45331" width="600"/>

Select Programs:

<img src="https://github.com/user-attachments/assets/4b227210-f342-4585-b890-4e2a35853814" width="600"/>

Select Programs and Features:

<img src="https://github.com/user-attachments/assets/c914fdc1-0de6-4dbc-910c-b4396ae855a1" width="600"/>

Select View Installed Updates:

<img src="https://github.com/user-attachments/assets/f459041c-1c99-401e-afd4-4e603187b311" width="600"/>

And all Windows 8.1 Updates are Installed:

<img src="https://github.com/user-attachments/assets/c7d42ed0-6837-4dc4-b462-28f22b4a7501" width="600"/>

## Enabling Microsoft .Net 3.5 Framework

Select Turn Windows Features On or Off:

<img src="https://github.com/user-attachments/assets/6e1958d1-8ed2-47a8-871b-998ef8069b5e" width="600"/>

Microsoft .Net 3.5 was considered legacy in Windows 8.1 and wasn't enabled by default.

<img src="https://github.com/user-attachments/assets/2f7dc7cc-4fc9-401d-88ca-8f844e5454ec" width="600"/>

It is better to install this feature from the Windows 8.1 ISO. Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/d2755b71-241a-4a6b-96c0-f20c719e6a58" width="600"/>

Use the dropdown list to select the previously used Windows 8.1 ISO:

<img src="https://github.com/user-attachments/assets/f9d75ff7-1800-4dd6-9fd5-8ef4327fe635" width="600"/>

<img src="https://github.com/user-attachments/assets/303bde16-b92f-4c29-a702-ec0df9ee8007" width="600"/>

Right click he Start Button and select Command Prompt (Admin):

<img src="https://github.com/user-attachments/assets/efe52270-a7c3-4954-a085-7215be441800" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/50d109a3-6518-42ee-8740-7ebafa73f530" width="600"/>

Input the command:

```powershell
DISM /Online /Enable-Feature /FeatureName:NetFx3 /All /LimitAccess /Source:D:\sources\sxs
```

<img src="https://github.com/user-attachments/assets/184be2db-bdbf-42a4-baf4-a0ebbe359011" width="600"/>

The .NET Framework 3.5 will now be enabled:

<img src="https://github.com/user-attachments/assets/b1819dae-3c05-46db-b638-e6f162b6d154" width="600"/>

Use te WSUS Offline Update again to apply .NET Framework 3.5 Updates.

## Backing up the VM

Shut down the Windows 8.1 VM and then create a copy of the VM folder. Should you encounter problems with your VM after installing software, you can delete the original folder and rename the copied folder to the original folders name. Essentially this will give you a VM to roll back to:

<img src="https://github.com/user-attachments/assets/42f7e69c-c4f7-442e-a0c8-f78c87a31aa1" width="600"/>

## Shared Folders

Create a new folder on the Windows 11 Host or Ubuntu 24.10 Host PC called `vmshared`:

<img src="https://github.com/user-attachments/assets/2c6992d8-2956-4ed3-82c3-40d31a9652c1" width="600"/>

<img src="https://github.com/user-attachments/assets/00f073e9-a589-4bdb-b114-22f1c5e69986" width="600"/>

Select Player → Manage → Virtual Machine Settings:

<img src="https://github.com/user-attachments/assets/474b50f5-b5c6-4dd4-bf48-3a5602518cca" width="600"/>

Select Options → Shared Folders and change the setting to Always Enabled and check Map Network Drive in Windows Guests. Then select Add:

<img src="https://github.com/user-attachments/assets/cf897dbd-5bde-4dbb-9c2b-0d467149592d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/57bdb469-9831-4649-aca7-72f049a2d4ce" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/b98799dc-eba2-4d58-bced-9503772a83c1" width="600"/>

Select the `vmshared` folder and select OK:

<img src="https://github.com/user-attachments/assets/f48f9285-1573-4bd0-8b70-bfa3fdb8d9ab" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/e69723de-493c-466b-9c0a-b75544cc1515" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/09568bed-f686-4227-bb1a-49fa7ee6bc8c" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/ebe94dfa-e317-41be-9c63-963973acd09f" width="600"/>

Select File Explorer. this PC and Shared Folders:

<img src="https://github.com/user-attachments/assets/5fc1db5b-e2d5-4e7a-bea2-2dcfc11de82c" width="600"/>

Select `vmshared`:

<img src="https://github.com/user-attachments/assets/70ba3a64-7a8f-4eb6-8df2-232fb6c3e77c" width="600"/>

A file added to this folder on the Windows 11 Host can be seen in the Windows 8.1 Guest VM:

<img src="https://github.com/user-attachments/assets/5b74d84e-6843-4887-abe3-a2f4f7535da6" width="600"/>

## Installing Python

Python will be used as an example of installing a program on Windows 8.1. [python-3.8.10-amd64.exe](https://www.python.org/downloads/release/python-3810/) is the latest version of Python to work on Windows 8.1. The installer can be downloaded on the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/53b12abd-f0dd-4462-9a56-b25ca63bc681" width="600"/>

When using a Windows 11 Host, the file can be dragged and dropped over to the VM. On a Linux host, the most commonly used Desktop Environment GNOME (and less common Desktop Environments) are not supported and shared folders have to be configured:

<img src="https://github.com/user-attachments/assets/0fc50be4-310e-4296-b9fd-50d124f5628c" width="600"/>

Launch the setup:

<img src="https://github.com/user-attachments/assets/a3c17c79-e0da-4b5d-88ac-1567f20042fa" width="600"/>

Select add to path and then select install now:

<img src="https://github.com/user-attachments/assets/9f79076e-c234-452a-af19-97fa2a339c83" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/dd861b4f-4c5f-48ed-9265-a5a2fcf81a3c" width="600"/>

Select Close:

<img src="https://github.com/user-attachments/assets/43c6c5a6-e58c-4363-a73a-6c95dc885274" width="600"/>

Right click the start button and select Command Prompt:

<img src="https://github.com/user-attachments/assets/b85fc72d-3d2b-4ebe-9d82-89a37cd9a8d0" width="600"/>

To launch Python input:

```powershell
python
```

Notice the change to the Python prompt `>>>`:

<img src="https://github.com/user-attachments/assets/153a618e-0394-4955-971b-a229d7f8697f" width="600"/>

Python code can now be used:

```python
print('Hello World!')
```

<img src="https://github.com/user-attachments/assets/ff82ffa3-7323-4b12-a645-180796832f94" width="600"/>

To exit python input the function:

```python
exit()
```

<img src="https://github.com/user-attachments/assets/ce5a84eb-7364-4e12-be88-0703eddbcec3" width="600"/>

Notice the return to the CMD prompt. 

To use the package manager requires Internet Connectivity. Select Player → File → Network Adaptor → Connect:

<img src="https://github.com/user-attachments/assets/2da94029-f839-41a0-adc6-591c792e3f2c" width="600"/>

Recall however that Windows 8.1 is past end of life and is not safe to use online for general web use.

The Python package can be installed using:

```powershell
pip install pyserial==3.5
```

<img src="https://github.com/user-attachments/assets/8b7e558d-57ec-4218-a0ba-e67701767b27" width="600"/>

And can be imported into a Python program:

<img src="https://github.com/user-attachments/assets/0264cd37-baeb-415b-b235-6d9a6253bc76" width="600"/>


























## Activation Popup

Microsoft have closed down Windows 8.1 Activation Servers, so Windows 8.1 cannot be activated. A watermark displays to the bottom right and some personalisation settings cannot be used. There is a periodic popup prompting for Product Activation. This popup can be removed by pressing `⊞` and `r` and typing in:

```
regedit
```

Then navigating to the folder:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform\Activation
```

Creating a new DWORD (32-Bit) value called: 

```
Manual
```

And setting to a value of:

```
1
```




Task Scheduler Library > Microsoft > Windows > Windows Activation Technologies

You’ll see tasks like ValidationTask or Notification.

Right-click → Properties → Triggers tab.

Either disable the triggers or change them to run once a month instead of daily/hourly.

Apply and close.

