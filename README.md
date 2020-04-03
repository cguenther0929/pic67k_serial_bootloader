# PIC 67K Serial Bootloader
This is a serial bootloader, originally written for the **PIC18F66K22** MCU, but adapted for the **PIC18F67K22**.  It's quite possible that the PIC18F66 version runs perfectly fine on the PIC18F67K version, but this theory is untested.  The base bootloader has been provided by Microchip under the AN1310 engineering application.  At the time of writing this, the best set of instructions for how to implement and use the bootloader can be found under the BART PTE production documentation set.  It's critical that the main application have an offset of 0x800, to avoid clobbering the bootloader which 'lives' at the beginning of program space.  Since the bootloader 'lives' at the beginning of program space, interrupt vectors have been appropriately offset (they too get an offset of 0x800).  

# Architecture
The Panel Interface Processor (PIP) is the **PIC18F67K22**.  Serial communication is achieved via an FTDI Serial-to-USB converter (**FT232RL**). MCU serial pins utilized are pins 31 (MCU TX), and 32 (MCU RX).    

# Dependencies
* IDE and version: MPLAB X v5.10
* Compiler and version: mpasmx v5.82
* Linker and version: mplink v5.09
* PIC18 Bootloader.asm
* bootconfig.inc
* devices.inc
* preprocess.inc

# Tagged Versions 
"Out of the box", the bootloader was sitting at revision v1.6.  Therefore, the first tagged version will sit at v2.0.     

* Revision v2.0 -- Bootload BAUD rate hardcoded at 115200bps (implemented as early as BART PTE).  Bootloader size adjusted accordingly.  Bootloader resides at the beginning of program space, thus reset/interrupt vectors have been remapped.  MPLABX project now defines the target device to be the PIC18F67K22.    