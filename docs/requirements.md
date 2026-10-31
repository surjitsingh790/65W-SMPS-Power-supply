# PSU-65-19 — Product Requirements Document

- **Document ID:** PRD-001
- **Revision:** 0.1 (draft)
- **Status:** Open for engineering review
- **Scope:** 65W isolated, mains-input AC-DC SMPS; 19V DC output

## 1. Objective
Define measurable targets and unresolved design decisions before schematic capture. These are proposed targets, **not measured results or compliance claims**.

## 2. Electrical requirements

| ID | Requirement | Proposed acceptance criterion | Verification approach |
|---|---|---|---|
| REQ-001 | AC input | 90–264 VAC, 50/60 Hz | Design analysis; qualified laboratory test |
| REQ-002 | DC output | Nominal 19 V | Design analysis; qualified laboratory test |
| REQ-003 | Rated power | 65 W continuous, subject to ambient/thermal feasibility | Thermal analysis; qualified load test |
| REQ-004 | Rated output current | ≥3.42 A at rated output | Analysis; qualified load test |
| REQ-005 | Voltage regulation | ±5% across specified line/load/temperature, ranges TBD | Qualified line/load test |
| REQ-006 | Output ripple | ≤190 mV peak-to-peak; bandwidth and test method TBD | Qualified oscilloscope test |
| REQ-007 | Full-load efficiency | ≥88% initial goal; line/ambient conditions TBD | Loss budget; qualified power measurement |
| REQ-008 | Protections | OCP, SCP, OVP, OTP; trip/recovery thresholds TBD | Fault analysis; qualified fault testing |
| REQ-009 | Cooling | Passive; 0–40°C ambient initial goal | Thermal model; qualified temperature test |
| REQ-010 | Isolation | Primary-to-secondary isolation appropriate to end-product safety classification | Standards review; qualified safety laboratory |
| REQ-011 | EMI/EMC | Applicable conducted/radiated emissions limits TBD | Standards review; qualified EMC laboratory |

**Calculation:** 65 W / 19 V = 3.421 A. For 19 V at 3.42 A, delivered power is approximately 64.98 W.

## 3. Architecture candidates
An isolated flyback converter is the initial candidate, **not an approved topology**. Compare alternatives based on cost, efficiency, control complexity, transformer availability, thermal performance, and EMC before selection. Prefer reputable manufacturer reference designs.

## 4. Safety and regulatory planning
- Determine intended market, installation category, product class, pollution degree, altitude, enclosure, and user accessibility.
- Identify applicable editions and national deviations of IEC/UL/CSA 62368-1 and relevant EMC requirements; confirm applicability with qualified specialists.
- Document insulation system, creepage/clearance, transformer construction, protective devices, discharge provisions, and abnormal-operation analysis.
- No mains energization or hazardous-voltage prototyping without qualified supervision, suitable laboratory facilities, and independent safety review.
- KiCad ERC/DRC and simulation do not establish isolation safety or regulatory compliance.

## 5. Design and documentation deliverables
- Architecture trade study and decision record
- Reference-design/controller selection rationale
- Calculations and simulation evidence
- KiCad schematic, PCB, design-rule reports, and BOM
- Design-review checklist and verification matrix
- Test results only where actually obtained, with conditions and instruments recorded

## 6. Open decisions
1. End use, intended markets, enclosure, output connector, and load profile
2. Safety classification and relevant standards/editions
3. Topology, controller, transformer and isolation strategy
4. PCB size/layer count, thermal and EMC feasibility
5. Ripple bandwidth, regulation test matrix and efficiency conditions
6. Laboratory capabilities and prototype test authorization

## 7. Milestone 1 exit criteria
- [ ] Review and approve electrical requirements
- [ ] Record architecture comparison
- [ ] Identify safety/EMC standards and assumptions
- [ ] Define verification matrix and review responsibilities
- [ ] Resolve or explicitly track outstanding decisions

## Revision history
| Revision | Change |
|---|---|
| 0.1 | Initial draft for review |
