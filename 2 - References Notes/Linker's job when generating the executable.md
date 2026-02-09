---
tags:
  - source/video
time: 2026-02-09 16:33
status: done
---
# References
- [[@csZiXueSheQu13CompilationAssembly]]

# Linker's job when generating the executable
Linker puts multiple object files together, and outputs the executable file. Linker enables separate compilation of files. The job of the linker can be generally described as follows.
1. Put all the text segment within all the object files together.
2. Put all the data segment within all the object files together and concatenate them onto the end of the text segment.
3. Resolve references, fill in the relocation table with the actual absolute address.

Internal function address using `auipc` and `jalr`, external function reference `auipc` and `jalr` and static data reference often `lui` and `addi`, require relocation.

Linker assumes the first text segment begins at `0x10000`, and it knows the length of each text segment and data segment and their order. Linker needs to calculate the absolute address of each label to be jumped to and each piece of data being referenced.