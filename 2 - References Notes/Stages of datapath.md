---
tags:
  - source/video
time: 2026-02-11 11:46
status: done
---
# References
- [[@csZiXueSheQu18SingleCycleCPU]]

# Stages of Data-path
It's not realistic to build a single logic cloud to perform all the instructions, but it's reasonable to build several shared smaller stages to form the whole data path. Smaller stages are easier to design, and it's easier to optimize one stage without impacting the others. In general, the stages can be divided as follows.
1. Instruction Fetching
2. Instruction Decoding
3. Instruction Execution
4. Memory Access
5. Write Back to register

In general, within the data path, the program counter will point to instruction memory to fetch which instruction to execute. Secondly, the instruction is decoded and read the register needed. Third, we execute the instruction, then using the result of ALU to access memory. Finally, write back to the register. All these five stages are going to happen within a clock cycle.