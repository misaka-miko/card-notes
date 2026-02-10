---
tags:
  - source/video
time: 2026-02-10 10:56
status: done
---
# References
- [[@csZiXueSheQu15StateState]]

# Finite State Machine and the implementation
The finite state machine describes the state transition pattern within a system. To draw a finite state machine, the states should be placed, then the transition pattern should be marked through an arrow from initial state to next state with given input and output on it.

The implementation is simple. Generally speaking, we need a *Combinational Logic* Unit to deal with the state transition, which means given previous state and input, generate the next state and output. Using a register to wrap the next state every clock cycle.