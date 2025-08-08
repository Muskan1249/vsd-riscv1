# VSDsuadron mini internship 2025
<details>
<summary><b>Task 1:</b> 
<br>
In this task we refer the c based  and RISCV based lab and execute it in oracel virtual box ,and comiling it with c code using gcc and RISCV compiler </summary>
  
## C language based LAB
In this task we followed the following steps to compile our ".c" code in our machine
1. Open ther virtual box, run the machine you are working on  ,then open the terminal ;then we a command cd
   
 **cd=is used in the terminal to navigate to the directory where your C source files are before compiling or running them.**
   
2. Then we opened a leafpad to write our code
   
       ....leafpad sum5ton.c....
   
   if leafpad is not installed
    
         .....sudo apt install leafpad....command is  used to install it
   
    We write the code in the leafpad
   
 3. then to compile with code with gcc we give the command
   
          ......gcc sum5ton.c......
 
 **gcc=gcc command is used to compile C programs using the GNU Compiler Collection (GCC).**
   
4.then we checked the directory to our file is listed 

      ....ls -ltr.......
   
   all the files located in the directory will be shown
   
     ...   ./a.out    .....is used to compile the program
    
   **./a.out=./a.out is the default output file created by gcc or g++ when you compile C or C++ code without specifying an output name**

   ## RISCV based LAB

   1.Open the terminal and run the given command 
   
        .....cat sum5ton.c.....
    
    the code which is we have written in sum5ton.c 
    whole program will be displayed on the terminal
    
  2. with the c code write a command to compile it with RISCV compiler

               .....riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum5ton.o sum5ton.c.....
    
  3. Open new terminal and give the command
   
           .....riscv64-unknown-elf-objdump -d sum5ton.o....
     
       this is is used to disassemble the object file sum5ton.o, which has been compiled for the RISC-V 64-bit architecture using a cross-compiler toolchain.
   
  4. the assembly level language code will be displayed ,type
     
          ..... :/main.....
     
         to locate main section of our code

     ***riscv64-unknown-elf-gcc =	The RISC-V GCC cross-compiler for bare-metal systems (i.e., no OS like Linux). It's used to compile C code for RISC-V 64-bit embedded targets.***
     
     ***O1	= Enables level 1 optimization. It improves performance a bit without increasing compile time too much.***
     
     ***mabi = lp64	Sets the RISC-V ABI (Application Binary Interface) to lp64, meaning:***
              l = long (and pointers) are 64-bit
              p64 = 64-bit pointers
              Used for 64-bit integer code.
     
     ***arch = rv64i	Targets the RV64I base integer instruction set of RISC-V. This excludes floating-point or vector extensions.***
     
     ***-o sum5ton.o =	Specifies the output file name, in this case sum_1ton.o (an object file).***
     
     ***sum5ton.c =	The input C source file to be compiled.***
     
     ***riscv64-unknown-elf-objdump =	This is the RISC-V version of GNU objdump, part of the cross-compilation toolchain. It works with binaries compiled for RISC-V 64-bit (bare-metal) targets (no OS).***
     
     ***-d = Tells objdump to disassemble the .text section (the code section) of the object file. This shows the machine instructions in assembly language.***
     </details>
     

------------------------------------------------------------------------------------------------------------------------------------------------------------------------



<details> 
<summary><b>Task 3:</b> 
to Review the RISC-V software documentation to understand the R, I, S, B, U, and J instruction types. </summary>
   
## What is RISC-V
RISC-V (Reduced Instruction Set Computer - V) is an open standard instruction set architecture (ISA) based on established reduced instruction set computing principles. Unlike proprietary ISAs, RISC-V is free and open, enabling unrestricted academic and commercial use without licensing fees. This has made RISC-V an attractive option for research, education, and industry applications, fostering innovation and development across various domains.
### BASICS
 # Instructions types 
 | Format     | Used By                      | Fields                                                    |
| ---------- | ---------------------------- | --------------------------------------------------------- |
| **R-type** | Register-register arithmetic | `opcode`, `rd`, `funct3`, `rs1`, `rs2`, `funct7`          |
| **I-type** | Immediate, load, some jumps  | `opcode`, `rd`, `funct3`, `rs1`, `imm[11:0]`              |
| **S-type** | Store instructions           | `opcode`, `imm[11:5]`, `rs2`, `rs1`, `funct3`, `imm[4:0]` |
| **B-type** | Conditional branches         | `opcode`, `imm`, `rs2`, `rs1`, `funct3`                   |
| **U-type** | Upper immediate              | `opcode`, `rd`, `imm[31:12]`                              |
| **J-type** | Jump instructions            | `opcode`, `rd`, `imm[20:1]`                               |

# 1. R-Type Instructions
**Format:**

   '| funct7 | rs2 | rs1 | funct3 | rd | opcode |'
'   |  7b    | 5b  | 5b  |  3b    | 5b |   7b   |
**Used For:**
Arithmetic and logical operations between two registers.

**Examples:**
ADD x5, x1, x2 → x5 = x1 + x2

SUB x6, x1, x2 → x6 = x1 - x2

AND x7, x1, x2 → x7 = x1 & x2

** Key Fields:**
rs1, rs2: Source registers

rd: Destination register

funct3/funct7: Operation modifiers

opcode: Tells processor this is an R-type instruction

# 2. I-Type Instructions
**Format:**

    | imm[11:0] | rs1 | funct3 | rd | opcode |
    |   12b     | 5b  |   3b   | 5b |  7b    |
