 instructions represented as bit patterns
 - program can be stored in memory to be read or written like data.
 - can reprogram quickly, don't have to rewire computer

**Everything has a memory address**
instrucions and data are stored in memory, everything has a memory address
- both branches and jumps use these

*program counter* (PC): pointer to memory, pointing to the next instrucion to be executed

**Binary compatibility**
- programs are distributed in binary form(not source program) (*I don't think so lol*)
- new machines run old programs
- backward-compatible instruction set

most data we work with is in words ($32$-bit chunks)
- each register is a word
- `lw` and `sw` access memory one word at a time

instructions stored with fixed-size $32$-bit words, same $32$-bit instructions used for RV32, RV64, RV128

instrucion divided into *fields*, each of them tells processor something about instruction.
- R-format: register-register arithmetic operations
- I-format: register-immediate arithmetic operations and loads
- S-format: stores
- B-format: branches (minor variant of S-format)
- U-format: $20$-bit upper immediate instructions
- J-format: jumps (minor variant of U-format)

R-format:
- $0 - 6$: opcode
- $7 - 11$: `rd` - destination register 
	- only $5$-bit chunk is enough for $32$ registers
- $12 - 14$: funct3
- $15 - 19$: `rs1`
- $20 - 24$: `rs2`
- $25 - 31$: funct7
- opcode: partially specifies what instrucion it is
	- for all R-format instrucions, it is $0110011_{\text{two}}$
- funct7 + funct3: combined with opcode, describe what operation to perform

`slt`: set on less than - if `rs1` < `rs2`, set `rd` to $1$
`sltu`: set on less than - if `rs1` < `rs2`, set `rd` to $1$ (*unsigned version*)

I-format:
- $0 - 6$: opcode
- $7 - 11$: `rd` - destination register 
	- only $5$-bit chunk is enough for $32$ registers
- $12 - 14$: funct3
- $15 - 19$: `rs1`
- $20 - 31$: `imm`: $-2048 \to +2047$

`addi x15, x1, -50`: `0b111111001110 00001 000 01111 0010011`

`slti`: if `rs1` < `imm`, set `rd` to $1$
`sltiu`: if `rs1` < `imm`, set `rd` to $1$ (*unsigned version*)
shift amout is limited to $5$-bit chunk

RISC-V loads also uses I-format
- $0 - 6$: opcode - Load
- $7 - 11$: `rd` - destination register 
	- only $5$-bit chunk is enough for $32$ registers
- $12 - 14$: funct3
- $15 - 19$: `rs1`
- $20 - 31$: offset
- the $12$-bit signed immediate is added to the base address in `rs1` to form memory address

`lw x14, 8(x2)`: `0b 000000001000 00010 010 01110 0000011`