# Windows ISO Download Tool

## Download the Windows ISO Download Tool:

The Windows ISO Download Tool is an Unofficial Windows Application that lists ISO Downloads from Dell and Microsoft Servers. Microsoft recently removed Windows 7, Windows 8.1 and older builds of Windows 10 from their servers so only the Dell section works however these ISO images can be used for a VM.

The Windows Application cannot natively be run on Linux by default:

* [Windows ISO Download Tool](https://www.heidoc.net/joomla/technology-science/microsoft/67-microsoft-windows-and-office-iso-download-tool)

## Wine

Open up the Terminal to add the 32 Bit architecture input:

```bash
sudo dpkg --add-architecture i386
```

The following will display Note that `sudo` means super user do and an authentication prompt will display:

To create the directory `keyrings` use:

```bash
sudo mkdir -pm755 /etc/apt/keyrings
```

Note that this is a system wide directory found under `/etc/apt`. Because this is a system wide directory `sudo` is required to run the command make directory `mkdir`. `-p` is an instruction to create the parent directories if required. `-m755` sets permissions `7` (read, write, and execute for the duper user), `5` (read and execute for the group of the user), `5` (read and execute for others).

Change the directory to Downloads:

```bash
cd ~/Downloads
```

The wine repository key can be added to this keyring:

```bash
sudo wget "https://dl.winehq.org/wine-builds/winehq.key" -O /etc/apt/keyrings/winehq-archive.key
```

`wget` is a command line tool which is used to download a file from a URL. `-O` is an instruction to output the key to the file `/etc/apt/keyrings/winehq-archive.key`. 

wine has Ubuntu version specific repositories. To check the Ubuntu version use:

```bash
cat /etc/os-release
```

The terminal will display the `UBUNTU_CODENAME` in this case is `noble` (Ubuntu 24.04 LTS).

Add only the repository which matches the `UBUNTU_CODENAME`:

<details>
<summary>Ubuntu 24.04 VERSION_CODENAME=noble</summary>

```bash
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/noble/winehq-noble.sources
```

</details>


<details>
<summary>Ubuntu 24.10 VERSION_CODENAME=oracular</summary>

```bash
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/oracular/winehq-oracular.sources
```

</details>

To update the repositories used by `apt` use:

```bash
sudo apt update
```

To install wine use:

```bash
sudo apt install wine wine32 wine64 libwine fonts-wine winetricks playonlinux
```

The package `wine` allows Windows applications to run on Ubuntu. `wine32` allows Windows 32 Bit applications to run on 64 Bit Ubuntu. `wine64` allows Windows 64 Bit applications to run on 64 Bit Ubuntu.

The package `libwine` is a core dependency of `wine`. The package `fonts-wine` is required for proper font rendering.

`wine-mono` is a .NET Framework replacement for wine:

```bash
wget "https://dl.winehq.org/wine/wine-mono/9.4.0/wine-mono-9.4.0-x86.msi"
```

```bash
wine start wine-mono-9.4.0-x86.msi
```

`wine-gecko` is a replacement for Internet Explorer for wine:

```bash
wget "https://dl.winehq.org/wine/wine-gecko/2.47.4/wine-gecko-2.47.4-x86_64.msi"
```

```bash
wine start wine-gecko-2.47.4-x86_64.msi
```

## Windows ISO Download Tool

To download the Windows ISO Tool use:


```bash
wget "https://www.heidoc.net/php/Windows-ISO-Downloader.exe"
```

To launch it using wine use:

```bash
wine start Windows-ISO-Downloader.exe
```

Microsoft recently removed Windows 7, Windows 8.1 and older builds of Windows 10 from their servers so only the Dell section works. Although Dell lists their downloads as model specific, the ISO images do not have Dell driver packs installed and are generic. 

## Dell Windows 7

### GDXKK_X8V66A00_W7SP1PRO64_ROW.iso

Select the OptiPlex 7040:

* `GDXKK_X8V66A00_W7SP1PRO64_ROW.iso`

This is a multi-lingual, multi-edition ISO containing:

* Windows 7 Home Basic 64 Bit 2011
* Windows 7 Home Premium 64 Bit 2011
* Windows 7 Professional 64 Bit 2016
* Windows 7 Ultimate 64 Bit

By default this ISO has an `EI.cfg` in the `sources` folder locking the edition to Windows 7 Pro. `sources/$OEM$/$$/setup/scripts` has a `slp.cmd` that inputs the generic Dell Windows 7 Pro OEM SLP key:

```
cscript %windir%\system32\slmgr.vbs -ilc %windir%\system32\oem\OEM.xrm-ms
cscript %windir%\system32\slmgr.vbs -ipk 32KD2-K9CTF-M3DJT-4J3WC-733WD
```

|Edition|OEM SLP Key|
|---|---|
|Windows 7 Pro|`32KD2-K9CTF-M3DJT-4J3WC-733WD`|

OEM will fail unless the Virtual Machine has a SLIC 2.1.

### Easy Install

When easy install is used to install Windows 7, it ignores the OEM customisation and overrides the choice in the `ei.cfg`. The generic keys can be used to install but not activate Windows 7:

|Edition|Generic Key|
|---|---|
|Windows 7 Professional|`HYF8J-CVRMY-CM74G-RPHKF-PW487`|
|Windows 7 Starter|`7Q28W-FT9PC-CMMYT-WHMY2-89M6G`|
|Windows 7 Home Basic|`YGFVB-QTFXQ-3H233-PTWTJ-YRYRV`|
|Windows 7 Home Premium|`RHPQ2-RMFJH-74XYM-BH4JX-XM76F`|
|Windows 7 Ultimate|`D4F6K-QK3RD-TMVMJ-BBMRX-3MBMV`|
|Windows 7 Enterprise|`H7X92-3VPBB-Q799D-Y6JJ3-86WC6`|

### Rearm

Windows 7 will install licensed with a 30 day grace period. To see the remaining time search for CMD in the Start menu, right click it and select Run as Administrator:

```powershell
slmgr /dlv
```

Windows 7 can be rearmed allowing an additional 180 days:

```powershell
slmgr /rearm
```

### OEM Downgrade Rights

6th-8th Generation PCs shipped with Windows 10 Pro with Downgrade rights to Windows 7 Pro have a SLIC 2.1 which can be passed through to the VM. These are the only PCs with an OEM License powerful enough to run a Ubuntu 24.04 Host and Windows 7 Guest.

To check if the host PC has a SLIC input:

```bash
cd /sys/firmware/acpi/tables/
```

Then:

```bash
dir
```

SLIC will be listed in the output if the Host PC has a SLIC.

In files navigate to the `Home` folder and select the `vmware` folder. Select the `Windows 7 x64` subfolder for the Windows 7 Guest. Open `Windows 7 x64.vmx` in notepad and add the lines:

```
acpi.passthru.slic = "TRUE"
acpi.passthru.slicvendor = "TRUE"
SMBIOS.reflecthost = "TRUE"
```

In the Windows 7 Guest mount the ISO and navigate to `sources/$OEM$/$$/system32/OEM`. Copy the `OEM-xrm.ms` file to `C:\`:

```

```

## Dell Windows 8.1

### 9MW1YA00_W81x64ROW(DL).iso

Select the OptiPlex 7040:

* `9MW1YA00_W81x64ROW(DL).iso`

For Windows 8.1, for example, select the OptiPlex 7020:

|Edition|Generic Key|
|---|---|
|Windows 8.1 Pro|`XHQ8N-C3MCJ-RQXB6-WCHYG-C9WKB`|
|Windows 8.1 Home|`334NH-RXG76-64THK-C7CKG-D3VPT`|

## Dell Windows 10