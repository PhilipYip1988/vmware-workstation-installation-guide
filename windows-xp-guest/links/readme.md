### Windows XP Windows Volume License Installation ISO

The Windows XP Professional SP3 Volume License ISO and associated Product Key is not yet available to download on WinWorld:

* [WinWorld Placeholder: Windows XP ISO and Product Key](https://winworldpc.com/product/windows-xp/final) 

Which otherwise lists abandoned Windows Versions from Windows 1 through to Windows ME.

The Windows XP Professional SP3 Volume License ISO was sold to large organisations such as Universities, Governments and Enterprise companies and is preferred for a Windows XP Professional Virtual Machine as it activates offline and does not have the hassles of Microsoft Product Activation.

<details>
  <summary>Unofficial Download Links (Untested)</summary>

Unofficially a copy of the Volume License ISO appears to be listed here:

* [Archive Org Microsoft Windows XP SP3 Reinstallation ISO](https://archive.org/details/win-xp-pro-sp-3-x-86)

Unofficially Volume License Keys are listed on this GitHub repository:

* [GitHub: Windows XP All Keys Universal Product Key Collection All Keys](https://github.com/Fuwn/xp)

</details>

### Dell Windows XP OEM Reinstallation ISO

The Dell Windows XP Professional SP3 Reinstallation ISO and associated Product Key is not yet available to download on WinWorld:

* [WinWorld Placeholder: Windows XP ISO and Product Key](https://winworldpc.com/product/windows-xp/final) 

The Dell Windows XP Reinstallation CD/DVD was fairly common and an ISO can be created by converting the Windows XP Reinstallation CD/DVD to an ISO using ImgBurn.

OEM SLP activation is not carried out by default when using a Windows XP Virtual Machine as the Virtual Machine lacks the SLIC 1.0, SLIC 2.0 (Windows Vista Business Edition to Windows XP Professional Downgrade Rights) or SLIC 2.1 (Windows 7 Professional Downgrade Rights to Windows XP Professional Downgrade Rights) in the Virtual BIOS by default. This will result in a 30 Day Trial:

<details>
  <summary>30 Day Trial...</summary>

Windows XP has an initial 30 day grace period. After this grace period you are forcefully logged out and can only login to activate.

Details about the days remaining in grace period can be seen when going to Start and selecting run and then inputting:

```
%systemroot%\system32\oobe\msoobe.exe /a
```

The windows product activation timer can be reset four times by opening the registry editor and navigating to:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WPAEvents
```

and then changing the `OOBETimer` value from `FF` to `00` and then rebooting. 

Once again go to Start and select run and then input:

```
%systemroot%\system32\oobe\msoobe.exe /a
```

Select Activate by Telephone, then back and remind me later. Restart Windows XP. Go to Start and select run and then input:

```
rundll32.exe syssetup,SetupOobeBnk
```

</details>

<details>
  <summary>Unofficial Links (Untested)</summary>

Unofficially a copy of the Dell Windows XP SP3 Reinstallation ISO appears to be listed here:

* [Archive Org Dell Windows XP SP3 Professional Reinstallation ISO](https://archive.org/details/dell.-xp-pro-sp-3)
* [Archive Org Dell Windows XP SP2 Home Reinstallation ISO](https://archive.org/details/dell-xp-home-sp-2)
* [Archive Org Dell Windows XP SP2 Media Center Reinstallation ISO](https://archive.org/details/xp-mce-sp-2)

</details>

### Windows XP Full Retail ISO

Windows XP had Retail and Retail Upgrade Licenses and the Product Keys for these Licenses are incompatible with each others installation media and incompatible with the Volume License and OEM installation media. Only the Retain Full Licenses can be used in a Virtual Machine as upgrading a Windows 2000 Virtual Machine to Windows XP is not supported and will not work properly:

The Windows XP Professional or Home SP3 Retail License ISO and associated Product Key is not yet available to download on WinWorld:

* [WinWorld Placeholder: Windows XP ISO and Product Key](https://winworldpc.com/product/windows-xp/final) 

Which otherwise lists abandoned Windows Versions from Windows 1 through to Windows ME.

<details>
  <summary>Retail Licenses</summary>

The Full Retail License for Windows XP Home or Professional is the correct license for a Virtual Machine however:

* Online product activation for Windows XP Professional using a Retail Product key cannot be carried out because Microsoft have decommissioned the Product Activation servers and Windows XP Professional Retail Product Keys can therefore no longer be used to activate Windows XP.

* Phone product activation to an automated line for Windows XP using a Retail Product key may still work. You are unlikely to be passed through to a Microsoft employee if the automated process does not work because the product has passed end of life and is no longer supported. You may have issues transferring your Windows XP Retail License from one Virtual Machine to another.

</details>

<details>
  <summary>Unofficial Links (Untested)</summary>

Unofficially a copy of the Windows XP Retail SP3 Installation ISO appears to be listed here:

* [Archive Org Windows XP SP3 Retail Full Installation ISO](https://archive.org/details/5.1.2600.5512.xpsp.-080413-2111-x-86fre-client-professional-retail-en-us-grtmpfpp-en

</details>

### Windows XP Mode

The mouse in the Windows XP Mode VM cannot be used in VMware and installation of VMware tools gives a black screen resulting in poor performance:

<details>
  <summary>Windows XP Mode</summary>

Windows XP Mode can be downloaded from:

* [Windows XP Mode](https://download.cnet.com/windows-xp-mode/3000-18513_4-77683344.html)

A VM can be created from this by renaming the file `WindowsXPMode_en-us.exe` to `WindowsXPMode_en-us.zip`. Then extracting the zip file and going to the sources folder. Then renaming the `xpm` to `xpm.zip` and renaming the `VirtualXPVHD` to `VirtualXP.VHD`. The `VirtualXP.VHD` can be used as a Virtual Drive in VMware Workstation Player but results in a VM where the mouse doesn't work. Installation of VMware tools gives a black screen.

</details>

