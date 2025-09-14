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

## Installing Windows 2000 SP4 and Post-SP4 Updates

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

## Backing up the Windows 2000 VM

When the VM is powered down the VM can be backed up by copying the folder Windows 2000 Professional found in Documents → Virtual Machines on the Windows 11 Host PC.

## Shared Folders

Create a new folder on the Windows 11 Host or Ubuntu 24.10 Host PC called `vmshared`:

<img src="https://github.com/user-attachments/assets/af1724a7-cb93-4870-a0ad-a39a5982e1e8" width="600"/>

Select Player → Manage → Virtual Machine Settings:

<img src="https://github.com/user-attachments/assets/d262ae7c-8962-4ca2-a6c2-9ae4a42df2ab" width="600"/>

Select Options → Shared Folders and change the setting to Always Enabled and check Map Network Drive. Select Add:

<img  src="https://github.com/user-attachments/assets/3a5b8380-2f0f-4859-af3b-cdb62b8cdfef" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/6a2792c7-6978-4748-9d1f-cfd2e444a4d5" width="600"/>

Select browse:

<img src="https://github.com/user-attachments/assets/f89fa1a7-2024-4552-b5c6-aede00e32896" width="600"/>

Select the folder vmshared on the Windows 11 Host PC or Ubuntu 24.10 Host PC and then next:

<img src="https://github.com/user-attachments/assets/a390f734-3a8f-42bd-a433-fd03ef17c154" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/97f27e3c-6f95-4495-9b1f-d76c86f63249" width="600"/>

Select Enable this Share and Finish:

<img src="https://github.com/user-attachments/assets/1559bd61-96fd-4ca7-998d-3a7b7dbcf8ef" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/648545e2-9ad9-4d74-a974-38d6f1dbfc31" width="600"/>

The shared folder is now mapped as a network drive in the Windows 2000 Guest. Go to My Computer:

<img src="https://github.com/user-attachments/assets/6b519d55-e696-44f0-b2d9-899f56015fbd" width="600"/>

Select shared folders on host:

<img src="https://github.com/user-attachments/assets/1c2ff062-d266-4de0-97a3-b3472403186a" width="600"/>

Then the `vmshared` folder:

<img src="https://github.com/user-attachments/assets/2daab45f-77e3-4746-a3c8-83a88d47d6f7" width="600"/>

Files can be bidirectionally copied and pasted to this folder between the Windows 2000 guest and the Windows 11 host. On the Windows 2000 guest, the folder may need to be refreshed to view changes made on the Windows 11 or Ubuntu 25.10 host. To do this blank click some empty space in the folder and select refresh:

<img src="https://github.com/user-attachments/assets/2f5a58a4-28e1-41b0-9b68-43e1324e41b5" width="600"/>

## Installing Python

Python will be used as an example of installing a program on Windows 2000:

