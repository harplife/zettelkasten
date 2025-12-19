# 4.7 Logarithmic Scales

## Key Concepts

- The pH Scale
- The Richter Scale
- The Decibel Scale


## The pH Scale

The <mark class="hltr-trippy">pH scale</mark> is a scale that measures how **acidic** or **basic** a solution is. Specifically, it measures the **concentration of hydrogen ions** in a solution.

The pH is defined as :

$$
pH=-\log[H^{+}]
$$

Where :
- $H^{+}$ is the Hydrogen ions
- $[H^{+}]$ means concentration ($[H^{+}]<1$) of Hydrogen ions (moles per liter)
- The logarithm is in base 10

> [!important] The negative sign flips the direction of the scale.
> Because $[H^{+}]<1$, its logarithm is negative. We want the scale to be in positive numbers, so the negative sign is used to flip the sign.

> [!important] Pure water is $7$ on the pH scale - which is considered neutral.
> This means that solutions that have $ph<7$ are *acidic*, and $ph>7$ are *basic*. The pH scale generally ranges from $0$ to $14$, but extremely strong acids or bases can technically have pH values outside this range.

> [!important] Given pH, using the inverse can find the concentration.
> $$[H^{+}]=10^{-pH}$$

Hydrogen ion concentrations can vary many orders of magnitude. The typical values are :
- $1$ mol/L
- $10^{-7}$ mol/L
- $10^{-14}$ mol/L

In which case, the logarithm helps by :
- Compressing huge ranges into small numbers
- Turning multiplicative changes into additive ones

> [!important] Logs turn multiplication into addition.
> A change of pH scale by $1$ means the solution is $10$ times more acidic/basic. In other words, multiplying $[H^{+}]$ by $10$ is the same as subtracting $1$ from pH, and dividing by $10$ is the same as adding $1$.


## The Richter Scale

The <mark class="hltr-trippy">Richter Scale</mark> measures the magnitude of an earthquake. Specifically, it measures the amplitude of seismic waves recorded by seismographs.

The Richter scale is defined as :

$$
M = \log\left( \frac{A}{A_{0}} \right)
$$

Where :
- $M$ = earthquake magnitude
- $A$ = measured wave amplitude
- $A_{0}$ = reference amplitude
- The logarithm is in base 10

> [!important] The reference amplitude $A_{0}$, defined as magnitude $0$ on the Richter scale, has maximum amplitude of $1$ micrometer ($0.001$ mm) measured at a distance of $100$ km (using a Wood-Anderson seismograph).

Earthquake wave amplitudes vary from barely detectable vibrations to waves that move the ground by meters - which is a difference of millions of times. Logarithmic scale is necessary to compress the measurements.

> [!important] The Richter scale does not have an upper bound.
> There is no theoretical maximum on the Richter scale because it's based on ratios (not percentages). Stronger earthquakes just give larger numbers on the scale.
> 
> Similarly, it is *theoretically* possible for an earthquake to have magnitude below $0$.

> [!important] Difference of $1$ magnitude means $10$ times higher/lower amplitude.
> It also means $32$ times more/less energy released.

> [!warning] The Richter scale was used for several decades (since 1935) but was replaced because it could not accurately measure large earthquakes or reflect the true physics of fault rupture. The **Moment Magnitude Scale (Mw)** keeps the logarithmic idea but fixes those limitations.
> Today, the term "magnitude" is still being used but it refers to the Moment Magnitude Scale.


## The Decibel Scale

The <mark class="hltr-trippy">Decibel</mark>, denoted as **dB**, is a relative unit of measurement equal to *one-tenth* of a **bel (B)**. It expresses the ratio of two values of a power (or root-power) quantity on a logarithmic scale.

> [!important] The strict usage of the term Decibel only expresses a relative change. However, Decibel can also be used for expressing an *absolute value* that is relative to some fixed reference value; in which case, the dB symbol is often suffixed with letter codes that indicate the reference value.
> For example, for the reference value of $1$ volt, a common suffix is "V", which makes the symbol **dBV**.

> [!important] Power Quantity and Root-Power Quantity
> A **Power Quantity** is a physical measurement that is directly proportional to power. For example, energy density, acoustic intensity, and luminous intensity are considered power quantities.
> 
> A **Root-Power Quantity** is a physical measurement whose *square* is proportional to power. For example, amplitude, voltage, current, and sound pressure are considered root-power quantities.
> 
> Power is often calculated from two root-power quantities (e.g. $P=V \times I$). Think of **Power** as the *total energy* delivered per second (watts), and **Root-Power** as the *cause* or *driving force* that creates that power when multiplied by another related factor.

Decibel for power is :

$$
dB = 10 \log\left( \frac{P}{P_{0}} \right)
$$

Where :
- $P$ = measured power
- $P_{0}$ = reference power
- The logarithm is in base 10

> [!important] Change of $10$ dB means $10$ times more/less power.
> Change of $20$ means $100$ times, $30$ means $1000$, and so on.
> 
> Note that $0$ dB does not mean "no power". It just means it is equal to the reference.

> [!important] The ratio is *dimensionless*, which means there is no upper or lower limit to decibel.

Decibel for root-power is :

$$
dB = 20 \log\left( \frac{V}{V_{0}} \right)
$$

> [!important] Note that the formula above uses $V$ for voltage. This just depends on the context. For example, $A$ for amplitude can be used instead.

