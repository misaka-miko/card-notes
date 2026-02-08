---
tags:
  - source/video
time: 2026-02-08 15:41
status: done
---
# References
- [[@csZiXueSheQu12RISCVInstruction]]

# J-format instruction in RISC-V
J-format instruction is just for jump instruction in RISC-V, which is `jal`. The following table describes the layout of J-format.

| $31$      | $30-21$     | $20$      | $19-12$      | $11-7$ | $6-0$    |
| --------- | ----------- | --------- | ------------ | ------ | -------- |
| `imm[20]` | `imm[10:1]` | `imm[11]` | `imm[19:12]` | `rd`   | `opcode` |
- `jal` saves $PC+4$ in register `rd`, which is the return address, and sets program counter to $PC+\text{offset}$, which again is program counter relative jump, targeting $\pm 2^{19}$ locations, which are $2$ bytes apart.