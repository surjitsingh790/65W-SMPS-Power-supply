# ADR-001: Isolated AC/DC topology evaluation

**Status:** Proposed — topology decision pending  
**Project:** 65 W, nominal 19 V DC output (65/19 = 3.42 A)  
**Confirmed input:** 85–265 V AC RMS, 50/60 Hz (2026-10-31)

## Context
Develop a mains-powered, galvanically isolated AC/DC supply as an engineering learning and portfolio project. The universal input range is confirmed; **no topology, controller, safety classification or production design has been approved.** Mains-connected hardware must not be energized without qualified review, appropriate isolation/protection, and a controlled test plan.

## Candidates

| Candidate | Transfer mechanism | Benefits | Challenges | Assessment |
|---|---|---|---|---|
| Conventional flyback | Stores energy during switch ON, transfers on OFF | Relatively simple and economical; common at 65 W | Leakage spikes, switching loss, EMI, thermal design | Baseline candidate |
| Active-clamp flyback | Flyback with controlled clamp and energy recovery | Potential ZVS and improved efficiency/power density | Additional switch, complex timing and control; ZVS load-dependent | Advanced candidate |
| Forward converter | Transfers power while primary switch ON; output inductor sustains load on OFF | Good current ripple control; scalable | Transformer reset, extra output inductor and rectification | Alternative |
| LLC resonant | Resonant network transfers energy, often with frequency regulation | Excellent efficiency potential and soft switching | Complex gain/control and wide-input/light-load behavior | Alternative |

## Evaluation criteria (to quantify)
- Input: **85–265 VAC RMS, 50/60 Hz confirmed**; nominal ideal rectified peak approximately 120–375 V; low-line bulk ripple and high-line stress must be analyzed
- Output: 19 V nominal; 65 W rated; regulation and transient limits TBD
- Ripple/noise: <=190 mVpp **provisional**, with proposed 20 MHz oscilloscope bandwidth and short-ground measurement; input/load/temperature test matrix TBD
- Efficiency at low/nominal/high line and light/half/full load: TBD
- Safety isolation, creepage/clearance, insulation, surge, EMI and certification targets: TBD
- Component availability, magnetics feasibility, cost, PCB area, thermal margin, testability and development risk: TBD

## Preliminary direction
Shortlist conventional flyback and active-clamp flyback for a quantitative trade study. **This is not a selection.** Forward and LLC remain documented alternatives.

## Decision gates
1. Approve remaining measurable electrical, mechanical, environmental and safety requirements.
2. Calculate first-pass stresses, losses and magnetic feasibility at both input extremes for shortlisted topologies.
3. Compare controller reference designs and manufacturer datasheets.
4. Review safety strategy and test infrastructure before schematic design.
5. Record selected topology, evidence and trade-offs in a follow-up ADR revision.

## Verification note
Peak-to-peak ripple must be specified with bandwidth, probing method, operating conditions and acceptance criteria; ripple is distinct from DC regulation. The operating input range does not define surge immunity.
