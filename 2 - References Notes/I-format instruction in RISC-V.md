---
tags:
  - source/video
time: 2026-02-07 20:05
status: done
---
# References
- [[@csZiXueSheQu11RISCVInstruction]]

# I-format instruction in RISC-V
I-format instructions are used for register immediate arithmetic operations and *load* operations. The following is the fields of I-format.

| $31 - 20$ | $19-15$ | $14-12$  | $11-7$ | $6-0$    |
| --------- | ------- | -------- | ------ | -------- |
| `imm`     | `rs1`   | `funct3` | `rd`   | `opcode` |
- Since we don't need two source registers like R-format, `rs2` field and `funct7` field are deprecated and used to hard code a $12$-bit immediate value.
- `imm` field now can hold a immediate ranging from $-2048$ to $2047$. They are always sign extended to $32$-bit before use in an arithmetic operation.

| `imm[11:0]`        | `rs1` | `000` | `rd` | `0010011` | `addi`  |
| ------------------ | ----- | ----- | ---- | --------- | ------- |
| `imm[11:0]`        | `rs1` | `010` | `rd` | `0010011` | `slti`  |
| `imm[11:0]`        | `rs1` | `011` | `rd` | `0010011` | `sltiu` |
| `imm[11:0]`        | `rs1` | `100` | `rd` | `0010011` | `xori`  |
| `imm[11:0]`        | `rs1` | `110` | `rd` | `0010011` | `ori`   |
| `imm[11:0]`        | `rs1` | `111` | `rd` | `0010011` | `andi`  |
| `000000` + `shamt` | `rs1` | `001` | `rd` | `0010011` | `slli`  |
| `000000` + `shamt` | `rs1` | `101` | `rd` | `0010011` | `srli`  |
| `000000` + `shamt` | `rs1` | `101` | `rd` | `0010011` | `srai`  |
| `imm[11:0]`        | `rs1` | `000` | `rd` | `0000011` | `lb`    |
| `imm[11:0]`        | `rs1` | `001` | `rd` | `0000011` | `lh`    |
| `imm[11:0]`        | `rs1` | `010` | `rd` | `0000011` | `lw`    |
| `imm[11:0]`        | `rs1` | `100` | `rd` | `0000011` | `lbu`   |
| `imm[11:0]`        | `rs1` | `101` | `rd` | `0000011` | `lhu`   |

- The field of `funct3` is the almost the same as their non-immediate version in R-format, that is basically reuse the hardware.
- The immediate for shift operations is set to only have $5$ valid bits, since we only have $32$ bits within a register, the shift exceeds 32 bits makes no sense.
- `lh` means load half word, which is $16$ bits. `lh` and `lb` by default needs sign extension to fit into $32$ bits, and the unsigned version is also provided and controlled through the highest bit of `funct3` field.