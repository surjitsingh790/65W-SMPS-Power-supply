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
| PSU-REQ-016 | **Preliminary cooling architecture: passive natural convection without fan** | **Selected for feasibility evaluation (2026-11-01)**; subject to enclosure, component and thermal verification |
| PSU-REQ-017 | **Preliminary enclosure: ventilated, fanless** | **Selected for concept evaluation (2026-11-01)**; material, dimensions, vents and ingress protection TBD |
| PSU-REQ-018 | **Preferred concept orientation: vertical, lower inlet and upper outlet airflow** | Preliminary mechanical/thermal hypothesis; installation restrictions and alternate orientations TBD |
| PSU-REQ-019 | Enclosure must prevent access to hazardous live parts and meet applicable fire, insulation, mechanical and ingress criteria | Mandatory safety design objective; standard/classification and acceptance criteria TBD |
| PSU-REQ-020 | **Class I protective-earth safety architecture** | Selected for **preliminary evaluation** (2026-11-01), not yet safety approved; metal enclosure and bonding concept TBD |
| PSU-REQ-021 | Protective-earth continuity, accessible conductive-part bonding and fault protection | Safety objectives; acceptance limits and test method require applicable standard and qualified review |
| PSU-REQ-022 | Primary-to-accessible-secondary transformer insulation and PCB insulation coordination | Safety objectives; insulation grade, working voltage, creepage/clearance, dielectric tests TBD |
| PSU-REQ-023 | Safety-rated EMI capacitors and protective-conductor/touch-current limits | TBD after standard and circuit architecture selection |
| PSU-REQ-024 | **Intended end use: 19 V / 65 W PSU for arcade gaming equipment** | Confirmed application intent (2026-11-01); exact game/load and installation TBD |
| PSU-REQ-025 | **Preliminary integration concept: PSU installed within an arcade cabinet** | Proposed, **not yet confirmed**; external adapter remains an alternative |
| PSU-REQ-026 | Product safety standards applicability: IEC 60335-2-82, UL 22, IEC 62368-1 | Candidates only; market, complete-machine classification and national editions TBD |
| PSU-REQ-027 | Verify actual arcade load requires 19 V DC and stays within 65 W, including startup and transients | Pending load/interface characterization; not a universal arcade PSU |
| PSU-REQ-028 | **Project validation scope: personal noncommercial testing on owner's own arcade equipment** | **Confirmed (2026-11-02)**; no commercial arcade installation, sale or distribution planned |

## 40°C continuous full-load thermal requirement
- The 40°C value refers to **ambient air around the intended product**, not component surface or semiconductor junction temperature. Define measurement location and enclosure/mounting configuration before validation.
- Rated output of 19 V at 65 W must be sustainable at 40°C ambient without output-power derating over the confirmed 85–265 VAC, 50/60 Hz operating input range.
- **Natural convection (fanless) is the selected preliminary cooling approach**, not yet demonstrated to meet requirements. Revisit if thermal/safety margins are inadequate. PCB area, copper, heatsinks, vent geometry, allowable orientations and accessible surface temperatures remain open.
- Check MOSFET and rectifier junction temperatures, transformer winding/core hot spots and insulation class, electrolytic capacitor case temperature and lifetime, control IC limits, PCB materials and enclosure surfaces against actual part specifications and safety criteria. Allocate reliability and measurement margins.
- Illustrative thermal derating above 40°C is **not** an approved operating curve. Define any high-temperature operation and power limits separately.
- Proposed verification: safety-reviewed controlled chamber at 40°C with intended enclosure/orientation, continuous rated load and 85/115/230/265 VAC corners (50/60 Hz as relevant); measure calibrated input/output power and component hot spots after a documented thermal-equilibrium criterion. Verify output regulation and protective behavior; document instrumentation uncertainty.
- **No mains-powered thermal testing until qualified review and a safe test procedure are approved.**

## Passive cooling design and verification considerations
- Enclosure: **ventilated fanless concept selected for evaluation**. Evaluate lower inlet/upper outlet vents in preferred vertical orientation; vent placement, fire containment, ingress, accessibility of hazardous voltages, installation clearances and accessible surface temperatures require qualified safety review. No vent geometry or production enclosure is approved yet.
- PCB: spread heat with appropriately sized copper areas and thermal vias within each permitted net/isolation region. Avoid compromising creepage, clearance or EMI with copper near the isolation barrier or high-dv/dt nodes.
- Heatsinks: evaluate component power loss and thermal resistance chain (junction-to-case, interface, heatsink-to-ambient). Electrically live heatsinks require safe insulation/accessibility arrangements and isolation verification.
- Capacitors should be separated from hot rectifiers, magnetics and heatsinks where practical; check ripple-current heating and lifetime at measured temperature.
- Passive thermal validation must use intended enclosure, mounting orientation and still-air environment at 40°C ambient with continuous 65 W output. Measure hot spots at low/high AC line after documented thermal equilibrium, compare to component ratings and margin criteria.
- If passive cooling cannot meet all electrical, safety and lifetime limits, redesign heat paths, PCB/enclosure or reopen the cooling architecture decision. Do not assume a fan is automatically required.

