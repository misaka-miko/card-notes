---
tags:
  - source/video
time: 2026-02-07 20:04
status: working
---
# References
- [[@csZiXueSheQu11RISCVInstruction]]

# R-format instruction in RISC-V
R-format instructions stand for register-register arithmetic operations. The instruction is divided into these fields.


| $31 - 25$ | $24 - 20$ | $19-15$ | $14-12$  | $11-7$ | $6-0$    |
| --------- | --------- | ------- | -------- | ------ | -------- |
| `funct7`  | `rs2`     | `rs1`   | `funct3` | `rd`   | `opcode` |
- register `rd`, `rs1`, `rs2` are respectively destination register, source register $1$, and source register $2$, these register only take $5$ bits each since we only have $32$ registers in RISC-V, so $5$ bits is adequate.
- `opcode`, namely *operation code*, partially determines what instruction it is. In R-format, it is always `0b0110011`.
- `funct7` and `funct3` are combined with `opcode` to describe what operation to perform.