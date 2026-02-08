---
tags:
  - source/video
time: 2026-02-08 15:42
status: done
---
# References
- [[@csZiXueSheQu12RISCVInstruction]]

# U-format instruction in RISC-V
U-format instruction helps to deal with longer immediates, which stands for upper immediates.


| $31-12$      | $11-7$ | $6-0$    |
| ------------ | ------ | -------- |
| `imm[31:12]` | `rd`   | `opcode` |
- The other format only assigns $12$ bits for a immediate into a instruction. The U-format holds the upper $20$ bits of a $32$ bits immediate.
- `lui` and `auipc` uses U-format. `lui` stands for *load upper immediate*, what it does is to load the upper $20$ bits to the register and set the lower $12$ bits to $0$. `auipc` stands for *add upper immediate to program counter*, which adds the immediate to program counter and saves the result in `rd`.
- `lui` combined with `addi` can load a $32$ bits immediate into a register, but don't directly using these two instructions since there are some problems with sign extension of the lower $12$ bits of the immediate, instead just use the pseudo instruction `li` to replace the know process.
- `auipc` can help get the address of a label. For instance, using `label: auipc x10, 0`, will add $0$ to program counter (which is just do nothing), and store the result in `x10`.