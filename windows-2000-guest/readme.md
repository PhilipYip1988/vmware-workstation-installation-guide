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

### Windows 2000 SP4

* [Windows 2000 SP4](https://winworldpc.com/download/41c38361-6518-c39a-11c3-a4e284a2c3a5)

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

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive. you may want to move this to a loal only location) and select next:

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

<img src="https://github.com/user-attachments/assets/1cfd94f7-69ce-41d2-a186-44b94da7ae34" widh="600"/>

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

## USB Devices

A Logitech Pro 9000 can be used as an example USB device. When it is attached to the Host PC USB port, an option will display to connect it to the Windows 11 Host PC or the Windows 2000 VM:

<img src="https://github.com/user-attachments/assets/bc4a926a-b216-4df6-ac70-1ef5b5f1fc66" width="600"/>

The USB Device cam also be connected to the Windows 2000 VM by selecting Player → Manager and then selecting the USB Device and selecting Connect:

<img src="https://github.com/user-attachments/assets/23afdaaf-1c6d-49db-8fa8-12b7fa2f4c86" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/4a1791de-1634-4aa9-8524-c037ade1561f" width="600"/>

The found new hardward wizard will display:

<img src="https://github.com/user-attachments/assets/e726b33f-f8c2-48c3-be72-3cd63a70e96a" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/764e0bd6-ddfd-42e3-b6c0-25fe176a34a6" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/5695f18b-edce-4d37-b9c6-e5ad22c9c00c" width="600"/>

The driver won't be found select Finish:

<img src="https://github.com/user-attachments/assets/c74886bb-b4ce-4caf-9092-3f47a980a46b" width="600"/>

Copy the installer for the device over to the VM:

<img src="https://github.com/user-attachments/assets/53cde465-0c0f-4746-997b-b3de0b07f381" width="600"/>

Note many installers are Windows XP and later:

<img src="https://github.com/user-attachments/assets/b1523191-1826-4321-a8ba-7a71fe3c03d6" width="600"/>

There is a Windows 2000 installer [qc1051enu-logicool-exe](https://download.cnet.com/download/qc1051enu-logicool-exe/3000-18493_4-157513.html):

<img src="https://github.com/user-attachments/assets/85188fa0-9523-4b79-83b1-73f2906e1c00" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/bdc0a471-9d88-4006-8c5f-b8143cf81502" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/5bc930b2-2118-4c4f-9ce6-c6f6391805af" width="600"/>

Select cancel:

<img src="https://github.com/user-attachments/assets/34ba3fee-cd8b-40c5-abe4-261f2488d538" width="600"/>

Select I accept and next:

<img src="https://github.com/user-attachments/assets/256f14b3-324c-42f4-8f00-5dbe08f1666f" width="600"/>

Select I do not want to activate this service and select next:

<img src="https://github.com/user-attachments/assets/d6d598b7-4121-44d7-a495-9b15fa9e9fe5" width="600"/>

In this example, the Windows 2000 driver does not work on the Logitech Pro 9000 and therefore the webcam is not detected:

<img src="https://github.com/user-attachments/assets/0db20c47-c3d4-417a-94ff-9d6b4e0cdf90" width="600"/>





