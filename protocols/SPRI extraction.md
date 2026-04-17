---
layout: default
title: SPRI beads (hybrid)
ancestor: Protocols
parent: Extraction
---

# SPRI bead-based DNA extraction
This protocol uses the [QIAGEN DNEasy lysis buffer](https://www.qiagen.com/ec/resources/download.aspx?id=68f29296-5a9f-40fa-8b3d-1c148d0b3030&lang=en) to release DNA, and SPRI beads to isolate it. Developed by Dr. Flávia Esteves.

{: .note }
If you are extracting DNA from small samples that are stored in EtOH, it is best to dry your sample of any EtOH before carrying out the extraction. You can do this by placing open tubes in the incubator; check on them every (approximately) 5 minutes.

### Gather the following materials _(per sample):_

#### Materials/Reagents
- (1) Eppendorf tube, locking, 1.5 mL, labeled
- (1) Sample storage tube (Eppendorf or screw-cap, 1.5–2 mL), labeled
- Proteinase K <code style="color : blue">(small blue tube)</code>
- ATL buffer <code style="color : blue">(large blue tube)</code>
- SparQ PureMag SPRI beads (aliquot, at room temperature)
- Magnetic bead separation rack (suitable for tube/plate size)
- 100% ethanol (EtOH), molecular-grade (~350 µL / sample)
- Water, molecular-grade (and 0.1X TE buffer, if eluting/storing in TE)
- Falcon tube or similar container for ethanol wash (minimum volume ~400 µL / sample)
- Plastic trough (for ethanol wash, if using a multi-channel pipette)
- PCR tubes (if larger tubes are used, ensure wash volume is sufficient to cover pelletized beads)

### Protocol (Lysis)

1. Cut up tissue into very small (~25 mg) pieces and add to the locking tube.
    Cut tissue on either a glass petri dish or a piece of parafilm. Be sure to use clean forceps and a clean scalpel/razor blade for each sample. You may reuse your forceps if utilizing the “Germinator”, but please return forceps to the dirty container when finished.
2. **Add 180 µL ATL Buffer** <code style="color : blue">(large blue tube)</code> to each 1.5 mL locking tube.
    The ATL Buffer may precipitate at room temperature. Incubate at 55°C for a few minutes and the precipitate will re-dissolve.
3. **Add 20 µL proteinase K** <code style="color : blue">(small blue tube)</code> to each locking tube.

    {: .note}
    When extracting insect tissues, we recommend increasing proteinase K volume to 60 µL per sample. For very small samples, the total volume of lysis buffer and proteinase K can be proportionally reduced.

4. Vortex tubes and incubate at 55°C 4 hours–overnight. Use a rocking platform or thermal mixer, if available.
5. **Remove digested samples from the incubator and spin down.**

    {: .caution}
    Be mindful when opening your tubes as the lids can be dirty with solution after being inverted during incubation. If at any point your gloves become dirty, change them. Be very careful not to allow any cross-contamination of the samples.

### Protocol (Extraction)
6. Prepare a fresh aliquot of 80% EtOH using molecular-grade water. If using a multi-channel pipette, dispense into a plastic trough immediately prior to wash steps.

    {: .note}
    The volume of 80% EtOH is not critical, provided that it is sufficient to completely cover the pelletized SPRI beads. 200 µL is typical for extractions in PCR tubes, while 700 µL is typical for 1.5 mL Eppendorf tubes. When calculating the volume of ethanol wash to prepare, keep in mind that you will perform two wash steps (e.g., 2·200 = 400 µL / sample).

7. Bring beads to room temp. and vortex thoroughly. Re-vortex periodically if settling is present.
8. Spin down samples and 2X the volume of bead solution relative to the volume of lysis buffer (e.g., 400 µL SPRI beads for 200 µL lysis buffer). Mix thoroughly by pipetting, or vortex and briefly spin.
9. Incubate at least 5 min at room temperature (off magnet). 
10. Place sample tube(s) on magnet to pelletize beads and bound DNA. Keep on magnet until elution.
11. Incubate at room temperature until beads are pelletized and supernatant is clear (~5 min).
12. Remove and discard supernatant, taking care not to disturb the beads and bound DNA.
13. Add sufficient 80% ethanol wash to completely cover the pelletized beads. Incubate 30 sec. at room temperature. Remove and discard wash.

    {: .warning }
    <img src='https://github.com/CCG-CAS/gh-pages/blob/main/assets/GHS-flammable.png?raw=true'
    alt='GHS Flammable'
    width="48"
    align='left'>
    Properly dispose of ethanol in the designated ethanol waste containers. Ethanol is a flammable chemical and cannot be disposed of in the trash or down the sink. 

14. Repeat wash step once for a total of two washes. Remove all visible liquid. If necessary, briefly spin down, return to magnet, and remove remaining ethanol with a small (e.g., p10) pipette.
15. Air-dry beads for 1-2 minutes at room temperature, on the magnet with lid open.

    {: .caution }
    Do not over-dry the beads! Beads are sufficiently dry when pellets are dark and glossy, but all visible liquid has evaporated. If pellets change to light brown or start to crack, they are too dry.

16. Remove sample tubes from magnet and resuspend beads in molecular-grade water or TE buffer. Pipette thoroughly to mix, or vortex and spin. 

    {: .note }
    Some buffer is often lost in the bead pellet during elution and transfer. Consider eluting in a slightly larger volume (appx. +2 µL) than what will be transferred and retained in Step 19 (and/or measuring the final volume by pipetting). Example: elute in 12 µL of buffer, but transfer only 10 µL.

17. Incubate at least 2 minutes at room temperature (off magnet) to allow DNA to elute from beads.
18. Return samples to magnet and incubate at room temperature until solution is clear (~5 min).
19. Transfer samples to new tubes and discard used tubes with beads. Samples can be stored at -20 °C.
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
