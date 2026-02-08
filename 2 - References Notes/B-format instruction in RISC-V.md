---
tags:
  - source/video
time: 2026-02-08 15:40
status: done
---
# References
- [[@csZiXueSheQu12RISCVInstruction]]

# B-format instruction in RISC-V
B-format instructions are used for branching operations, they are very similar to S-format instructions. The table describes the layout of B-format.


| $31$      | $30-25$     | $24-20$ | $19-15$ | $14-12$  | $11-8$     | $7$       | $6-0$    |
| --------- | ----------- | ------- | ------- | -------- | ---------- | --------- | -------- |
| `imm[12]` | `imm[10:5]` | `rs2`   | `rs1`   | `funct3` | `imm[4:1]` | `imm[11]` | `opcode` |

- The jump that B-format instructions support is *PC relative*, if not a branch, the value in program counter add itself by $4$. If take a branch, the value in the program counter add itself by `imm * 2`. The reason why it doesn't increment by `imm * 4` is to support compressed instruction.
- The least significant bit of immediate is always $0$, therefore it actually ranges from $-4096 \to  4095$.

| `imm[12;10:5]` | `rs2` | `rs1` | `000` | `imm[4:1;11]` | `1100011` | `beq`  |
| -------------- | ----- | ----- | ----- | ------------- | --------- | ------ |
| `imm[12;10:5]` | `rs2` | `rs1` | `001` | `imm[4:1;11]` | `1100011` | `bne`  |
| `imm[12;10:5]` | `rs2` | `rs1` | `100` | `imm[4:1;11]` | `1100011` | `blt`  |
| `imm[12;10:5]` | `rs2` | `rs1` | `101` | `imm[4:1;11]` | `1100011` | `bge`  |
| `imm[12;10:5]` | `rs2` | `rs1` | `110` | `imm[4:1;11]` | `1100011` | `bltu` |
| `imm[12;10:5]` | `rs2` | `rs1` | `111` | `imm[4:1;11]` | `1100011` | `bgeu` |