## Intended application and standards scoping — arcade gaming equipment
- **Confirmed testing scope:** educational prototype, intended for personal testing with the owner's own arcade equipment only. No commercial deployment, product sale or certification claim is planned. Private use does not by itself establish exemption from Ontario electrical approval or safe testing obligations.
- Intended end use: isolated 19 V, 65 W PSU for **arcade gaming equipment**, not an unspecified universal adapter.
- Proposed first integration scenario: installed within an arcade cabinet. **User has not yet confirmed internal vs external mounting.** If external, reevaluate enclosure accessibility, cabling, mains connector, adapter-specific testing and cooling.
- The arcade machine may include processors, displays, motors, solenoids and other loads; the PSU is not assumed to replace existing 5 V, 12 V or 24 V rails. Verify exact 19 V load, 65 W steady-state budget, inrush and dynamic load behavior before electrical design.
- Candidate safety standards for applicability review: **IEC 60335-2-82:2024** (commercial amusement machines; https://webstore.iec.ch/en/publication/85016), **UL 22** (commercial amusement/gaming machines, US; https://www.shopulstandards.com/ProductDetail.aspx?productId=UL22), and **IEC 62368-1:2023** (applicable AV/ICT equipment, subassemblies and external PSUs; https://webstore.iec.ch/en/publication/69308). None is assigned as the governing standard yet.
- Decide target market(s), intended indoor environment, machine-level versus PSU-level assessment, installation/accessibility and relevant national editions with qualified compliance review. Do not assume arcade equipment is always ICT equipment.
- Retain Class I PE architecture as a **candidate** pending cabinet grounding/interface details; PE bonding and insulation requirements must be reviewed for the integrated product.
- Identify applicable conducted/radiated EMI, immunity, mains harmonics, surge and efficiency requirements based on market and end product.

## Class I protective-earth architecture — preliminary evaluation
- Use distinct L, N and PE conductors. PE is a protective connection, **not** an operating return; never substitute neutral for PE.
- If accessible conductive enclosure panels or heatsinks require protective bonding, specify reliable dedicated PE termination, bonding across panels, corrosion/loosening resistance, fault-path continuity and verification per the applicable standard.
- **The 19 V secondary return is not automatically bonded to PE**; decide floating versus earth-referenced output based on system requirements, EMC, touch-current and fault analysis.
- Class I earthing of a metal enclosure does **not** replace the insulation protection required between hazardous mains primary and an accessible isolated 19 V output. Define transformer insulation system, winding arrangement, auxiliary/feedback barrier crossings, dielectric strength and relevant construction tests.
- Determine creepage (along insulating surfaces) and clearance (through air) from the selected standard and design conditions: working/transient voltage, insulation grade, pollution degree, material group, altitude and environment. No generic fixed millimeter spacing is approved.
- Review appropriate safety-certified Y capacitors for any EMI paths crossing safety barriers or to PE; establish touch current, protective-conductor current and fault limits. Do not use ordinary capacitors in safety-critical positions.
- Ventilated enclosure requires assessment of access to live parts through openings, conductive-panel PE bonding, fire containment, cable entry/strain relief, mechanical strength, ingress and accessible temperatures.
- Select the product safety and EMC standards based on intended use and sales regions (IEC/CSA/UL 62368-1 only if applicable), then derive measurable pass/fail criteria and qualified review gates.
- Required safety verification planning includes PE continuity, dielectric withstand, insulation assessment, leakage/touch current, abnormal operation and accessible-part checks. **No mains prototype energization until qualified safety review and controlled test approval.**
- Class I is a **candidate under evaluation**, not a compliance claim or final approved architecture. Compare against Class II if system requirements warrant.

## Enclosure concept acceptance and thermal verification
- Preferred concept mounting: vertical with a continuous unobstructed natural-convection path from lower inlets to upper outlets; define mounting hardware, orientation tolerance, free space around vents and whether horizontal mounting is permitted.
- Do not assume airflow direction/strength without enclosure testing; avoid positioning electrolytic capacitors directly in the hottest rising-air stream where practical.
- Define enclosure construction, openings, mechanical strength, cable strain relief, accessible metalwork and protective-earth or double-insulation strategy after selecting the applicable product safety standard. Vent openings must not permit contact with hazardous parts or compromise fire containment.
- Document intended indoor/outdoor use, dust/humidity/liquid ingress expectations, installation surfaces and maximum accessible-surface temperatures; do not claim an IP rating or certification before testing.
- Before any powered prototype tests, obtain qualified safety review of mains isolation, grounding, guarding, protective components and laboratory procedures.
- Thermal verification plan: test assembled enclosure in still air at 40°C ambient, preferred vertical mounting, continuous 65 W, at 85/115/230/265 VAC and relevant frequencies; use calibrated thermocouples for key components and measure accessible surfaces. Establish temperature stabilization criterion and uncertainty margins before acceptance.
- Repeat tests for any permitted mounting orientations and foreseeable vent obstructions; define whether obstruction is an abnormal-condition safety test rather than a rated-operation test.
- Compare measured temperatures and efficiency/regulation against component ratings and defined reliability/safety margins; redesign vents, heatsinks or PCB heat paths if needed.

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
