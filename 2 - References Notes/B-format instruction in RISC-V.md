---
tags:
  - source/video
time: 2026-02-08 15:40
status: working
---
# References
- [[@csZiXueSheQu12RISCVInstruction]]

# B-format instruction in RISC-V
B-format instructions are used for branching operations, they are very similar to S-format instructions. The table describes the layout of B-format.


| $31$      | $30-25$     | $24-20$ | $19-15$ | $14-12$  | $11-8$     | $7$       | $6-0$    |
| --------- | ----------- | ------- | ------- | -------- | ---------- | --------- | -------- |
| `imm[12]` | `imm[10:5]` | `rs2`   | `rs1`   | `funct3` | `imm[4:1]` | `imm[11]` | `opcode` |
