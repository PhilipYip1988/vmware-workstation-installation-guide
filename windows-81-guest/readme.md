# Notes

```
monitor.virtual_exec = "hardware"
mks.enableVulkanRenderer = "FALSE"
```

## Downloads

### Windows 8.1 ISO

The Website Archive.org hosts the ISO created from Microsoft before Microsoft removed Windows 8.1 downloads from their download servers. The ISO Checksums should match the ISOs I downloaded from Microsoft's servers before the downloads got removed:

|Language|Name|SHA256|Architecture|Editions|
|---|---|---|---|---|
|English (UK)|[Win8.1_EnglishInternational_x64](https://archive.org/details/win8.1x32x64)|DE3D15AFBDA350F77C27AAD76844477E396E947302D7402C09A16F3FA7254C68|64|Home<br>Pro|
|English (UK)|[Win8.1_EnglishInternational_x32](https://archive.org/details/win8.1x32x64)|777D22B51326697A8227741D4565AD5A52376BD295862C0DD96BA53E47514137|32|Home<br>Pro|
|English (UK)|[Win8.1_SingleLang_EnglishInternational_x64](https://archive.org/details/win8.1x32x64)|FCE8ECD85C4443521A2658421F6AD371255971632D7AD6CF935233D61B91588F|64|HomeSL|
|English (UK)|[Win8.1_SingleLang_EnglishInternational_x32](https://archive.org/details/win8.1x32x64)|2ECA572129838E29C60103B2800C3EA094478D272EC72D9AB1369788246655D0|32|HomeSL|
|English (UK)|Win8.1_Pro_N_EnglishInternational_x64|6676DC2301A8C5DFB046C33EB4D34DE29BA1E8193CB3259116247D35D56587B7|64|HomeN<br>ProN|
|English (UK)|Win8.1_Pro_N_EnglishInternational_x32|3EAB61937D6337FAA01925F0398279F9151D6C87EED58719156BAADCDA809902|32|HomeN<br>ProN|
|English (US)|[Win8.1_English_x64](https://archive.org/details/win-8.1-english-x-64\_20240121)|D8333CF427EB3318FF6AB755EB1DD9D433F0E2AE43745312C1CD23E83CA1CE51|64|Home<br>Pro|
|English (US)|Win8.1_English_x32|A569191631A41A260CD180B0D6B926CD2064235F0AC0E3E4CCC387F440E0827A|32|Home<br>Pro|
|English (US)|[Win8.1_SingleLang_English_x64](https://archive.org/details/win-8.1-single-lang-english-x-64\_202301)|28BB2FCF46DB2B8C31A0ADA8E405D71170EE3CBE5772FDD2DA64B6500BE93097|64|HomeSL|
|English (US)|[Win8.1_SingleLang_English_x32](https://archive.org/details/win-8.1-single-lang-english-x-32\_202301)|29B4AF02988EB768F2D01EC6991CAD84AD87B4453C0C7365160D36E95CC1C1CF |32|HomeSL|
|English (US)|Win8.1_Pro_N_English_x64|BCFAAFA3A370BEA1C3A9991784D1D2534B42F09AAE55AE7CAA59FBB0168324A1|64|HomeN<br>ProN|
|English (US)|Win8.1_Pro_N_English_x32|C4A4BA7FBC1928AF7A4C462CE40FFB481697EA37BD3C85C627600FE79B3EC902|32|HomeN<br>ProN|

### Generic Product Keys

Windows 8.1 can be installed on the Windows 8.1 VM using a generic product key. This gives a 30 day trial, after the 30 day trials, the Windows Desktop will be watermakred saying activate Windows.

|Edition|Generic Product Key|
|---|---|
|Windows 8.1 Home|334NH-RXG76-64THK-C7CKG-D3VPT|
|Windows 8.1 Home Single Language|Y9NXP-XT8MV-PT9TG-97CT3-9D6TC|
|Windows 8.1 Pro|XHQ8N-C3MCJ-RQXB6-WCHYG-C9WKB|
|Windows 8.1 Home N|6NPQ8-PK64X-W4WMM-MF84V-RGB89|
|Windows 8.1 Professional N|JRBBN-4Q997-H4RM2-H3B7W-Q68KC|
|Windows 8.1 Professional with Media Center|GBFNG-2X3TC-8R27F-RMKYB-JK7QT|

### WSUS Offline Update

The WSUS Offline Update still supports Windows 8.1:

* [WSUS Offline Update](https://download.wsusoffline.net/)

Download the most recent version:

<img src="https://github.com/user-attachments/assets/98096a2d-c2e6-4a3c-930c-2d2cc8d0214d" width="600"/>

Right click WSUS Offline 120:

<img src="https://github.com/user-attachments/assets/f05fcea4-bef6-4d41-9cdb-0487d7133133" width="600"/>

Select Extract All...:

<img src="https://github.com/user-attachments/assets/5221527c-cd34-454a-ab4f-1c3cbc428440" width="600"/>

Select Extract:

<img src="https://github.com/user-attachments/assets/d63b6d13-bce1-4f0b-a273-b25de25392e0" width="600"/>

Go to the `wsusoffline` folder:

<img src="https://github.com/user-attachments/assets/bb3aa358-5dfb-4cc7-828f-259ec73f9261" width="600"/>

Run `UpdateGenerator.exe`:

<img src="https://github.com/user-attachments/assets/7238080e-2def-4125-8438-a54245bf9489" width="600"/>

Uncheck all Windows 10 Versions:

<img src="https://github.com/user-attachments/assets/6a74f132-a4dc-4813-9b65-fa304e60d8a9" width="600"/>

Select Windows 8.1 x64 (64 Bit) or Windows 8.1 x86 (32 Bit). Under options select verify downloaded updates and include C++ Runtime Libraries and .NET Frrameworks. Under ISO image(s) select per selected produt and language/ Select Start:

<img src="https://github.com/user-attachments/assets/de0b3b61-a706-40b2-a212-4f693e429e76" width="600"/>

The updates will download:

<img src="https://github.com/user-attachments/assets/d10d7bd2-b3d1-4e7c-b6ff-59f4028905da" width="600"/>

And the ISO will be created:

<img src="https://github.com/user-attachments/assets/dfebf033-7f03-4e43-afca-4dbb0a494b0c" width="600"/>

It is found in the `iso` folder:

<img src="https://github.com/user-attachments/assets/acd2da1e-a11a-4394-b684-f593d6117c19" width="600"/>

## Configuring Virtual Hardware for a Windows 8.1 Guest

<img src="https://github.com/user-attachments/assets/c7d23c1c-78a6-4146-ac11-0f7cd72c77f6" width="600"/>

<img src="https://github.com/user-attachments/assets/19a2c964-1044-40c6-a2e3-d530c9eef01c" width="600" />


## Windows 8.1 Guest Virtual Machine Configuration File





### Modern Generation Processors (11-14th Generation)

Certain legacy settings may need to be configured to run older guest operating systems such as Windows 8.1:

## Installing the Windows 8.1 Guest OS

Select the Windows 8.1 Virtual Machine and select Play:


## Installing Windows 8.1 Updates

<img src="https://github.com/user-attachments/assets/b87027a4-0114-4742-834f-ba05f61978ee" width="600"/>
















Task Scheduler Library > Microsoft > Windows > Windows Activation Technologies

You’ll see tasks like ValidationTask or Notification.

Right-click → Properties → Triggers tab.

Either disable the triggers or change them to run once a month instead of daily/hourly.

Apply and close.

