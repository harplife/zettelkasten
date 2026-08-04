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
- **HbR tends to absorb 760 nm**
- **HbO tends to absorb 850 nm**

Using two or more wavelengths allows solving for both concentrations using the modified Beer-Lambert law.

> [!important] The Beer-Lambert law
> The Beer-Lambert law is a scientific formula that states the absorption of light shining through a material is directly proportional to the concentration of the absorbing chemical inside it and the distance the light travels.
> 
> For use of BCI, the law is modified to take account for light scatter inside the head.




## Subsystems

![[fNIRS BCI System Diagram.png]]