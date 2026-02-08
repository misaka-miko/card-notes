Compiling assembling linking loading CALL

translation v.s. interpreter

interpreter is a program that executes other program

language translation transfer a high level language to a low level one

translator / interpreter

why interpret machine code in software? for simulation (RISC-V), useful for debug / learn

interpret old ISA to new ISA, like emulator

it's easier to write interpreter, closer to high level language, can give better debugging information / error msgs

interpreter provides instruction set. Run on any machine

translated/compiled program almost always faster
translation/compilation help hides the program source from the user

# Compiler
`foo.c` to `foo.s`: `gcc -O2 -S -c foo.s` 
output may contain pseudo instructions, which the assembler understands but not the machine.

# Assembler
takes a .s file, turn into .o file
.s file: assembly language code (pseudo ops)
.o file: information tables (true assembly only)

assembler directives
give directions to assembler, do not produce machine instructions
- .text: subsequent items put in user text segment (machine code)
- .data: subsequent items put in user data segment (source file data in binary)
- .globl sym: declare sym global and can be referenced from other files
- string str: store the string str in memory and null-terminate it
- .word wl...wn: store the n 32-bit quantities in successive memory words

`not t0, t1` = `xori t0, t1, -1`
`beqz t0, loop` = `beq t0, zero, loop`
load address `la t0, str` = `lui t0, str[31:12]` `addi t0, t0, str[11:0]`

producing machine language
- simple case: arithmetic, logical, shifts
- info within instruction 
- branch and jump: pc-relative (beq bne jal)

The first pass: replace pseudo and track labels

symbol table (share): list of items in this file that may be used by other files
- labels: function calling
- data: anything in .data section; variables which may be accessed across files

relocation table (to do): list of items whose address this file needs
- any absolute label jumped to: jal, jalr
- any piece of data in static section `la`, `lw`/`sw`

obj file format
- object file header: size, position of the other pieces of the object file
- text segment: machine code
- data segment: binary representation of the static data in the source file
- relocation information
- symbol table
- debugging info

# linker
output executable code
combine object file into one executable

four types of address

resolving references
text segment begins at `0x10000`