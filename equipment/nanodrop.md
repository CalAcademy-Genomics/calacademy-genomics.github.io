---
layout: default
title: NanoDrop
parent: Quantification
parent: Lab Equipment
ancestor: Protocols
ancestor: Lab Equipment
---

# Checking DNA purity with the NanoDrop Spectrophotometer

{: .note } 
The CCG currently maintains two NanoDrop devices: the newer NanoDrop Ultra and an older NanoDrop 2000C. Both function similarly, except that the Ultra is a self-contained unit with touchpad controls while the 2000C is operated by a separate computer. Full user guides are available from ThermoFisher ([Ultra](https://documents.thermofisher.com/TFS-Assets/CAD/Product-Guides/nanodrop-ultra-user-guide-en.pdf), [2000C](https://documents.thermofisher.com/TFS-Assets/CAD/manuals/NanoDrop-2000-User-Manual-EN.pdf)).

{: .note } 
Although NanoDrop spectrophotometers will display a concentration value, this is generally not considered an accurate measurement. Nucleic acid concentrations can be measured accurately using a fluorometer, such as the Qubit.

## Protocol
### Setup
1. Power on the device.
   - **Ultra:** Press the vertical black button on the lower right side of the device and allow the instrument to conduct its routine verification of wavelength.
   - **2000C:** Power on the control computer and double-clock the "NanoDrop 2000C" icon on the desktop.
2. Select the appropriate assay.
   - **Ultra:** Select the "dsDNA" icon. On the "dsDNA Setup" menu, accept the default values or press "X" to proceed to measurement.
   - **2000C:** With the group set to CLASSIC, click on the option for NUCLEIC ACID. Allow the instrument to conduct its routine verification of wavelength.
3. Raise the device arm and wipe down the pedestal with a clean, damp Kimwipe. *Gently* lower the arm.
4. To blank the instrument, raise the arm and load 1–2 µL of AE buffer  (or water, or TE buffer, whatever your DNA is resuspended in) onto the pedestal. Lower the arm and click BLANK.

### Data Collection
5. Raise the device arm and wipe down the pedestal with dry Kimwipe.

   {: .note } 
   Both NanoDrop instruments have an "Auto-Measure" feature, in which the instrument will take a new reading automatically every time the arm is lowered. 
   - **Ultra:** If Auto-Measure is ON, the icon of a running man will be bright blue. If Auto-Measure is OFF, the icon will be dark.
   - **2000C:** Auto-Measure!
   
7. Type your SAMPLE ID for your first sample in the top right corner.
8. Gently mix your sample first for accurate concentration reading.
9. Load 1–2 µL of your sample onto the pedestal. Lower the arm and click MEASURE.

   {: .note } 
   Both NanoDrop devices save measurement data for export. 
      - **Ultra:** Experiments are saved automatically and can be accessed from the clipboard icon on the left navifation bar.
      - **2000C:** You will be asked to name the NanoDrop workbook you are creating. Navigate to your Molecular folder, edit filename, and save workbook (leave as .twbk file).

10. Your DNA concentration value will appear in the top right corner of the screen with the units in ng/µL. An ideal DNA concentration for PCR will be between 25–100 ng/µL. Ideal A260/280 and A260/230 ratios will be about 2.0.

    Example of results for a good quality nucleic acid sample:

    <img src='https://github.com/CCG-CAS/gh-pages/blob/main/assets/nanodrop.jpg?raw=true'
      alt="Nanodrop curve"
      width='300'>

    [This useful guide](https://tools.thermofisher.com/content/sfs/brochures/TN52646-E-0215M-NucleicAcid.pdf) to interpreting NanoDrop DNA/RNA curves is available from ThermoFisher.
11. Once you have finished reading all of your samples, wipe down the NanoDrop pedestal with a damp Kimwipe to clean it and return the arm of the instrument to the lowered position.
12. To export your table, click on the REPORTS option in the lower left corner. Highlight all of your samples that you wish to export and click EXPORT. Save as an .xml file (to open later in excel) on a flash drive. Close the software when done.

{: .note }
For samples with DNA concentrations >100 ng/µL, a dilution of 25 ng/µL should be made to work with for PCR.
