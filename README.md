# DFX Tutorial VPK120

Welcome to the Dynamic Function eXchange (DFX) repository for the Xilinx Versal VPK120 evaluation board.

What is DFX?

Dynamic Function eXchange (DFX)—previously known as Partial Reconfiguration (PR)—allows you to dynamically modify a specific region of an FPGA or Adaptive SoC at runtime. While a designated Reconfigurable Partition (RP) is being updated with a new Reconfigurable Module (RM), the remaining Static Region of the design continues to operate without interruption or loss of data.

On the Versal platform, this workflow leverages Block Design Containers (BDCs) to cleanly isolate, floorplan, and swap custom IP configurations.

Access the Complete Tutorial Guide

For complete, step-by-step instructions to implement this design from scratch, please refer to the PDF document included in this repository:

DFX Guide for Versal.pdf

The detailed guide covers:

Hardware Design Flow (Vivado 2023.2): Splitting your block design into static and dynamic hierarchies, creating BDCs, floorplanning using Pblocks, and configuring the DFX Wizard.

Automated Compilation: A Tcl automation script to build synthesis, standard implementations, and child configurations, exporting both hardware platform files (.xsa) and boot device images (.pdi).

PetaLinux Software Design (PetaLinux 2023.2): Configuring the Linux kernel with FPGA Manager enabled, setting up the EXT4 root filesystem, and generating Device Tree Overlays (.dtbo).

On-Board Verification (VPK120): Interactive terminal commands to swap active modules using fpgautil and safely inspect active memory registers using devmem at runtime.

Quick Reference: Architecture Layout

Static Region: Constant processing foundation (Versal CIPS, NoC, Clocking, and reset logic).

rp1 (Reconfigurable Partition): The target interchangeable block design container slot.

rp1rm1 (RM 1): Returns 0xFEEDC0DE at address 0x201_8000_0000.

rp1rm2 (RM 2): Returns 0xFACEFEED at address 0x201_8001_0000.
