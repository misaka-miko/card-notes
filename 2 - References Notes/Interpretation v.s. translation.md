---
tags:
  - source/video
time: 2026-02-09 15:20
status: done
---
# References
- [[@csZiXueSheQu13CompilationAssembly]]

# Interpretation v.s. translation
The *interpretation* of a program relies on *interpreter*. The interpreter itself is a program, and the programs get interpreted have nothing to do with the underlying hardware, which means as long as you have a interpreter installed, then you can run the program, say Python, on any hardware.

*Translation* generally means the origin source code turned into another language but performs the same function through *translator*. And the translated programs, of course, are specific to hardware.

The interpretation is useful for some emulation work, for instance, running RISC-V assembly on **VENUS**, or we want the old program still run on the new machine, we can use interpreter as a layer of simulation to pretend we still have the same ISA. As interpretation is close to high level language, we can output useful debug information, which makes it easier to program.

The translation is useful to hide code details from the user, the program can be distributed in binary form. As the process of decompiling is hard, the right of the source code writer can be protected. Also, since the language is translated down to machine code, it runs way more faster than interpretation language.