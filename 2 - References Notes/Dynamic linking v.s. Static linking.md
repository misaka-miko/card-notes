---
tags:
  - source/video
time: 2026-02-09 16:56
status: done
---
# References
- [[@csZiXueSheQu13CompilationAssembly]]

# Dynamic linking v.s. Static linking
Static linking is like "baking" the library into the program, it has some benefit, the program using static linking is *self-contained*, if the executable is working, then it's done, it won't crash done due to some change on the library.

But if we have some change on the library, we won't directly enjoy the update in the statically linked program, we need to recompile it, and this is not enjoyable.

Dynamic linking allows the program to reference to a library at runtime, so that when the library get updated, then the executable can get the update instantly, but if the library accidentally break up, then the executable itself won't work either.