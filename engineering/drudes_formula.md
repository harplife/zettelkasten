# Drude's Formula for Electrical Conductivity

$$
\sigma = \frac{ne^2 \tau}{m}
$$

Where:
- $\sigma$ = electrical conductivity
- $n$ = free electron density
- $e^2$ = elementary charge
- $\tau$ = relaxation time
- $m$ = electron mass


## Derivation of the formula

The derivation of Drude's formula relies on treating free electrons in a metal like a gas of classical particles (similar to an ideal gas) bouncing around a lattice of fixed, positive atomic ions.

The formula is derived in three main conceptual steps:
1. Finding the force and Acceleration on an Electron
2. Calculating the Drift Velocity
3. Linking Drive Velocity to Current Density using Ohm's Law


### Step 1: Find the Force and Acceleration on an Electron

When an external electric field $\vec{E}$ is applied to a material, it exerts an electrostatic force on each free electron. According to Newton's Second Law $\vec{F}=m\vec{a}$, the force is equal to the electron's mass $m$ times its acceleration $\vec{a}$.

Rearranging this gives the steady acceleration of an electron due to the electric field:
$$
\vec{a} = \frac{e\vec{E}}{m}
$$

> [!important] Electron's Mass
> Electron's mass (aka Rest Mass) is approximately $9.109 \times 10^{-31} \,\text{kg}$. It is also $\frac{1}{1836}$ the mass of a proton.


### Step 2: Calculate the Drift Velocity

In the absence of an electric field, electrons move completely at random, meaning their average velocity is zero.

When the electric field is turned on, electrons accelerate but constantly collide with the heavy atomic lattice. The *Drude model* assumes that each collision completely resets an electron's velocity back to a random direction.
![[Drude Model.svg | drude model | center | 300]]
The average time an electron manages to travel between these resetting collisions is the relaxation time $\tau$. Therefore, the average net velocity an electron picks up - known as the drift velocity $\vec{v}_{d}$ - is simply acceleration multiplied by this average time:

$$
\vec{v}_{d} = \vec{a}\tau = \left( \frac{e\vec{E}}{m} \right) \tau
$$