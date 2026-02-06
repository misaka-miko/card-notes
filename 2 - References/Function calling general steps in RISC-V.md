---
tags:
  - source/book
time: 2026-02-04 20:19
status: done
---

# References
[[@csZiXueSheQu9RISCVDecisions]]

# Function calling general steps in RISC-V
The function calling step can be divided into the following six parts. The first step is to put the arguments to where the *callee*, namely the function get called, can access. Then the *caller* should move control to the function get called. After that, the function should acquire some local resources to function properly if needed. Until this step, we have finished the preparation step for calling a function, the next step is to simply execute what the function is meant to.

This is not the whole story, actually we should store the return value of the function where the calling code have access to and **restore** the register which we used. As we have finished clean up, we can finally move control back to the calling code. Congratulations, you have finished up your first function call in RISC-V!