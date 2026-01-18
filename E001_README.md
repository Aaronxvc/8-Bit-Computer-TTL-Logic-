## Experiment E001 — Startup Bias Baseline


## Purpose

Quantify how often a dominant startup pattern appears under a stable physical configuration, and document the electrical conditions under which that behavior occurs.

This experiment does **not** attempt to fix the behavior or assign causality beyond what is explicitly observable.

---

## System Configuration (as tested)

- **Build status**
  - Clock module: complete
  - Register A: working
  - Register B: working
  - ALU: partially implemented
  - ALU output stage: partially implemented

- **Clock during power-up**
  - Clock present in system
  - No intentional clocking during observation window

- **Power**
  - 5 V TTL supply
  - Power up method: manual power cycling
  - Ramp speed: unknown (no scope measurement)

- **Bus transceiver**
  - 74LS245 powered (VCC and GND connected)
  - **/OE (pin 10): floating**
  - **DIR (pin 1): floating**
  - No explicit enable or direction control

- **Logic chips**
  - Two 74LS86 (XOR) chips physically present
  - **Inputs unconnected (floating)**

- **Indicators**
  - LED indicators present on register outputs

---

## Observation Method

- N = 24 power up observations (hand recorded)
- Each cycle:
  1. Power on
  2. Wait 3 - 5 seconds
  3. Record visible LED pattern
  4. Power off fully before next cycle
- Observation window confirmed stable after settling  
  (no value changes observed once powered)

---

## Raw Observation Notes

Handwritten observation log ( Blue notepad showing run to run variation:

![Handwritten startup observations](/IMG_DD6A09EB-9CC6-49CF-84FC-D4903C6F20E8.jpeg)

Key observed patterns include:

- **Dominant pattern:** `11111111`
- **Occasional non dominant patterns**, e.g.:
  - `01111010`
  - `01111011`
  - `00100000`

Patterns vary **between power cycles** but remain **stable after power up settles**.

---

## Wiring Context (ALU / Bus)

Current documented pin level wiring between ALU, registers, and bus transceiver:

![ALU and bus wiring notes](/IMG_90890C19-61EE-4C57-BB5F-508A4283EEE9.jpeg)

Notable recorded conditions in these notes:

- Multiple ALU related pins marked as **floating**
- Bus transceiver control pins not tied to defined logic levels
- XOR chips present but not driven

---

## Observations 

- The pattern `A = B = OUT = 11111111` appears frequently on power up.
- Other structured 8 bit patterns appear less frequently.
- The observed value after power up remains stable during the observation window.
- The final state varies across power cycles under nominally identical conditions.

No causal explanation is claimed at this stage.

---

## Hypotheses (explicitly provisional)

- **H1 (confidence: low):** Floating control pins on the bus transceiver influence which values are captured during power-up.
- **H2 (confidence: low):** Default HIGH bias of TTL inputs contributes to the dominance of `11111111`.

These are **not conclusions** and may be revised or discarded.

---

## Notes on Experimental Scope

- This experiment documents **startup bias**, not time domain randomness.
- No claim is made that the system is probabilistic or stochastic.
- Undefined or floating logic is treated as a **measured condition**, not a bug to be fixed yet.

---

## Next Step (change only one thing)

Tie **one** previously floating control pin (e.g., 74LS245 /OE) to a defined logic level and repeat E001 as a new experiment (E002), keeping all other conditions unchanged.

---

**Important:**  
This log records observed distributions under the stated conditions.  
It does not imply causality or generalize beyond this specific build.
