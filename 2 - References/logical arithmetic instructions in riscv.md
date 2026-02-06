---
tags:
  - source/video
time: 2026-02-03 18:38
status: done
---
# References
- [[@csZiXueSheQu9RISCVDecisions]]

# logical arithmetic instructions in RISC-V
There are six kinds of logical arithmetic instructions in RISC-V.
1. `and`/`andi` stands for bitwise **AND** operation in RISC-V.
2. `or`/`ori` stands for bitwise **OR** operation in RISC-V.
3. `xor`/`xori` stands for bitwise **XOR** operation in RISC-V.
4. `sll`/`slli` stands for *shift left logically* in RISC-V.
5. `srl`/`srli` stands for *shift right logically* in RISC-V.
6. `sra`/`srai` stands for *shift right arithmetically* in RISC-V. Doing sign extension, which means deploy the high order bit into the empty bits.

For the sake of simplicity, there is no bitwise **NOT** instruction in RISC-V ISA, since it can be simply implemented using the `xori` instruction with `0xFFFF FFFF` as the immediate operand.

Also, there is no `sla`/`slai` instrucion, since we don't need sign extension when we left shift a register, but if with no sign extension, we will make any negative number look like positive when we right shift a register logically.