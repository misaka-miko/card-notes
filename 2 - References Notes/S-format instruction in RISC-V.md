---
tags:
  - source/video
time: 2026-02-07 20:06
status: done
---
# References
- [[@csZiXueSheQu11RISCVInstruction]]

# S-format instruction in RISC-V
Since there is not destination register in store instructions, we need another format for representing a store instruction. The following is the layout of S-format.


| $31-25$     | $24-20$ | $19-15$ | $14-12$  | $11-7$     | $6-0$    |
| ----------- | ------- | ------- | -------- | ---------- | -------- |
| `imm[11:5]` | `rs2`   | `rs1`   | `funct3` | `imm[4:0]` | `opcode` |
- Store instruction needs to read two registers, `rs1` is for base memory address, and `rs2` holds the value to be stored.
- The layout is divided in order to be consistent to other kinds of format, so that the use of the hardware can be more compact.

| `imm[11:5]` | `rs2` | `rs1` | `000` | `imm[4:0]` | `0100011` | `sb` |
| ----------- | ----- | ----- | ----- | ---------- | --------- | ---- |
| `imm[11:5]` | `rs2` | `rs1` | `001` | `imm[4:0]` | `0100011` | `sh` |
| `imm[11:5]` | `rs2` | `rs1` | `010` | `imm[4:0]` | `0100011` | `sw` |
