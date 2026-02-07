---
tags:
  - source/video
time: 2026-02-07 16:44
status: done
---
# References
- [[@csZiXueSheQu10RISCVProcedures_BiLiBiLi_bilibili]]

# Prologue and epilogue in RISC-V
A *Prologue* is used for acquiring stack memory and backup of the values in saved registers. Prologue is not a necessary part of a function, especially for *leaf functions*, but if you have nested function call or try to overwrite *saved registers*, then you should have a prologue. A typical prologue looks like this:

```asm
funcName:
	# Prologue
	addi sp, sp, -16
	sw ra, 0(sp)
	sw s0, 4(sp)
	sw s1, 8(sp)
	sw s2, 12(sp)
	# End Prologue
```

A *Epilogue* is used for restoring values in saved registers and return address register, restore the stack pointer. A typical epilogue looks like this:

```asm
function:
	# ... function body
	
	# Epilogue
	lw ra, 0(sp)
	lw s0, 4(sp)
	lw s1, 8(sp)
	lw s2, 12(sp)
	addi sp, sp, 16 
	# End Epilogue
	ret
```