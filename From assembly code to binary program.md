---
tags:
  - source/video
time: 2026-02-03 23:14
status: working
---
# References
- [[@csZiXueSheQu9RISCVDecisions]]

# From assembly code to binary program
Say we have two assembly source code `foo.s` and `bar.s`, like what we do in C, the assembly source file is turned into object files `foo.o` and `bar.o` through assembler, then if the program needs existing object file `lib.o` for instance, using *linker* to link these object files and generate the binary program `a.out`.