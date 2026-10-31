# 65W Isolated AC-DC SMPS (19V Output)

> **Status:** Requirements definition — engineering concept, not a validated or safe-to-build mains design.

## Objective
Develop and document a nominal 65W, 19V isolated AC-to-DC switch-mode power supply using a professional hardware engineering workflow. KiCad will be used for schematic and PCB development; GitHub will track decisions, changes, reviews, and verification evidence.

## Preliminary targets (not verified)
| Parameter | Initial target |
|---|---|
| Input | 90–264 VAC, 50/60 Hz |
| Output | 19 V DC |
| Power | 65 W nominal |
| Output current | At least 65/19 = 3.42 A |
| Efficiency | ≥88% aspirational, feasibility pending |
| Regulation | ±5% aspirational |
| Ripple | ≤190 mV peak-to-peak, measurement bandwidth TBD |
| Cooling | Passive, feasibility pending |
| Architecture | Isolated flyback candidate, not selected |

## Engineering workflow
1. Define requirements and acceptance criteria.
2. Compare architectures and identify relevant safety/EMC standards.
3. Select manufacturer reference design and key components.
4. Perform analysis and simulation; design schematic and PCB in KiCad.
5. Conduct documented reviews and verification planning.
6. Record qualified lab testing if performed; never claim unperformed testing.

## Documentation
- [Product requirements (draft v0.1)](docs/requirements.md)

## Safety notice
**Mains voltage can be lethal, and capacitors can retain hazardous energy after disconnection.** This repository is an educational engineering design study, not construction instructions or evidence of compliance. No mains-powered prototype should be energized without qualified supervision, appropriate facilities, and independent safety review. ERC/DRC are not electrical-safety certification.

## Project status
Requirements drafted; topology, insulation design, safety classification, component selection, and validation are pending.
