# VMware Workstation 

Step-by-step guides for VMware Workstation 17.6.4, focused on running Legacy Windows versions (Windows 98SE, Windows 2000, Windows XP, Windows Vista, Windows 7, Windows 8.1) in virtual environments. Learn to enable shared folders, USB passthrough and serial port passthrough to control legacy scientific instruments and laboratory hardware, making older software and devices compatible with modern systems. Ideal for university researchers, lab technicians, and IT staff supporting legacy lab equipment.

## Host Setup

This guide looks at the setup of VMWare Workstation on Windows and Ubuntu and creating a Virtual Machine of a supported version of Windows or Ubuntu:

* [Windows Host](./windows-host/readme.md)
* [Ubuntu Host](./ubuntu-host/readme.md)

## Legacy Windows Guest Virtual Machines

Virtual Machines are often used to continue to run bespoke legacy software for a USB or Serial Port peripheral device manufactured by a vendor that is out of business or has been made obsolete by the manufacturer and does not have updated drivers or software. This is important when the Original Host Device has failed for example due to a faulty power supply, failed hard drive or failed memory module and cannot be repaired or replaced with new parts. 

A Virtual Machine Guest of the Expected Legacy Versions of Windows Version can be created and the USB or Serial Port Device can be connected to the Virtual Machine. The Drivers and the Software used for the USB or Serial Port Device can be installed in the Virtual Machine.

In the 2000s, Windows Vista was released, representing a significant upgrade over Windows XP. However, most drivers at the time were designed for Windows XP and often ran unstably on Windows Vista. Additionally, the official minimum system requirements for Windwos Vista were understated and contributed to poor performance on hardware available at its time of release. Although Windows Vista received numerous patches, it is often regarded as a beta version of Windows 7, which became widely recognized for its stability. Windows 8.x built upon Windows 7 but also introduced the unpopular Metro interface, which was removed in Windows 10. As a consequence only Windows 7 and Windows 10 are commonly virtualised. Windows 10 had numerous builds, and its system requirements were elevated after Version 1709. Despite not being a Long Term Support build, Version 1709 is regarded as one of the most stable and is frequently used for virtualizing legacy hardware. The final build Windows 10 Version 22H2 is also commonly virtualised. All these Windows Versions had 32 Bit and 64 Bit Variants with the 64 Bit Variant being standard.

|NT (Modern Unified Line)|
|---|
|[**Windows 10 (1709) Guest**](./windows-1709-guest/readme.md)|
|[Windows 8.1 Guest](./windows-81-guest/readme.md)|
|[**Windows 7 Guest**](./windows-7-guest/readme.md)|
|[Windows Vista Guest](./windows-vista-guest/readme.md)|

In the 1990s, Windows operating systems were divided into two main branches. The NT branch targeted business and enterprise users, while the 9x branch was aimed at consumers. The consumer-focused 9x systems were DOS-based, offering greater flexibility with hardware and driver support. In contrast, the NT branch was built from the ground up for specialized hardware, such as workstations and servers, emphasizing stability and security. Because of this, NT did not support typical consumer PCs or standard consumer hardware and drivers. Windows 2000 extended NT’s capabilities to include broader support for consumer devices, and eventually the two branches merged with the release of Windows XP. This unified NT architecture combined the stability of the business-oriented systems with the wide driver compatibility of the consumer line.

As a result, the NT operating systems most commonly virtualised are Windows 2000 and Windows XP. Within the Windows 9x line, Windows 98 SE is the most frequently virtualised, since its successor, Windows ME, was short-lived and widely regarded as unstable. The earlier Windows 95, released before the internet era, received limited updates and patches, making it less commonly used in virtual environments.

|NT (Business Branch)|9x (Consumer Branch)|
|---|---|
|[**Windows XP Guest**](./windows-xp-guest/readme.md)|↖|
|[**Windows 2000 Guest**](./windows-2000-guest/readme.md)|[Windows ME Guest](./windows-me-guest/readme.md)|
|~~Windows NT 4.0~~|[**Windows 98SE Guest**](./windows-98SE-guest/readme.md)|
|~~Windows NT 3.x~~|[Windows 95 Guest](./windows-95-guest/readme.md)||

Windows 1.0 through 3.1 were early 16-bit operating systems with very limited virtualisation support. They supported only a narrow range of hardware, and only a small number of DOS applications could run on them. Most of these DOS applications, however, are compatible with Windows 98 SE, which is generally preferred for virtualisation. Additionally, VMware Tools is available only as a 32-bit or 64-bit application, and no 16-bit version was ever created for these early Windows releases. Installing these even on virtual hardware is moderately difficult and there is a limited advantage in doing so because device passthrough is also limited. The [PCjs Explorer](https://www.pcjs.org/software/pcx86/) emulates most of these OS in emulated Legacy PCs within the browser.

|3.x (Early Line)|
|---|
|~~Windows 3.1~~|
|~~Windows 2.0~~|
|~~Windows 1.0~~|
