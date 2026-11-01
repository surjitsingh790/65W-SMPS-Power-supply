# Preliminary engineering requirements — draft

| ID | Requirement | Status |
|---|---|---|
| PSU-REQ-001 | Isolated AC-to-DC mains-powered supply | Project objective; safety design TBD |
| PSU-REQ-002 | Nominal regulated output: 19 V DC | Proposed |
| PSU-REQ-003 | Rated output power: 65 W (approximately 3.42 A at 19 V) | Proposed |
| PSU-REQ-004 | Continuous operating input: **85–265 V AC RMS, 50/60 Hz** | **Confirmed project requirement (2026-10-31)** |
| PSU-REQ-005 | DC regulation, dynamic load response, startup/hold-up | TBD |
| PSU-REQ-006 | Efficiency, no-load consumption and temperature limits | TBD |
| PSU-REQ-007 | Output ripple and noise <=190 mV peak-to-peak | Provisional; 20 MHz bandwidth proposed; measurement setup/test conditions TBD |
| PSU-REQ-008 | Protection: OVP, OCP, SCP, OTP and inrush | TBD |
| PSU-REQ-009 | Isolation, creepage, clearance, EMI and applicable safety standard | TBD; qualified review required |
| PSU-REQ-010 | Architecture | Not selected; see ADR-001 |
| PSU-REQ-011 | AC surge, abnormal input, brownout and recovery behavior | TBD; separate from continuous 85–265 VAC range |

## Universal input engineering implications
- Ideal rectified peak bus spans approximately 120.2 V at 85 VAC to 374.8 V at 265 VAC, **not** including bridge losses, bus ripple, surges or tolerances.
- The bulk capacitor voltage rating, ripple-current rating and hold-up time must be validated; do not assume 400 V is adequate.
- MOSFET stress includes DC bus, reflected voltage, leakage overshoot and transient margin; a nominal voltage class is not a selection.
- Magnetics, current limit, thermal losses and control must be checked at low line, high line and intermediate points.
- Confirm mains frequency tolerance, input power factor/harmonic applicability, EMI, inrush and surge immunity in a safety review.
- Verification matrix: 85/115/230/265 VAC × no-load/light/half/full load as applicable, at 50 and 60 Hz; acceptance criteria still TBD.

**Note:** These are design inputs, not demonstrated performance or safety claims. No mains-powered prototype is approved for energization.
