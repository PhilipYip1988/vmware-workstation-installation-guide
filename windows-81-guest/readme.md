# Windows 8.1 Guest

## Notes

Step-by-step guides for VMware Workstation 17.6.4, focused on running Windows 8.1 in a virtual environments. Learn to enable shared folders, USB passthrough and serial port passthrough to control legacy scientific instruments and laboratory hardware, making older software and devices compatible with modern systems. Ideal for university researchers, lab technicians, and IT staff supporting legacy lab equipment. Windows 8.1 reached its official end of life in January 2023, meaning Microsoft no longer provides security updates, bug fixes, or technical support for this operating system. Activation servers have also been retired, so installations can only proceed with generic keys in an unactivated state, leaving a permanent watermark and limited customization options.

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

## USB Passthrough

A legacy USB Device can be passed through from the Windows 11 Host or Ubuntu 24.10 to the Windows 8.1 Guest. In this example a Brother QL-570 label printer will be used. The Windows 8.1 driver and software can be downloaded on the Windows 11 Host:

<img src="https://github.com/user-attachments/assets/da43f4fd-6998-4744-94ce-ad5ecaca3fb2" width="600"/>

The printer driver and p-touch editor will be downloaded:

<img src="https://github.com/user-attachments/assets/a2720f5a-0239-4f04-9282-04d2b350208d" width="600"/>

And copied to the folder `vmshared`:

<img src="https://github.com/user-attachments/assets/90e4cc4c-f7d4-4098-af59-a412bea97cdb" width="600"/>

This can be accessed in the Windows 8.1 Guest:

<img src="https://github.com/user-attachments/assets/eefe5520-4229-4421-a1a3-601cdb6ee6e3" width="600"/>

<img src="https://github.com/user-attachments/assets/76af4a98-3c32-4cde-a831-d36a2574e2a4" width="600"/>

If the files do not show, right click empty space in the folder and select refresh:

<img src="https://github.com/user-attachments/assets/9e768f96-7079-4249-b5ca-cbb87d830291" width="600"/>

The printer driver can be installed by launching the application:

<img src="https://github.com/user-attachments/assets/e5f09f44-4009-4999-ab98-88f93b953b72" width="600"/>

And extracting it:

<img src="https://github.com/user-attachments/assets/ceec1e71-1f20-4891-b3e8-4b92f463a080" width="600"/>

<img src="https://github.com/user-attachments/assets/a40436d3-a1df-4635-a414-88b3fcbe8f42" width="600"/>

Then launching the setup from the extracted folder in vmshared:

<img src="https://github.com/user-attachments/assets/ce1d42ae-b6d6-4332-90bd-0d5d637f76f8" width="600"/>

Accepting the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/a4adc1ba-1f8f-4b29-a8f4-c3b8f340df69" width="600"/>

And then selecting Start:

<img src="https://github.com/user-attachments/assets/03126062-bd6a-4d7b-84d4-2598a550720b" width="600"/>

The printer driver will now ask for the printer to be connected to the PC. Select Player → Removable Devices → Brother WL-570 → Connect:

<img src="https://github.com/user-attachments/assets/c68176ad-5445-4319-98cc-574d3388b33d" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/e13b0699-8ef5-41df-903f-6b5f3fbfc604" width="200"/>

Select OK:

<img src="https://github.com/user-attachments/assets/3cdd3b3c-ef22-46fe-9384-96f458ef75cc" width="600"/>

The Windows 8.1 VM will restart, now the ptouch editor software can be installed. Launch the setup:

<img src="https://github.com/user-attachments/assets/30d682d9-007a-46a0-9d0d-8cb123af22e2" width="600"/>

Accept the User Account Control Prompt:

<img src="https://github.com/user-attachments/assets/e4b6e02b-2313-45a4-8ef5-a363b84f06d0" width="600"/>

Accept the license agreement:

<img src="https://github.com/user-attachments/assets/e3e4ae3e-fb4d-46f8-8a2f-69be02ba9b5b" width="600"/>

Select install:

<img src="https://github.com/user-attachments/assets/b95767e3-1c5b-4d3e-a06b-7b12498a881e" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/fb0a03c8-b5da-40b0-a32d-ece4586d264b" width="600"/>

Launch the ptouch editor software:

<img src="https://github.com/user-attachments/assets/4cdfc9ca-4dce-4587-b1a5-f45bee585d24" width="600"/>

<img src="https://github.com/user-attachments/assets/2553d51e-78a7-4d27-8b16-a2bffc61507b" width="600"/>

Type in a label and select print:

<img src="https://github.com/user-attachments/assets/257f61d4-07cc-41bf-ba82-bdb6d1dd632b" width="600"/>

Select print:

<img src="https://github.com/user-attachments/assets/0e29dc3d-08b8-4403-99c6-9f0cabca2348" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/1d993525-2399-4d19-903d-e7af10a2d642" width="600"/>

The label is printed using the QL-570 label printer attached to a USB port on the Windows 11 Host PC that is passed through to the ptouch editor softare on the Windows 8.1 VM Guest:

<img src="https://github.com/user-attachments/assets/8340a673-b5e6-4a1e-b640-b9718ff441bb" width="600"/>

## Serial Port Passthrough

Close the Windows 8.1 VM. Attach a USB to Serial Port to the Window 11 Host PC:

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

<img src="https://github.com/user-attachments/assets/05fb8c57-6ba6-49c9-8a57-002133ad60ad" width="600"/>

Select Add...:

<img src="https://github.com/user-attachments/assets/9077ecd0-5ee2-48eb-bfd4-b5e067fe35fa" width="600"/>

Select Serial Port and Finish:

<img src="https://github.com/user-attachments/assets/53f4a23b-226a-4761-b2a5-475c3c5e183f" width="600"/>

