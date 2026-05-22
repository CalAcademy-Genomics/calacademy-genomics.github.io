---
layout: default
title: ExoSAP-IT PCR purification
ancestor: Protocols
parent: DNA & sample cleanups
---

# ExoSAP-IT PCR purification

{: .caution }
Enzymatic cleanup of PCR products can be used for any PCR product yielding only one band on the agarose gel. In cases where more than one PCR product is seen, we recommend trying to optimize your PCR to reduce non-specific amplification. 

<details open markdown="block">
<summary>Click here to show/hide this section.</summary>

Exo/SAP is short for the enzymes Exonuclease I and Shrimp Alkaline Phosphatase. Exo/SAP purification of your PCR products prior to sequencing is essential for obtaining a clean sequence, as the Exonuclease I will degrade any excess primer from the original PCR, while the SAP will de-phosphorylate any dNTPS from the original PCR. These excess primers and dNTPS must be removed to prevent priming of both strands of DNA during cycle sequencing (removal of excess primers by Exonuclease I accomplishes this) and skewing the ratio of dye terminators dNTPs to non-dye terminator dNTPS (de-phosphorylation of the excess dNTPs by SAP accomplishes this).

<img src='https://github.com/CCG-CAS/CCG-CAS.github.io/blob/main/assets/ExoSap%20Diagram.jpeg?raw=true' alt="ExoSAP-IT Diagram">
</details>

### Protocol

1. Gather the following materials:

    - [ExoSAP-IT enzyme](https://www.thermofisher.com/order/catalog/product/78201.1.ML?ICID=search-782011ML#/78201.1.ML?ICID=search-782011ML), 50 µL aliquot (sign out from bottom shelf of gel room freezer)
    - Water, molecular-grade or double-distilled (e.g., Millipore)
    - PCR tubes, labeled+
    - Ice bucket and ice
2. Dilute 50 µL aliquot with 200 µL water (1:5 dilution). Vortex, spin, and place on ice.

    {: .note }
   Note: Your diluted ExoSAP-IT has a reduced shelf life compared to the undiluted stock. If you will only be using a small amount, dilute half of your stock tube (25 µL enzyme and 100 µL water).
3. Set up the following reaction on ice:

    |                           | Strong band | Faint band |
    |:--------------------------|:------------|:-----------|
    | PCR Product (µL)          | 10          | 14         |
    | EoSAP-IT (diluted, µL)    | 4           | 2          |
    | **Total reaction volume** | 14          | 16         |

    {: .note }
   Use the ladder in your gel image to help determine if a band is strong or faint. When in doubt, treat your sample as a faint band.
4. Cap and briefly spin tubes.
5. Place the tubes in a PCR machine and run the following EXOSAP-IT program:
    - Incubate at 37ºC for 30 minutes
    - Incubate at 80ºC for 15 minutes
    - Hold at 8ºC

{: .note }
If the ExoSAP-IT purified product will be stored for more than a couple days before use, it is best to store the product at -20 °C.
