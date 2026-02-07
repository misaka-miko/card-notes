---
tags:
  - source/video
time: 2026-02-07 17:44
status: done
---
# References
- [[@csZiXueSheQu11RISCVInstruction]]

# Stored program computer, Everything has a address
The modern computer originates from the idea of stored-program computer, which means the program itself is stored as data. As a result, we don't need to rewire the computer to run a different program.

Since all the text and data are stored in memory, everything as a memory address so that we can easily access them. The pointer in C is basically a memory address, which can point to anything, causing unexpected bugs.

There's one register, whose name is *program counter*, holds a pointer to the next instruction to be executed. It is basically a pointer to memory.