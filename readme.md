# VMWare Workstation Pro Install Ubuntu
## Installing VMware Perquisites

Install the following packages:

```bash
sudo apt install gcc-12 libgcc-12-dev build-essential
```

## Downloading VMware Workstation

Download the compatible version of VMware Workstation from VMware. This is in the core folder and has the extensions `.bundle.tar`:

* [VMware Workstation](https://softwareupdate.vmware.com/cds/vmw-desktop/ws/)

Note that it takes time for the host modules to be developed and therefore there may not be a host module for the latest version of VMware Workstation Player.

## Installing VMWare Workstation

Extract the `.tar` to get to the extracted folder with the `.bundle` file. Right click the `.bundle` file and select properties:


Select Executable as Program:


Right click empty space in the folder and select open in terminal.

In the terminal input the following command with a space (but don't run this command):

```bash
chmod +x 
```

This command changes the permissions of a file to execution. Drag the bundle file into the terminal and run the command:

```bash
chmod +x '/home/philip/Downloads/VMware-Workstation-17.6.2-24409262.x86_64.bundle/VMware-Workstation-17.6.2-24409262.x86_64.bundle' 
```

Now that the file is executable it can be run as a super using. Input the following command with a space (but don't run this command):

```bash
sudo 
```

Drag the bundle file into the terminal and run the command:

```bash
sudo '/home/philip/Downloads/VMware-Workstation-17.6.2-24409262.x86_64.bundle/VMware-Workstation-17.6.2-24409262.x86_64.bundle'  
```

## Configuring Secure Boot

Secure Boot will block the Virtual Monitor Kernel Module and Virtual Network Adaptor Module.

A Machine Owner Key (MOK) must be created which signs these modules.

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

## Uninstall VMware Workstation

```bash
cd /usr/bin
```

```bash
sudo vmware-installer -u vmware-workstation
```