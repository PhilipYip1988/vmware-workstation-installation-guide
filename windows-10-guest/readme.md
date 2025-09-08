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

## Windows 10 Media Creation Tool (All Builds)

Microsoft used to host all the ISOs as direct download links however as Windows 10 approaches end of life many of the ISO download links are removed. The GitHub Repository Windows 10 Media Creation Tool.bat is a Universal Media Creation Tool wrapper script for all Windows 10/11 versions from 1507 to 22H2!

* [GitHub: Windows 10 Media Creation Tool.bat](https://github.com/AveYo/MediaCreationTool.bat)
  * [GitHub: Windows 10 Media Creation Tool.bat lzw29107 fork](https://github.com/lzw29107/MediaCreationTool.bat)

Note Microsoft make frequent changes to the files used by the last version of the Windows 10 media Creation Tool and it takes time for developers to update the .bat file in the GitHub Repository. One of the forks maintained by lzw29107 is more up to date but in my testing didn't work with 22H2:

* [Windows 10 Media Creation Tool](https://www.microsoft.com/en-gb/software-download/windows10)

<img src="https://github.com/user-attachments/assets/c1cdedfa-5868-44f8-9a32-b3e89a0e1947" width="300"/>

In this example, I will use the Windows 10 Media Creation Tool to download Windows 10 (Version 1709). Go to the GitHub respository and select Code:

<img src="https://github.com/user-attachments/assets/f14aef6a-edc5-498a-826c-792d2ee9f451" width="600"/>

Then Download ZIP:

<img src="https://github.com/user-attachments/assets/9bc6b0fa-decd-440a-a806-b9d6e3f5355a" width="600"/>

Go to Downloads, right click the zip file and select Extract All:

<img src="https://github.com/user-attachments/assets/61bf7c75-79ac-47b3-bfcb-4a07ecfc7ad6" width="600"/>

Select Etract:

<img src="https://github.com/user-attachments/assets/e79c8c23-c3b3-4d25-ba44-0d4461a553c4" width="600"/>

Select the extracted folder:

<img src="https://github.com/user-attachments/assets/7e67b28b-afba-4090-b02c-466b9053f898" width="600"/>

Right click `MediaCreationTool.bat`:

<img src="https://github.com/user-attachments/assets/642bfe3a-b1d0-42b7-a937-84db590f00e9" width="600"/>

And select Open:

<img src="https://github.com/user-attachments/assets/85bf06f1-3b85-4522-b3ca-7a559e289a4a" width="600"/>

Select Run:

<img src="https://github.com/user-attachments/assets/0c1f8fa1-0361-4d85-bf1e-10277c02a499" width="600"/>

Select the Build, in this example 1709:

<img src="https://github.com/user-attachments/assets/5d7d840c-99ae-45f8-a87e-23754dc13f4a" width="600"/>

Then select, select:

<img src="https://github.com/user-attachments/assets/3c855bff-3965-4308-9de2-d6c09bf2edbf" width="600"/>

Details about the downloads will display:

<img src="https://github.com/user-attachments/assets/e569ef02-6501-4901-846b-5a8f80fa3f73" width="600"/>

The Media Creation Tool for that Build will display:

<img src="https://github.com/user-attachments/assets/8c0f68ec-3db8-4b09-9605-8d2e80ed58a1" width="600"/>

Select the Language, Edition and Architecture:

<img src="https://github.com/user-attachments/assets/5f0d6324-86ae-44de-8b94-30aedbf76154" width="600"/>

Select ISO file and next:

<img src="https://github.com/user-attachments/assets/951915ba-ae9b-4546-8263-b2ee750ea7ed" width="600"/>

Select the Downloads fodler and save the ISO:

<img src="https://github.com/user-attachments/assets/6ec06c7d-0ff4-4045-a038-b6e79c4257f8" width="600"/>

The Media Creation Tool will download the setup files and create the IISO as requested:

<img src="https://github.com/user-attachments/assets/eddaf210-b335-42aa-a534-6293fb3e3368" width="600"/>

## WSUS Offline Update

The WSUS Offline Update is a utility that can be used to download all the updates for a Windows Build and create an ISO which can be used for offline update. The Original Developer maintained the WSUS Offline Update project until April 2020, just after Windows 7 Reached End of Life. After April 2020 it was forked into a Community Edition. The Community Edition is better for Windows 10 Builds released post-2020 and the Long Term Support Build/Channel (LTSB/LTSC) Builds 1507/1607/1809/21H2.

WSUS Offline Update Community 12.6H6:

<img src="https://github.com/user-attachments/assets/b9519a7c-4fa5-4de8-8475-d524f4f412b7" width="600"/>

* [WSUS Offline Update Community](https://gitlab.com/wsusoffline/wsusoffline/-/releases)

WSUS Offline Update 12.0:

<img src="https://github.com/user-attachments/assets/14fd73bc-c36b-46b3-b525-ac69e8b8f8e2" width="600"/>

* [WSUS Offline Update](https://download.wsusoffline.net/)






