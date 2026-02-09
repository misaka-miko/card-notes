---
tags:
  - source/video
time: 2026-02-09 16:22
status: done
---
# References
- [[@csZiXueSheQu13CompilationAssembly]]

# Object file format
The object file consists of the following $6$ parts:
1. object file header, which contains the size and position of the other pieces of the object file.
2. text segment, which is basically machine code.
3. data segment, which is the binary representation of the static data in the source file.
4. relocation information, which tells which lines of code need to be fixed up later.
5. symbol table, which is a list of this file's label and static data that can be referenced.
6. debugging information.