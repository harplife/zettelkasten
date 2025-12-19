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

