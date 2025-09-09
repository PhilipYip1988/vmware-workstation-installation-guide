# VMware Workstation 

Step-by-step guides for VMware Workstation 17.6.4, focused on running Legacy Windows versions (Windows 98SE, Windows 2000, Windows XP, Windows Vista, Windows 7, Windows 8.1) in virtual environments. Learn to enable shared folders, USB passthrough and serial port passthrough to control legacy scientific instruments and laboratory hardware, making older software and devices compatible with modern systems. Ideal for university researchers, lab technicians, and IT staff supporting legacy lab equipment.

## Host Setup

This guide looks at the setup of VMWare Workstation on Windows and Ubuntu and creating a Virtual Machine of a supported version of Windows or Ubuntu:

* [Windows Host](./windows-host/readme.md)
* [Ubuntu Host](./ubuntu-host/readme.md)

## Legacy Windows Guest Virtual Machines

Virtual Machines are often used to continue to run bespoke legacy software for a USB or Serial Port peripheral device manufactured by a vendor that is out of business or has been made obsolete by the manufacturer and does not have updated drivers or software. This is important when the Original Host Device has failed for example due to a faulty power supply, failed hard drive or failed memory module and cannot be repaired or replaced with new parts. 

A Virtual Machine Guest of the Expected Legacy Versions of Windows Version can be created and the USB or Serial Port Device can be connected to the Virtual Machine. The Drivers and the Software used for the USB or Serial Port Device can be installed in the Virtual Machine.

* [Windows 10 Guest](./windows-10-guest/readme.md)
* [Windows 10 (1709) Guest](./windows-1709-guest/readme.md)
* [Windows 8.1 Guest](./windows-81-guest/readme.md)
* [Windows 7 Guest](./windows-7-guest/readme.md)
* [Windows Vista Guest](./windows-vista-guest/readme.md)
* [Windows XP Guest](./windows-xp-guest/readme.md)
* [Windows 2000 Guest](./windows-2000-guest/readme.md)
* [Windows 98SE Guest](./windows-98SE-guest/readme.md)
