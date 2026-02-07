---
tags:
  - source/book
time: 2026-02-04 20:42
status: done
---

# References
- [[@csZiXueSheQu9RISCVDecisions]]
- [[@csZiXueSheQu10RISCVProcedures_BiLiBiLi_bilibili]]

# Conventions in RISC-V helps you with coding in assembly
The following discusses the conventional usage of the $32$ registers in RISC-V.

Register `x0` is hard wired to $0$ for the sake of simplicity.

Register `x1` has a alias `ra`, which stands for return address, it conventionally holds the return address when the code tries to call a function.

Register `x2`, `x3` and `x4` holds some special pointers. Register `x2`, whose alias is `sp`, namely stack pointer, holds the address of the *stack* pointer, which is used for tracking stack usage. Register `x3` is `gp` and register `x4` is `tp`, which stand for global pointer and thread pointer respectively.`

The remaining registers are divided into $2$ kinds of registers: saved registers and temporary registers. The saved registers are guaranteed to remain the same after a function call, therefore the *callee* should save the value in them and restore them **if necessary**. In contrast to saved registers, the temporary registers may be overwritten after a function call, if the caller want to use them afterwards, *caller* should save the value.

Argument registers are caller-saved registers, used for passing function call parameters, and two of them are special, namely `a0` and `a1`, which are responsible for storing return values.