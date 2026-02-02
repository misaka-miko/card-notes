Function Call example
```c
int Leaf(int g, int h, int i, int j) {
	int f;
	f = (g + h) - (i + j);
	return f;
}
```
- parameters `g, h, i, j` are in argument registers `a0` - `a3`. `f` in `s0`
- assume need one temporary register `s1`

we need to restore the value in saved registers `s0` and `s1`, this can be done with stack
- stack is in memory, we need register pointing to it.
- `sp` is the *stack pointer* in RISC-V (`x2`)
- stack grows down from high to low address
	- push decrements `sp`, pop increments `sp`

```asm
Leaf: 
# Prologue
addi sp, sp, -8 # adjust stack for 2 items
sw s1, 4(sp)
sw s0, 0(sp)

add s0, a0, a1
add s1, a2, a3
sub a0, s0, s1

# Epilogue
lw s0, 0(sp) # restore register 0 for caller
lw s1, 4(sp)
addi sp, sp, 8 # adjust stack to delete 2 items
jr ra
```

Nested Function Calls
```c
int sumSquare(int x, int y) {
	return mult(x, x) + y;
}
```
need to save `sumSquare` return address before the call to `mult`, again, we can use stack.

When callee returns after executing, the caller needs to know which registers may have changed and which are guaranteed to be unchanged

To reduce the expensive loads and stores from spilling and restoring registers, RISC-V splits the registers into $2$ categories:
- preserved across function call
	- Caller can rely on values being unchanged
	- `sp`, `gp`, `tp`, `s0` - `s11` (`s0` as `fp)
- not preserverd across function call
	- Caller *cannot* rely on values being unchanged
	- `a0` - `a7`, `ra`, temporary registers `t0` - `t6`

the first one let the callee to handle the restore job
the second one let the caller to handle the store job

Memory allocation

C has two storage classes
- automatic: local to function, discarded when function exits
- static: exist across the procedure

Use stack for automatic variables that don't fit into the registers

*Procedure frame* or *activation record*: segment of stack with saved registers and local variables

Where is stack in memory?
- RV32 convention
- stack starts in high memory and grows down
	- hexadecimal: `bfff_fff0`
	- must be aligned on $16$-byte boundary
- RV32 programs (*text segment*) in low end
	- `0001_0000`
- *static data segment* (constants and other static variables) above text for static variables
	- RISC-V convention *global pointer* points to static
	- RV32 `gp = 1000_0000`
- heap above static for data structures that grow and shrink, grows to high address