# Windows 10 Guest

Windows 10 Version 22H2 is the final build of Windows 10 and reached end of life in October 2025.

## Download Windows 10

### Windows 10 Builds

Windows 10 is a 10 year old series of Windows Operating System that had multiple versions. Initially each version was named YYMM corresponding to the year and month respectively however this gave the expectation for a build to be released to RTM on the Month. Often it was delayed slightly in order for Microsoft to improve stability and as a consequence they switched to the naming convention YYHX correponding to the year and year half respectively.

A major version is essentially a full OS swap refreshing the Windows Kernel, while the minor version builds on the previous versions Windows Kernel.

|Version|Date|Notes|Long Term|
|---|---|---|---|
|1507|Half 2 2015|Initial Release|LTSB|
|1511|Half 2 2015|Minor: Fixed Product Activation||
|1607|Half 2 2016|Major|LTSB|
|1703|Half 1 2017|Major||
|1709|Half 2 2017|Major: Best Performance on Old Hardware||
|1803|Half 1 2018|Major||
|1809|Half 2 2018|Major|LTSC|
|1903|Half 1 2019|Major||
|1909|Half 2 2019|Minor||
|2004|Half 1 2020|Major||
|20H2|Half 2 2020|Minor||
|21H1|Half 1 2021|Minor||
|21H2|Half 2 2021|Minor|LTSC|
|22H2|Half 2 2022|Major||

## Windows 10 Media Creation Tool

Microsoft used to host all the ISOs as direct download links however as Windows 10 approaches end of life many of the ISO download links are removed. The GitHub Repository Windows 10 Media Creation Tool.bat is a Universal Media Creation Tool wrapper script for all Windows 10/11 versions from 1507 to 21H2!

* [GitHub: Windows 10 Media Creation Tool.bat](https://github.com/AveYo/MediaCreationTool.bat)

<img src="https://github.com/user-attachments/assets/c1cdedfa-5868-44f8-9a32-b3e89a0e1947" width="300"/>

## WSUS Offline Update

WSUS Offline Update Community 12.6H6:

The WSUS Offline Update is a utility that can be used to download all the updates for a Windows Build and create an ISO which can be used for offline update. The Original Developer maintained the WSUS Offline Update project until April 2020, just after Windows 7 Reached End of Life. After April 2020 it was forked into a community version. The community version is better for Windows 10 Builds released post-2020 and the Long Term Support Build/Channel (LTSB/LTSC) Builds 1507/1607/1809/21H2.

<img src="https://github.com/user-attachments/assets/b9519a7c-4fa5-4de8-8475-d524f4f412b7" width="600"/>

* [WSUS Offline Update Community](https://gitlab.com/wsusoffline/wsusoffline/-/releases)

WSUS Offline Update 12.0:

<img src="https://github.com/user-attachments/assets/14fd73bc-c36b-46b3-b525-ac69e8b8f8e2" width="600"/>

* [WSUS Offline Update](https://download.wsusoffline.net/)






