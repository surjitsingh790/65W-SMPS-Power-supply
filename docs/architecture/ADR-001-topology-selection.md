# ADR-001: Isolated AC/DC topology evaluation

**Status:** Accepted — conventional flyback selected (2026-11-05); detailed design and safety approval pending  
**Project:** 65 W, nominal 19 V DC output (65/19 = 3.42 A)  
**Confirmed input:** 85–265 V AC RMS, 50/60 Hz (2026-10-31)

## Context
Develop a mains-powered, galvanically isolated AC/DC supply as an engineering learning and portfolio project. The universal input range is confirmed; **conventional flyback has been selected as the topology, but no controller, safety classification or production design has been approved.** Mains-connected hardware must not be energized without qualified review, appropriate isolation/protection, and a controlled test plan.

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

## First-pass comparison (2026-11-02; qualitative, not validated)
For 65 W output and 90% efficiency: real AC input power must be <=72.22 W and aggregate conversion loss <=7.22 W. At 92% efficiency the corresponding loss is 5.65 W (1.57 W less); these are targets/scenarios, **not measured or predicted topology performance**.

| Dimension | Conventional flyback | Active-clamp flyback |
|---|---|---|
| Primary power switches | Usually one | Usually two |
| Leakage energy | Typically dissipative clamp/snubber | Controlled clamp, potentially recovers energy |
| Soft switching | Usually hard switching, although QR/valley-switching variants reduce turn-on loss | Potential ZVS under suitable operating conditions; not guaranteed at all loads |
| Controller/gate drive | Less complex | More complex clamp timing, drive and startup/fault behavior |
| Loss and 90% goal | Plausible with optimized magnetics, rectification and switching; requires calculations | Potential efficiency advantage; must be shown over 85–265 VAC and load range |
| EMI/thermal | Switching edges, leakage spikes, rectifier losses require analysis | Resonant/clamp dynamics add EMI and control trade-offs |
| BOM/cost/testability | Generally lower and easier to debug | Generally higher; more waveforms and failure modes |
| Learning project | Strong first isolated-converter baseline | Valuable advanced follow-up or redesign |

**Selected topology (2026-11-05): conventional flyback**, chosen for reduced implementation and verification risk in the learning project. Selection does **not** demonstrate that 90% efficiency or safety requirements are met. Compare candidate quasi-resonant/valley-switching controllers as a conventional flyback variant; consider secondary synchronous rectification if the diode loss budget requires it.

### Quantitative comparison still required
1. Choose plausible controller/reference designs for each candidate; review actual datasheets, availability and safety implications.
2. Define switching mode/frequency and worst-case bulk bus minimum/maximum under line/load/ripple conditions.
3. Estimate transformer turns ratio, magnetizing inductance, peak/RMS currents, core/copper/leakage losses and insulation feasibility.
4. Calculate primary MOSFET voltage stress (bus + reflected voltage + leakage overshoot), conduction and switching losses; evaluate clamp loss/recovery and device ratings.
5. Estimate secondary diode versus synchronous rectification losses, output capacitor RMS/ripple and feedback/auxiliary power.
6. Compare loss budget against <=7.22 W at rated load at both 85 VAC and 265 VAC; examine 40°C still-air fanless enclosure hot spots.
7. Compare BOM cost, board area, EMC filtering, control-loop design, light-load/no-load behavior and fault handling.
8. Document assumptions and confidence levels; make topology selection only after reviewing evidence.

## Preliminary direction
**Decision: conventional flyback.** Active-clamp flyback remains the principal rejected alternative for this phase; forward and LLC remain documented alternatives. Reopen the decision if quantitative losses, thermal limits, or other requirements cannot be satisfied.

## Decision gates
1. Approve remaining measurable electrical, mechanical, environmental and safety requirements.
2. Calculate first-pass stresses, losses and magnetic feasibility at both input extremes for shortlisted topologies.
3. Compare controller reference designs and manufacturer datasheets.
4. Review safety strategy and test infrastructure before schematic design.
5. **Completed:** record conventional flyback topology selection (2026-11-05); controller selection and design verification remain open.

## Verification note
Peak-to-peak ripple must be specified with bandwidth, probing method, operating conditions and acceptance criteria; ripple is distinct from DC regulation. The operating input range does not define surge immunity.
