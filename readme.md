# VMware Workstation 

Step-by-step guides for VMware Workstation 17.6.4, focused on running Legacy Windows versions (Windows 98SE, Windows 2000, Windows XP, Windows Vista, Windows 7, Windows 8.1) in virtual environments. Learn to enable shared folders, USB passthrough and serial port passthrough to control legacy scientific instruments and laboratory hardware, making older software and devices compatible with modern systems. Ideal for university researchers, lab technicians, and IT staff supporting legacy lab equipment.

## Host Setup

This guide looks at the setup of VMWare Workstation on Windows and Ubuntu and creating a Virtual Machine of a supported version of Windows or Ubuntu:

* [Windows Host](./windows-host/readme.md)
* [Ubuntu Host](./ubuntu-host/readme.md)

## Legacy Windows Guest Virtual Machines

Virtual Machines are often used to continue to run bespoke legacy software for a USB or Serial Port peripheral device manufactured by a vendor that is out of business or has been made obsolete by the manufacturer and does not have updated drivers or software. This is important when the Original Host Device has failed for example due to a faulty power supply, failed hard drive or failed memory module and cannot be repaired or replaced with new parts. 

A Virtual Machine Guest of the Expected Legacy Versions of Windows Version can be created and the USB or Serial Port Device can be connected to the Virtual Machine. The Drivers and the Software used for the USB or Serial Port Device can be installed in the Virtual Machine.

|NT (Modern Unified Line)|
|---|
|**[Windows 10 (1709) Guest](./windows-1709-guest/readme.md)**|
|[Windows 8.1 Guest](./windows-81-guest/readme.md)|
|**[Windows 7 Guest](./windows-7-guest/readme.md)**|
|[Windows Vista Guest](./windows-vista-guest/readme.md)|

In the 1990s, there were two main branches of Windows operating systems. The NT branch targeted business and enterprise users, while the 9x branch was aimed at consumers. The consumer branch was DOS-based and generally offered more flexibility with hardware and driver support. The two branches eventually merged with the release of Windows XP, unifying business and consumer editions under the NT architecture:

|NT (Business Branch)|9x (Consumer Branch)|
|---|---|
|**[Windows XP Guest](./windows-xp-guest/readme.md)**|↖|
|**[Windows 2000 Guest](./windows-2000-guest/readme.md)**|[Windows ME Guest](./windows-me-guest/readme.md)|
|Windows NT 4.0|**[Windows 98SE Guest](./windows-98SE-guest/readme.md)**|
|Windows NT 3.x|[Windows 95 Guest](./windows-95-guest/readme.md)||

Windows 1 to 3.1 were early operating systems that were 16-bit only and offered very limited support for virtualisation. These Operating Systems had very limited hardware support. In addition VMware Tools is a 32-bit or 64-bit application and no 16 Bit version was created for these early Windows versions:

|3.x (Early Line)|
|---|
|Windows 3.1|
|Windows 2.0|
|Windows 1.0|