Select Connect at Power On. Autodetect is useful for a single port, but for multipe ports, it is more useful to select the serial Port indiviually. In this example COM3 will be used:

<img src="https://github.com/user-attachments/assets/0a293fbd-f37f-4576-a3eb-4e21a1ed2f6b" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/dae7d96c-d19b-4d1c-a08a-919754333180" width="600"/>

Launch the Windows 8.1 VM:

<img src="https://github.com/user-attachments/assets/20402eac-ab05-406a-9b44-db8e041eeed3" width="600"/>

Right click computer and select properties:

<img src="https://github.com/user-attachments/assets/e871700c-aa65-4944-9d1e-221321691e2e" width="600"/>

Select Device Manager:

<img src="https://github.com/user-attachments/assets/b8f53273-9c07-4804-a624-c42cfe43e1b5" width="600"/>

Expand ports, note the Windows 11 COM3 is passed through to the Windows 8.1 VM as COM1:

<img src="https://github.com/user-attachments/assets/5b906def-7e6d-4c8b-a608-7b368725ca45" width="600"/>

Right click the communication port and select Properties:

<img src="https://github.com/user-attachments/assets/b56b66cb-f619-48a8-9f2b-db0e03e53e23" width="600"/>

Select the Port Settings tab. The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects (consistent with the settings on the Windows 11 Host):

<img src="https://github.com/user-attachments/assets/701147c6-d674-4a08-b767-30b4fff2a0d3" width="600"/>

Select Advanced:

<img src="https://github.com/user-attachments/assets/16c62122-fc51-4fca-ab82-a85ed1920968" width="600"/>

Update the COM Port Number to be consistent with the Windows 11 Host. In this case COM3. Select OK:

<img src="https://github.com/user-attachments/assets/53733154-7fda-40a8-8e93-5b5aa9aa7dac" width="600"/>

The Serial Port should now display as COM3. If the Serial Port still displays as COM1, select refresh:

<img src="https://github.com/user-attachments/assets/2d16b91f-d27b-42ae-90b9-b875171e9b56" width="600"/>

Although the Serial now displays as COM3 in the evice Manager, it oftens isn't accessible using that port number until the Windows 8.1 VM is restarted. I don't have a device that connects via Serial Port, so will test the Serial Port using Python with pyserial. The Serial Port looks like the following:

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

<img src="https://github.com/user-attachments/assets/8e7d410e-2a42-4c83-9f45-01515a4bd97f" width="600"/>

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

<img src="https://github.com/user-attachments/assets/55bec621-bf10-4e27-b433-6eb5964d02fc" width="600"/>

Select file → save as:

<img src="https://github.com/user-attachments/assets/d7a2cb77-ec45-43c0-8454-dc80f6dc6e45" width="600"script.py/>

Save the file as `script.py` ensuring that save as type is All Files and Encoding is UTF-8:

<img src="https://github.com/user-attachments/assets/345ff5fd-f64d-466b-8d19-78159b780947" width="600"/>

The script file is in Documents, which is a Library of folders:

<img src="https://github.com/user-attachments/assets/e3c03d7d-15b8-4286-adee-45c4f943a032" width="600"/>

Right click the script file and select Properties:

<img src="https://github.com/user-attachments/assets/98d9b011-f579-420c-b0ae-0b4cc93a585b" width="600"/>

This will give the folder path:

<img src="https://github.com/user-attachments/assets/3eba065c-06bc-46c0-ab15-8584638169ea" width="600"/>

Right click the start button and select command prompt:

<img src="https://github.com/user-attachments/assets/3cee5376-49a7-4daa-a81c-74fe8ac042c2" width="600"/>

Launch the script file in the command prompt:

```powershell
python C:\Users\Philip\Documents\script.py
```

Because the Windows 8.1 VM has not been restarted, Pyserial cannot find the port at COM3:

<img src="https://github.com/user-attachments/assets/a60e68af-837a-4d1a-bcea-5edc74aa9187" width="600"/>

After a restart with no pins connected, the following shows:

<img src="https://github.com/user-attachments/assets/e0842283-bc24-4526-a8e9-e92c91a986fe" width="600"/>

<img src="https://github.com/user-attachments/assets/a0b70f5a-30cf-4a8e-a239-5dacfce62a5f" width="600"/>

With pins 2 and 3 connected, the following shows:

<img src="https://github.com/user-attachments/assets/0ec50a62-e408-469d-ae8f-493599320523" width="600"/>

<img src="https://github.com/user-attachments/assets/27e9ed86-4ee4-440f-9677-c7377ca25f4a" width="600"/>

The code works as expected and interfaces with the Serial Port which is passed through to the Windows 8.1 VM from the Windows 11 Host PC.

## Parallel Port Passthrough

VMware can theoretically passthrough a physical parallel port. However, USB-to-parallel adapters are designed exclusively for printers and do not provide true parallel port functionality for other hardware. By the time of Windows 8.1, parallel ports were already considered legacy and were rarely included on new PCs. I do not have a parallel port printer available to test passthrough functionality.

## PCI/PCIe Card Passthrough

VMware does not support direct passthrough of PCI or PCIe cards to a guest virtual machine. Additionally, there are no USB adapters that replicate the functionality of PCI/PCIe expansion cards.

## Activation

Microsoft have closed down Windows 8.1 Activation Servers, so Windows 8.1 cannot be activated. A watermark displays to the bottom right and some personalisation settings cannot be used. Otherwise the Windows 8.1 VM is fully usable:

Return to [VMware Installation Guide](../readme.md).

Python is just used as an example of a legacy program to run in a Windows 7 VM and not covered in detail in this tutorial. For details about using Python, see my other GitHub repository [Python Tutorials](https://github.com/PhilipYip1988/python-tutorials).
