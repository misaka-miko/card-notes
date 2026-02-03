B-format:
- $0 - 6$: opcode
- $7$: `imm[11]`
- $8 - 11$: `imm[1:4]`
- $12 - 14$: funct3
- $15 - 19$: `rs1`
- $20 - 24$: `rs2`
- $25 - 30$: `imm[5:10]`
- $31$: `imm[12]`

branch calculation
- if don't take the branch: $PC = PC+4$
- if do take the branch: $PC = PC+imm \times 4$ **not what we do in RISC-V**
- if do take the branch: $PC = PC+imm \times 2$

RISC-V feat: $n \times 16$-bit instructions
to enable this, scale the branch offset by $2$ bytes even when no $16$-bit instrucions.
can only reach $\pm 2^{10} \times 32$-bit instrucions on either side of PC

long immediates
U-format
- $0 - 6$: opcode
- $7 - 11$: `rd`
- $12 - 31$: `imm[12:31]`

- `lui` - load upper immediate
- `auipc` - add upper immediate to PC
	- used for PC-relative addressing
	- `Label: auipc x10, 0` puts address of Label in `x10`

using `li` to combine `lui` and `addi` to load immediate

J-format:
- $0 - 6$: opcode
- $7 - 11$: `rd`
- $12 - 19$: `imm[12:19]`
- $20$: `imm[11]`
- $21 - 30$: `imm[1:10]`
- $31$: `imm[1]`
- $20 - 24$: `rs2`
- $25 - 30$: `imm[5:10]`
- $31$: `imm[12]`

uses of `jal`
`j Label = jal x0, Label` discard return address

call function within $2^{18}$ instrucions of PC
`jal ra, FuncName`

`jalr` uses I-format
`jalr rd, rs, imm`: jump to absolute address
`ret` and `jr` pseudo-instrucions: `ret = jr ra = jalr x0, ra, 0`