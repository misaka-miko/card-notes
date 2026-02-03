---
tags:
  - source/video
time: 2026-02-03 18:53
status: done
---
# References
- [[@csZiXueSheQu9RISCVDecisions]]

# meaningful use case of some logical arithmetic instructions in riscv
In order to isolate some bits within a register, we can use bitwise instruction `andi` like what we do in C programming language, simply using `andi x10, x10, 0xFF00 0000` can isolate the most significant byte of a word, which is the rightmost byte, using `andi x10, x10, 0x0000 00FF` can isolate the least significant byte of a word, which is the leftmost byte.

The meaning of `sll`/`slli` can be treated as a multiplication of $2$'s power, `slli x10, x10, 2` means times the value stored in `x10`, multiplies it by $2^{2} = 4$ and assign it back to register `x10`.

But when the value in register is negative, `srai` doesn't means divide the value by $2$, which means we should take extra efforts to implement division instrucion.