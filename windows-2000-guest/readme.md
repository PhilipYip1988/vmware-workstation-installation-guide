# Windows 2000

## Notes

VMware Workstation Player 17.6.4 has Windows 2000 as an option for a Virtual Machine. However Windows 2000 is regarded as a legacy Operating System and isn't tested by Broadcom. Moreover the VMware Tools 12.5.3 which comes with VMware workstation player doesn't support Windows 2000. VMware Tools 6.5.5 is the last version of VMware Tools to support Windows 2000 and should be downloaded seperately as an ISO. 

On modern hardware, with a 11th-14th Generation Processor, the following entries should be added to the VMX file:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

Before installing VMWare Tools 6.6.5, Windows 2000 SP4 should be installed alongside post-SP4 updates. An ISO of the SP4 update will need to be created and mounted to the VM for installation. The post-SP4 updates should be installed using the WSUS Offline Update 6.6.5 ISO.

## Downloads

### Windows 2000 ISO

Windows 2000 is considered abandonware and the Windows 2000 ISO and Product Key can be obtained from WinWorld:

* [WinWorld](https://winworldpc.com/library/operating-systems)

### WSUS Offline Update

The last version of WSUS Offline Update to support Windows 2000 was 6.6.5. The Website Archive.org hosts the ISO created from WSUS Offline Update before Microsoft removed Windows 2000 downloads from their download servers:

* [WSUS Offline Update Windows 2000](https://archive.org/details/wsusoffline-w2k-enu)

### VMware Tools ISO

The Windows 2000 drivers for the Windows 2000 Guest are contained in the VMware Tools Installation ISO. The Website Archive.org hosts the ISO created by VMware before Broadcom removed it:

* [vmware-tools-655-win.iso](https://archive.org/details/vmware-tools-collection)

## Configuring Virtual Hardware for a Windows 2000 Guest

Select Player → File → New Virtual machine...

<img src="https://github.com/user-attachments/assets/40c10c2a-d4ad-401d-8cfe-2e609e30725c" width="600"/>

Select I will install this operating system later and then next:

<img src="https://github.com/user-attachments/assets/580444bd-cb3d-41a2-8fad-3e434c248bab" width="600"/>

Select Windows 2000 Professional and then next:

<img src="https://github.com/user-attachments/assets/15133c99-2dba-4ef2-87d8-e319a19e1f03" width="600"/>

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive, you may want to move this to a local only location) and select next:

<img src="https://github.com/user-attachments/assets/d1b95fda-74a1-4730-a05d-5ef8b1159ab0" width="600"/>

Select 20 GB and select next:

<img src="https://github.com/user-attachments/assets/24dd4b12-5717-4265-a185-09ca82041a2c" width="600"/>

Select customise hardware:

<img src="https://github.com/user-attachments/assets/2fd1b7c9-c122-430b-9fab-0307fe2fb325" width="600"/>

Set the memory to 512 MB:

<img src="https://github.com/user-attachments/assets/67232df2-7094-48e7-8289-b2280ee6fd98" width="600"/>

Set the number of processors to 1:

<img src="https://github.com/user-attachments/assets/19602989-7bee-4685-b05c-9877ccc89f65" width="600"/>

Under CD/DVD ensure connected at power on is checked and select browse to browse for the Windows 2000 Professional ISO:

<img src="https://github.com/user-attachments/assets/94f3f417-cc69-4d9a-99a0-92565da23117" width="600"/>

Select the Windows 2000 Professional ISO:

<img src="https://github.com/user-attachments/assets/2e4ea6ac-1a57-4424-b160-dd87f2c609f1" width="600"/>

<img src="https://github.com/user-attachments/assets/11877ead-169f-4cf3-883a-5a024d6e458e" width="600"/>

<img src="https://github.com/user-attachments/assets/6381c218-4692-45d5-91a7-9b3a33555ab1" width="600"/>

<img src="https://github.com/user-attachments/assets/2a969d3f-a3cb-408b-9103-d697b5baf44b" width="600"/>

Uncheck Connect at Power On for Network Adaptor:

<img src="https://github.com/user-attachments/assets/cac9fc38-ba76-4710-90c1-7367616a79b5" width="600"/>

Under USB Controller, select USB 2.0:

<img src="https://github.com/user-attachments/assets/e6d01ffb-2694-47b1-8018-c917d45f130a" width="600"/>

Under Sound Card, use the default settings:

<img src="https://github.com/user-attachments/assets/b65b5f79-16e8-49f9-8f7f-161345489d72" width="600"/>

Under display uncheck accelerate 3d Graphics:

<img src="https://github.com/user-attachments/assets/c21bbe05-3e1d-42e7-b699-911e62109ecb" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/128a6d37-4c68-4708-a6bb-06aee806a56f" width="600"/>

## Windows 2000 Guest Virtual Machine Configuration File

Navigate to the directory on the Windows 11 Host that the Windows 2000 Guest is installed:

<img src="https://github.com/user-attachments/assets/2dc2d68d-16c3-446b-b3bc-7a3e59934cd8" width="600"/>

Look for the `Windows 2000.vmx` file:

<img src="https://github.com/user-attachments/assets/6233c0ed-cbbb-42a4-b649-2fcccf52208d" width="600"/>

Open in Notepad or Notepad++ (recommended):

<img src="https://github.com/user-attachments/assets/0f503d19-2e66-43f0-9bba-ab88b3425bf5" width="600"/>

Press Ctrl+f to begin a search for an option for example `bios.bootDelay`:

<img src="https://github.com/user-attachments/assets/36f9b154-62c5-410b-b215-38e7f30a0dec" width="600"/>


If the line exists it can be modified to a new value. In this case it doesn't exist so can be appended to the end:

```
bios.bootDelay = "20000"
```

<img src="https://github.com/user-attachments/assets/5dc470aa-83e2-4f7a-a064-98f1b806bd67" width="600"/>

### Modern Generation Processors (11-14th Generation)

Certain legacy settings may need to be configured to run older guest operating systems such as Windows 2000.

Legacy CPU settings:

```
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

These settings help emulate older CPU instructions that Windows 2000 expects.

Legacy monitor / virtualization settings

```
mks.enableVulkanRenderer = "FALSE"
```

This disables the Vulkan renderer, forcing VMware to use a more compatible DirectX/software renderer.

Legacy monitor / virtualization settings:

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
These settings ensure proper CPU and MMU handling for legacy guests.
```

<img src="https://github.com/user-attachments/assets/a29ba670-d136-4198-a3d7-64ec96083a01" width="600"/>

## Installing the Windows 2000 Guest

Select the Windows 2000 Guest and select Play:

<img src="https://github.com/user-attachments/assets/3baaf7f0-4ed2-49ae-95a8-c05e7db914d4" width="600"/>

The Windows 2000 Professional setup will begin:

<img src="https://github.com/user-attachments/assets/b5330825-ee8d-4e67-b06d-4195bb0b445c" width="600"/>

Click into the VM and press `↵` to proceed:

<img src="https://github.com/user-attachments/assets/27465a9e-dcd4-4b8c-b8ea-de8f944069ef" width="600"/>

Note once clicked into the VM, the VM will capture the mouse. To return the mouse to the host PC, press `Ctrl` + `Alt`.

Press `c` to proceed:

<img src="https://github.com/user-attachments/assets/f21b88eb-e892-4984-8b0c-c07b008d32ca" width="600"/>

Press `↵` to install onto the 20 GB Virtual Drive:

<img src="https://github.com/user-attachments/assets/c329d6dc-35b1-436f-9d0e-e8b7f2bfe4f1" width="600"/>

Press `↵` to format the 20 GB Virtual Drive using NTFS:

<img src="https://github.com/user-attachments/assets/f4aa0a15-a638-4121-9044-c95ee7c40f76" width="600"/>

Under system locale, select customise:

<img src="https://github.com/user-attachments/assets/9e45a509-48ed-4941-a396-bfa31e6c17a5" width="600"/>

Select your locale from the dropdown menu and select apply:

<img src="https://github.com/user-attachments/assets/88b11384-0090-4f71-8dca-f7431644d4fc" width="600"/>

Under keyboard layout, select customise:

<img src="https://github.com/user-attachments/assets/887d83fb-ca4b-48c1-8e51-a895cc83e0d1" width="600"/>

Select your input language and select apply:

<img src="https://github.com/user-attachments/assets/2993cae5-7bd2-4f3c-80e4-42e208041970" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/0bf48444-8e1d-45cc-b127-5c91ea770971" width="600"/>

Input your name and select next:

<img src="https://github.com/user-attachments/assets/79e303ae-c654-498b-a9c2-4332f59e9f93" width="600"/>

Input the product key supplied by WinWorld and select next:

<img src="https://github.com/user-attachments/assets/4b487f59-4b1d-4c09-bd79-c8a85c59dc5b" width="600" />

Input the computer name and select next:

<img src="https://github.com/user-attachments/assets/0109eb5d-3545-4018-8d6f-a7c67f920f62" width="600"/>

Select your timezone and select next:

<img src="https://github.com/user-attachments/assets/a898c401-a46a-4a6c-a406-9924153c714c" width="600"/>

Select typical settings and select next:

<img src="https://github.com/user-attachments/assets/3ef270a0-b740-4c6c-bd72-967cb8838f4d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/046837b5-043e-45a0-b9e3-610737753fc1" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/d207a22f-525e-4195-827f-3f4ad17c445c" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/816317ca-de25-4e6f-8fbb-71c0a4e1be17" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/8f9f80fc-5ca2-4a8f-8e35-0f0e39153b74" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/d076c5d8-5382-458b-b580-050a9d75fa26" width="600"/>

Uncheck show this screen at startup and select exit:

<img src="https://github.com/user-attachments/assets/bcbc535c-9748-43fe-be8e-d5303de64bd0" width="600"/>

## Install Windows 2000 SP4 and Post-SP4 Updates

Select Player → Manage → CD/DVD and select Settings:

<img src="https://github.com/user-attachments/assets/d3209bbe-966a-4050-bd42-9a82af59dcf6" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/88a3be7c-fc69-48be-8809-b9bd146d4a69" width="600"/>

Select the `wsusoffline-w2k-enu.iso`:

<img src="https://github.com/user-attachments/assets/1cfd94f7-69ce-41d2-a186-44b94da7ae34" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/ea84822c-f0bf-49c5-90e3-dab42b376a8a" width="600"/>

Select My Computer:

<img src="https://github.com/user-attachments/assets/f6646040-5dfd-4ce1-bade-e4cd4477a3c4" width="600"/>

Right click the `D:` drive and select explore:

<img src="https://github.com/user-attachments/assets/5580dcc0-8bab-4518-96d2-e84cf3ad3213" width="600"/>

Launch the `update` command script (1):

<img src="https://github.com/user-attachments/assets/04e053c1-6f68-404d-bcf0-761f2ca1a832" width="600"/>

The service pack will install:

<img src="https://github.com/user-attachments/assets/5b4014b3-f0b0-4c82-aec8-0f30f8a71f13" width="600"/>

<img src="https://github.com/user-attachments/assets/939e60aa-b65d-45fa-a319-b50461f2efca" width="600"/>

<img src="https://github.com/user-attachments/assets/fbbdedc6-b9b7-463f-b2f4-86927b56f933" width="600"/>

Restart the VM when prompted:

<img src="https://github.com/user-attachments/assets/8dd78b26-ee70-40d2-baa8-8fd2f94cdf7a" width="600" />

Select Restart and OK:

<img src="https://github.com/user-attachments/assets/cb62ae99-74b0-4d35-aa5d-60b1f3e57e08" width="600"/>

Relaunch the `update` script (2) and restart the VM when prompted:

<img src="https://github.com/user-attachments/assets/4600dc58-05f2-41e8-96fc-a83bf3156d8e" width="600"/>

<img src="https://github.com/user-attachments/assets/ece3a986-75da-43ee-85d1-42aa43a38f63" width="600"/>

Relaunch the `update` script (3) and restart the VM when prompted:

<img src="https://github.com/user-attachments/assets/ab4ac236-d651-434e-9b83-1073115246e2" width="600"/>

<img src="https://github.com/user-attachments/assets/e5936bcf-fa28-4101-a6e7-5315b9b5a3d2" width="600"/>

Relaunch the `update` script (4):

<img src="https://github.com/user-attachments/assets/f8e4578c-7f40-4dd9-af72-71f1fb0f48b8" width="600"/>

When all updates are installed no missing update found. Nothing to do! will display.

## Install VMware Tools

In the Windows 2000 VM. Select Player → Removable Drives → CD/DVD and then settings:

<img src="https://github.com/user-attachments/assets/c4d69023-2708-4cdd-8d02-9dd422620cf5" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/61d2612c-2b24-416e-a149-a93e89a6bc25" width="600"/>

Select the `vmware-tools-655-win.iso`:

<img src="https://github.com/user-attachments/assets/705aed7c-3a7b-40d8-a34c-929bc344a225" width="600"/>

Select ok:

<img src="https://github.com/user-attachments/assets/7466cbdb-7e4d-4649-b404-a8dc20ec4f67" width="600"/>

Open My Computer and select the CD/DVD (the CD/DVD label and icon are sometimes slow to update on Windows 2000):

<img src="https://github.com/user-attachments/assets/cbb59fec-9c31-4868-a998-8cca91942a89" width="600"/>

Launch the setup:

<img src="https://github.com/user-attachments/assets/3d1ae51d-508a-43ac-89fb-31824b318c53" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/4b20cddb-121e-4566-a910-2aff5028ec59" width="600"/>

Select typical and next:

<img src="https://github.com/user-attachments/assets/65977ac1-3028-46a7-81bb-2ff9d7d4c093" width="600"/>

Select Install:

<img src="https://github.com/user-attachments/assets/026e55d1-6790-4c94-9dd6-e22b495e91dd" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/c6e5fefb-92aa-437c-a1ec-4a76722151d6" width="600"/>

Select Yes to restart the VM:

<img src="https://github.com/user-attachments/assets/6795fdd8-f14e-4337-b1d6-6b9c6f5c2cbc" width="600"/>

Right click My Computer and select Properties:

<img src="https://github.com/user-attachments/assets/3eeeb0cc-1ca8-434c-9da2-f0afba2350b3" width="600"/>

Select the hardware tab and select Device Manager:

<img src="https://github.com/user-attachments/assets/28c1cd96-beba-4a2f-be61-4af7d04ed92c" width="600"/>

There is one unknown device:

<img src="https://github.com/user-attachments/assets/c8e25c41-cfb9-41b9-820b-5114b9d43ec5" width="600"/>

Right click it and select Properties:

<img src="https://github.com/user-attachments/assets/6412b478-8a8b-45a8-89bb-bb8cce28c9a6" width="600"/>

Select Reinstall Driver:

<img src="https://github.com/user-attachments/assets/dcd9d58f-0e9d-44f2-8a90-dac747ba4ca1" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/51e6d2f6-e214-4178-a091-c1923627da68" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/114f2aa9-2856-4d46-a784-6be3946efb34" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/dcad2478-e42c-43a9-a847-f543626c7153" width="600"/>

Selet next:

<img src="https://github.com/user-attachments/assets/91c0a86a-642c-4d70-bbc5-7fc5e122a3f6" width="600"/>

Select finish:

<img src="https://github.com/user-attachments/assets/eec565a5-2fe7-48e9-a188-00c207cf1678" width="600"/>

Select close:

<img src="https://github.com/user-attachments/assets/c2050036-7124-4e4b-abd7-4a98f7d72bea" width="600"/>

Now there are no errors in the Device Manager:

<img src="https://github.com/user-attachments/assets/007d79f7-9052-4b68-9bfc-1c928536f477" width="600"/>

With VMware tools installed, the VM can be resized:

<img src="https://github.com/user-attachments/assets/a4669e36-9128-4d04-9616-467e3819bad0" width="600"/>

When the VM is powered down the VM can be backed up by copying the folder Windows 2000 Professional found in Documents → Virtual Machines on the Windows 11 Host PC.

## Installing Python

Python will be used as an example of installing a program on Windows 2000. [python-2.4.4.msi](https://www.python.org/downloads/release/python-244/) is the latest version of Python to work on Windows 2000. In theory drag and drop should work bi-directionally from the Windows 11 Desktop to the Windows 2000 VM. However it typically does not work correctly with a Windows 2000 VM and its older implementation of VMware tools... The python-2.4.4.msi can be copied from the Host PC and pasted to the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/ead35b6b-9db0-4aff-bd93-ed61e92f6070" width="600"/>

<img src="https://github.com/user-attachments/assets/19754735-8378-46ac-bb19-0e4693501bcd" width="600"/>

Launch the Python 2.4.4 setup and select install for all users and then select next:

<img src="https://github.com/user-attachments/assets/35599691-869f-4296-b00d-b7d7c33250cf" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/d0d0c9f3-ed7f-4813-b71d-4149cb549a88" width="600"/>

Select next again:

<img src="https://github.com/user-attachments/assets/ce390724-0253-436e-bb12-2d4b9574a6c2" wodth="600"/>

Select finish:

<img src="https://github.com/user-attachments/assets/77d59572-773d-44e6-901d-e9edd6648f47" width="600"/>

Open the command prompt:

<img src="https://github.com/user-attachments/assets/3a23d84f-d1eb-4ae9-84f6-78afc9122b7d" width="600"/>

Change directory to the python directory and launch Python using:

```
cd C:\python24
python
print 'Hello World!'
```

<img src="https://github.com/user-attachments/assets/ff49f6d3-1a9b-4827-a68f-0e5b747f8ae6" width="600" />

## Upgrade Virtual Hardware

Now that Service Pack 4 and the post-SP4 Updates have been installed, the virtual hardware used by the VM can be upgraded. Shut down the VM and select Edit Virtual Machine Settings:

<img src="https://github.com/user-attachments/assets/9d493a75-cf01-4820-8992-f6db27123bb7" width="600"/>

Update the memory to 4096 MB:

<img src="https://github.com/user-attachments/assets/05810138-0b76-4d1c-9d76-e57680845208" width="600"/>

And the processor cores to 2:

<img src="https://github.com/user-attachments/assets/97492860-4b62-4b18-8e5f-3686f4b91fa9" width="600"/>

Relaunch the Virtual Machine.

## USB Device Passthrough

A Brother QL-570 label printer will be used as an example of a USB Device that can be connected to the Windows 2000 VM. The [Brother QL-570 Windows 2000](https://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=lpql570eas&os=43) Driver can be downloaded from from the Brother website using the Windows 11 Hst PC and copied over to the Windows 2000 VM Desktop:

<img src="https://github.com/user-attachments/assets/23de78d9-4710-43c4-bd88-26296cf46a4d" width="600"/>

The driver can be installed:

<img src="https://github.com/user-attachments/assets/5d65733a-7301-4df4-8293-024db6afe83c" width="600"/>

Select unzip:

<img src="https://github.com/user-attachments/assets/88b090fa-0773-46ed-b9c2-c33503008e3f" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/ba47ea42-3bc0-490f-a03b-6142d69ecf43" width="600"/>

Select close:

<img src="https://github.com/user-attachments/assets/4972149e-56e8-4297-a681-68c55c66c559" width="600"/>

Go to the extracted folder:

<img src="https://github.com/user-attachments/assets/8efcc74e-874b-45c7-8193-ea19c6ab3c47" width="600"/>

Launch the setup:

<img src="https://github.com/user-attachments/assets/ef8b20f1-9beb-4e2a-b8cb-937cd5b8399b" width="600"/>

Select Start:

<img src="https://github.com/user-attachments/assets/f2d0c8a5-017a-4a3e-b8bd-cde4a32d506a" width="600"/>

The driver install will prompt for connection to the printer:

<img src="https://github.com/user-attachments/assets/5076eb5d-cf36-4c82-8237-d775351b3b27" width="600"/>

When a USB device is connected to the Windows 11 Host PC and the Windows 2000 VM is launched, there will be a prompt to connect it to the Windows 11 Host PC or the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/c96f66a3-ffad-4a80-8256-a604c2103eb4" width="600"/>

Alternatively the USB device can be connected by going to Player → Removable Devices → Brother QL-570 and selecting Connect:

<img src="https://github.com/user-attachments/assets/b82aee5b-9757-4821-8ace-8e2540336a16" width="600"/>

Sellect OK:

<img src="https://github.com/user-attachments/assets/fefa2ae7-28c1-4579-a620-15b28b50fd70" width="600"/>

The Brother QL-570 passes through to the Windows 2000 VM via the Windows 11 host USB port is detected:

<img src="https://github.com/user-attachments/assets/a751ce38-4394-4d4f-af9a-9a5097031185" width="600"/>

To complete the printer driver installation the Windows 2000 VM needs to be restarted:

<img src="https://github.com/user-attachments/assets/92c00a06-aa10-489d-a400-bceb47b2b63d" width="600"/>

The p-touch editor can now be installed:

<img src="https://github.com/user-attachments/assets/5141a7c1-5976-46f6-b588-78f534f3bbf8" wodth="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/7697e79d-44e9-4faa-8c9c-b915d2d3a615" width="600"/>

Input your user name and select next:

<img src="https://github.com/user-attachments/assets/5344cafa-9245-46d6-a60b-60a2002dcc69" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/0b38c79d-a95b-4153-b6a1-eeb5e9a93f9d" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/e855638a-50ae-479c-a5d7-81b43e6340b5" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/d805eb43-e690-48c7-94da-b3dde348806e" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/0bda3352-56a4-4898-8ace-245f65483348" width="600"/>

Select finish and restart the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/e3a40afd-3db8-40ce-8513-f917f8d689c4" width="600"/>

Launch the p-touch editor:

<img src="https://github.com/user-attachments/assets/9b640093-b1c5-49b0-8db8-6838ddd00868" width="600"/>

Select the BrotherQL-570 printer:

<img src="https://github.com/user-attachments/assets/66d489bc-5998-415f-be5b-f71375db8787" width="600"/>

Create a test label:

<img src="https://github.com/user-attachments/assets/7e17576e-63de-404a-a01b-5370cff561cd" width="600"/>

Select print:

<img src="https://github.com/user-attachments/assets/d3f090f4-587e-4ecb-a011-bc3a83a02220" width="600"/>

The ptouch editor on the Windows 2000 VM prints to the QL-570 attached to the host PC using VMwares USB passthrough:

<img src="https://github.com/user-attachments/assets/cd119cbf-51b5-4274-9715-b4646a5d361c" width="600"/>

## Serial Port Passthrough

Close the Windows 2000 VM. Attach a USB to Serial Port to the Window 11 Host PC:

<img src="https://github.com/user-attachments/assets/0ef84622-10c0-4bff-8cf1-9edf492137ba" width="600"/>

On the Windows 11 Host PC, right click the Start Button and select Device Manager:

<img src="https://github.com/user-attachments/assets/622bcb44-367d-42b6-aaf8-fea04bf18ebd" width="400"/>

Expand ports (COM & LPT). In this example, the USB Serial COM Port is COM3:

<img src="https://github.com/user-attachments/assets/7a133968-f0fc-4b26-9d75-2e4233f0dc1e" width="600"/>

Right click it and select properties:

<img src="https://github.com/user-attachments/assets/530c8c0b-ac42-4ad8-8ef4-7d1dbbe75aa5" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects:

<img src="https://github.com/user-attachments/assets/60686db0-b415-4ea7-a82e-a758329f4fb0" width="600"/>

The port number can be changed by selecting Advanced:

<img src="https://github.com/user-attachments/assets/3ac282d1-9dbc-4a17-b42f-bb3c9aab24f2" width="600"/>

In this case it will be left at port 3:

<img src="https://github.com/user-attachments/assets/04cd83bf-c91f-4ca1-84ae-f93b09257e10" width="600"/>

Open VMware Player and select Edit Virtual Machine Settings:

<img src="https://github.com/user-attachments/assets/865199af-f476-4d3a-b821-41d5568a7058" width="600"/>

Select Add...:

<img src="https://github.com/user-attachments/assets/8ed534f3-f9a8-4c54-b5fc-2103d640e700" width="600"/>

Select Serial Port and Finish:

<img src="https://github.com/user-attachments/assets/3b4c2dc4-84e5-4f27-91df-773f3a9bb67b" width="600"/>

Select Connect at Power On. Autodetect is useful for a single port, but for multipe ports, it is more useful to select the serial Port indiviually. In this example COM3 will be used:

<img src="https://github.com/user-attachments/assets/98fc0369-8b8a-4299-b7d6-3eed19bf55dc" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/47ce415a-ec42-4ab7-a7ab-eb2b37c83fa9" width="600"/>

Launch the VM:

<img src="https://github.com/user-attachments/assets/c37f2fdb-e39b-46e1-83ac-59fdbabc3d14" width="600"/>

Right click My Computer and select Properties:

<img src="https://github.com/user-attachments/assets/30514a5d-70f4-4bf0-bc5c-245734a565d8" width="600"/>

Select the hardware tab and then device manager:

<img src="https://github.com/user-attachments/assets/fc66c338-8512-4b06-b982-2a7165b15acd" width="600"/>

Expand ports, note the Windows 11 COM3 is passed through to the Windows 2000 VM as COM1:

<img src="https://github.com/user-attachments/assets/072cbe90-58c4-4f9b-8cbe-a8c90480afde" width="600"/>

Right click the communication port and select properties:

<img src="https://github.com/user-attachments/assets/e85d671c-7b30-45c1-9016-fa6b55da28da" width="600"/>

The Baud rate will be shown, in this case 9600 Bits per second. Update this to match the speed the device you want to connect expects (consistent with the settings on the Windows 11 Host):

<img src="https://github.com/user-attachments/assets/af4fa0e1-acdc-481f-a1d6-be3e1799c5ab" width="600"/>

Select Advanced:

<img src="https://github.com/user-attachments/assets/b25ca227-6356-4da1-ad17-8c4b40ff92f5" width="600"/>

Update the COM Port Number to be consistent with the Windows 11 Host:

<img src="https://github.com/user-attachments/assets/dd217523-f84b-415e-a9f7-5730f57ff293" width="600"/>

In this case COM3. Select OK:

<img src="https://github.com/user-attachments/assets/8b395e07-919e-4b87-8acb-07e98dd2fc88" width="600"/>

The Serial Port COM3 is now ready for use in the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/a2fa4051-045f-4861-9aa4-d8c613e4db07" width="600"/>