* [Python 3.2](https://www.python.org/download/releases/3.2/)
* [Pyserial 3.0.1](https://github.com/pyserial/pyserial/releases/tag/v3.0.1)

Note the Windows Installer for Python 3.2 will work on Windows 2000 however the Windows installer for PySerial will only work on Windows XP and later. For PySerial the zipped `.tar.gz` folder should be used. This should be extracted on the Windows 11 Guest. The Python 3.2 folder and Pyserial 3.0.1 folder can be dragged and dropped from the Windows 11 Host to the Windows 2000 Guest. However drag and drop isn't totally reliable and sometimes stops working until the Windows 2000 Guest is restarted. Therefore shared folders is often better:

<img src="https://github.com/user-attachments/assets/de2b166e-3840-4497-b078-d5c014b34c13" width="600"/>

Launch the Python 3.2 setup:

<img src="https://github.com/user-attachments/assets/5f172a30-9bd2-48dc-a6c0-f490c42a38e0" width="600"/>

Select Install for all User:

<img src="https://github.com/user-attachments/assets/36632e90-9089-4080-9520-27ecfaf41f00" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/c2406a9a-8486-4214-8c61-f414398301bd" width="600"/>

Select Next:

<img src="https://github.com/user-attachments/assets/da4b6027-c613-4cd4-97a1-ab294094bce0" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/02180fa6-f95b-4563-9d5c-4ffda21fd0ca" width="600"/>

Open My Computer:

<img src="https://github.com/user-attachments/assets/469844d1-78a8-4aad-b51d-d9873cb2a0db" width="600"/>

Navigate to the `C:` Drive:

<img src="https://github.com/user-attachments/assets/2a785cdb-0ca7-4a26-afb0-98fbb2921a89" width="600"/>

Python 3.2 is installed in the `Python32` folder:

<img src="https://github.com/user-attachments/assets/2920a9f1-0710-4590-a8a3-8868e52b9552" width="600"/>

In this folder there is the `python.exe`:

<img src="https://github.com/user-attachments/assets/8fafd024-7661-4554-a876-a241e74ba1ad" width="600"/>

There is no `Scripts` folder or Python Package Manager `pip` in this version of Python. The `Lib` folder containns python's standard libraries:

<img src="https://github.com/user-attachments/assets/01ee99b7-ef54-4a76-aa27-16397fa1da4e" width="600"/>

In this folder is a subfolder called `site-packages`, where third-party libraries are installed:

<img src="https://github.com/user-attachments/assets/274b179f-c5bb-42ad-9e92-b6bf242c283d" width="600"/>

In the extracted folder `pyserial-3.0.1` (package), copy the `serial` folder (library):

<img src="https://github.com/user-attachments/assets/1665794b-b329-4723-ae6a-5f9f85399356" width="600"/>

And paste this to `site-packages`:

<img src="https://github.com/user-attachments/assets/59662f83-08c6-46dd-a733-25dfdc6cc84f" width="600"/>

For `pyserial`, there is the `pyserial` (package) folder and `serial` (library) folder. Normally the name of package and library are consistent however sometimes these differ as in the case of `pyserial`. Usually the differences are for historical reasons (for example a package being forked and the forked package being maintained and the original package being depreciated).

Python was not added to the path during installation, which means the full directory to the `python.exe` needs to be specified from the command prompt. To add to the path, right click Computer and select Properties:

<img src="https://github.com/user-attachments/assets/b98b3c31-94aa-4fd0-8b60-99f291485fb5" width="600"/>

Select the Advanced Tab and select Environmental Variables:

<img src="https://github.com/user-attachments/assets/60baf6f9-8659-4cb5-b552-7d3a017ea5c1" width="600"/>

Under System Variables select Path and Edit:

<img src="https://github.com/user-attachments/assets/8c695d07-316a-44f2-a548-9030b8f3fd27" width="600"/>

Append the value:

```
;C:\Python34\
```

<img src="https://github.com/user-attachments/assets/cef9fdca-2595-4a86-8924-55b54830830b" width="600"/>

For clarity my full path looks like the following. The semi-colon is a delimiter:

```
%SystemRoot%\system32;%SystemRoot%;%SystemRoot%\System32\Wbem;C:\Python32
```

Newer versions of Windows often display this in a list for convenience. Using a new line instead, this becomes:

```
%SystemRoot%\system32
%SystemRoot%
%SystemRoot%\System32\Wbem
C:\Python32\
```

The command prompt looks for a command in all of the directories listed in the path as well as the current working directory. 

Select OK:

<img src="https://github.com/user-attachments/assets/4544852b-8794-4d51-a6d2-7a534a8c88a0" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/5922381f-f01f-4097-9b9c-38fbf35156e6" width="600"/>

Select Start All Programs → Accessories → Command Prompt:

<img src="https://github.com/user-attachments/assets/b95729f6-99cb-422c-bcf5-c0188ae36d12" width="600"/>

If the following is input:

```powershell
python
```

Notice the Python program is found (which is in the folder `C:\Python32\` which is on the Windows path) and the prompt changes to the Python Prompt. The Python `print` function can be called, supplying a `str` as an input argument:

```python
print('Hello World!')
```

<img src="https://github.com/user-attachments/assets/b51475b2-f5cc-4d8b-bdc1-7016eda0dce3" width="600"/>

The library `serial` can be imported using:

```python
import serial
```

<img src="https://github.com/user-attachments/assets/296e56fa-1949-4023-9bc1-e3d3e35c319f" width="600"/>

To exit the Python program use the function call:

```python
exit()
```

<img src="https://github.com/user-attachments/assets/96313c86-f85f-46da-ab6e-78498af18149" width="600"/>

This exits the Python program and returns to the command prompt.

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

<img src="https://github.com/user-attachments/assets/5141a7c1-5976-46f6-b588-78f534f3bbf8" width="600"/>

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

