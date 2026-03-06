---
layout: default
title: TapeStation
parent: Quantification
ancestor: Protocols
ancestor: Lab Equipment
---

# Checking DNA fragment length with the TapeStation

The TapeStation is an automated electrophoresis solution for quality control of samples of DNA and RNA. This also contains a quantification estimate for your samples as well. 

**If you are new to the instrument, please ask CCG Staff for training.**

### Setup

1. Take appropriate DNA ScreenTape, buffer, and ladder (either Genomic DNA or High Sensitivity D1000) out of the gel room fridge. Let these reach room temperature (15-30 min).
    - Make sure you get the correct reagents. gDNA and D1000 reagents are **NOT** interchangeable.
    - When opening the ScreenTape device foil bag for the first time, remember to write the opening date onto the bag.
    - Sign-out number of runs, including ladder, and what chip you will use on sheet by computer (HS# = High Sensitivity D1000; G# = Genomic DNA).
2. Make sure that your sample concentrations and size range fall into the quantitative range of the kit that you selected. Measure the concentrations using Qubit. Dilute the samples if needed using water or 0.1X TE buffer.
    {: .note } 
    The requirements are flexible to some degree. Refer to the [orientation slides](https://drive.google.com/drive/folders/1wcy_76QfHGXK6I3UQ0IUnglkVranbxjw) on the CCG lab users drive.

    |                       | HS D1000 ScreenTape | gDNA ScreenTape |
    |:----------------------|:--------------------|:----------------|
    | Sizing range (bp)     | 25–1,000            | 200–60,000      |
    | Concentration (ng/µL) | 0.01–1              | 10–100          |

3. Switch on the computer and the instrument and launch the Agilent TapeStation Controller Software.
    {: .note }
    The ScreenTape should be used within two weeks after opening the ScreenTape device foil bag.

### TapeStation Workflow

1. Open the lid of the TapeStation. Flick the ScreenTape device once to reduce air bubbles and insert it into the ScreenTape nest of the TapeStation instrument – make sure that the barcode is facing the reader (green light) on the right side of the nest.
2. Select required sample positions and name your samples in the TapeStation Controller Software. Ladder is exclusively loaded from location A1 on the tube strip holder.
    {: .note }
    For best sizing and molarity quantification results, a ladder per ScreenTape device is recommended. Alternatively, an electronic ladder is available for HS D1000 and can be selected in the Agilent TapeStation Controller software by right-clicking the mouse when over the A1 well and choosing “Use Electronic ladder”. Electronic ladder CANNOT be used with Genomic DNA kits.
3. Verify that there are sufficient tips for your run, and that the waste bin is not too full.
4. Take out the appropriate number of strip tubes and tube caps from your lab’s drawer. **Use only USA Scientific strip tubes that we stock in the lab.**
5. Vortex and spin down buffer, ladder, and samples.

|                    | HS D1000 ScreenTape | gDNA ScreenTape |
|:-------------------|:--------------------|:----------------|
| Sample buffer (µL) | 2                   | 10              |
| Sample/Ladder (µL) | 2                   | 1               |

6. Add sample buffer to each well of the strip tube.
7. If using a ladder, add a DNA ladder to the first tube (A1).
8. Add sample to each sample tube.
9. Put caps on the strip tube and mix liquids using the IKA vortexer at 2,000 rpm for 1 min. When you press “Start”, the vortexing automatically lasts 1 min. Centrifuge the strip tube.
10. Carefully remove caps of the strip tubes. Visually confirm that the liquid is positioned at the bottom. If not, put the cap back on and spin down again.
11. Place the strip tubes in the holder with the ladder (if using) in the A1 position.
12. Close the TapeStation lid.
13. In the software, select the wells in the graphic for your ladder and samples. They will come up on the right side of the screen.
14. In the area on the right side, name each well with your sample number/ID.
15. **Verify that the strip tube caps are removed and the tip waste bun is not full.**
16. Press ‘Start.’ The run will begin, and display an estimated run time.

### Cleanup
1. Empty the tip waste bin and clean it with distilled water, dry, and put back in the instrument.
2. Throw away the used strip tube.
3. Put the ScreenTape back into the foil bag, seal the bag tightly with lab tape.
4. Mark on top of the bag how many reactions have been used from that ScreenTape.
5. Take the ScreenTape bag, buffer, and ladder back to the gel room refrigerator.
6. Switch off the TapeStation instrument and laptop if you are the last user of the day.

### Analysis:
1. The TapeStation Analysis software should open by itself within a minute. If it does not, click into the “TapeStation Data” folder on the desktop, find the folder with today’s date. There should be the analysis file for your data. If you click on it, it will open in the analysis software.
    {: .note }
   The TapeStation Analysis software is available as a [free download](https://www.agilent.com/en/product/automated-electrophoresis/tapestation-systems/tapestation-software/tapestation-software-379381) from Agilent for windows users.
2. What comes up first looks like a gel image. Click on the Electropherogram to be able to look at each sample individually. The trace shows you basically what the gel would look like if you sliced vertically through a gel. The area under the curve is the brightness of the gel or the amount of the DNA. The x-axis is the size of the DNA and the y-axis is the intensity/how much DNA is at that size.
3. To save the file, go to File > Create Report. Save the pdf to your lab’s folder. You can then email the pdf to yourself.
4. Close the Analysis and Controller software.
5. Turn off the TapeStation from the button on the machine.
6. Shut down the computer.
