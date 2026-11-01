# Preliminary engineering requirements — draft

| ID | Requirement | Status |
|---|---|---|
| PSU-REQ-001 | Isolated AC-to-DC mains-powered supply | Project objective; safety design TBD |
| PSU-REQ-002 | Nominal regulated output: 19 V DC | Confirmed nominal setpoint |
| PSU-REQ-003 | Rated output power: 65 W (approximately 3.42 A at 19 V) | Project baseline; load details TBD |
| PSU-REQ-004 | Continuous operating input: **85–265 V AC RMS, 50/60 Hz** | **Confirmed (2026-10-31)** |
| PSU-REQ-005 | **Steady-state average output voltage 19 V ±2% (18.62–19.38 V)** | **Confirmed target (2026-10-31)**; across specified input and load operating envelope, including combined errors |
| PSU-REQ-006 | **Full-load AC-input-to-DC-output efficiency >=90% at 65 W across 85–265 VAC, 50/60 Hz** | **Confirmed preliminary target (2026-10-31)**; steady-state at rated load, test conditions TBD; other load efficiencies and no-load consumption TBD |
| PSU-REQ-007 | Output ripple and noise <=190 mV peak-to-peak | Provisional; 20 MHz bandwidth proposed; measurement setup/test conditions TBD |
| PSU-REQ-008 | Protection: OVP, OCP, SCP, OTP and inrush | TBD |
| PSU-REQ-009 | Isolation, creepage, clearance, EMI and applicable safety standard | TBD; qualified review required |
| PSU-REQ-010 | Architecture | Not selected; see ADR-001 |
| PSU-REQ-011 | AC surge, abnormal input, brownout and recovery behavior | TBD; separate from continuous 85–265 VAC range |
| PSU-REQ-012 | Load-step undershoot, overshoot, settling time and step slew rate | TBD; distinct from steady-state ±2% |
| PSU-REQ-013 | Steady-state load range, no-load regulation and minimum operating temperature | TBD |
| PSU-REQ-014 | **Deliver continuous rated 65 W output at ambient temperature up to 40°C without thermal derating** | **Confirmed design requirement (2026-11-01)**; minimum temperature, cooling/enclosure and orientation TBD |
| PSU-REQ-015 | Thermal derating above 40°C | Not specified; no operation above 40°C is implied |

## 40°C continuous full-load thermal requirement
- The 40°C value refers to **ambient air around the intended product**, not component surface or semiconductor junction temperature. Define measurement location and enclosure/mounting configuration before validation.
- Rated output of 19 V at 65 W must be sustainable at 40°C ambient without output-power derating over the confirmed 85–265 VAC, 50/60 Hz operating input range.
- Investigate natural-convection cooling as a **candidate**, not an approved method. PCB area, copper, heatsinks, enclosure, airflow, mounting orientation and accessible surface temperatures remain open.
- Check MOSFET and rectifier junction temperatures, transformer winding/core hot spots and insulation class, electrolytic capacitor case temperature and lifetime, control IC limits, PCB materials and enclosure surfaces against actual part specifications and safety criteria. Allocate reliability and measurement margins.
- Illustrative thermal derating above 40°C is **not** an approved operating curve. Define any high-temperature operation and power limits separately.
- Proposed verification: safety-reviewed controlled chamber at 40°C with intended enclosure/orientation, continuous rated load and 85/115/230/265 VAC corners (50/60 Hz as relevant); measure calibrated input/output power and component hot spots after a documented thermal-equilibrium criterion. Verify output regulation and protective behavior; document instrumentation uncertainty.
- **No mains-powered thermal testing until qualified review and a safe test procedure are approved.**

## Full-load efficiency and thermal planning
- Efficiency is measured from **real AC input power** to DC output power: eta = Pout / Pin. Do not use apparent power (VA) as input power.
- At 65 W output and 90% efficiency, Pin <= 72.22 W and total loss <= 7.22 W. These are system-level limits, not per-component limits.
- Illustrative loss allocation (not a simulation or bill of materials): bridge/input 0.65 W, primary MOSFET 1.60 W, transformer 1.45 W, secondary rectification 1.75 W, output filtering 0.35 W, control/auxiliary 0.60 W, miscellaneous 0.82 W = 7.22 W.
- Low-line operation can increase RMS current and conduction losses; high-line operation can increase switching stress/losses. Neither corner is assumed worst-case without analysis.
- Efficiency is load-dependent: define test points at 25%, 50%, 75% and 100% load, and no-load **input power** separately. Only the full-load 90% minimum is approved so far.
- Test using a calibrated true-power AC analyzer and DC voltage/current measurement after thermal stabilization, across specified AC input and frequency. Define ambient, measurement uncertainty and acceptance margins before testing.
- Thermal design must distribute component losses, check junction/core/capacitor temperatures and account for PCB copper, enclosure, airflow and ambient; 7.22 W alone cannot predict temperatures.
- This efficiency target is a project goal, not evidence of regulatory energy-efficiency compliance.

## Regulation interpretation
- The ±2% is an **overall** allowable steady-state average output deviation from nominal 19 V, not ±2% independently for line, load, temperature and feedback.
- Line regulation: variation of average output with AC input at fixed load.
- Load regulation: variation of average output with load current at fixed input.
- Feedback accuracy budget must include reference tolerance, divider tolerances, drift, controller behavior and calibration.
- Output ripple/noise and fast load transients are evaluated against separate limits; neither is implicitly allowed to exceed or required to remain within the steady-state ±2% band during transients.
- Verification shall sweep 85/115/230/265 VAC at 50 and 60 Hz and defined load/temperature corners; establish warm-up and measurement method before acceptance testing.
- Need to specify whether no-load is within regulated range and whether rated load is continuous across all ambient conditions.

## Universal input engineering implications
- Ideal rectified peak bus spans approximately 120.2 V at 85 VAC to 374.8 V at 265 VAC, **not** including bridge losses, bus ripple, surges or tolerances.
- The bulk capacitor voltage rating, ripple-current rating and hold-up time must be validated; do not assume 400 V is adequate.
- MOSFET stress includes DC bus, reflected voltage, leakage overshoot and transient margin; a nominal voltage class is not a selection.
- Magnetics, current limit, thermal losses and control must be checked at low line, high line and intermediate points.
- Confirm mains frequency tolerance, input power factor/harmonic applicability, EMI, inrush and surge immunity in a safety review.

**Note:** These are design inputs, not demonstrated performance or safety claims. No mains-powered prototype is approved for energization.
