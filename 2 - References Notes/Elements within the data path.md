---
tags:
  - source/video
time: 2026-02-11 12:40
status: done
---
# References
- [[@csZiXueSheQu18SingleCycleCPU]]

# Elements within the data path
In order to have state within the data path, the register must exist. A register will only change it's value on clock's rising edge and will not change otherwise. The value changed will directly on output bus.

Register file consists of $32$ registers. Since the amount of registers we can access at a time is limited, we should be able to read $2$ registers out of the register file and write to one of these registers.

States required by the instruction set architecture includes registers within register file, the program counter which holds the address of current instruction, and the memory which we manually divided into *data memory* and *instruction memory*.