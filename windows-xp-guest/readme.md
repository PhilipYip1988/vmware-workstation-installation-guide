# Windows XP

Step-by-step guides for VMware Workstation 17.6.4, focused on running Windows XP in a virtual environments. Learn to enable shared folders, USB passthrough and serial port passthrough to control legacy scientific instruments and laboratory hardware, making older software and devices compatible with modern systems. Windows XP has widespread legacy use as many scientific instruments from the late 1990s to late 2000s shipped with Windows XP drivers only. Ideal for university researchers, lab technicians, and IT staff supporting legacy lab equipment. Windows XP reached its official end of life in April 2014, meaning Microsoft no longer provides security updates, bug fixes, or technical support for this operating system. Activation servers have also been retired, so installations can only proceed with generic OEM SLP keys. 

## YouTube Video

* [YouTube](https://www.youtube.com/watch?v=UCgV4CsyyIE)

## Notes

VMware Workstation Player 17.6.4 has Windows XP as an option for a Virtual Machine. However Windows XP is regarded as a legacy Operating System and isn't tested by Broadcom. Moreover the VMware Tools 12.5.3 which comes with VMware workstation player doesn't support Windows XP and the following errors will display if they are attempted to be installed in the Windows XP VM:

VMware Tools 10.0.12 is the last version of VMware Tools to support Windows XP and should be downloaded seperately as an ISO. This ISO should be mounted in the VM so they can be installed manually.

On modern hardware, with a 11th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

The first setting allows the CPU to optimise the VM performance, the VM may be very slow without this setting. The second setting prevents use of a memory management unit that Windows XP doesn't understand and can lead to a Blue Screen of Death (BSOD). The third setting prevents VMware from using Vulkan for rendering, which isn't supported by Windows XP and often leads to black screens. The last two settings prevent Windows XP from seeing unsupported CPU features which Windows XP doesn't understand and can lead to a Blue Screen of Death (BSOD).

## Installation Media

The biggest difficulty to setting up a Windows XP Virtual Machine is obtaining the installation as Microsoft nor its OEMs provided official download links. WinWorld hasn't been updated to include Windows XP:

* [WinWorld Placeholder: Windows XP ISO and Product Key](https://winworldpc.com/product/windows-xp/final) 

<details>
  <summary>Archive.org</summary>

The Website Archive.org hosts each Unofficial Dell Windows XP Reinstallation ISO:

* [Dell Windows XP SP3 Professional Reinstallation ISO](https://archive.org/details/dell.-xp-pro-sp-3)
* [Dell Windows XP SP2 Home Reinstallation ISO](https://archive.org/details/dell-xp-home-sp-2)
* [Dell Windows XP SP2 Media Center Reinstallation ISO](https://archive.org/details/xp-mce-sp-2)

The ISO Checksums can be used to ensure a complete download but these do not match official Dell or Microsoft records as they would have been created from a CD/DVD by an end user:

|ISO|sha256 ISO Checksum|
|---|---|
|XP Pro|a4cf4e53ac9157cf20913a77f438a64e4fa3b908e4e28cb0d2a08d49fa62e49f|
|XP Home|aa0629a1d076c835b49b4b4e97d6f7717813d051cfbeba8d9d69ee6d8f6e8866|
|XP MCE|293a5f6424888f78865e78f33dfd0714bbe54e61dcf27c9c16cacfa08eb4fa0a|

</details>

### Creating a Installation ISO from a CD

Dell Systems came with a Windows XP Reinstallation CD/DVD which can be converted into an ISO using nLite:

* [Using nLite to Create a Windows XP Installation ISO from a Dell Windows Reinstallation CD/DVD](./integration/readme.md)

### WSUS Offline Update

The Website Archive.org hosts the ISO created from WSUS Offline Update before Microsoft removed Windows XP downloads from their download servers:

* [WSUS Offline Update Windows XP (Windows XP 32 Bit=wxp-enu)](https://archive.org/details/wsusoffline-eol-windows)

</details>

### VMware Tools ISO

The Windows XP drivers for the Windows XP Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

* [VMware Tools Version 10.0.12 ISO](https://archive.org/details/vmware_tools_pre_vista)

## Windows 11 Host or Ubuntu 24.10 Host System Requirements

Your Windows 11 Host PC or Ubuntu Host PC should satisfy the minimum system the system requirements of Windows 11 and have additional overhead to run a Virtual Machine in addition to these requirements. It is recommended to have a Host PC with at least:

* i5 or i7 11th Generation Intel Processor or Newer
* 16 GB RAM
* 1 TB SSD

## Configuring Virtual Hardware for a Windows XP Guest

Select Player → File → New Virtual machine...

<img src='./images/img_001.png' alt='img_001' width='600'/>

It is recommended to instead use "I Will Install this Operating System Later":

<img src='./images/img_002.png' alt='img_002' width='600'/>

Select Microsoft Windows and Windows XP Professional and select Next:

<img src='./images/img_003.png' alt='img_003' width='600'/>

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive, you may want to move this to a local only location) and select next:

<img src="https://github.com/user-attachments/assets/0fc05e4e-7148-422a-b3e7-872b6bf7377b" width="600"/>

The default maximum size of the Windows XP Guest is 40 GB which is too small, I recommend increasing this to 120 GB. Note the files on the Windows 11 Host won't be 120 GB but can be up to 120 GB if the Windows XP Guests Virtual Drive is fully occupied with files:

<img src='./images/img_005.png' alt='img_005' width='600'/>

Select Customise Hardware:

<img src='./images/img_006.png' alt='img_006' width='600'/>

The default memory used by the Windows XP Guest is 512 MB (0.5 GB). If the Windows 11 Host PC has ≥16 GB RAM, this can be upped to 4096 MB (4 GB) for increased performance of the VM. Note if the Windows 11 Host PC has ≤8 GB of RAM, setting the RAM to 4096 MB (4 GB) may throttle the Host PC leading to decreased performance and 2048 MB (2 GB) may be more approprate:

<img src="https://github.com/user-attachments/assets/dac7f86b-765b-44af-9131-180fffe636a8" width="600"/>


The default number of processors cores used by the Windows XP Guest is 1. This can be upped to 2 if the Windows 11 Host has a processor with ≥ 16 cores. If the Windows 11 Host PC has ≤16 cores, setting this to a higher value may throttle the Host PC leading to an decreased performance:

<img src="https://github.com/user-attachments/assets/c6c02251-1d81-440d-8623-2486c4ac3895" width="600"/>

Under CD/DVD select browse:

<img src="https://github.com/user-attachments/assets/491ba68f-8b39-4fb6-977d-786c0df26cd9" width="600"/>

Load the Dell Windows XP Reinstallation ISO or Windows XP Volume License Installation iSO:

<img src="https://github.com/user-attachments/assets/40a31853-42a2-44d6-973a-9a17e58fb822" width="600"/>

Ensure connected at power on is enabled:

<img src="https://github.com/user-attachments/assets/66d71780-14f2-448f-905a-e8037ee3636a" width="600"/>

Uncheck Connect at Power On for Network Adaptor:

<img src="https://github.com/user-attachments/assets/abe59d92-ffc8-4a9e-8b3e-262e60b089c0" width="600"/>

The default USB Controller for Windows XP is USB 2.0 and Windows XP does not have any drivers for USB 3.0:

<img src='./images/img_013.png' alt='img_013' width='600'/>

The default Sound Card can be used for the Windows XP Guest:

<img src='./images/img_014.png' alt='img_014' width='600'/>

The default Display can be used for the Windows XP Guest:

<img src='./images/img_015.png' alt='img_015' width='600'/>

Select Close and Finish.

<img src='./images/img_016.png' alt='img_016' width='600'/>

## Windows XP Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows XP Guest is installed: 

<img src='./images/img_017.png' alt='img_017' width='600'/>

Look for the `Windows XP.vmx` file:

<img src='./images/img_018.png' alt='img_018' width='600'/>

Open in Notepad or Notepad++ (recommended):

<img src='./images/img_019.png' alt='img_019' width='600'/>

Press `Ctrl+f` to begin a search for an option for example `bios.bootDelay`:

<img src='./images/img_020.png' alt='img_020' width='600'/>

If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src='./images/img_021.png' alt='img_021' width='600'/>

The command above will change the time the Windows XP Guest Virtual BIOS displays before selecting the default boot option giving more time to select the option to boot from CD/DVD. This line can be removed post-installation.

### Modern Generation Processors (11-14th Generation)

Certain legacy settings may need to be configured to run older guest operating systems such as Windows XP.

<img src="https://github.com/user-attachments/assets/0ab7f057-a395-46bb-a2e6-01cf4dd5c92d" width="600"/>

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

The my digital life forums has a post about a modded Virtual BIOS which includes a Dell SLIC 1.0 compatible with Dell Windows XP Professional OEM SLP. These ROMs are not supported by Microsoft or Dell (but then neither is Windows XP). You will need to log into their forums to view the files:

* [My Digital Life: SLIC 1.0, 2.1 Mod](https://forums.mydigitallife.net/threads/vmware-workstation-esxi-bios-efi-slic-mod.64693/#post-1132133)

Extract the downloaded file and navigate to the `17.6.0 Modded ROMs` folder. Rename `WORKSTATION_17.6.0_DELL2.7_SLIC_BIOS.440_(497).ROM` to `modded_BIOS.440.ROM` and copy the modded ROM to the directory of the Windows XP Guest. Update the Virtual Machine Configuration file to:

```
bios440.filename = "modded_BIOS.440.ROM"
```

Note if the corresponding ROM is not found in the directory the above line of code will prevent the Windows XP Guest from booting.

</details>

## Installing the Windows XP Guest OS

Select the Windows XP Guest and select Play:

<img src='./images/img_022.png' alt='img_022' width='600'/>

The WIndows XP Setup will begin:

<img src='./images/img_023.png' alt='img_023' width='600'/>

Press `↵` to continue:

<img src='./images/img_024.png' alt='img_024' width='600'/>

Press `F8` to proceed:

<img src='./images/img_025.png' alt='img_025' width='600'/>

Press `↵` to install Windows XP on the unpartitioned space:

<img src='./images/img_026.png' alt='img_026' width='600'/>

Select Format the System using NTFS (quick):

<img src='./images/img_027.png' alt='img_027' width='600'/>

Select Customise and change the Regional Settings, Location and Keyboard Settings:

<img src='./images/img_028.png' alt='img_028' width='600'/>

<img src='./images/img_029.png' alt='img_029' width='600'/>

<img src='./images/img_030.png' alt='img_030' width='600'/>

Select Next:

<img src='./images/img_031.png' alt='img_031' width='600'/>

Input your User Name and select Next:

<img src='./images/img_032.png' alt='img_032' width='600'/>

Input the computer name and select Next:

<img src='./images/img_033.png' alt='img_033' width='600'/>

Select the Time Zone and select Next:

<img src='./images/img_034.png' alt='img_034' width='600'/>

Select Typical Settings:

<img src='./images/img_035.png' alt='img_035' width='600'/>

Select No, leaving WORKGROUP as the default and then next:

<img src='./images/img_036.png' alt='img_036' width='600'/>

Select OK:

<img src='./images/img_037.png' alt='img_037' width='600'/>

Select OK:

<img src='./images/img_038.png' alt='img_038' width='600'/>

You will be taken to the Windows XP Desktop:

<img src='./images/img_039.png' alt='img_039' width='600'/>

Select the red warning in the system tray, then select Change the way Security Centre Alerts Me:

<img src="https://github.com/user-attachments/assets/8a338f00-979a-40d7-812a-47498ce0f21f" width="600"/>

Uncheck the three boxes:

<img src="https://github.com/user-attachments/assets/67044f4e-3b39-40d7-98f9-cae1ae91e748" width="600"/>

## Installing Windows SP3 and Post-SP3 Updates

Select Player → Manage → CD/DVD and select Settings:

<img src="https://github.com/user-attachments/assets/d3c5d77d-7ece-4916-baff-4af608f7b5ce" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/93f07d33-04b8-4637-babc-bc873699398a" width="600"/>

Select `wsusoffline-wxp-enu.iso`:

<img src="https://github.com/user-attachments/assets/7dec184f-4e9f-4f07-9768-cd754c46ee69" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/593b2247-3cc7-460f-99ec-0553697b38dd" width="600"/>

Select My Computer:

<img src="https://github.com/user-attachments/assets/db0044ea-8918-435b-8f60-985c459fda34" width="600"/>

Right click the D: drive and select explore:

<img src="https://github.com/user-attachments/assets/8f0e8a17-7199-4d38-9151-b8be2cf3a78e" width="600"/>

Select UpdateInstaller:

<img src="https://github.com/user-attachments/assets/20846e29-071e-4983-938d-7d21bc379041" width="600"/>

Select the following options:

<img src="https://github.com/user-attachments/assets/e6fe201f-7fe1-4c11-b93d-de81f7e1aef7" width="600"/>

Updates will install and the VM will reboot multiple times:

<img src="https://github.com/user-attachments/assets/06350ff9-7d6a-4395-8fa6-87c3d2b9d92a" width="600"/>

When finished, the following will display no missing updates found. Nothing to do!

<img src="https://github.com/user-attachments/assets/ab7a80f7-51e3-48c0-99ed-2ef791315635" width="600"/>

## Installing VMware Tools

Select Player → Removable Devices → CD/DVD → Settings:

<img src="https://github.com/user-attachments/assets/b69097ab-b61a-4819-b0f2-613a5f357167" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/1d7254f8-bcb5-4f60-9d00-d03a1048ed7c" width="600"/>

Select the `winPreVista.iso` and select open:

<img src="https://github.com/user-attachments/assets/6c9dce4d-ec46-44c3-9bb2-73b503f80675" width="600"/>

Windows XP has autoplay enabled by default and the VMware Tools installation should begin. If it does not go to Computer in the Windows XP Guest and start the setup from the CD/DVD:

<img src='./images/img_042.png' alt='img_042' width='600'/>

Select Next:

<img src='./images/img_043.png' alt='img_043' width='600'/>

Select Next:

<img src='./images/img_044.png' alt='img_044' width='600'/>

Select Install:

<img src='./images/img_045.png' alt='img_045' width='600'/>

Select Yes to restart:

<img src='./images/img_046.png' alt='img_046' width='600'/>

The Windows XP Guest will restart and the window in the Windows 11 Host can now be resized, resizing the Windows XP Guest:

<img src='./images/img_047.png' alt='img_047' width='600'/>

On a Windows 11 Host, drag and drop to the Windows XP Guest is bi-directional. On a Ubuntu Host, drag and drop from the Ubuntu Host to the Windows XP Guest works but does not work from the Windows XP Guest to Ubuntu Host (Shared Folders can be configured for that). The Standalone Windows XP Service Pack 4 Update can be copied to the Windows XP Guest:

<img src='./images/img_048.png' alt='img_048' width='600'/>

<img src='./images/img_049.png' alt='img_049' width='600'/>

## Windows Product Activation Timer

The activation status can be seen by going to Start and selecting run:

<img src='./images/img_052.png' alt='img_052' width='600'/>

and then inputting:

```
%systemroot%\system32\oobe\msoobe.exe /a
```

<img src='./images/img_053.png' alt='img_053' width='600'/>

Details about the days remaining in grace period can be seen:

<img src='./images/img_054.png' alt='img_054' width='600'/>

If a Windows XP Professional Volume License ISO was used, Windows XP Professional should be activated. Alternatively if a Dell Windows XP Professional OEM on a Virtual Machine with a SLIC 1.0 passed through, Windows XP Professional should be activated.

## Shared Folders

Create a new folder on the Windows 11 Host or Ubuntu 24.10 Host PC called `vmshared`:

<img src='./images/img_055.png' alt='img_055' width='600'/>

Select Player → Manage → Virtual Machine Settings:

<img src='./images/img_056.png' alt='img_056' width='600'/>

Select Options → Shared Folders and change the setting to Always Enabled and check Map Network Drive:

<img src='./images/img_057.png' alt='img_057' width='600'/>

Select Add, select the folder vmshared on the Windows 11 Host PC or Ubuntu 24.10 Host PC and then next:

<img src='./images/img_058.png' alt='img_058' width='600'/>

Select Enable this Share and Finish:

<img src='./images/img_059.png' alt='img_059' width='600'/>

<img src='./images/img_060.png' alt='img_060' width='600'/>

The shared folder is now mapped as a network drive in the Windows XP Guest:

<img src='./images/img_061.png' alt='img_061' width='600'/>

And the file created on the Windows XP Guest in this shared folder can be accessed in the Windows 11 Host or Ubuntu 24.10 Host:

<img src='./images/img_062.png' alt='img_062' width='600'/>

## Installing Python

Python will be used as an example of installing a program on Windows XP. [python-3.4.4.msi](https://www.python.org/downloads/release/python-344/) is the latest version of Python to work on Windows XP. The installer can be downloaded on the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/eab7e96a-f075-4f1f-aab1-21ced600f865" width="600"/>

And dragged and dropped over to the VM:

<img src="https://github.com/user-attachments/assets/5b1a54a6-6c5e-4110-a901-758c521b83bd" width="600"/>

Launch the setup:

<img src="https://github.com/user-attachments/assets/38db7318-97aa-4b01-83d4-99de325e923a" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/b0397e70-6c8a-479b-b0b4-6252c1ba6c49" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/e8d09ae6-4844-4c27-a4ca-9c1599335378" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/3bffc199-e63b-4bc0-ba2a-cba34e035565" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/c925f84d-4ec1-4124-bf06-16dc4693cdcc" width="600"/>

Open My Computer:

<img src="https://github.com/user-attachments/assets/bbb5da46-37d5-47ee-b74a-81b9df19d122" width="600"/>

Navigate to the `C:` Drive:

<img src="https://github.com/user-attachments/assets/ee36920e-54a7-47b5-8fd9-b387a27fff52" width="600"/>

To the left, select Show Contents of this Drive:

<img src="https://github.com/user-attachments/assets/77f5cbce-a4f5-4379-aafd-41df2287d77f" width="600"/>

Python 3.4 is installed in the `Python34` folder:

<img src="https://github.com/user-attachments/assets/fc1ff42d-646d-4bef-95a8-b6d86c7e6e57" width="600"/>

In this folder there is the `python.exe`:

<img src="https://github.com/user-attachments/assets/ed77521e-5408-4187-8099-a78999e83eda" width="600"/>

And `Scripts` subfolder:

<img src="https://github.com/user-attachments/assets/63c85936-af8e-4103-a605-339cf8917417" width="600"/>

With the script called `pip`:

<img src="https://github.com/user-attachments/assets/1fe9f2da-de58-4d1c-8e92-fcc7ee543648" width="600"/>

The `Lib` folder contaisn python's standard libraries:

<img src="https://github.com/user-attachments/assets/3ae37bce-a18d-4c6b-ab8f-e4371b381a12" width="600"/>

In this folder is a subfolder called `site-packages`:

<img src="https://github.com/user-attachments/assets/4a89e3ad-2185-47dd-9a92-5e73b5bb4da3" width="600"/>

Where third-party libraries are installed such as the package manager Python Install Package `pip`:

<img src="https://github.com/user-attachments/assets/9e9eb7c1-b505-4629-be60-1ac39bbaadf3" width="600"/>

Normally there is a folder corresponding to the package and a second folder which gives the details and version of the package.

Python was not added to the path during installation, which means the full directories to the `python.exe` and `pip` script need to be specified from the command prompt. To add to the path, right click Computer and select Properties:

<img src="https://github.com/user-attachments/assets/da9c995c-379b-4dee-9038-bd797680064a" width="600"/>

Select the Advanced Tab and select Environmental Variables:

<img src="https://github.com/user-attachments/assets/255ee501-3cd5-4bd3-9abf-591111928327" width="600"/>

Under System Variables select Path and Edit:

<img src="https://github.com/user-attachments/assets/68498948-f5fa-4110-b9ff-69ecc3763f24" width="600"/>

Append the two values:

```
;C:\Python34\;C:\Python34\Scripts\
```

<img src="https://github.com/user-attachments/assets/f75e27e8-696b-4f89-8f25-b206d4b691e8" width="600"/>

For clarity my full path looks like the following. The semi-colon is a delimiter:

```
%SystemRoot%\system32;%SystemRoot%;%SystemRoot%\System32\Wbem;C:\WINDOWS\system32\WindowsPowerShell\v1.0;C:\Python34\;C:\Python34\Scripts\S
```

Newer versions of Windows often display this in a list for convenience. Using a new line instead, this becomes:

```
%SystemRoot%\system32
%SystemRoot%
%SystemRoot%\System32\Wbem
C:\WINDOWS\system32\WindowsPowerShell\v1.0
C:\Python34\
C:\Python34\Scripts\
```

The command prompt looks for a command in all of the directories listed in the path as well as the current working directory. 

Select OK:

<img src="https://github.com/user-attachments/assets/ae706596-a8e5-4312-a5bf-aa7c6bf9f346" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/b7a13702-ad84-4ba3-add1-e1b84a5c9511" width="600"/>

Select Start All Programs → Accessories → Command Prompt:

<img src="https://github.com/user-attachments/assets/9368f5df-19c5-4b70-9e6d-e2cafe08ea02" width="600"/>

If the following is input:

```powershell
python
```

Notice the Python program is found (which is in the folder `C:\Python34\` which is on the Windows path) and the prompt changes to the Python Prompt. The Python `print` function can be called, supplying a `str` as an input argument:

```python
print('Hello World!')
```

<img src="https://github.com/user-attachments/assets/45a6165a-388c-47f3-988a-ec9b393c26ea" width="600"/>

To exit the Python program use the function call:

```python
exit()
```

<img src="https://github.com/user-attachments/assets/1d77514e-ec2e-4526-9222-5f8dd3c09163" width="600"/>

This exits the Python program and returns to the command prompt, the Python Install Package Command `pip` can be used:

```powershell
pip
```

<img src="https://github.com/user-attachments/assets/1b9e8062-9e09-4e42-a744-569b530b7b8c" width="600"/>

`pip` is in the folder `C:\Python34\Scripts` which is on the Windows path. Use of pip requires internet access, which is risky on a legacy operating system like Windows XP. Select Player → Removable Devices → Network Adapter → Connect:

<img src="https://github.com/user-attachments/assets/31991f53-9acc-4671-a83f-0bccb58b0c01" width="600"/>

The network icon will display to the bottom right:

<img src="https://github.com/user-attachments/assets/eb43e3b5-c9a6-4379-a45b-f07989e1e7b2" width="600"/>

Now pip can be used to install pyserial:

```powershell
pip install pyserial==3.0.1
```

<img src="https://github.com/user-attachments/assets/5b465fec-addb-4c3b-90d7-f3e363ed8c3a" width="600"/>

The `==` means is equal to an a specific version needs to be specified that works with Windows XP. Newerr versions rely on newer Windows protocols which aren't present in Windows XP.

Notice in the `site-packages` folder there is a `pyserial` `dist-info` (package) folder giving details about the version and a `serial` (library) folder. Normally the name of package and library are consistent however sometimes these differ for historical reasons (for example a package being forked and the forked package being maintained and the original package being depreciated):

<img src="https://github.com/user-attachments/assets/317f40ea-e6ca-4aba-8488-ac5b2cbe7c0b" width="600"/>

A new Python program can be ran using:

```powershell
python
```

```python
import serial
```

<img src="https://github.com/user-attachments/assets/c971c0c7-17ce-482c-811b-ebf94a4f41de" width="600"/>

## USB Passthrough

A legacy USB Device can be passed through from the Windows 11 Host or Ubuntu 24.10 to the Windows XP Guest. In this example a Logitech Pro 9000 webcam will be used. The Logitech Pro 9000 is a USB 2.0 camera which had HD 720p (1280×720 pixels) and 30 fps which is effectively at the limit of USB 2.0. The Windows XP driver and software can be downloaded on the Windows 11 Host:

<img src="https://github.com/user-attachments/assets/f3bbf58c-2e35-4999-9ef7-6b10927f333a" width="600"/>

And dragged and dropped to the VM:

<img src="https://github.com/user-attachments/assets/10d1d1c2-531f-41ba-ac88-17cd5072c860" width="600"/>

The installer can be run on the Windows XP VM:

<img src="https://github.com/user-attachments/assets/7ed0b744-fac8-4292-a0ab-e56d2ca25383" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/fb1408ea-0b83-4b62-96b8-396777e1b0b5" width="600"/>

When prompted to connect the webcam, pass through the USB device from the Windows 11 Host to the VM using Player → Removable Devices → Logitech USB Device → Connect:

<img src="https://github.com/user-attachments/assets/5bc3fa2a-89e4-4cc2-bc3b-688ba6f6802f" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/c719f71f-e1cf-4aab-badf-f1d9ea19ea03" width="600"/>

The found new hardware wizard will show:

<img src="https://github.com/user-attachments/assets/07be6ba7-9878-4cdc-b1b4-65729eef7ae9" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/16d84a8c-ab72-4404-abb4-783f88dc7f29" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/ffd7bf69-414b-4a0f-a1be-71c58948d441" width="600"/>

The image from the webcam displays, select next:

<img src="https://github.com/user-attachments/assets/e44bb276-95d3-445a-8705-492b4c7c9724" width="600"/>

Select check out my webcam:

<img src="https://github.com/user-attachments/assets/b216a6b0-873c-43cd-b1c6-d9b02229ae87" width="600"/>

Select quick capture:

<img src="https://github.com/user-attachments/assets/bc826dfd-0d07-4a21-b07b-8b95978502af" width="600"/>

The webcam software can be used in Windows XP to control the Logitech Pro 9000 which has been passed through from the Windows 11 Host PC:

<img src="https://github.com/user-attachments/assets/4c793c78-43c2-4ee4-a36b-c18c13b841ba" width="600"/>

## Serial Port Passthrough

Close the Windows XP VM. Attach a USB to Serial Port to the Window 11 Host PC:

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

<img src="https://github.com/user-attachments/assets/80609833-c175-4396-bd7b-7003685ac7c5" width="600"/>

Select Add...:

<img src="https://github.com/user-attachments/assets/677cc262-6c3b-41e7-a247-4e1749362127" width="600"/>

Select Serial Port and Finish:

<img src="https://github.com/user-attachments/assets/0cb110f4-96ac-4409-ade9-026ecd0b6899" width="600"/>

Select Connect at Power On. Autodetect is useful for a single port, but for multipe ports, it is more useful to select the serial Port indiviually. In this example COM3 will be used:

<img src="https://github.com/user-attachments/assets/a0698610-4b78-4499-974d-316f111df752" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/bdd5685f-bd62-4fd4-bb3d-1d2edfa9c9ad" width="600"/>

Launch the VM:

<img src="https://github.com/user-attachments/assets/1ee29d32-f767-4bc2-90e4-c953b6cb71c3" width="600"/>

Go to Start and right click computer and select properties:

<img src="https://github.com/user-attachments/assets/bf49569e-2548-446e-948f-98665af57b25" width="600"/>

Go to the hardware tab and select Device Manager:

<img src="https://github.com/user-attachments/assets/67eb8f7d-bee5-46a7-8a27-b5934f61902e" width="600"/>

Expand ports, note the Windows 11 COM3 is passed through to the Windows 2000 VM as COM1:

<img src="https://github.com/user-attachments/assets/a34c1ef9-1fab-4d4c-8185-05a29ddc7c93" width="600"/>

Right click the communication port and select properties:

<img src="https://github.com/user-attachments/assets/37ca2bb1-b3f1-4504-bba9-a1998c2e29a9" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects (consistent with the settings on the Windows 11 Host)

<img src="https://github.com/user-attachments/assets/2ab58a0f-3ee4-43ed-9e2f-b4d2bb4c011a" width="600"/>

Select Advanced:

<img src="https://github.com/user-attachments/assets/0e7f1613-ba76-4261-a1cc-b6278a9f0dbc" width="600"/>

Update the COM Port Number to be consistent with the Windows 11 Host. In this case COM3. Select OK:

<img src="https://github.com/user-attachments/assets/21ae0b09-164f-42dd-8481-8107e6c0d3f1" width="600"/>

The Serial Port COM3 is now ready for use in the Windows XP Guest:

<img src="https://github.com/user-attachments/assets/876e14b7-348c-4de3-a611-bb43bd71650e" width="600"/>

If the port number has not updated, select Action → Scan for hardware changes. After refreshing COM3 now displays correctly in the device manager but is not available for use in other programs until the Windows XP Guest is restarted.

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

<img src="https://github.com/user-attachments/assets/bd381af0-08e4-46a2-9cf4-aa720a1c935c" width="600"/>

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
print('Sent: {}'.format(test_data))

# Read back data
received = ser.read(len(test_data))
print('Received: {}'.format(received))

# Check if the loopback worked
if received == test_data:
    print('Serial loopback test passed!')
else:
    print('Serial loopback test failed!')

ser.close()
```

<img src="https://github.com/user-attachments/assets/b8bd70fd-7398-427f-903b-7e21df8302fe" width="600"/>

Select file → save as:

<img src="https://github.com/user-attachments/assets/ffb68f9c-a600-468e-8056-0a4a4cf9f1b7" width="600"/>

Save the file as `script.py` ensuring that save as type is All Files and Encoding is UTF-8:

<img src="https://github.com/user-attachments/assets/b990279b-0370-411b-861b-54c6d28c813a" width="600"/>

The script file is in Documents. Right click the script file and selectProperties:

<img src="https://github.com/user-attachments/assets/385c5d52-02fd-449f-bb2c-0cb78cbf2868" width="600"/>

Copy the file location:

<img src="https://github.com/user-attachments/assets/2e624086-3705-4c84-9167-2a01df927bce" width="600"/>

The file path contains spaces:

```powershell
C:\Documents and Settings\Philip\My Documents\script.py
```

To prevent CMD from taking `C:\Documents`, `and`, `Settings\Philip\My` and `Documents\script.py` as seperate command line arguments, double quotations much be used:

```powershell
"C:\Documents and Settings\Philip\My Documents\script.py"
```

Because this is a long path name, the DOS path is often more convenient:

```powershell
C:\DOCUME~1\Philip\MYDOCU~1\script.py
```

The Python script can be launched using:

```powershell
python C:\DOCUME~1\Philip\MYDOCU~1\script.py
```

With no pins connected, the following shows:

<img src="https://github.com/user-attachments/assets/6e595ec7-3bd9-40cb-aa13-d88515524eec" width="600"/>

With pins 2 and 3 connected, the following shows:

<img src="https://github.com/user-attachments/assets/04bcbbb3-16d3-42ab-b564-b5037a992c03" width="600"/>

The code works as expected and interfaces with the Serial Port which is passed through to the Windows XP Guest VM from the Windows 11 Host PC.

## Parallel Port Passthrough

VMware can theoretically passthrough a physical parallel port. However, USB-to-parallel adapters are designed exclusively for printers and do not provide true parallel port functionality for other hardware. By the time of Windows XP, parallel ports were already considered legacy and were rarely included on new PCs. I do not have a parallel port printer available to test passthrough functionality.

## PCI/PCIe Card Passthrough

VMware does not support direct passthrough of PCI or PCIe cards to a guest virtual machine. Additionally, there are no USB adapters that replicate the functionality of PCI/PCIe expansion cards.

Return to [VMware Installation Guide](../readme.md).

Python is just used as an example of a legacy program to run in a Windows 7 VM and not covered in detail in this tutorial. For details about using Python, see my other GitHub repository [Python Tutorials](https://github.com/PhilipYip1988/python-tutorials).
