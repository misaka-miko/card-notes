---
tags:
  - source/video
time: 2026-02-09 22:50
status: done
---
# References
- [[@csZiXueSheQu14IntroSynchronous]]

# Register details
A $n$-bit register is composed of $n$ one-bit flip-flops, generally has a input D for *data* and an output Q for *quiescent*. The flip-flop's output is always between $1$ and $0$. The $n$ flip flops are parallel.

On the rising edge of the clock, the input *d* is sampled and transferred to the output, and at all the other time, *d* is ignored.

But what if the input is not stable, it might trigger some problem. So we require the input to be stable in which the time is before rising edge of the clock and the hold time of flip-flop. The former is called setup time and the latter is called hold time. The time from rising edge to output *q* updated is called *clock-to-q* delay.