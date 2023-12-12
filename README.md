# RISC-V MYTH Workshop

![](risv/day1/flyer.png)


# Table of contents

- [Overview](#overview)
- [Day 1 : Introduction to RISC-V ISA](#Day1)
  - [GNU compiler toolchain](#GNU)
  - [Installation of GNU toolchain](#Installation)
- [Introduction to ABI](#ABI)
  - [Combinational logic in TL verilog using Makerchip IDE](#combinational)
  - [Combinational Calculator](#cal)
  - [Sequential Calculator](#seq)
  - [Pipelining](#pipe)
  - [Validity](#valid)
  - [Calculator with memory](#mem)
- [Basic RISC-V CPU micro-architecture](#archi)
  - [Fetch](#fetch)
  - [Decode](#decode)
  - [Execute and Register file read/write](#register)
  - [Pipelining the RISC-V microarchitecture](#micro)
  - [Load, store and data memory](#load)
  - [Completing the RISC-V CPU](#risc)
- [Acknowledgement](#ack)


# Overview

The five-day RISC-V Myth (microprocessor for you in thirty hours) workshop is led by [Redwood EDA](https://www.redwoodeda.com/tl-verilog)  and [VLSI system design](https://www.vlsisystemdesign.com/riscv-based-myth/?v=a98eef2a3105). Beginning with the fundamentals of software and hardware integration, this workshop teaches participants how to write basic C programs for assembly language programs, which leads to the construction of a RISC-V pipelined architecture. All of the workshop materials, tests, and initial labs are completed on the VSD-IAT platform, which is an intelligent cloud-based platform. After that, the RTL implementation of the RISC-V core is carried out using the TL-based Makerchip platform provided in the github repository https://github.com/stevehoover/RISC-V_MYTH_Workshop. Before the core is implemented, the Makerchip platform implements a few basic digital logics and a calculator to help users better understand the platform and TL verilog.

# Introduction to RISC-V ISA

RISC-V ISA is a base integer ISA and must be present in any implemenatation along with some optional extension. The RISC-V has been designed to support extensive customization and specialization which can be extended  with  one  or  more  optional  instruction-set  extensions,  but  the  base  integer instructions cannot be redefine. The different instructions included in RISC-V are listed below.

1. Pseudo instructions
2. Base integer instruction (RV64I, RV32I)
3. Multiply extension (RV64M)
4. Single and double floating point instruction (RV64F, RV64D)
5. Application binary instruction
6. Memory allocation and stack pointer



# GNU compiler toolchain

The GNU compile toolchain is a set of programming tools in the LINUX system that can be used to compile code to build executable programs, libraries, and debuggers, as detailed in 1 and 2. One such toolchain is RISC-V, which supports C and C++ cross compilers. It supports two build modes: a generic ELF/Newlib toolchain and a more advanced Linux-ELF/glibc toolchain, which may be found on github.

To begin, a c program was built to build sums from 1 to n, which is stored in the codes folder as sum1to9.c. Both the gcc and RISC-V compilers are used to compile the software. For typical gcc compilation, simply type gcc filename.c> at the terminal to generate an object file a.out, which is then run with./a.out.

* To use the RISC-V gcc compiler or simulator, type

```typescript
riscv64-unknown-elf-gcc <-01/-Ofast> -mabi=lp64 -march=rv64i -o <object filename.o> <filename.c>
```

![](risv/day1/Screenshot%202023-12-12%20131310.png)

Here is the basic C code to test the output in the Compiler.

![](risv/day1/Screenshot%202023-12-12%20131018.png)

```typescript
riscv64-unknown-elf-objdump <object file> -d <object filename.o>
```

![](risv/day1/3.png)

Type: Ofast

![](risv/day1/4.png)

To use SPIKE simulator to run object file
```typescript
spike pk <object filename.o>
```

![](risv/day1/5.png)

The SPIKE simulator can be used to manually debug the code

```typescript
spike - d pk <object filename.o>
```
![](risv/day1/6.png)
