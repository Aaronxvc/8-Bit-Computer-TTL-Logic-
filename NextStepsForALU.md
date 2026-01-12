# ALU Integration – Pause / Return Notes

## Current State
- Clock module complete and stable
- Registers:
  - Register A: working
  - Register B: working
  - Output register: partially integrated
- ALU: partially built, integration phase

## Observed Issues
- Output LEDs sometimes show:
  - mixed values from Register A and Register B
  - intermittent contention like behavior
- Suspected causes:
  - bus contention
  - enable timing overlap
  - incorrect or missing gating on shared bus lines

## Known Review Items
- **Pin connections between Register A and Register B to the ALU need review**
  - Verify that only one register is driving the bus at a time
  - Re-check enable (OE / EN) logic and timing
  - Confirm no floating or double-driven lines during clock transitions

## Hypotheses
- Mixed LED output likely caused by:
  - simultaneous enables on A/B registers
  - ALU inputs not fully isolated during inactive phases
  - output register latching unstable bus values

## Next Suggested Steps
1. Isolate ALU output register from main bus
2. Verify control line logic for:
   - Register A enable
   - Register B enable
   - ALU output enable
3. Re-test ALU inputs with:
   - single register driving bus at a time
4. Cross-check enable timing against control signals / microcode intent

## Open Questions
- Exact intended enable sequencing for ALU operations
- Whether additional buffering or stricter gating is needed before output register
- Whether clock edge timing is contributing to transient contention


## Status  
State captured for clean re entry  