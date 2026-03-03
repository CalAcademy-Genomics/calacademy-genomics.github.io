---
layout: default
title: QIAGEN DNeasy Plant Kit
nav_order: 1
ancestor: Protocols
parent: Extraction
---

# QIAGEN DNeasy Plant Mini Kit
This protocol is modified from the [QIAGEN Plant Mini Kit Quick Start Protocol](https://www.qiagen.com/us/resources/download.aspx?id=6b9bcd96-d7d4-48a1-9838-58dbfb0e57d0&lang=en).

{: .note }
If possible, use material taken from young, freshly formed leaves since they contain more cells per weight and will result in higher yields. If using dried material, use 20 mg of tissue. If using fresh material, use 100 mg of tissue.

### Gather the following materials _(per sample):_
#### Consumables
- (1) Sample storage tube, standard screw-cap, 2 mL, labeled
- (1) Sample storage tube, cryogenic screw-cap, labeled
- (1) QIAshredder Mini spin column (lilac), labeled
- (2) Eppendorf tube, 1.5 mL, labeled
- (1) QIAGEN DNEasy Mini spin column, labeled
- (3) QIAGEN collection tubes
- Homogenization beads, 2mm glass (soft tissues), 2.3 mm zirconia (tough tissues), or steel bearings (_very_ stubborn tissues)
#### Reagent aliquots, labeled (including your initials):
- RNAse A
- Buffer AP1 
- Buffer P3
- 100% ethanol, molecular-grade
- AW1 wash
- AW2 wash
- AE buffer

### Complete the following preparations:
1. Preheat an incubator or heat block to 65°C. 
2. Ensure Buffer AP1 is fully dissolved. If a precipitate is present, vortex or warm to 55–65 °C.
3. Pre-warm Buffer AE to 55°C.
4. Label bags of plant tissue material with the appropriate DNA extraction or sample numbers.
5. Cut tissue samples into small pieces and place into a standard screw-cap tube.

### Protocol (per sample tube)

{:style="counter-reset:none"}
6. Add approximately ¼ tube of homogenization beads and securely tighten the cap.

   {: .note }
Dry, homogenized plant tissue (especially those with fine/fuzzy trichomes) tends to misbehave due to static electricity generated during homogenization. Powdery fragments often stick to tube lids even after being spun down, which can lead to material escaping the tube when the lid is removed. Adding the AP1 buffer (Step 10) to the sample tubes _prior to homogenization_ may reduce this tendency and the risk of cross-contamination.

8. Load tubes into the [TissueLyser (click for detailed instructions](https://calacademy-genomics.github.io/protocols/TissueLyser%20II.html).
9. Select the desired preset or set a custom program. A typical setting for plant tissue disruption is two 1-2 min cycles @ 20-30 Hz. 
10. Remove tubes and check that the dried tissue is ground to a fine powder (or the fresh tissue is ground well).  Repeat homogenization step once as required. If unground tissue remains, it may be necessary to reduce the total amount of Buffer AE used in the DNA elution. 
11. Spin down samples thoroughly. 

{: .note }
Note that dried plant tissue may stick to tube lids due to static cling; open these tubes very carefully. If AP1 was added prior to homogenization, additional spin time may be necessary to reduce foaming.

{:style="counter-reset:none"}

12. Add 400 µL Buffer AP1 (if not previously included) and 4 µL RNaseA.
13. Vigorously vortex the tubes (so no tissue clumps are visible).
14. Incubate 10+ minutes @ 65°C. Invert to mix 2–3 times during incubation. 

{: .note }
If you have unground tissue, you can incubate the tubes at 65°C for up to 30 minutes, be sure to mix 2 or 3 times every 10 minutes.

{:style="counter-reset:none"}

15. Spin down tubes.
16. Add 130 µL Buffer P3. Vortex briefly and spin.
17. Incubate 5 min on ice. This step precipitates detergent from the lysis buffer, proteins, and polysaccharides. You can incubate the tubes for up to 30 mins.
18. Centrifuge 5 min @ 20,000 rcf.
19. Transfer supernatant to a new QIAshredder Mini spin column (lilac) in a 2 mL collection tube.
20. Centrifuge 2 min @ 20,000 rcf. This step filters out most precipitates and cell debris.
21. Transfer flowthrough into a new 1.5 mL tube, taking care not to disturb the debris pellet at the bottom of the collection tube.  Typically 450 µL of lysate is recovered. Dispose of the used lilac spin column and used collector tube.
22. Add 1.5 volumes Buffer AW1. Pipette or invert to mix. A precipitate may form after adding Buffer AW1, but this will not affect the DNeasy procedure.
23. Pipette 650 µL of the mixture into a new DNeasy Mini spin column (clear) placed in a 2 mL collection tube.
24. Centrifuge 1 min @ 6,000 rcf. Discard flowthrough into guanidine hydrochloride/EtOH hazardous waste container. **Reuse the collection tube.**
25. Repeat steps 23 and 24 with the remaining mixture. Discard the used collection tube.
26. Transfer the DNeasy Mini spin column to a new 2 mL collection tube.
27. Add 500 µL Buffer AW2.
28. Centrifuge 1 minute @ 6,000 rcf.
29. Verify that all liquid has moved from the spin column into the collection tube. If you see liquid still in the spin column, this means the filter in the column is clogged. Spin any clogged tubes 15 seconds @ 13,000 rcf. Pipette off and discard any supernatant still remaining in their spin columns before proceeding. Discard the flowthrough into the hazardous waste container. Re-use the spin column and collection tube.
30. Add 500 µL Buffer AW2.
31. Centrifuge 2 minutes @ 20,000 rcf. Discard flowthrough.
32. Centrifuge 15 seconds @ 20,000 rcf to dry the filter. Discard any remaining flowthrough.
33. **If the filter membrane remains significantly colored after the final washing with Buffer AW2:** Add 500 µL molecular grade EtOH to the spin column and centrifuge 2 minutes @ 20,000 rcf. Be careful not to let the flowthrough come into contact with the spin column. If this happens then do a 15 second spin at the same speed to dry the column. Discard the flowthrough into the container for guanidine hydrochloride/EtOH hazardous waste.  Discard the used collection tube.
34. Transfer spin column to a labeled 1.5 mL locking or 2 mL cryo tube.
35. Add 100 µL pre-heated (55°C) Buffer AE directly onto the filter membrane.
36. Incubate 5-10 minutes at room temperature.
37. Centrifuge 1 minute @ 6,000 rcf to elute DNA.
38. Repeat steps 35–37, using the same spin column and sample tube. Remove the spin column and discard.
39. Proceed with QC.

{: .warning }
<img src='https://github.com/CCG-CAS/gh-pages/blob/main/assets/GHS-corrosive.png?raw=true'
    alt="GHS Corrosive" 
    width='48'
    align='left'>
<img src='https://github.com/CCG-CAS/gh-pages/blob/main/assets/GHS-flammable.png?raw=true'
    alt='GHS Flammable'
    width="48"
    align='left'>
All guanidine hydrochloride/EtOH waste must be disposed of in its designated waste bottle. This includes all Buffer AL, EtOH, Buffer AW1, and Buffer AW2 waste. Buffer AW1 with EtOH added must read: “Guanidine hydrochloride - Warning! Irritant, Reactive - Do not mix with Bleach” & “Ethanol – Danger! Flammable.”
Buffer AW2 with EtOH added must read: “Ethanol – Danger! Flammable.”
