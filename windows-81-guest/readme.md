

## Downloads

### Windows 8.1 ISO Checksums

The Website Archive.org hosts the ISO created from Microsoft before Microsoft removed Windows 8.1 downloads from their download servers. The ISO Checksums are from the ISOs I downloaded from Microsoft's servers before the downloads got removed. I've not checked all the downloads on Archive.org but they should match these:

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












Task Scheduler Library > Microsoft > Windows > Windows Activation Technologies

You’ll see tasks like ValidationTask or Notification.

Right-click → Properties → Triggers tab.

Either disable the triggers or change them to run once a month instead of daily/hourly.

Apply and close.

