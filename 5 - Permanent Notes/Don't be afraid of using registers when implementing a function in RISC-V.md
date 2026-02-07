---
tags:
  - knowledge/computer_science
  - knowledge/assembly
  - knowledge/coding_tricks
time: 2026-02-07 16:06
status: done
---
# References
🚀 Notes I found relevant to this topic:
- [[Conventional register usage in RISC-V helps you with coding in assembly]]
- [[Function calling general steps in RISC-V]]
- [[Jump instructions in RISC-V]]

# Don't be afraid of using registers when implementing a function in RISC-V
When you try to implement some rather *complex* function in assembly, which in out context, is in RISC-V, Some may be overwhelmed by convention of RISC-V and don't know where to start. But the truth is that you don't need to think too much, rather you just need to stick to few principles.

Usually, it is really helpful to save some arguments passed to the function, this will help you reflecting which of them may not need to be saved through out the program. Don't be afraid of using saved registers. Simply follow the function calling convention will not cause any problem. 

However, if some content in saved register is no longer needed, say you opened a file and got a file descriptor, then simply **replace** it, rather than **use a new register**.

Some may think *temporary registers* are unsafe and refuse to use them, but actually they are really powerful, especially when you are implementing a "*leaf function*" (not a caller), just feel free to use them. 

If you are implementing a nested function, don't be afraid, a simple step can make a it work smoothly. You only need to decrement the stack pointer, and store the temporary registers may be violated onto stack, and after the function call pop them out, then you won't lose anything.