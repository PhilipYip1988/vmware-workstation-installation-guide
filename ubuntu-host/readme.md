# VMware Workstation Pro Install Ubuntu

This guide looks at installation of VMware Workstation Pro on Ubuntu 24.04 or 24.10. VMware has recently been acquired by Broadcom and VMware Workstation has been made free for non-commercial use. The previous free lesser products have been depreciated in order to reduce development costs.

## YouTube Video

* [YouTube](https://www.youtube.com/watch?v=lcGVWj8q46U)

## Installing VMware Perquisites

VMware is written using C++ and requires the following perquisite packages such as the GNU Compiler Collection and build essential which is a package group that contains packages required for C++ development. Open up the Terminal and input:

```bash
sudo apt install gcc-12 libgcc-12-dev build-essential
```

<img src='./images/img_001.png' alt='img_001' width='600'/>

Input `y`:

<img src='./images/img_002.png' alt='img_002' width='600'/>

The perquisite packages are now installed:

<img src='./images/img_003.png' alt='img_003' width='600'/>

## Downloading VMware Workstation

Although a number of improvements have been made in VMware itself. The front-end to the website redirects to the Broadcom website:

* [Broadcom: Download VMware Workstation Pro](https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion)

There have been a number of issues logging in to the Broadcom website:

<img src='./images/img_004.png' alt='img_004' width='600'/>

If there are issues the backend to the software downloads can be used:

* [VMware Workstation](https://softwareupdate.vmware.com/cds/vmw-desktop/ws/)

Download the compatible version of VMware Workstation Player from VMware. This is in the core folder and has the extensions `.bundle.tar`.

<img src='./images/img_005.png' alt='img_005' width='600'/>

<img src='./images/img_006.png' alt='img_006' width='600'/>

<img src='./images/img_007.png' alt='img_007' width='600'/>

<img src='./images/img_008.png' alt='img_008' width='600'/>

<img src='./images/img_009.png' alt='img_009' width='600'/>

## Installing VMWare Workstation Player

Extract the `.tar` to get to the extracted folder with the `.bundle` file. 

<img src='./images/img_010.png' alt='img_010' width='600'/>

<img src='./images/img_011.png' alt='img_011' width='600'/>

Right click the `.bundle` file and select properties:

<img src='./images/img_012.png' alt='img_012' width='600'/>

Select Executable as Program:

<img src='./images/img_013.png' alt='img_013' width='600'/>

To change permissions to executable input the following command into the terminal with a space (but don't run this command):

```bash
chmod +x 
```

Drag and drop the bundle file into the terminal to complete the command and run:

<img src='./images/img_014.png' alt='img_014' width='600'/>

<img src='./images/img_015.png' alt='img_015' width='600'/>

This command changes the permissions of a file to execution. Now that the file is executable it can be run as a super user. Input the following command with a space (but don't run this command):

```bash
sudo 
```

Drag and drop the bundle file into the terminal to complete the command and run:

<img src='./images/img_016.png' alt='img_016' width='600'/>

VMware Workstation Player is now installed and displays in the start screen: 

<img src='./images/img_017.png' alt='img_017' width='600'/>

Launch VMware Player, accept the license agreement and select Next:

<img src='./images/img_018.png' alt='img_018' width='600'/>

Select Yes and Next:

<img src='./images/img_019.png' alt='img_019' width='600'/>

Opt in or out of the customer experience program and select Next:

<img src='./images/img_020.png' alt='img_020' width='600'/>

To compile the kernel modules (requires the perquisites packages to perform the compiling) and install them system wide, authentication is required. Input your password and select authenticate:

<img src='./images/img_021.png' alt='img_021' width='600'/>

## Configuring Secure Boot

An attempt to launch a VM will fail because access the virtual monitor kernel module vmmon because it is blocked by Secure Boot:

<img src='./images/img_037.png' alt='img_037' width='600'/>

An error message, failed to start monitor device will display:

<img src='./images/img_038.png' alt='img_038' width='600'/>

Secure Boot will block the Virtual Monitor Kernel Module and Virtual Network Adaptor Module. A Machine Owner Key (MOK) must be created which signs these modules. Open the Terminal:

<img src='./images/img_039.png' alt='img_039' width='600'/>

Navigate to Documents in the terminal using the command change directory `cd`:

```bash
cd ~/Documents
```

<img src='./images/img_040.png' alt='img_040' width='600'/>

Create a new directory called mok using the command make directory:

```bash
mkdir mok
```

Navigate to this directory using:

```bash
cd mok
```

<img src='./images/img_041.png' alt='img_041' width='600'/>

Generate a new Machine Owner Key:

```bash
openssl req -new -x509 -newkey rsa:2048 -keyout VMWARE17.priv -outform DER -out VMWARE17.der -nodes -days 36500 -subj "/CN=VMWARE/"
```

<img src='./images/img_042.png' alt='img_042' width='600'/>

The following files will be created:

<img src='./images/img_043.png' alt='img_043' width='600'/>

Sign the kernel module vmmon:

```bash
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE17.priv ./VMWARE17.der $(modinfo -n vmmon)
```

<img src='./images/img_044.png' alt='img_044' width='600'/>

<img src='./images/img_045.png' alt='img_045' width='600'/>

Sign the kernel module vmnet:

```bash
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE17.priv ./VMWARE17.der $(modinfo -n vmnet)
```

<img src='./images/img_046.png' alt='img_046' width='600'/>


Importing the MOK with MOK management system:

```bash
sudo mokutil --import VMWARE17.der
```

<img src='./images/img_047.png' alt='img_047' width='600'/>

In the terminal create a MOK password for example:

```
vmware1234
```

<img src='./images/img_048.png' alt='img_048' width='600'/>

Confirm the password:

```
vmware1234
```

<img src='./images/img_049.png' alt='img_049' width='600'/>

Reboot using:

```bash
sudo reboot
```

<img src='./images/img_050.png' alt='img_050' width='600'/>

The system will reboot to BIOS:

<img src='./images/img_051.png' alt='img_051' width='600'/>

And display MOK management:

<img src='./images/img_052.png' alt='img_052' width='600'/>

Select Enrol MOK:

<img src='./images/img_053.png' alt='img_053' width='600'/>

Select Continue:

<img src='./images/img_054.png' alt='img_054' width='600'/>

Select Yes:

<img src='./images/img_055.png' alt='img_055' width='600'/>

Input the MOK created earlier:

```
vmware1234
```

Select Reboot:

<img src='./images/img_056.png' alt='img_056' width='600'/>

**This section may need to be repeated after a significant VMware or Ubuntu update.**

## Windows Guest

Instructions are similar for both Windows 10 and Windows 11 Guests.

### System Requirements

Windows 11 has relatively high system requirements such as an 8th generation processor, 8 GB of RAM and a 1 TB SSD boot drive. To run Windows 11 as a Virtual Machine, the host PC should significantly exceed these system requirements and therefore have a high end 11th generation processor, at least 16 GB of RAM and at least a 512 GB SSD. Go to Settings, to the left hand side select System:

<img src='./images/img_022.png' alt='img_022' width='600'/>

Then select About:

<img src='./images/img_023.png' alt='img_023' width='600'/>

### Download ISO

A Windows ISO can be downloaded from Microsoft:

* [Windows 11](https://www.microsoft.com/en-us/software-download/windows11)
* [Windows 10](https://www.microsoft.com/en-gb/software-download/windows10ISO)

\* Microsoft removed old Windows 10 Builds and Windows 8.1 after Windows 8.1 reached end of life.

Select the Windows 11 ISO and select Download now:

<img src='./images/img_024.png' alt='img_024' width='600'/>

Select the Language and select Confirm:

<img src='./images/img_025.png' alt='img_025' width='600'/>

Select 64 Bit Download:

<img src='./images/img_026.png' alt='img_026' width='600'/>

The ISO will download:

<img src='./images/img_027.png' alt='img_027' width='600'/>

### Configure VM

Select File → Create a New Virtual Machine:

<img src='./images/img_028.png' alt='img_028' width='600'/>

Select the Windows 11 ISO and select Open:

<img src='./images/img_030.png' alt='img_030' width='600'/>

Windows 11 will automatically be detected and the default VM settings for the Windows 11 Guest will be applied:

<img src='./images/img_031.png' alt='img_031' width='600'/>

The name and location of the Windows 11 Guest will be shown. Select Next:

<img src='./images/img_032.png' alt='img_032' width='600'/>

Windows 11 requires an encryption key for the TPM. Input an 8 digit password and confirm the password:

<img src='./images/img_033.png' alt='img_033' width='600'/>

The default disk size is 64 GB. This can be expanded if more disk space is required:

<img src='./images/img_034.png' alt='img_034' width='600'/>

Select Next:

<img src='./images/img_035.png' alt='img_035' width='600'/>

Select Close:

<img src='./images/img_036.png' alt='img_036' width='600'/>

### Installing Windows 11 in the Windows 11 Guest VM

The Windows 11 Guest can now be selected. Select Power On:

<img src='./images/img_058.png' alt='img_058' width='600'/>

Select OK:

<img src='./images/img_059.png' alt='img_059' width='600'/>

Select Download and Install:

<img src='./images/img_060.png' alt='img_060' width='600'/>

To authenticate input your password:

<img src='./images/img_061.png' alt='img_061' width='600'/>

Select OK:

<img src='./images/img_062.png' alt='img_062' width='600'/>

The prompt to boot from installation media will have timed out while these prompts display. Select Virtual Machine Power and Restart Guest:

<img src='./images/img_063.png' alt='img_063' width='600'/>

Select Yes:

<img src='./images/img_064.png' alt='img_064' width='600'/>

Select Restart:

<img src='./images/img_065.png' alt='img_065' width='600'/>

Click in the Windows 11 Guest and press a key like `h`:

<img src='./images/img_066.png' alt='img_066' width='600'/>

The Windows 11 Guest will boot from the ISO. Select your language and select Next:

<img src='./images/img_067.png' alt='img_067' width='600'/>

Select the keyboard settings and select Next:

<img src='./images/img_068.png' alt='img_068' width='600'/>

Select Install Windows 11 and accept the agreement, then select Next:

<img src='./images/img_069.png' alt='img_069' width='600'/>

Select I don't have a Product Key:

<img src='./images/img_070.png' alt='img_070' width='600'/>

Select the Windows 11 Edition:

<img src='./images/img_071.png' alt='img_071' width='600'/>

Select Accept:

<img src='./images/img_072.png' alt='img_072' width='600'/>

Select the Virtual Disk0 and select Next: 

<img src='./images/img_073.png' alt='img_073' width='600'/>

Select Install:

<img src='./images/img_074.png' alt='img_074' width='600'/>

Select the country or region:

<img src='./images/img_075.png' alt='img_075' width='600'/>

Select the keyboard layout:

<img src='./images/img_076.png' alt='img_076' width='600'/>

Select Skip:

<img src='./images/img_077.png' alt='img_077' width='600'/>

Input the Device Name:

<img src='./images/img_078.png' alt='img_078' width='600'/>

Select Setup for Personal Use:

<img src='./images/img_079.png' alt='img_079' width='600'/>

A number of updates will download:

<img src='./images/img_080.png' alt='img_080' width='600'/>

After the updates have downloaded, select Sign In:

<img src='./images/img_081.png' alt='img_081' width='600'/>

By default you will be unable to create a Local Account. To get around this select Virtual Machine, Virtual Machine Settings:

<img src='./images/img_082.png' alt='img_082' width='600'/>

Select Network Adaptor and uncheck Connected and Connect at power on:

<img src='./images/img_083.png' alt='img_083' width='600'/>

Press `⇧`+`F10` to open up the command prompt and input:

```powershell
oobe\bypassnro
```

<img src='./images/img_084.png' alt='img_084' width='600'/>

The Windows 11 Guest will reboot:

<img src='./images/img_085.png' alt='img_085' width='600'/>

Select the keyboard layout:

<img src='./images/img_086.png' alt='img_086' width='600'/>

Select skip:

<img src='./images/img_087.png' alt='img_087' width='600'/>

Select I don't have internet:

<img src='./images/img_088.png' alt='img_088' width='600'/>

Input your local account name and select Next:

<img src='./images/img_089.png' alt='img_089' width='600'/>

Input your (optional) local account password and select next: 

<img src='./images/img_090.png' alt='img_090' width='600'/>

Once all the privacy settings have been selected. Select Virtual Machine → Virtual Machine Settings:

<img src='./images/img_091.png' alt='img_091' width='600'/>

Select Network Adaptor and check Connected and Connect at power on:

<img src='./images/img_092.png' alt='img_092' width='600'/>

Windows 11 is now installed:

<img src='./images/img_093.png' alt='img_093' width='600'/>

### Installing VMware Tools

VMware tools are essentially the Virtual Machines device drivers. Select Virtual Machine → Install VMware Tools:

<img src='./images/img_094.png' alt='img_094' width='600'/>

If this is grayed out. Manually download the ISO:

* [VMware Tools ISO](https://packages.vmware.com/tools/releases/)

Use the latest release for Windows 11. Use 11.0.6 for Windows Vista and Windows 7. Use 10.0.12 for Windows XP.

Mount the ISO in the VM and begin the install as normal.

Select Install:

<img src='./images/img_095.png' alt='img_095' width='600'/>

Launch the setup64.exe:

<img src='./images/img_096.png' alt='img_096' width='600'/>

Accept the User Account Control Prompt:

<img src='./images/img_097.png' alt='img_097' width='600'/>

Select Next:

<img src='./images/img_098.png' alt='img_098' width='600'/>

Select Typical and then Next:

<img src='./images/img_099.png' alt='img_099' width='600'/>

Select Install:

<img src='./images/img_100.png' alt='img_100' width='600'/>

Select Finish:

<img src='./images/img_101.png' alt='img_101' width='600'/>

Select Yes to Reboot the Windows 11 Guest:

<img src='./images/img_102.png' alt='img_102' width='600'/>

Now that VMware tools are installed, the Windows 11 Guest can be resized:

<img src='./images/img_103.png' alt='img_103' width='600'/>

Drag and drop from the Ubuntu Host to the Windows 11 Guest works:

<img src='./images/img_104.png' alt='img_104' width='600'/>

But drag and drop from the Windows 11 Guest to the Ubuntu Host doesn't work:

<img src='./images/img_105.png' alt='img_105' width='600'/>

### Shared Folders

A folder can be created in Documents of the Host PC:

<img src='./images/img_106.png' alt='img_106' width='600'/>

Name it VMShared:

<img src='./images/img_107.png' alt='img_107' width='600'/>

Select Virtual Machine → Virtual Machine Settings:

<img src='./images/img_108.png' alt='img_108' width='600'/>

Select Shared fodlers, check always enabled and map as a network drive. Select Add:

<img src='./images/img_109.png' alt='img_109' width='600'/>

Name it VMShared and select Browse:

<img src='./images/img_110.png' alt='img_110' width='600'/>

Navigate to Documents and select the folder VMShared:

<img src='./images/img_111.png' alt='img_111' width='600'/>

Slect Save:

<img src='./images/img_112.png' alt='img_112' width='600'/>

Shared folders display as a network drive in the Windows 11 Guest:

<img src='./images/img_113.png' alt='img_113' width='600'/>

<img src='./images/img_114.png' alt='img_114' width='600'/>

<img src='./images/img_115.png' alt='img_115' width='600'/>

A file from the Windows 11 Guest can be added to it:

<img src='./images/img_116.png' alt='img_116' width='600'/>

And retrieved in the Ubuntu Host:

<img src='./images/img_117.png' alt='img_117' width='600'/>

## Ubuntu Guest

Instructions are similar for both Ubuntu 24.04 and Ubuntu 24.10 Guests.

### System Requirements

To run Ubuntu as a Virtual Machine, the host PC should have a high end 11th generation processor, at least 16 GB of RAM and at least a 512 GB SSD. Go to Settings, to the left hand side select System:

<img src='./images/img_022.png' alt='img_022' width='600'/>

Then select About:

<img src='./images/img_023.png' alt='img_023' width='600'/>

### Download ISO

The Ubuntu 24.10 or 24.04 LTS ISO can be downloaded from Canonical:

* [Download Ubuntu Desktop](https://ubuntu.com/download/desktop)

<img src='./images/img_118.png' alt='img_118' width='600'/>

<img src='./images/img_119.png' alt='img_119' width='600'/>

### Configure VM

Select File → Create a New Virtual Machine:

<img src='./images/img_120.png' alt='img_120' width='600'/>

Under select ISO Image, select Browse:

<img src='./images/img_121.png' alt='img_121' width='600'/>

Select the Ubuntu 24.10 ISO and select open:

<img src='./images/img_122.png' alt='img_122' width='600'/>

Ubuntu 24.10 will be detected:

<img src='./images/img_123.png' alt='img_123' width='600'/>

Input your full name, username and password:

<img src='./images/img_124.png' alt='img_124' width='600'/>

The name and location of the Ubuntu 24.10 Guest will be shown. Select Next:

<img src='./images/img_125.png' alt='img_125' width='600'/>

The default disk size is 20 GB. This can be expanded if more disk space is required:

<img src='./images/img_126.png' alt='img_126' width='600'/>

Select Finish:

<img src='./images/img_127.png' alt='img_127' width='600'/>

### Installing Ubuntu 24.10 in the Ubuntu 24.10 Guest VM

The Ubuntu 24.10 Guest will start booting from the Ubuntu 24.10 Live ISO:

<img src='./images/img_128.png' alt='img_128' width='600'/>

<img src='./images/img_129.png' alt='img_129' width='600'/>

Select your Language:

<img src='./images/img_130.png' alt='img_130' width='600'/>

Select Next:

<img src='./images/img_131.png' alt='img_131' width='600'/>

Select your keyboard layout and then select Next:

<img src='./images/img_132.png' alt='img_132' width='600'/>

Select use wired connection and select Next:

<img src='./images/img_133.png' alt='img_133' width='600'/>

Select Install Ubuntu and select next:

<img src='./images/img_134.png' alt='img_134' width='600'/>

Select Interactive Installation:

<img src='./images/img_135.png' alt='img_135' width='600'/>

Select Default Selection:

<img src='./images/img_136.png' alt='img_136' width='600'/>

Check Install third-party software for graphics and Wi-Fi hardware and Download and install support for additional media formats and select Next:

<img src='./images/img_137.png' alt='img_137' width='600'/>

Select Erase Disk and install Ubuntu:

<img src='./images/img_138.png' alt='img_138' width='600'/>

Input your full name, computer name\*, username\* and password:

\* These should be lower case characters with no spaces, the `-` is the only special character allowed. The user name `philip` becomes the name of the home folder `/home/philip` which is also represented by `~` in the terminal:

<img src='./images/img_139.png' alt='img_139' width='600'/>

Select your time zone and select Next:

<img src='./images/img_140.png' alt='img_140' width='600'/>

Select Next:

<img src='./images/img_141.png' alt='img_141' width='600'/>

Select Reboot Now:

<img src='./images/img_142.png' alt='img_142' width='600'/>

Select Next:

<img src='./images/img_143.png' alt='img_143' width='600'/>

Select Next:

<img src='./images/img_144.png' alt='img_144' width='600'/>

Select Finish:

<img src='./images/img_145.png' alt='img_145' width='600'/>

Ubuntu 24.10 is now installed in the Ubuntu 24.10 Guest Virtual Machine. The system drivers (`open-vm-tools`) are included in the Linux Kernel and do not have to be installed. The Ubuntu 24.10 guest can be maximised to full size:

<img src='./images/img_146.png' alt='img_146' width='600'/>

### Shared Folders

Power off the Ubuntu 24.10 Guest:

<img src='./images/img_147.png' alt='img_147' width='600'/>

Open VMware player, highlight the Ubunti 24.10 Guest and select Virtual Machine Settings. Select Options and Shared Folders. Select Always Enabled and select Add:

<img src='./images/img_148.png' alt='img_148' width='600'/>

Under name select VMShared:

<img src='./images/img_149.png' alt='img_149' width='600'/>

Select the VMShared folder under the Ubuntu 24.04 host Documents folder:

<img src='./images/img_150.png' alt='img_150' width='600'/>

Select OK:

<img src='./images/img_151.png' alt='img_151' width='600'/>

Select Save:

<img src='./images/img_152.png' alt='img_152' width='600'/>

Launch the Ubuntu 24.10 Guest, the shared folder will not automatically be mounted. Under `home` also known as `~` create a folder called `vmshared` where the shared folder can be mounted to:

<img src='./images/img_153.png' alt='img_153' width='600'/>

<img src='./images/img_154.png' alt='img_154' width='600'/>

<img src='./images/img_155.png' alt='img_155' width='600'/>

Launch Startup Applications:

<img src='./images/img_156.png' alt='img_156' width='600'/>

Under name select `VMware Shared Folder`. 

Under command input the following command

```bash
/usr/bin/vmhgfs-fuse .host:/ /home/philip/vmshared -o subtype=vmhgfs-fuse
```

Replacing `philip` with your user name and `vmshared` with the name of the folder. If `vmshared` is under `Documents` use:

```bash
/usr/bin/vmhgfs-fuse .host:/ /home/philip/Documents/vmshared -o subtype=vmhgfs-fuse
```

<img src='./images/img_157.png' alt='img_157' width='600'/>

Restart the Ubuntu 24.10 Guest:

<img src='./images/img_158.png' alt='img_158' width='600'/>

The folder `vmshared` is now mounted as a shared folder:

<img src='./images/img_159.png' alt='img_159' width='600'/>

And the files can be accessed from the Ubuntu 24.10 Guest and Ubuntu 24.04 Host:

<img src='./images/img_160.png' alt='img_160' width='600'/>

<img src='./images/img_161.png' alt='img_161' width='600'/>

## Uninstall VMware Workstation

It is common to uninstall VMware Workstation in order to install the latest version, when a new version is released. Open up the Terminal and change directory to:

```bash
cd /usr/bin
```

<img src='./images/img_162.png' alt='img_162' width='600'/>

```bash
sudo vmware-installer -u vmware-workstation
```

Uninstallation is an operation in a system directory, input your password to authenticate:

<img src='./images/img_163.png' alt='img_163' width='600'/>

Input `y` in order to proceed:

<img src='./images/img_164.png' alt='img_164' width='600'/>

VMware Workstation is now uninstalled:

<img src='./images/img_165.png' alt='img_165' width='600'/>

The latest version of VMware Workstation can now be installed. A MOK for the kernel services blocked by Secure Boot will need to be created.

Return to [VMware Installation Guide](../readme.md)