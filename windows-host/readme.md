# VMware Workstation Pro Install Ubuntu

This guide looks at installation of VMware Workstation Pro on Windows 11 or Windows 10. VMware has recently been acquired by Broadcom and VMware Workstation has been made free for non-commercial use. The previous free lesser products have been depreciated in order to reduce development costs.

## Installing VMware Perquisites

## Downloading VMware Workstation

Although a number of improvements have been made in VMware itself. The front-end to the website redirects to the Broadcom website:

* [Broadcom: Download VMware Workstation Pro](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion)

There have been a number of issues logging in to the Broadcom website. If there are issues the backend to the software downloads can be used:

* [VMware Workstation](https://softwareupdate.vmware.com/cds/vmw-desktop/ws/)

Download the compatible version of VMware Workstation Player from VMware. This is in the core folder and has the extensions `.bundle.tar`.

<img src='./images/img_001.png' alt='img_001' width='600'/>

<img src='./images/img_002.png' alt='img_002' width='600'/>

<img src='./images/img_003.png' alt='img_003' width='600'/>

<img src='./images/img_004.png' alt='img_004' width='600'/>

<img src='./images/img_005.png' alt='img_005' width='600'/>

<img src='./images/img_006.png' alt='img_006' width='600'/>

## Installing VMWare Workstation Player

Extract the `.tar` to get to the extracted folder with the `.exe` file:

<img src='./images/img_007.png' alt='img_007' width='600'/>

<img src='./images/img_008.png' alt='img_008' width='600'/>

Launch the setup.exe to begin the install:

<img src='./images/img_009.png' alt='img_009' width='600'/>

Accept the User Account Control Prompt:

<img src='./images/img_010.png' alt='img_010' width='400'/>

Select next:

<img src='./images/img_011.png' alt='img_011' width='600'/>

Accept the License Agreement and select next:

<img src='./images/img_012.png' alt='img_012' width='600'/>

Check add VMware Workstation Tools tools into system path and select next:

<img src='./images/img_013.png' alt='img_013' width='600'/>

Check, check for updates and select next:

<img src='./images/img_014.png' alt='img_014' width='600'/>

Check Start Menu Folder and select next:

<img src='./images/img_015.png' alt='img_015' width='600'/>

Select install:

<img src='./images/img_016.png' alt='img_016' width='600'/>

Select finish:

<img src='./images/img_017.png' alt='img_017' width='600'/>

## Installing Windows Virtualisation Features

Press `⊞+r` to bring up the run dialog and input:

```
appwiz.cpl
```

<img src='./images/img_018.png' alt='img_018' width='400'/>

Select Turn Windows Features on or off:

<img src='./images/img_019.png' alt='img_019' width='600'/>

Select Virtual Machine Platform and Windows Hypervisor Platform:

<img src='./images/img_020.png' alt='img_020' width='600'/>

Select Restart Now:

<img src='./images/img_021.png' alt='img_021' width='600'/>

## Ubuntu Guest

Instructions are similar for both Ubuntu 24.04 and Ubuntu 24.10 Guests.

### System Requirements

To run Ubuntu as a Virtual Machine, the host PC should have a high end 11th generation processor, at least 16 GB of RAM and at least a 512 GB SSD. Press `⊞+r` to bring up the run dialog and input:

```
msinfo32
```

<img src='./images/img_022.png' alt='img_022' width='600'/>

<img src='./images/img_023.png' alt='img_023' width='600'/>

<img src='./images/img_024.png' alt='img_024' width='600'/>

<img src='./images/img_025.png' alt='img_025' width='600'/>

### Download ISO

The Ubuntu 24.10 or 24.04 LTS ISO can be downloaded from Canonical:

* [Download Ubuntu Desktop](https://ubuntu.com/download/desktop)

<img src='./images/img_026.png' alt='img_026' width='600'/>

<img src='./images/img_027.png' alt='img_027' width='600'/>

### Configure VM

Open up VMware Workstation Player:

<img src='./images/img_028.png' alt='img_028' width='600'/>

Select File → Create a New Virtual Machine:

<img src='./images/img_029.png' alt='img_029' width='600'/>

Under select ISO Image, select Browse. Select the Ubuntu 24.10 ISO and select open:

<img src='./images/img_030.png' alt='img_030' width='600'/>

Ubuntu 24.10 will be detected. Input your full name, username and password:

<img src='./images/img_031.png' alt='img_031' width='600'/>

The name and location of the Ubuntu 24.10 Guest will be shown. Select Next:

<img src='./images/img_032.png' alt='img_032' width='600'/>

The default disk size is 20 GB, which is quite restrictive. It is recommended to expand this to 256 GB. 

> Note the Ubuntu 24.10 Guest won't occupy the full 256 GB. This setting means the disk can reach up to a maximum value of 256 GB.

Select next:

<img src='./images/img_033.png' alt='img_033' width='600'/>

Select Customise Hardware:

<img src='./images/img_034.png' alt='img_034' width='600'/>

Under memory, the default memory is 4096 GB, this should only be increased if the system has >32 GB of RAM:

<img src='./images/img_035.png' alt='img_035' width='600'/>

Under processors, the number of processors is 2, this can be increased if the processor has more cores and threads but increasing this too much can cripple the Windows 11 Host and therefore this will cripple the Ubuntu 24.10 Guest leading to poor performance:

<img src='./images/img_036.png' alt='img_036' width='600'/>

Under CD/DVD, ensure that the Ubuntu 24.10 ISO is selected and that Connect at Power On is checked:

<img src='./images/img_037.png' alt='img_037' width='600'/>

Under Network Adapter, leave the default settings:

<img src='./images/img_038.png' alt='img_038' width='600'/>

Under USB Controller, change the default setting USB 2.0 to USB 3.1:

<img src='./images/img_039.png' alt='img_039' width='600'/>

Under Sound Card, leave the default settings:

<img src='./images/img_040.png' alt='img_040' width='600'/>

Under Display, leave the default settings and select close:

<img src='./images/img_041.png' alt='img_041' width='600'/>

Select finish:

<img src='./images/img_042.png' alt='img_042' width='600'/>

### Installing Ubuntu 24.10 in the Ubuntu 24.10 Guest VM

The Ubuntu 24.10 Guest will start booting from the Ubuntu 24.10 Live ISO:

<img src='./images/img_043.png' alt='img_043' width='600'/>

<img src='./images/img_044.png' alt='img_044' width='600'/>

Select your Language:

<img src='./images/img_045.png' alt='img_045' width='600'/>

Select next:

<img src='./images/img_046.png' alt='img_046' width='600'/>

Select your keyboard layout and then select next:

<img src='./images/img_047.png' alt='img_047' width='600'/>

Select use wired connection and select next:

<img src='./images/img_048.png' alt='img_048' width='600'/>

Select Install Ubuntu and select next:

<img src='./images/img_049.png' alt='img_049' width='600'/>

Select Interactive Installation and select next:

<img src='./images/img_050.png' alt='img_050' width='600'/>

Select default installation and select next:

<img src='./images/img_051.png' alt='img_051' width='600'/>

Check Install third-party software for graphics and Wi-Fi hardware and Download and install support for additional media formats and select next:

<img src='./images/img_052.png' alt='img_052' width='600'/>

Select Erase DIsk and install Ubuntu and select next:

<img src='./images/img_053.png' alt='img_053' width='600'/>

Input your full name, computer name\*, username\* and password:

\* These should be lower case characters with no spaces, the `-` is the only special character allowed. The user name `philip` becomes the name of the home folder `/home/philip` which is also represented by `~` in the terminal.

Select next:

<img src='./images/img_054.png' alt='img_054' width='600'/>

Select your time zone and select next:

<img src='./images/img_055.png' alt='img_055' width='600'/>

Select next:

<img src='./images/img_056.png' alt='img_056' width='600'/>

Select reboot now:

<img src='./images/img_057.png' alt='img_057' width='600'/>

Log in:

<img src='./images/img_058.png' alt='img_058' width='600'/>

<img src='./images/img_059.png' alt='img_059' width='600'/>

Select next:

<img src='./images/img_060.png' alt='img_060' width='600'/>

Select next:

<img src='./images/img_061.png' alt='img_061' width='600'/>

Select finish:

<img src='./images/img_062.png' alt='img_062' width='600'/>

Ubuntu 24.10 is now installed in the Ubuntu 24.10 Guest Virtual Machine. The system drivers (`open-vm-tools`) are included in the Linux Kernel and do not have to be installed. The Ubuntu 24.10 guest can be maximised to full size.

From the all applications screen select software updater:

<img src='./images/img_063.png' alt='img_063' width='600'/>

Select install now:

<img src='./images/img_064.png' alt='img_064' width='600'/>

An authentication prompt displays, the Ubuntu counterpart to the WIndows User Account Control Prompt:

<img src='./images/img_065.png' alt='img_065' width='600'/>

To authenticate input your password and select Authenticate:

<img src='./images/img_066.png' alt='img_066' width='600'/>

Select restart now:

<img src='./images/img_067.png' alt='img_067' width='600'/>

### Removing Mounted Drives

VMware automatically added a floppy drive and second CD/DVD in order to facilitate installation of open-vm-tools. This mechanism is typically used for older Ubuntu versions as Ubuntu 24.04 LTS and Ubuntu 24.10 have open-vm-tools preinstalled.

Ubuntu 24.10 displays mounted drives by default. If the CD/DVD has an ISO image displayed it will display on the panel, the floppy drive will always display whether or not it has an image loaded:

<img src='./images/img_068.png' alt='img_068' width='600'/>

Select Player → Removable Devices → CD/DVD → Settings:

<img src='./images/img_069.png' alt='img_069' width='600'/>

Ensure connected and Connected at Power On are unchecked:

<img src='./images/img_070.png' alt='img_070' width='600'/>

Do the same for CD/DVD 2:

<img src='./images/img_071.png' alt='img_071' width='600'/>

And floppy and then select ok:

<img src='./images/img_072.png' alt='img_072' width='600'/>

Select yes:

<img src='./images/img_073.png' alt='img_073' width='400'/>

The mounted optical drive icon now disappears but the floppy drive icon remains: 

<img src='./images/img_074.png' alt='img_074' width='600'/>

Select Player → Floppy → CD/DVD → Settings:

<img src='./images/img_075.png' alt='img_075' width='600'/>

Select remove:

<img src='./images/img_076.png' alt='img_076' width='600'/>

Removal requires the Ubuntu 24.10 Guest to be powered off. Select OK:

<img src='./images/img_077.png' alt='img_077' width='600'/>

Power off the Ubuntu 24.10 Guest:

<img src='./images/img_078.png' alt='img_078' width='600'/>

<img src='./images/img_079.png' alt='img_079' width='600'/>

<img src='./images/img_080.png' alt='img_080' width='600'/>

Select OK:

<img src='./images/img_081.png' alt='img_081' width='600'/>

Select Edit Virtual Machine Settings:

<img src='./images/img_082.png' alt='img_082' width='600'/>

Now select Floppy and remove:

<img src='./images/img_083.png' alt='img_083' width='600'/>

Select ok:

<img src='./images/img_084.png' alt='img_084' width='600'/>

The floppy drive icon is now removed:

<img src='./images/img_085.png' alt='img_085' width='600'/>

### Shared Folders

Unfortunately VMware doesn't support drag and drop to or from the Ubuntu 24.10 Guests Desktop:

<img src='./images/img_086.png' alt='img_086' width='600'/>

<img src='./images/img_087.png' alt='img_087' width='600'/>

<img src='./images/img_088.png' alt='img_088' width='600'/>

Create a subfolder in the Windows 11 Host Documents folder called:

```
vmshared
```

<img src='./images/img_089.png' alt='img_089' width='600'/>

Select Player → Manage → Virtual Machine Settings:

<img src='./images/img_090.png' alt='img_090' width='600'/>

Select Options → Shared Folders and check Always Enabled. Select Add:

<img src='./images/img_091.png' alt='img_091' width='600'/>

Select next:

<img src='./images/img_092.png' alt='img_092' width='400'/>

Select the vmshared folder and select next:

<img src='./images/img_093.png' alt='img_093' width='400'/>

Select enable this share and select finish:

<img src='./images/img_094.png' alt='img_094' width='400'/>

Select OK:

<img src='./images/img_095.png' alt='img_095' width='600'/>

Launch Startup Applications:

<img src='./images/img_096.png' alt='img_096' width='600'/>

Select add:

<img src='./images/img_097.png' alt='img_097' width='600'/>

Create a subfolder in the Ubuntu 24.10 Guest Documents folder called:

```
vmshared
```

<img src='./images/img_098.png' alt='img_098' width='600'/>

<img src='./images/img_099.png' alt='img_099' width='600'/>

Under name select `VMware Shared Folder`. 

Under command input the following command

```bash
/usr/bin/vmhgfs-fuse .host:/ /home/philip/Documents/vmshared -o subtype=vmhgfs-fuse
```

Replacing `philip` with your user name and `vmshared` with the name of the folder. 

Select add:

<img src='./images/img_100.png' alt='img_100' width='600'/>

Select close and the restart the Ubuntu 24.10 Guest:

<img src='./images/img_101.png' alt='img_101' width='600'/>

The folder `vmshared` is now mounted as a shared folder:

<img src='./images/img_102.png' alt='img_102' width='600'/>

And the files can be accessed between the Ubuntu 24.10 Guest and Windows 11 Host:

<img src='./images/img_103.png' alt='img_103' width='600'/>

<img src='./images/img_104.png' alt='img_104' width='600'/>

<img src='./images/img_105.png' alt='img_105' width='600'/>

Note the shared folder needs to be refreshed in the Ubuntu 24.10 Guest in order to view changes made on the Windows 11 Host. This can be done quickly by selecting Documents and then pressing back:

<img src='./images/img_106.png' alt='img_106' width='600'/>

<img src='./images/img_107.png' alt='img_107' width='600'/>

<img src='./images/img_108.png' alt='img_108' width='600'/>

## Windows Guest

Instructions are similar for both Windows 10 and Windows 11 Guests.

### System Requirements

Windows 11 has relatively high system requirements such as an 8th generation processor, 8 GB of RAM and a 1 TB SSD boot drive. To run Windows 11 as a Virtual Machine, the host PC should significantly exceed these system requirements and therefore have a high end 11th generation processor, at least 16 GB of RAM and at least a 512 GB SSD. Press `⊞+r` to bring up the run dialog and input:

```
msinfo32
```

<img src='./images/img_109.png' alt='img_109' width='400'/>

<img src='./images/img_110.png' alt='img_110' width='600'/>

<img src='./images/img_111.png' alt='img_111' width='600'/>

<img src='./images/img_112.png' alt='img_112' width='600'/>

### Download ISO

A Windows ISO can be downloaded from Microsoft:

* [Windows 11](https://www.microsoft.com/en-us/software-download/windows11)
* [Windows 10](https://www.microsoft.com/en-gb/software-download/windows10ISO)

\* Microsoft removed old Windows 10 Builds and Windows 8.1 after Windows 8.1 reached end of life.

Select the Windows 11 ISO and select download now:

<img src='./images/img_113.png' alt='img_113' width='600'/>

Select the language and select confirm:

<img src='./images/img_114.png' alt='img_114' width='600'/>

Select 64 Bit download:

<img src='./images/img_115.png' alt='img_115' width='600'/>

The ISO will download:

<img src='./images/img_116.png' alt='img_116' width='600'/>

### Configure VM

Select Player → File → Create a New Virtual Machine:

<img src='./images/img_117.png' alt='img_117' width='600'/>

Select installer disc image (ISO) and load the Windows 11 ISO:

<img src='./images/img_118.png' alt='img_118' width='600'/>

Windows 11 will automatically be detected and the default VM settings for the Windows 11 Guest will be applied. The name and location of the Windows 11 Guest will be shown. Select next:

<img src='./images/img_119.png' alt='img_119' width='600'/>

Windows 11 requires an encryption key for the TPM. Input an 8 digit password and confirm the password:

<img src='./images/img_120.png' alt='img_120' width='600'/>

The default disk size is 64 GB which is quite restrictive. It is recommended to expand this to 256 GB. 

> Note the Windows 11 Guest won't occupy the full 256 GB. This setting means the disk can reach up to a maximum value of 256 GB.

Select next:

<img src='./images/img_121.png' alt='img_121' width='600'/>

Select customise hardware:

<img src='./images/img_122.png' alt='img_122' width='600'/>

Under memory, the default memory is 4096 GB, this should only be increased if the system has >32 GB of RAM:

<img src='./images/img_123.png' alt='img_123' width='600'/>

Under processors, the number of processors is 2, this can be increased if the processor has more cores and threads but increasing this too much can cripple the Windows 11 Host and therefore this will cripple the Windows 11 Guest leading to poor performance:

<img src='./images/img_124.png' alt='img_124' width='600'/>

Under CD/DVD, ensure that the Windows 11 ISO is selected and that Connect at Power On is checked:

<img src='./images/img_125.png' alt='img_125' width='600'/>

Under Network Adapter, leave the default settings:

<img src='./images/img_126.png' alt='img_126' width='600'/>

Under USB Controller, leave the default settings at USB 3.1:

<img src='./images/img_127.png' alt='img_127' width='600'/>

Under Sound Card, leave the default settings:

<img src='./images/img_128.png' alt='img_128' width='600'/>

Under Display, leave the default settings and select close:

<img src='./images/img_129.png' alt='img_129' width='600'/>

Select finish:

<img src='./images/img_130.png' alt='img_130' width='600'/>

### Installing Windows 11 in the Windows 11 Guest VM

The Windows 11 Guest will now launch however a dialog box will display to download VMware tools, select download and install:

<img src='./images/img_131.png' alt='img_131' width='600'/>

Accept the user account control prompt:

<img src='./images/img_132.png' alt='img_132' width='600'/>

The VMware tools ISO will be loaded. However as VMware does not let you click into the Windows 11 Guest at this time, the boot menu will have timed out taking you to the Windows 11 Guest's BIOS setup. Select restart the system:

<img src='./images/img_133.png' alt='img_133' width='600'/>

Click into the Windows 11 Guest and press any key such as `h`:

<img src='./images/img_134.png' alt='img_134' width='600'/>

The Windows 11 Guest will boot from the ISO. Select your language and select next:

<img src='./images/img_135.png' alt='img_135' width='600'/>

Select the keyboard settings and select next:

<img src='./images/img_136.png' alt='img_136' width='600'/>

Select Install Windows 11 and accept the agreement, then select next:

<img src='./images/img_137.png' alt='img_137' width='600'/>

Select I don't have a Product Key:

<img src='./images/img_138.png' alt='img_138' width='600'/>

Select the Windows 11 Edition and select next:

<img src='./images/img_139.png' alt='img_139' width='600'/>

Select accept:

<img src='./images/img_140.png' alt='img_140' width='600'/>

Select the virtual disk 0: Unallocated Space and select next:

<img src='./images/img_141.png' alt='img_141' width='600'/>

Select install: 

<img src='./images/img_142.png' alt='img_142' width='600'/>

Select the country or region and select yes:

<img src='./images/img_143.png' alt='img_143' width='600'/>

Select the keyboard layout and select yes:

<img src='./images/img_144.png' alt='img_144' width='600'/>

Select skip:

<img src='./images/img_145.png' alt='img_145' width='600'/>

Input the name of your Windows 11 Guest and select next:

<img src='./images/img_146.png' alt='img_146' width='600'/>

Select setup for personal use and select next:

<img src='./images/img_147.png' alt='img_147' width='600'/>

A number of updates will download:

<img src='./images/img_148.png' alt='img_148' width='600'/>

<img src='./images/img_149.png' alt='img_149' width='600'/>

After the updates have downloaded, select sign in:

<img src='./images/img_150.png' alt='img_150' width='600'/>

By default you will be unable to create a local account. To get around this select Virtual Machine → Virtual Machine Settings:

<img src='./images/img_151.png' alt='img_151' width='600'/>

Select player → Removable Devices → Network Adapter → Settings...

<img src='./images/img_152.png' alt='img_152' width='600'/>

Select Network Adaptor and uncheck Connected and Connect at power on, then select ok:

<img src='./images/img_153.png' alt='img_153' width='600'/>

Press `⇧`+`F10` to open up the command prompt:

<img src='./images/img_154.png' alt='img_154' width='600'/>

Input:

```powershell
oobe\bypassnro
```

<img src='./images/img_155.png' alt='img_155' width='600'/>

The Windows 11 Guest will reboot. Select the country or region and select yes:

<img src='./images/img_156.png' alt='img_156' width='600'/>

Select the keyboard layout and select yes:

<img src='./images/img_157.png' alt='img_157' width='600'/>

Select skip:

<img src='./images/img_158.png' alt='img_158' width='600'/>

Select I don't have internet:

<img src='./images/img_159.png' alt='img_159' width='600'/>

Input your local account name and select next:

<img src='./images/img_160.png' alt='img_160' width='600'/>

Input your (optional) local account password and select next: 

<img src='./images/img_161.png' alt='img_161' width='600'/>

The privacy settings will now display. Select Virtual Machine → Virtual Machine Settings:

<img src='./images/img_162.png' alt='img_162' width='600'/>

Select Network Adaptor and check Connected and Connect at power on and select ok:

<img src='./images/img_163.png' alt='img_163' width='600'/>

Once all the privacy questions have been answered, the Windows 11 Guest will be installed:

<img src='./images/img_164.png' alt='img_164' width='600'/>

### Installing VMware Tools

VMware tools are essentially the Virtual Machines device drivers. Select Player → Virtual Machine → Install VMware Tools:

<img src='./images/img_165.png' alt='img_165' width='600'/>

If this is grayed out. Manually download the ISO:

* [VMware Tools ISO](https://packages.vmware.com/tools/releases/)

Use the latest release for Windows 11. Use 11.0.6 for Windows Vista and Windows 7. Use 10.0.12 for Windows XP.

Mount the ISO in the VM and begin the install as normal.

Launch the setup64.exe:

<img src='./images/img_166.png' alt='img_166' width='600'/>

Accept the User Account Control Prompt:

<img src='./images/img_167.png' alt='img_167' width='600'/>

Select next:

<img src='./images/img_168.png' alt='img_168' width='600'/>

Select next:

<img src='./images/img_169.png' alt='img_169' width='600'/>

Select install:

<img src='./images/img_170.png' alt='img_170' width='600'/>

Select finish:

<img src='./images/img_171.png' alt='img_171' width='600'/>

Select yes:

<img src='./images/img_172.png' alt='img_172' width='600'/>

Now that VMware tools are installed, the Windows 11 Guest can be resized:

<img src='./images/img_173.png' alt='img_173' width='600'/>

Bi-directional drag and drop from the Windows 11 Host to the Windows 11 Guest works:

<img src='./images/img_174.png' alt='img_174' width='600'/>

