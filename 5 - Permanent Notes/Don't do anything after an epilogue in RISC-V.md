---
tags:
  - knowledge/assembly
  - knowledge/coding_tricks
  - knowledge/computer_science
  - knowledge/best_practice
time: 2026-02-08 22:05
status: done
---
# References
🚀 Notes I found relevant to this topic:
- [[Function calling general steps in RISC-V]]
- [[Prologue and epilogue in RISC-V]]

# Don't do anything after an epilogue in RISC-V
An inexperienced assembly programmer may come into this situation, where he may think he has finished the most of the job, and he finished the *epilogue*. Accidentally, he found that the function should return something, say a pointer, but he forgot to copy it to specified return value register. Luckily he saved the value to a saved register. "Nothing to worry, it is in a saved register and won't be modified unexpectedly, just add a simple `mv` instruction will work!"

Unfortunately, the program didn't act as expected, but why? Because he added the `mv` instruction after the epilogue, and the origin value stored in the saved register had already been restored.

This example tells us that the usage of saved register almost always leads to a bug, but temporary register won't lead to this kind of error, since we don't restore them.
But I don't recommend to do this since it add extra consideration, which just brings brain damage. Recall what we learned in [[Function calling general steps in RISC-V]], actually a little bit different, getting return value in place should always before restoring registers, since the latter wipe out some data, which is not what we want. 