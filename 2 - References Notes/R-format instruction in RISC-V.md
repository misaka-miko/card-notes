---
tags:
  - source/video
time: 2026-02-07 20:04
status: done
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

| `0000000` | `rs2` | `rs1` | `000` | `rd` | `0110011` | `add`  |
| --------- | ----- | ----- | ----- | ---- | --------- | ------ |
| `0100000` | `rs2` | `rs1` | `000` | `rd` | `0110011` | `sub`  |
| `0000000` | `rs2` | `rs1` | `001` | `rd` | `0110011` | `sll`  |
| `0000000` | `rs2` | `rs1` | `010` | `rd` | `0110011` | `slt`  |
| `0000000` | `rs2` | `rs1` | `011` | `rd` | `0110011` | `sltu` |
| `0000000` | `rs2` | `rs1` | `100` | `rd` | `0110011` | `xor`  |
| `0000000` | `rs2` | `rs1` | `101` | `rd` | `0110011` | `srl`  |
| `0100000` | `rs2` | `rs1` | `101` | `rd` | `0110011` | `sra`  |
| `0000000` | `rs2` | `rs1` | `110` | `rd` | `0110011` | `or`   |
| `0000000` | `rs2` | `rs1` | `111` | `rd` | `0110011` | `and`  |
- The instruction `add` and `sub` shares the same `funct3` field since subtract operation is actually add with the 2's complement form, therefore shares the same hardware. What differs these instruction is the $1$ in `funct7` field, which tells that the operation needs sign extension.
- `slt` means "set destination register if less than", what it do is compares the value stored in `rs1` and `rs2` and if value in `rs1` is less than the one in `rs2`, set `rd` to $1$. In order to deal with negative numbers, by default it's comparing the 2's complement form. We provide a unsigned version.