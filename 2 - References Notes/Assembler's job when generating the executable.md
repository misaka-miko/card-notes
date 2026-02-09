---
tags:
  - source/video
time: 2026-02-09 15:36
status: done
---
# References
- [[@csZiXueSheQu13CompilationAssembly]]

# Assembler's job when generating the executable
The assembler will take assembler directives, but it doesn't produce any machine code in this step. Common assembler directives are shown as follows.
- `.text`: Subsequent items of this directives are basically the instructions to put in the text segment, which will finally be the machine code.
- `.data`: Subsequent items of this directives are some data like a huge area to put in the user data segment.
- `.globl sym`: This directive expose the symbol `sym` to global scope so that `sym` can be referenced in other files.
- `.string str`: This directive simply stores `str` in memory and null-terminate it.
- `.word w1 ... wn`: Store $n$ $32$-bit word in successive memory words.

After reading the directives, assembler now can start to replace the pseudo Instructions. For some basic arithmetic operations and PC-relative jump operation, this is easy. The assembler can first scan for all labels, and in the second scan, replace all branch labels to a hard-coded value.

In order to handle the case of absolute addressing, two tables will be created. The symbol table tells what stuff can be referenced within this file, basically containing labels for function calling and the data under `.data` section.

The relocation table is a to-do table, containing list of items whose address this file needs. That's generally some absolute jump instructions and address loading `la` and `jalr`.