---
tags:
  - source/video
time: 2026-02-07 17:02
status: done
---
# References
- [[@csZiXueSheQu10RISCVProcedures_BiLiBiLi_bilibili]]

# Memory layouts and allocations in C and RISC-V respectively
In a general C program, there are three memory area allocated. The first is *static* areas, the variables on the area is declared once in one program, and they are destroyed once the execution completes. The second is *heap* area, variables declared dynamically or say manually live in the area. The third is *stack* area, space there are used by procedures during execution, where register values are saved

he memory layout in RISC-V $32$ is as follows. The stack grows from high memory address to low memory address, which in hexadecimal is `bfff fff0`, and should be aligned on $16$-byte boundary. The text segment (program) lives in low memory address, but not the very bottom.

The static data segment lives on the top of text segment, by convention, global pointer `gp` points to the static, and in RISC-V 32, `gp` have a value of `0x1000_0000`.

Heap lives above the static data segment, and dynamically grows and shrinks, grows up to high address.