# CSE 510/610 Project: Naïve ISA implementation ![Language](https://img.shields.io/badge/language-Verilog-orange.svg)
An ISA is an interface between software and hardware. Through this naïve ISA implementation, we are able to dabble into 
the design art of computer architecture. The classic ARM (v7/v8m) is a 32-bit RISC architecture. 
All instructions are 32 bits long and most instructions can be conditionally executed (by Condition code flags). 
It has six operating modes and 37 registers, and uses CPSR and SPSR to handle exceptions.   

For simplification, our project implementation:

* 32-bit, fixed length instructions
* basic ALU () with conditional branch
* a load/store architecture. Data processing instructions act only on registers. 
* 5 stages, unpipelined. 

## Modules:

### Top_pipeline.v
This file consists of the main parts of our processor. 
### Pipeline_testbench_complete.v
This file is our testbench, it instantiates Top_pipeline.v and generates clock and nrst signal in order for our Core module to work.
### ?register file?
### Mem_*.v
This module is our Instruction memory. (Size: 32x64)
### Mem_data.v
This module is our Data memory. (Size: 8x64)
### ?Test File?
These are our instructions that will be loaded in Instruction Memory to be executed.

## Prerequisites

This project requires a Verilog simulator/synthesis tool, such as Icarus.

## Installing

To use Icarus Verilog:
```
git clone git://github.com/steveicarus/iverilog.git
```

Alternatively, for usage of Xilinx Vivado in docker image:

```
apt install docker.io
./install-vivado-image.sh
```


## Running the tests

?The tests are located in the ./test/ directory. Everything is built and run using the make command.?

```
Give an example
```

## Authors

* **Blah blah** 


## Reference

* [ARM v8m Manual](https://static.docs.arm.com/ddi0487/a/DDI0487A_k_armv8_arm_iss10775.pdf)
* [Arm Instruction Set Documentation](http://vision.gel.ulaval.ca/~jflalonde/cours/1001/h17/docs/arm-instructionset.pdf)  
* [Exception Handling in ARM](https://static.docs.arm.com/100701/0200/amv8_m_exception_handling_100701_0200_en.pdf) 
* [RISC](https://cs.stanford.edu/people/eroberts/courses/soco/projects/2000-01/risc/risccisc/)  
* [Verilog Manual](http://sutherland-hdl.com/pdfs/verilog_2001_ref_guide.pdf) 
