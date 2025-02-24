Variety of Hardware parts in Machines are found and the role of The Operating system is to support all those hardware.

Configuration utility such as bios and uefi are offered by systems to manage the firmwares

UEFI has more sophisticated features for identification, testing, configuration and firmware
upgrades

### Device Activation

Config utility-BIOS is activated by pressing  Del, F2, F12, etc. 

It is possible to enable or disable integrated peripherals, activate basic error protection and change hardware settings like Interrupt Request and DMA.

Though doing changes in these things are mostly not required on modern machines, some specific issues might require doing it.

eg. There are RAM technologies capable of faster data transfer rates than default values and this can be changed according to the values specified by manufacturer. 

Some CPUs offers features that may not be necessary for the particular installation and they can be disabled to improve system security and reduce power consumption

### Device Inspection on Linux

If devices are identified, The OS shd associate corresponding software components. 

When an hardware feature is not working properly, 
- ##### Case 1 - Hardware not detected by OS:
			In this case, the issue is probably in the part or the port to which it is connected
- ##### Case 2 - Hardware detected but not working:
			problem form the OS Side

### Hardware Identification

Two ways for detection:
- Special commands
- Read specific files inside special filesystem

##### Commands for Inspection

- lspci
	 Shows all devices connected to the PCI (Peripheral Component Interconnect) bus.
	 eg:
	 - GPU
	 - Wifi / Ethernet adaptor
	 - Audi devices
	 - Storage devices - Nvme
- lsusb
	Shows all the USB devices. eg:
	- Mouse
	- Keyboards
	- Removable storage device

The system is not fully operational yet as every hardware parts identified above rquires a software component to control the corresponding device. 
This software component is called as **Kernel Module / Drivers** which can be a part of the **Official Linux kernel** or can be added separately from other sources.

Drivers for linux are not always supplied by the device's manufacturer. Only few provide their own binary drivers and majority of drivers are written by independent developers. 

Parts that work on windows may not have the drivers for linux . But at present, linux based OS has strong hardware support 

#### Kernel Module and Kernel Driver

**Kernel module is like a plugin or toolkit which has the tools required by the kernel to support specific hardware or its features.** 

**Kernel Driver uses the tools available in the module to operate a specific device. The Driver directly interacts with the hardware**

***The `nvidia` driver uses the NVIDIA module to communicate with the GPU.***

![[Pasted image 20241205123421.png]]

