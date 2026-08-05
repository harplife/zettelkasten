# fNIRS BCI

**Functional Near-Infrared Spectroscopy (fNIRS) Brain-Computer Interfaces (BCI)**

An **fNIRS BCI** is a system that measures **changes in blood oxygenation in the outer layers of the brain** using near-infrared light. Unlike EEG, it does **not** measure electrical activity directly. Instead, it measures the brain's **metabolic response** to neural activity.

Think of it as :
```
Neurons fire > neurons consume oxygen > blood flow changes > light absorption changes > computer estimates which brain regions are active.
```

When neurons become active :
1. Neurons require ATP
2. ATP requires oxygen and glucose
3. Nearby blood vessels dilate
4. Extra oxygenated blood arrives

fNIRS measure :
- The increase in **Oxygenated hemoglobin (HbO)**
- The decrease in **Deoxygenated hemoglobin (HbR)**

Hemoglobin absorbs light differently depending on whether it carries oxygen.

Without causing damage, near-infrared light (roughly 650-960 nm) penetrates :
- Skin
- Skull
- Cerebrospinal fluid
- Outer cortex

Different wavelengths are absorbed differently. For example,
- **HbR tends to absorb 730~760 nm**
- **HbO tends to absorb 810~850 nm**

Using two or more wavelengths allows solving for both concentrations using the modified Beer-Lambert law.

> [!important] The Beer-Lambert law
> The Beer-Lambert law is a scientific formula that states the absorption of light shining through a material is directly proportional to the concentration of the absorbing chemical inside it and the distance the light travels.
> 
> For use of BCI, the law is modified to take account for light scatter inside the head.

Light does not travel in a straight line through the head; it enters the scalp, scatters wildly, and arcs back up to the surface in a curved, banana-shaped path.

> [!important] The deepest part of the banana is approximately halfway between the emitter and detector.

![[Pasted image 20260804220924.png | center | 500]]
![[Pasted image 20260804231244.png | center | 500]]

To reach the brain tissue, the light must pass through and return from several distinct layers:
- Skin and scalp (extracerebral layer)
- Skull bone (cranial layer)
- Cerebrospinal fluid (CSF)
- Outermost surface of the brain (cerebral cortex)

Because the light only penetrates a few centimeters, fNIRS can only read signals from the cerebral cortex. It cannot reach deep brain structures like the hippocampus, thalamus, or basal ganglia.

> [!warning] Major signal-noise challenge with fNIR
> The light spends a lot of time passing through the scalp and skull. Advanced filters must be used to separate shallow blood flow in the skin from actual brain activity.

> [!important] Complete signal chain
> Neural firing > Metabolism increases > Blood flow increases > HbO up, HbR down > Optical absorption changes > Photodiodes detect intensity > Amplifier > ADC > Signal processing > Machine Learning > BCI output

These are the limitations of fNIR :
- Only images the outer 1~2 cm of cortex
- Hair reduces optical signal quality
- Motion can introduce artifacts (although more resilient than EEG)
- Ambient light and physiological rhythms can introduce noise

> [!warning] The biggest limitation with fNIR
> Although fNIR is known to provide better spatial resolution than EEG, it is much slower due to **hemodynamic delay**. The useful signal typically peaks 2~6 seconds after neurons become active. This makes it poorly suited for fast tasks such as controlling a robotic arm or typing at high speed.


## Emitter-Detector Layout

Most adult fNIR systems use 30 mm between the light emitter and detector. This gives reasonable penetration, acceptable signal strength, and usable cortical sensitivity.

|Separation|Typical Use|
|---|---|
|5–10 mm|Superficial tissue measurement|
|20 mm|Children / thin skulls|
|**30 mm**|Standard adult cortical measurement|
|35–40 mm|Deeper penetration, lower SNR|
|>45 mm|Rare in CW systems|

![[Pasted image 20260804232057.png]]

> [!important] Short-Separation Channels
> Modern fNIR systems often include extra detectors very close (5~10 mm) to the source. These short channels only measure blood flow changes in the skin and bone; these measurements are subtracted from the deep channels, leaving a clean map of actual brain activity.

### 10-20 Anchor System

[10-20 Anchor System (EEG BCI)](<https://en.wikipedia.org/wiki/10–20_system_(EEG)>) is an internationally recognized method to describe and apply the location of scalp electrodes. This method was developed to maintain standardized testing methods ensuring that a subject's study outcomes could be compiled, reproduced, and effectively analyzed and compared using the scientific method.

Scientists map the cap by measuring the distance between four major, unchanging bony landmarks on the skull :
- Nasion : the depression at the bridge of the nose
- Inion : the prominent bony bump at the very base of the back of the skull
- Preauricular Points : The small indentations just in front of each ear canal

The cap is divided into intersecting grid lines spaced out by **10% or 20%** of the total measured front-to-back or side-to-side distance of a person's skull.

![[Pasted image 20260805145406.png | center | 500]]
> Each electrode placement site has a letter to identify the lobe, or area of the brain it is reading from: **pre-frontal (Fp), frontal (F), temporal (T), parietal (P), occipital (O), and central (C)**. Note that there is no "central lobe". There are also **(z)** sites, where electrodes are placed on the midline sagittal plane of the skull and is present mostly for reference/measurement points.

![[Pasted image 20260805145947.png]]

> [!important] Hybrid EEG-fNIR BCI Layout
> There are several ways to go about how to place EEG and fNIR together, but the one that makes most sense to me is just placing EEG in between fNIR channels - considering fNIR emitters and detectors has to be 30 mm apart.



## Subsystems

![[fNIRS BCI System Diagram.png]]