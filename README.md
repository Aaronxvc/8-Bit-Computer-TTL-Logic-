# Discrete 8-Bit Computer (TTL Logic)

## Overview
Built a breadboard-based 8-bit computer using TTL logic, following a reference design.  
The goal was not originality, but to understand computation at the **signal, timing, and power** level through hands on implementation and debugging.

This project focuses on *physical computation*: how abstract logic becomes real behavior once voltage, timing, and noise are involved.

---

## What I Built
- Clock module (manual + astable)
- Registers with a shared bus
- Tri-state bus architecture
- ALU (basic arithmetic and logic operations)
- Output / display logic

---

## What I Learned
- Power integrity often matters more than schematics
- Floating inputs lead to undefined and unstable behavior
- Registers power up in random states
- Timing and enable signals are physical constraints, not abstractions
- Systems can be functional without being perfectly correct
- Debugging real hardware requires patience and iteration, not just theory

---

## What Didn’t Work (At First)
- Bus contention between multiple registers
- Inconsistent startup states across power cycles
- LED output behaving unpredictably
- Misleading “almost working” states

### Fixes and Adjustments
- Grounding unused enable lines
- Adding decoupling where needed
- Reworking signal flow and control assumptions
- Accepting and designing around imperfect behavior

---

## Status
- Functional but imperfect
- Built for learning and understanding, not polish
- Emphasis on system behavior over correctness

---

## Notes
This project was completed as a self-directed learning exercise to develop intuition for
digital systems, hardware debugging, and the realities of physical computation.
