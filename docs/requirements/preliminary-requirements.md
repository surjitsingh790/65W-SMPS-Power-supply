# Preliminary engineering requirements — draft

| ID | Requirement | Status |
|---|---|---|
| PSU-REQ-001 | Isolated AC-to-DC mains-powered supply | Project objective; safety design TBD |
| PSU-REQ-002 | Nominal regulated output: 19 V DC | Confirmed nominal setpoint |
| PSU-REQ-003 | Rated output power: 65 W (approximately 3.42 A at 19 V) | Project baseline; load details TBD |
| PSU-REQ-004 | Continuous operating input: **85–265 V AC RMS, 50/60 Hz** | **Confirmed (2026-10-31)** |
| PSU-REQ-005 | **Steady-state average output voltage 19 V ±2% (18.62–19.38 V)** | **Confirmed target (2026-10-31)**; across specified input and load operating envelope, including combined errors |
| PSU-REQ-006 | Efficiency, no-load consumption and temperature limits | TBD |
| PSU-REQ-007 | Output ripple and noise <=190 mV peak-to-peak | Provisional; 20 MHz bandwidth proposed; measurement setup/test conditions TBD |
| PSU-REQ-008 | Protection: OVP, OCP, SCP, OTP and inrush | TBD |
| PSU-REQ-009 | Isolation, creepage, clearance, EMI and applicable safety standard | TBD; qualified review required |
| PSU-REQ-010 | Architecture | Not selected; see ADR-001 |
| PSU-REQ-011 | AC surge, abnormal input, brownout and recovery behavior | TBD; separate from continuous 85–265 VAC range |
| PSU-REQ-012 | Load-step undershoot, overshoot, settling time and step slew rate | TBD; distinct from steady-state ±2% |
| PSU-REQ-013 | Steady-state load range, no-load regulation and operating temperature range | TBD |

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
