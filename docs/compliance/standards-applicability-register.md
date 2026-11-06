# Standards and approvals applicability register — learning prototype (draft)

**Project:** 65 W isolated 19 V AC/DC SMPS, 85–265 VAC, arcade gaming equipment intended test use, Class I PE candidate, fanless ventilated enclosure concept.

**Confirmed test scope (2026-11-02):** personal, noncommercial testing on the owner's own arcade equipment; no commercial arcade installation, sale or distribution planned. This does **not** automatically waive electrical approval, safe-work or equipment requirements.

**Status:** educational engineering project only. Not certified, approved, or authorized for mains energization or arcade deployment. This is a research register, not an exhaustive legal compliance determination. Exact product classification, installation, market, and editions remain open.

| Topic | Candidate source/standard | Relevance and decision gate |
|---|---|---|
| Ontario electrical product approval | Ontario Regulation 438/07; ESA product approval guidance | Approval is generally required for electrical products used or sold in Ontario; do not assume an educational prototype is automatically exempt. Seek ESA/qualified lab guidance before energizing or using in arcade equipment. |
| Arcade machine safety | IEC 60335-2-82:2024; Canadian adoption if applicable; UL 22 for US | Evaluate scope for complete commercial amusement machine, not automatically a standalone PSU. |
| AV/ICT power supply | IEC/UL/CSA 62368-1 | Candidate only if end-use/product scope warrants; determine Canadian/US editions and PSU subassembly evaluation. |
| Insulation coordination | IEC 60664-1 and requirements of governing product standard | Determine working/transient voltages, overvoltage category, pollution degree, material group, altitude, clearances/creepage and dielectric verification. |
| Transformer safety | IEC 61558 family or IEC 62368-1 component/insulation rules, as applicable | Select qualified transformer insulation construction and verify primary-to-accessible-secondary protection. |
| Component safety | IEC 60384-14 (X/Y capacitors), IEC 60127/UL 248 fuse families, IEC 62368-1/IEC 60335 component rules | Applicable ratings and approvals to be determined per architecture. |
| Canada EMC | ISED ICES-001, ICES-003 and ICES-Gen | ICES-001 explicitly addresses standalone switched-mode PSUs; ICES-003 addresses ITE/digital apparatus and associated external PSU scenarios. Classification depends on marketing/integration. |
| US EMC | FCC 47 CFR Part 15, as applicable | Assess final arcade equipment and separately marketed supply classification and emissions authorization. |
| International EMC | CISPR 11, CISPR 32, IEC 61000-4 series, IEC 61000-3-2/-3-3 as applicable | Emissions, immunity, harmonics and flicker depend on product scope, mains interface and market. |
| Energy efficiency | Canada NRCan external power supply regulations; US DOE external power supply rules; EU ecodesign if marketed there | Determine if integrated PSU versus external adapter and other exemptions affect applicability; 90% design target is not proof of compliance. |
| EU market (if pursued) | Low Voltage Directive 2014/35/EU, EMC Directive 2014/30/EU, RoHS 2011/65/EU, WEEE and ecodesign as applicable | CE conformity obligations only if in-scope product placed on EU market; additional laws may apply. |
| Environmental/materials | RoHS, REACH, applicable Canadian/US requirements | Evaluate only for intended markets and supply-chain declarations. |
| Engineering licensing (Ontario) | Professional Engineers Act / PEO | Personal learning does not automatically require P.Eng.; responsibility for professional engineering affecting public safety may require licence/supervision. No P.Eng. or professional sign-off is claimed. |
| Arcade operation/business permits | Municipal amusement/business licensing, provincial gaming/lottery rules where applicable | Depend on whether machine is coin-operated, prize-bearing, gambling-related, location and commercial operation; distinct from PSU certification. |

## Safety and evidence gates
1. **Confirmed:** learning-only and privately owned arcade test equipment; establish an authorized qualified testing arrangement before mains energization. No claim of certification.
2. Confirm prototype intended as **internal arcade cabinet module** or **external adapter** (still unresolved).
3. Identify exact arcade load and output interface; check 19 V, 65 W and startup/transient requirements.
4. Identify jurisdiction(s) (Ontario/Canada initial assumption for research only) and intended commercial or noncommercial use.
5. Obtain qualified review of product standard selection, PE bonding, primary-secondary insulation, accessible parts, enclosure vents, EMI and thermal protection.
6. Establish laboratory safe-work procedures and approvals before any mains energization; consider low-voltage-only development or simulations first.
7. Commercial deployment/sale is **out of current scope**. Reopen third-party certification/field evaluation, EMC/regulatory conformity and business licensing before any such change.

## Official reference starting points
- Ontario Regulation 438/07: https://www.ontario.ca/laws/regulation/r07438
- ESA approval exceptions: https://esasafe.com/electrical-products/product-approval-exceptions/
- IEC 60335-2-82: https://webstore.iec.ch/en/publication/85016
- ISED ICES-001: https://www.ised-isde.canada.ca/site/spectrum-management-telecommunications/en/devices-and-equipment/radio-equipment-standards/category-ii-equipment-standards-list/ices-001-industrial-scientific-and-medical-ism-equipment
- ISED ICES-003: https://ised-isde.canada.ca/site/spectrum-management-telecommunications/en/devices-and-equipment/interference-causing-equipment-standards-ices/ices-003-information-technology-equipment-including-digital-apparatus
- PEO public protection: https://www.peo.on.ca/knowledge-centre/frequently-asked-questions/public-protection-faq

**No standards compliance or licensing exemption is asserted by this document.**
