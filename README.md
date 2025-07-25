# VSDsuadron mini internship 2025
<details>
<summary><b>Task 1:</b> 
<br>
In this task we refer the c based  and RISCV based lab and execute it in oracel virtual box ,and comiling it with c code using gcc and RISCV compiler </summary>
  
## C language based LAB
In this task we followed the following steps to compile our ".c" code in our machine
1. Open ther virtual box, run the machine you are working onthen  ,then open the terminal ;then we a command cd 
 **cd=is used in the terminal to navigate to the directory where your C source files are before compiling or running them.**
   
2. Then we opened a leafpad to write our code 
   ....leafpad sum5ton.c....
   if leafpad is not installed 
   .....sudo apt install leafpad....command is  used to install it
    We write the code in the leafpad
   
3. then to compile with code with gcc we give the comand
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

     ***riscv64-unknown-elf-gcc	The RISC-V GCC cross-compiler for bare-metal systems (i.e., no OS like Linux). It's used to compile C code for RISC-V 64-bit embedded targets.***
     
     ***O1	Enables level 1 optimization. It improves performance a bit without increasing compile time too much.***
     
     ***mabi=lp64	Sets the RISC-V ABI (Application Binary Interface) to lp64, meaning:***
              l = long (and pointers) are 64-bit
              p64 = 64-bit pointers
              Used for 64-bit integer code.
     
     ***arch=rv64i	Targets the RV64I base integer instruction set of RISC-V. This excludes floating-point or vector extensions.***
     
     ***-o sum5ton.o	Specifies the output file name, in this case sum_1ton.o (an object file).***
     
     ***sum5ton.c	The input C source file to be compiled.***
     
     ***riscv64-unknown-elf-objdump	This is the RISC-V version of GNU objdump, part of the cross-compilation toolchain. It works with binaries compiled for RISC-V 64-bit (bare-metal) targets (no OS).***
     
     ***-d	Tells objdump to disassemble the .text section (the code section) of the object file. This shows the machine instructions in assembly language.***
