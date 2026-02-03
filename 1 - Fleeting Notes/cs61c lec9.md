risc-v logical instructions
- `and` / `andi`
- `or` / `ori`
- `xor` / `xori`
- `sll` / `slli`
- `srl` / `srli`

`andi` used for masking
- `andi` with `0000 00FF`
- `andi` with `FF00 0000`

`xor` with `FFFF FFFF` gets logical `NOT`

`slli x11, x12, 2` store in `x11` the value in `x12` shifted by $2$ bits left, inserting $0$ on right.
arithmetically $\times 2^{2}$

how to $\times 12$: `slli` by $4$ and $8$ then add them up

`sra/srai`: we only have shift right **arithmetically**, inserting high-order sign bit into empty bits.

how to get a assembly program run:
- `foo.s` $\to$ `foo.o`: assembler
- `foo.o`, `lib.o` $\to$ `a.out`: linker

*data* and *program* live in memory, memory is byte addressable

program counter, within data path, holding the address of next executing instruction
by default we add $4$ bytes (size of a word in $32$-bits machine) to move to the next instruction, but sometimes a branch

symbolic register names
- `a0` - `a7` for argument registers (`x10` - `x17`) for function calls
- `zero` for `x0`

Pseudo-instructions (kind of like *symbolic* instructions)
- `mv rd, rs` = `addi, rd, rs, 0`
- `li rd, 42` = `addi, rd, x0, 42`: load immediate
- `nop` = `addi x0, x0, 0`

Six steps for calling a function:
1. put arguments in place where function can access them
2. transfer control to function
3. acquire local storage resources needed for function
4. perform desired task of the function
5. put *return* value in place where calling code can access it and restore any register you used; release local storage
6. return control to point of origin

RISC-V function call conventions
- use registers instead of memory since they are fast
- `a0` - `a7` (`x10` - `x17`): $8$ argument registers and two return values `a0`, `a1`
- `ra`: return address register to return to the point of origin `x1`
- `s0` - `s1` (`x8` - `x9`) and `s2` - `s11` (`x18` - `x27`): saved registers

`jr ra`: return to the address of the value stored in `ra`
why not `j`: `j` requires to hard code the address, but function call can happen in many place

`jal`: jump and link 
Before
```asm
addi ra, zero, 1016
j sum
```
After
```asm
jal FunctionLabel
```
- link: form an address or link to calling site to allow function to return to proper address
- jump to address and save the address of the following instrucion in register `ra`

return from function `jr`: jump register
- assembler shorthand: `ret` = `jr ra`

Actually, only two instructions:
- `jal rd, Label`
- `jalr rd, rs, imm`

`j`, `jr` and `ret` are pseudo-instructions
- `j`: `jal x0, Label`