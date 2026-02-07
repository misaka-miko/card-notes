---
tags:
  - source/video
time: 2026-02-06 23:35
status: done
---
# References
- [[@csZiXueSheQu9RISCVDecisions]]

# Jump instructions in RISC-V
There are only two jump instructions in RISC-V. One of them is `jal rd, imm`, which first calculate the target number of the *program counter*, and that is $PC+imm$, then save the address of next instruction, which is $PC+4$, to destination register `rd`, finally program counter gets the target value and jump to the position. In real programming, the immediate is usually a `Label`.

The other one is `jalr rd, rs, imm`, unlike `jal` instruction, which requires us to hard code the immediate, we use the address stored in source register `rs` to calculate the jump address, which is $rs + imm$. Then store the return address in `rd`, which is again $PC+4$. The instruction is absolute address jump, usually used for function return.

These two instruction forms many pseudo instruction. If we don't save the return address, then we get the unconditional jump `j label`, which is the same as `jal x0, label`. If what we do is simply trying to call a function. By convention, we store the return address to `ra`, therefore the instruction is `jal ra, FunctionName`, this can be default to `jal FunctionName`.

In the context of returning from a function, we don't need to save the return address, and we want to jump to the address stored in `ra`, that requires *jump and link register* instruction, which is `jalr, x0, ra, 0`, this can be replaced with a more intuitive pseudo instruction `jr ra`, or simply `ret`.