# cse510/610 &nbsp; Computer Architecture
Mock ARM Processor
## Part1. &nbsp; The ARM architecture introduction
### 1. Main Features

- 32-bit architecture but with two instruction sets (32 ARM/16 'Thumb').
- All instructions are 32 bits long and most instructions can be conditionally executed (for 'Thumb', most intrustions are not conditionally executed).
- RISC : load/store architecture with data processing instructions act only on registers.
- Use CPSR (current program status register) and SPSR (saved program status register) to handle exceptions
- Six operate mode (0:Users (most cases)):
  1. FIQ (handle interrupt)
  2. IRQ (handle interrupt)
  3. Supervisor (handle Software Interrupt instruction)
  4. Abort (used to handle memory access violations)
  5. Undef (used to handle undefined instructions)
  6. System
### 2. Registers Set

1. 37 registers: 1 pc + 1 cpsr + 5 spsr + 30 general purpose registers
2. The Program Status Registers (CPSR and SPSRs):
  `|N|Z|C|V|27| | | | | | | | ... |5| Mode |`
  * Condition code flags
    * N = Negative result from ALU
    * Z = Zero result from ALU
    * C = ALU operation Carried out
    * V = ALU operation oVerflowed
3. r15 is the PC and r14 is used as the subroutine link register.
4. Exception handling
- Basically, when exception occurs, save cpsr to spsr, manipulate cpsr, and refer to a vector table.
- For details pls refer [Exception Handling ARM](https://static.docs.arm.com/100701/0200/amv8_m_exception_handling_100701_0200_en.pdf)

### 3. Instructions
#### 1. Three stages Pipeline:
  1. Fetch: 
  2. Decode:
  3. Excute: Register(s) read from Register Bank Shift and ALU operation Write register(s) back to Register Bank
#### 2. Conditional Execution Using 'Cond field'
  1. To execute an instruction conditionally, simply postfix it with the appropriate
condition:  
example: To execute this only if the zero flag is set:  

```ADDEQ r0,r1,r2```  
#### 3. Branch
  1. Branch : B{condition code} label  
  Branch with Link : BL{condition code} sub_routine_label  
#### 4. Data processing
1. Contains:  
  – Arithmetic operations  
  – Comparisons (no results ‐ just set condition codes)  
  – Logical operations  
  – Data movement between registers  
#### 5. Load/ Store Instructions 
1. General:  
  - Does not support memory to memory data processing operations.    
  – Must move data values into registers before using them.  
2. Contains:
  – Single register data transfer (LDR/ STR).  
  – Block data transfer (LDM/STM).  
  – Single Data Swap (SWP).  
#### 6. ARM Instruction set summary
1. like STR,LDR,ADD,MUL,AND,B,BL,...  
For details pls refer[arm instruction set](http://vision.gel.ulaval.ca/~jflalonde/cours/1001/h17/docs/arm-instructionset.pdf) 

## Part2. &nbsp; Our simplified ARM architecture design
### 0. "Foreword"
Although 8-bit version looks nice, it is pretty hard to include the basic elements of arm instructions using 8 bits. For the project, we should at least include:  
  - at least 5 instructions: STR, LDR, ADD, MUL, Branch 
  - three registers slot in an instruction due to the RISC requirement.  
Then, bits required for opcode is more than 2, which leaves the bits for 3 register slots are less than 6.  
For example, consider the code:  
```OP R0,R1,R2```  
So The space is not enough to represent the instructions.  I believe 16bits should be fine.  

