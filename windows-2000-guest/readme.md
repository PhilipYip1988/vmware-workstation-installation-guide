# Windows 2000

```
monitor.virtual_exec = "hardware"
monitor.virtual_mmu = "software"
mks.enableVulkanRenderer = "FALSE"
cpuid.0.eax = "0000000X"
cpuid.1.ecx = "00000001"
```

## Windows 2000 ISO

Windows 2000 is considered abandonware and the Windows 2000 ISO and Product Key can be obtained from WinWorld:

* [WinWorld](https://winworldpc.com/library/operating-systems)

## Windows 2000 SP4

* [Windows 2000 SP4](https://winworldpc.com/download/41c38361-6518-c39a-11c3-a4e284a2c3a5)

## WSUS Offline Update

The last version of WSUS Offline Update to support Windows 2000:

* ~~[WSUS Offline Update](https://download.wsusoffline.net/)~~

This no longer works as Microsoft removed the downloads WSUS Offline updates uses from their servers.

<details>
  <summary>Archive.org</summary>

The Website Archive.org appears to host the ISO created from WSUS Offline Update before Microsoft removed Windows Vista downloads from their download servers:

* [WSUS Offline Update Windows 2000](https://archive.org/details/wsusoffline-w2k-enu)

</details>

## VMware Tools ISO

The Windows 2000 drivers for the Windows 2000 Guest are contained in the VMware Tools Installation ISO. The Website Archive.org appears to host the ISO created by VMware before Broadcom removed it:

* [VMware Tools 6.5.5](https://archive.org/details/vmware-tools-collectio](https://archive.org/details/vmware-tools-collection)

## Configuring Virtual Hardware for a Windows 2000 Guest

Select Player → File → New Virtual machine...

<img src="https://github.com/user-attachments/assets/40c10c2a-d4ad-401d-8cfe-2e609e30725c" width="600"/>

Select I will install this operating system later and then next:

<img src="https://github.com/user-attachments/assets/580444bd-cb3d-41a2-8fad-3e434c248bab" width="600"/>

Select Windows 2000 Professional and then next:

<img src="https://github.com/user-attachments/assets/15133c99-2dba-4ef2-87d8-e319a19e1f03" width="600"/>

Use the default Virtual Machine Name and Location (if Documents is integrated with OneDrive. you may want to move this to a loal only location) and select next:

<img src="https://github.com/user-attachments/assets/d1b95fda-74a1-4730-a05d-5ef8b1159ab0" width="600"/>

Select 20 GB and select enxt:

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

### 12th-14 Generation Processors

On a 12th–14th Generation Intel processor, certain legacy settings may need to be configured to run older guest operating systems such as Windows 2000.

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

Select the Windows 98 Guest and select Play:

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

## Installing Windows 2000 SP4

Service Pack 4 is a prequisite for installing VMware tools. Since VMware tools are not installed drag and drop to the virtual machine won't work and the Windows application has to be supplied as part of an ISO file. The Service Pack 4 is a `.7z` archive. Extract the `.7z` archive:

<img src="https://github.com/user-attachments/assets/ac4403e1-d3c6-4e16-a62f-bd8a555778bf" width="600"/>

<img src="https://github.com/user-attachments/assets/07618f5c-8dc6-4cad-b591-8bcf33feebd0" width="600"/>

To get to the `.exe`:

<img src="https://github.com/user-attachments/assets/80f23711-8063-464d-ad2a-8cd67440b7ea" width="600"/>

Launch ImgBurn and select Create Image file from File/Folders:

<img src="https://github.com/user-attachments/assets/d096aaee-4355-4fae-b98a-bc09bdd0d9df" width="600"/>

Select the folder icon:

<img src="https://github.com/user-attachments/assets/311fc8b0-7d7b-462e-b387-86f37565a924" width="600"/>

Select the Windows 2000 Service Pack 4 folder and select, select folder:

<img src="https://github.com/user-attachments/assets/504308fc-b2cc-4ee2-8cc0-9034b07a6838" width="600"/>

Select the destination folder:

<img src="https://github.com/user-attachments/assets/8f68e921-cb0f-493c-b018-1a9340ca4448" width="600"/>

And save the ISO to downloads:

<img src="https://github.com/user-attachments/assets/389571ef-a9c7-4e80-96cb-c61d161705c7" width="600"/>

Select the File/Folders to Image button:

<img src="https://github.com/user-attachments/assets/301d6eda-7e9b-47ee-a77c-35b534a041fe" width="600"/>

Select yes:

<img src="https://github.com/user-attachments/assets/bbfaf87b-cf83-4366-9851-01f7ebba9f5e" width="300"/>

Select yes:

<img src="https://github.com/user-attachments/assets/85b1f66e-8ea0-4995-b3b2-151120ba699e" width="300"/>

Select ok:

<img src="https://github.com/user-attachments/assets/b7161ca3-7d92-498e-86ff-ea8ee7d9fafe" width="300"/>

Select ok:

<img src="https://github.com/user-attachments/assets/c40f454c-44db-4c63-976c-286cacdc4fed" width="300"/>

In the Windows 2000 VM. Select Player → Removable Drives → CD/DVD and then settings:

<img src="https://github.com/user-attachments/assets/cccdc86b-9153-4571-8c36-0a8e50a901ce" width="600"/>

Select Browse:

<img src="https://github.com/user-attachments/assets/af70e675-9261-40c2-b981-272a55ea7b87" width="600"/>

Select the Windows 2000 SP4 ISO:

<img src="https://github.com/user-attachments/assets/67e0a69d-1bef-4f37-880c-e825ddc18c55" width="600"/>

Select OK:

<img src="https://github.com/user-attachments/assets/8fbefd1d-a416-424e-a230-af257fa8d6d8" width="600"/>

Open My Computer and select the CD/DVD:

<img src="https://github.com/user-attachments/assets/4eb06676-0521-4832-874c-5770074c5d77" width="600"/>

Launch the application to install the Service Pack:

<img src="https://github.com/user-attachments/assets/89fa3e49-5248-4647-8e53-7e3740d79b74" width="600"/>

<img src="https://github.com/user-attachments/assets/f9ed24f6-c104-47c2-8628-58f4690a1338" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/e9431064-11ea-4a79-af4b-7325b53088c4" width="600"/>

Select I agree and next:

<img src="https://github.com/user-attachments/assets/b13d10be-d781-4793-a208-bcd4c94abceb" width="600"/>

Select next:

<img src="https://github.com/user-attachments/assets/12ae3611-8742-4035-93a2-1489ebbbc317" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/688544fa-bb0a-48db-81c6-af4f70e7c856" width="600"/>

## Install Windows 2000 SP4 Updates


















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

<img src="https://github.com/user-attachments/assets/bdcb2756-4db9-4d7b-9f48-7a48d75d24f1" width="600"/>

Select enxt:

<img src="https://github.com/user-attachments/assets/4b20cddb-121e-4566-a910-2aff5028ec59" width="600"/>

Select typical and next:

<img src="https://github.com/user-attachments/assets/65977ac1-3028-46a7-81bb-2ff9d7d4c093" width="600"/>

Select Install:

<img src="https://github.com/user-attachments/assets/026e55d1-6790-4c94-9dd6-e22b495e91dd" width="600"/>

Select Finish:

<img src="https://github.com/user-attachments/assets/c6e5fefb-92aa-437c-a1ec-4a76722151d6" width="600"/>

Select Yes to restart the VM:

<img src="https://github.com/user-attachments/assets/6795fdd8-f14e-4337-b1d6-6b9c6f5c2cbc" width="600"/>



















## Other Check

Install the 2005 and 2008:

* [Microsoft Visual C++ Redistributable](https://archive.org/details/microsoftvisualcredistributable_202004)

Install:

* [Microsoft .NET Framework Version 2.0](https://archive.org/details/dotnetfx2_202301)

Install:

* [Direct X 9.0C](https://archive.org/details/directx9-dec2006-redist)

Additional Windows 98 software can be found in:

* [Retro PC installation files](https://startup.retropc.se/win2k.html)