**Used For:**
Arithmetic/logical operations with immediate values

Load instructions

Jump register (JALR)

CSR (control and status register) access

**Examples:**
ADDI x5, x1, 10 → x5 = x1 + 10

LW x6, 0(x1) → Load 32-bit word from memory at x1 + 0 into x6

JALR x1, x2, 4 → Jump to address x2 + 4 and save return address in x1

# 3. S-Type Instructions
**Format:**

     | imm[11:5] | rs2 | rs1 | funct3 | imm[4:0] | opcode |
     |   7b      | 5b  | 5b  |   3b   |   5b     |  7b    |
**Used For:**
Store operations from register to memory
** Examples:**
SW x6, 0(x1) → Store word from x6 into memory at x1 + 0

SB x6, 4(x1) → Store byte from x6 into memory at x1 + 4

**Note:**
imm is split across the instruction and recombined in hardware

# 4. B-Type Instructions
**Format:**

    | imm[12|10:5] | rs2 | rs1 | funct3 | imm[4:1|11] | opcode |
    |     7b       | 5b  | 5b  |   3b   |     5b      |  7b    |
**Used For:**
Conditional branching based on comparison between two registers

**Examples:**
BEQ x1, x2, offset → Branch if x1 == x2

BNE x3, x4, offset → Branch if x3 ≠ x4

BLT, BGE, BLTU, BGEU for signed/unsigned comparisons

# 5. U-Type Instructions
**Format:**

    | imm[31:12] | rd | opcode |
    |    20b     | 5b |   7b   |
**Used For:**
Loading large constants or constructing addresses

**Examples:**
LUI x5, 0x12345 → Load upper 20 bits with 0x12345, lower 12 = 0 → x5 = 0x12345000

AUIPC x6, 0x1 → Add upper immediate to PC: x6 = PC + 0x1000

 # 6. J-Type Instructions
**Format:**

    | imm[20|10:1|11|19:12] | rd | opcode |
    |         20b          | 5b |   7b   |
**Used For:**
Unconditional jumps with link (save return address in rd)
**Examples:**
JAL x1, offset → Jump to PC + offset, save PC + 4 in x1

# 7. System Instructions (I-type style)
**Used For:**
Environment control, traps, and system-level access

**Examples:**
ECALL → Environment call (e.g., system call)
EBREAK → Breakpoint
CSR Instructions:
CSRRW, CSRRS, CSRRC, etc. for reading/writing system registers

 ## 15 instruction 
 
 **1.addw a1,a1,a5:**
  
  Type: R-Type
 
  Binary: 0000000 01101 01011 000    01011 0111011
  
  Hex: 00f585bb
  
  **2.addi sp,sp,-32:**
  
  Type: I-Type
  
  Binary: 11111111111000000000 00010 000 00010 0010011
       
        Hex: fe010113
        
 **3.lw a1,8(sp):**
  
  Type: I-Type
 
  Binary: 0000000000001000 00010   010 01011 0000011
       
        Hex: 00812583
        
 **4. sd ra,24(sp):**
       
        Type: S-Type
       
        Binary: 0000000 00001 00010 011 11000 0100011
        
        Hex: 00113c23
        
   **5. lui a0,0x2b:**
       
        Type: U-Type
       
        Binary: 000000000000000000101011 01010 0110111
        
        Hex: 0002b537



  **6.jal ra,10448:**
        
        Type: J-Type (UJ-Type in some documents, similar but specifically for jal)
        
        The jal instruction uses a complex imm calculation.
        
        Hex: 384000ef
        
  **7. addi a0,a0,-960:**
        
        Type: I-Type
        
        Binary: 11111001010000000000 01010 000 01010 0010011
        
        Hex: c405051
        
   **8. addi a1,sp,8:**
        
        Type: I-Type
        
        Binary: 0000000000001000 00010 000 01011 0010011
        
        Hex: 00810593
        
   **9.lw a5,12(sp):**
        
        Type: I-Type
        
        Binary: 0000000000001100 00010 010 01101 0000011
        
        Hex: 00c12783
        
  **10.addi sp,sp,32:**
        
        Type: I-Type
       
        Binary: 0000000000100000 00010 000 00010 0010011
       
        Hex: 02010113
        
  **11.li a0,0:**
       
        Type: I-Type ( pseudo-instruction, translates to addi a0,zero,0 )
       
        Binary: 0000000000000000 00000 000 01010 0010011
        
        Hex: 00000513
        
  **12.ret:**
       
        Type: I-Type ( pseudo-instruction, translates to jalr zero,0(ra) )
        
        Binary (for jalr zero,0(ra)): 000000000000 00001 000 00000 1100111
       
        Hex: 00008067
        
  **13.auipc a5,0xffff0:**
        
        Type: U-Type
        
        Binary: 11111111111111111111 01101 0110111
        However auipc is 1111111111111111111100000 01101 0110111 for the immediate
        
        Hex: ffff0797
        
  **14.beqz a5,10134:**
       
        Type: B-Type ( pseudo-instruction, translates to beq a5,zero,offset )
      
        Binary (Actual beq instruction): 0000000 00000 01101 000 00000 1100011
        The offset calculation for beqz would determine the exact binary.
      
        Hex: 00078863
        
  **15.j 101f0:**
       
        Type: J-Type (UJ-Type in some documents, similar but specifically for jal, however j uses the same opcode as jal with rd set to zero)
        The j instruction uses a complex imm calculation.
       
        Hex: 0c00006f
