RTL8111_driver_for_OS_X
=======================

OS X open source driver for the Realtek RTL8111/8168 family

*** Please note that this driver isn't maintained by Realtek! ***

Due to the lack of an OS X driver that makes use of the advanced features of the Realtek RTL81111/8168 series I started a new project with the aim to create a state of the art driver that gets the most out of those NICs which can be found on virtually any cheap board on the market today. Based on Realtek's Linux driver (version 8.035.0) I have written a driver that is optimized for performance while making efficient use of system resources and keeping the CPU usage down under heavy load.

Key Features of the Driver
- Supports Realtek RTL8111/8168 B/C/D/E/F/G found on recent boards.
- Support for multisegment packets relieving the network stack of unnecessary copy operations when assembling packets for transmission.
- No-copy receive and transmit. Only small packets are copied on reception because creating a copy is more efficient than allocating a new buffer.
TCP, UDP and IPv4 checksum offload (receive and transmit).
- TCP segmentation offload over IPv4 and IPv6.
- Support for TCP/IPv6 and UDP/IPv6 checksum offload.
- Fully optimized for Mountain Lion (64bit architecture) but should work with Lion too. Snow Leopard requies some changes.
- Supports Wake on LAN.
- Support for Energy Efficient Ethernet (EEE) which can be disabled by setting enableEEE to NO in the drivers Info.plist without rebuild. The default is YES.
- The driver is published under GPLv2.

Limitations
- As checksum offload doesn't work with jumbo frames they are currently unsupported and will probably never be.
- No support for 32bit kernels.

Installation

Before you install the driver you have to remove any installed driver for RTL8111/8168.

- Goto /S/L/E and delete the old driver (Lnx2mac, AppleRealtekRTL8169, etc.).
    
- Recreate the kernel cache.
    
- Open System Preferences and delete the corresponding network interface, e. g. en0. If you forget this step you might experience strange problems with certain Apple domains, iTunes and iCloud later.
    
- Reboot.
    
- Install the new driver and recreate the kernel cache.
    
- Reboot
    
- Open System Preferences again, select Network and check if the new network interface has been created automatically or create it manually now.
    
- Configure the interface.

- Install the prefpane

Current status

The driver has been successfully tested under 10.8.2 - 10.10.1 with the D (chipset 9), E (chipset 16) and F (chipset 17) versions of the RTL8111 and is known to work stable on these devices but you'll have to consider that there are 25 different revisions of the RTL8111. The RTL8111B/8168B chips have been reported to work since version 1.0.2 too.

Changelog

- Version 1.4.0 (2018-09-28)
    - Added macOS 10.13 compatibility

Known Issues
- There are still performance problems with regard to SMB in certain configurations. My tests indicate that Apple's Broadcom driver shows the same behavior with those configurations. Obviously it's a more general problem that is not limited to my driver.
- WoL refuses to work on some machines.

