---
layout: default
title: QIAGEN DNeasy B&T Kit (Blood)
nav_order: 1
ancestor: Protocols
parent: Extraction
---

# QIAGEN DNeasy Blood & Tissue Kit (Blood)
This protocol is modified from the [QIAGEN Blood & Tissue Kit Handbook](https://www.qiagen.com/ec/resources/download.aspx?id=68f29296-5a9f-40fa-8b3d-1c148d0b3030&lang=en).

For (non-blood) tissue samples, click [here](https://calacademy-genomics.github.io/protocols/QIAGEN%20DNeasy%20(Tissue).html).

### Gather the following materials _(per sample):_

#### Consumables
- (1) Eppendorf tube, locking, 1.5 mL, labeled
- (1) QIAGEN DNeasy Mini spin column and collection tube, labeled
- (2) QIAGEN collection tubes (additional)
- (1) Sample storage tube (Eppendorf or screw-cap, 1.5–2 mL), labeled
#### Reagent aliquots, labeled (including your initials):
- Proteinase K <code style="color : blue">(small blue tube)</code>
- AL buffer <code style="color : green">(green tube)</code>
- AW1 wash <code style="color : black">(white cap)</code>
- AW2 wash <code style="color : blue">(blue cap)</code>
- AE buffer <code style="color : olive">(yellow tube)</code>
#### Additional reagents, labeled (including your initials):
- 100% ethanol, molecular-grade
- Phosphate-buffered saline (PBS, 1X)

### Protocol

{: .note}
The QIAGEN DNeasy Blood & Tissue Kit can handle a range of sample types. The ATL buffer is used for solid tissue and is omitted when working with blood.

{: .caution}
Be mindful when opening your tubes as the lids can be dirty with solution after being inverted during incubation. If at any point your gloves become dirty, change them. Be very careful not to allow any cross-contamination of the samples.

1. Add the following to each tube:
>
> | Blood Sample Type        | ProK (µL) | Blood (µL) | 1X PBS (µL) | Total Volume (µL) |
> |:-------------------------|:----------|:-----------|:------------|:------------------|
> | Fresh, non-nucleated     | 20        | 50–100     | 100–150     | 220               |
> | Fresh, nucleated         | 20        | 5-10       | 190–195     | 220               |
> | NAP-preserved, nucleated | 40        | 70         | 180         | 290               |
> | LB-preserved, nucleated  | 40        | 50         | 180         | 270               |
>
> Note that liquid blood samples must be treated with an anticoagulant at the time of collection, and that undiluted nucleated blood can become *extremely* viscous as red blood cells release their DNA into solution. NAP = nucleic acid preservation buffer; LB = lysis buffer. Values for preserved, nucleated blood based on SOPs from the Galápagos Lab (Jack Dumbacher / Jaime Chaves), which primarily works with avian specimens. 
>
> {: .warning}
> <img src='https://github.com/CCG-CAS/gh-pages/blob/main/assets/ISO-biohazard.png?raw=true'
    alt='ISO Biohazard'
    width="48"
    align='left'>
> The CCG is a BSL-1 facility, and samples must meet USDA standards for BSL-1 before entering the lab space. Certain sample types (e.g., bird blood) may require elevated biosafety levels. When in doubt, assume a higher biosafety level and meet with Grace Kim *before* bringing these samples into the CCG.

2. **Add 200 µL AL Buffer** <code style="color : green">(green tube)</code> to each tube. Use filtered tips here as the soapy consistency of this buffer can otherwise cause the liquid to travel up the pipette shaft and into the pipette.
3. Vortex tubes and incubate at 56°C 10 min–overnight. Use a rocking platform or thermal mixer, if available.
4. **Remove digested samples from the incubator and spin down.**
5. **Add 200 µL 100% EtOH** to each tube. Use the same precautions as in step 6, including the use of filtered tips.
6. Ensure your tubes are locked closed. **Vortex thoroughly; spin down.**
> {: .note} 
> A white precipitate may form on addition of Buffer AL and ethanol. This precipitate does not interfere with the DNeasy procedure.

7. Pipette the mixture including any preciptate (≈600 µL) to DNeasy Mini Spin Columns with collection tubes.  
> Use a P1000 with a filtered tip. When taking up the solution, avoid clumps of undigested tissue to prevent clogging the filter. Be sure not to touch or puncture the spin column filter with your pipette tip. Very viscous samples may be easier to transfer with a wide-bore pipette.

8. **Centrifuge spin columns 1 min at 6,000 g** (8,000 rpm). 
> When you remove the tubes from the centrifuge, verify that all liquid transferred from the spin column to the collection tube. Discard flowthrough into the Hazardous Waste container. If you see liquid still in the spin column, this means the filter in the column is clogged. Before proceeding, spin those clogged tubes again for 15 seconds at 13,000 x g (12,700 rpm). If the filter remains clogged, use a pipette to aspirate off and discard the supernatant that is in the spin column before proceeding.

9. Transfer spin columns to new 2 mL collection tubes.
10. **Add 500 µL AW1 Buffer** <code style="color : black">(white cap)</code> to spin columns.
11. **Centrifuge spin columns 1 min at 6,000 g** (8,000 rpm). Discard flowthrough.
12. Transfer the spin columns to new 2 mL collection tubes.
13. **Add 500 µL of AW2 Buffer** <code style="color : blue">(blue cap)</code> to each of the spin columns.
14. **Centrifuge spin columns 3 min at 20,000 g** (14,000 rpm). 
> {: .caution}
> When removing the spin columns from the centrifuge, be careful not to let the flowthrough come into contact with the spin column. It is important to dry the membrane of the DNeasy Mini spin column, since residual ethanol may interfere with subsequent reactions. If this happens, spin for 15 sec at the same speed to dry the column again. Discard flowthrough.

15. Transfer the spin columns to labeled, 2.0 mL screw-cap tubes. 
> {: .note}
> It is very important at this step that you transfer the correct spin column to the correct labeled 2.0 mL storage tube! Be sure tubes are labeled with your extraction ID and extraction date.

16. **Add 50–200 µL AE Buffer** <code style="color : olive">(yellow tube)</code> to each of the spin columns.
> {: .note} 
> 30 µL is the minimum elution volume required to saturate the filter.

{:style="counter-reset:none"}
17. **Incubate 1–3 min at 55 °C** to increase DNA yield.
18. **Centrifuge 1 min at 6,000 g** (8,000 rpm).
19. Discard your spin columns. Cap your tubes (with labels).
20. Quantify your DNA concentration using the [Qubit Flurometer](https://ccg-cas.github.io/protocols/qubit.html).
21. Analyze your DNA purity using the [Nanodrop](https://ccg-cas.github.io/protocols/nanodrop.html).

{: .warning }
<img src='https://github.com/CCG-CAS/gh-pages/blob/main/assets/GHS-corrosive.png?raw=true'
    alt="GHS Corrosive" 
    width='48'
    align='left'>
<img src='https://github.com/CCG-CAS/gh-pages/blob/main/assets/GHS-flammable.png?raw=true'
    alt='GHS Flammable'
    width="48"
    align='left'>
All guanidine hydrochloride/EtOH waste must be disposed of in its designated waste bottle. This includes all Buffer AL, EtOH, Buffer AW1, and Buffer AW2 waste.

{: .greentip}
When extracting many samples at once, you can use the same tip to add the wash buffers. Be very careful when doing this to not let the tip come into contact with any of the tubes. Also, be very careful to eject the buffer slowly against the back wall of the spin column to reduce splashing, and change your tip when changing buffers.
