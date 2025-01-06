# VMware Workstation Pro Install Ubuntu

This guide looks at installation of VMware Workstation Pro on Ubuntu 24.04 or 24.10. VMware has recently been acquired by Broadcom and VMware Workstation has been made free for non-commercial use.

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

Download the compatible version of VMware Workstation from VMware. This is in the core folder and has the extensions `.bundle.tar`.

<img src='./images/img_005.png' alt='img_005' width='600'/>

<img src='./images/img_006.png' alt='img_006' width='600'/>

<img src='./images/img_007.png' alt='img_007' width='600'/>

<img src='./images/img_008.png' alt='img_008' width='600'/>

<img src='./images/img_009.png' alt='img_009' width='600'/>

## Installing VMWare Workstation

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

VMware Player is now installed and displays in the start screen: 

<img src='./images/img_017.png' alt='img_017' width='600'/>

Launch VMware Player, accept the license agreement and select Next:

<img src='./images/img_018.png' alt='img_018' width='600'/>

Select Yes and Next:

<img src='./images/img_019.png' alt='img_019' width='600'/>

Opt in or out of the customer experience program and select Next:

<img src='./images/img_020.png' alt='img_020' width='600'/>

To compile the kernel modules (requires the perquisites packages to perform the compiling) and install them system wide, authentication is required. Input your password and select authenticate:

<img src='./images/img_021.png' alt='img_021' width='600'/>

## Configuring a Windows 11 VM

Windows 11 has relatively high system requirements such as an 8th generation processor, 8 GB of RAM and a 1 TB SSD boot drive. To run Windows 11 as a VM, the host PC should significantly exceed these system requirements and therefore have a high end 11th generation processor, at least 16 GB of RAM and at least a 512 GB SSD. Go to Settings, to the left hand side select System:

<img src='./images/img_022.png' alt='img_022' width='600'/>

Then select About:

<img src='./images/img_023.png' alt='img_023' width='600'/>

A Windows 11 ISO can be downloaded from Microsoft:

* [Windows 11](https://www.microsoft.com/en-us/software-download/windows11)

Select the Windows 11 ISO and select Download now:

<img src='./images/img_024.png' alt='img_024' width='600'/>

Select the Language and select Confirm:

<img src='./images/img_025.png' alt='img_025' width='600'/>

Select 64 Bit Download:

<img src='./images/img_026.png' alt='img_026' width='600'/>

The ISO will download:

<img src='./images/img_027.png' alt='img_027' width='600'/>

Select File → Create a New Virtual Machine:

<img src='./images/img_028.png' alt='img_028' width='600'/>

Select the Windows 11 ISO and select Open:

<img src='./images/img_030.png' alt='img_030' width='600'/>

Windows 11 will automatically be detected and the default VM settings for Windows 11 will be applied:

<img src='./images/img_031.png' alt='img_031' width='600'/>

The name and location of the VM will be shown. Select Next:

<img src='./images/img_032.png' alt='img_032' width='600'/>

Windows 11 requires an encryption key for the TPM. Input an 8 digit password and confirm the password:

<img src='./images/img_033.png' alt='img_033' width='600'/>

The default disk size is 64 GB. This can be expanded if more disk space is required:

<img src='./images/img_034.png' alt='img_034' width='600'/>

Select Next:

<img src='./images/img_035.png' alt='img_035' width='600'/>

Select Close:

<img src='./images/img_036.png' alt='img_036' width='600'/>

The VM will attempt to launch however will be unable to access the virtual monitor kernel module vmmon because it is blocked by Secure Boot:

<img src='./images/img_037.png' alt='img_037' width='600'/>

An error message, failed to start monitor device will display:

<img src='./images/img_038.png' alt='img_038' width='600'/>

## Configuring Secure Boot

Secure Boot will block the Virtual Monitor Kernel Module and Virtual Network Adaptor Module. A Machine Owner Key (MOK) must be created which signs these modules.

Generate a new Machine Owner Key:

```bash
openssl req -new -x509 -newkey rsa:2048 -keyout VMWARE17.priv -outform DER -out VMWARE17.der -nodes -days 36500 -subj "/CN=VMWARE/"
```

Sign the kernel module vmmon:

```bash
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE17.priv ./VMWARE17.der $(modinfo -n vmmon)
```

Sign the kernel module vmnet:

```bash
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE17.priv ./VMWARE17.der $(modinfo -n vmnet)
```

Importing the MOK with MOK management system:

```bash
sudo mokutil --import VMWARE17.der
```

In the terminal create a MOK password for example:

```
vmware1234
```

Confirm the password:

```
vmware1234
```

Input:

```bash
sudo reboot
```

In the BIOS Setup, select Enrol MOK and supply the password above:

```
vmware1234
```

This section may need to be repeated after a significant update.

## Installing Windows 11 in a VM




## Uninstall VMware Workstation

```bash
cd /usr/bin
```

```bash
sudo vmware-installer -u vmware-workstation
```