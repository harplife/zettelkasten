# 5.6 Modeling Harmonic Motion

## Key Concepts

- Simple Harmonic Motion
- Damped Harmonic Motion
- Phase and Phase Difference


## (Extra) Periodic Motion

<mark class="hltr-trippy">Periodic Motion</mark> is any motion that repeats itself over regular, fixed intervals of time.

> [!warning] Periodic motion doesn't have to be *uniform* - many periodic motions change speed continuously.

Example of period motions :
- Pendulum
- Earth's orbit around the Sun

Key characteristics of periodic motion :
- Period $T$
- Frequency $f$
- Amplitude $A$

Periodic motion is often described as **rotational**, **oscillatory**, or **orbital**, depending on the geometry of the motion.
- Oscillation describes a periodic motion where the object moves back and forth about a fixed point

> [!important] Rotational, oscillatory, and orbital motion is *descriptive* but it is not categorical.
> In fact, these can overlap. Orbital motion is often just rotational motion, and oscillatory motion can be viewed as a projection of rotational motion.

The simplest kind of periodic motion is a **circular periodic motion**, where an object moves in a circle at constant speed and angle increases uniformly.
- e.g. clock hands, rotating wheels, planets (idealized)

> [!important] A periodic motion that is composed of two or more incommensurate frequencies is called a **Quasi-Periodic Motion**.
> Examples :
> - Planetary orbits with perturbations
> - Rotating objects with wobble
> - Music chords
> 
> Such motion never repeats exactly but it is still structured.

## Simple Harmonic Motion

<mark class="hltr-trippy">Simple Harmonic Motion</mark> (SHM) is a smooth and oscillatory periodic motion in which the restoring influence is proportional to the displacement from equilibrium and always directed toward it.

SHM is often represented by a sine (or cosine) wave. In its simplest form, the position of the object varies like :

$$
x(t) = A \sin(wt+\phi) \quad \text{ or } \quad x(t) = A \cos(wt+\phi)
$$

> [!important] A motion that creates a sine wave is said to be **Sinusoidal**.
> **Non-harmonic motion** is a motion that repeats but is not *sinusoidal*. Examples include :
> - Square waves
> - Sawtooth waves
> - Triangle waves
> - Heartbeat signals
> - Gait cycles in walking
> 
> It is also said that sinusoidal motion is *smooth*. In other words, non-harmonic motions are *not* smooth.

> [!important] In the context of mathematics, the term *Harmonic* really just means it oscillates smoothly and periodically.

<center>. . .</center>

Every harmonic system has a rest position, which is called <mark class="hltr-trippy">Equilibrium</mark>, and the motion occurs around that position.

Example :
- Mass on a spring --> equilibrium at spring's natural length
- Pendulum --> equilibrium at lowest point
- AC voltage --> equilibrium at $0$ volts.

<center>. . .</center>

**Amplitude** describes the maximum displacement from equilibrium.
- It determines how "big" the motion is
- Energy increases with amplitude
- It does not affect the timing of the motion

Example :
- Larger swing of a pendulum
- Louder sound
- Brighter light

<center>. . .</center>

**Period** describes time for one full cycle, whereas **Frequency** describes number of cycles per unit time.

<center>. . .</center>

<mark class="hltr-trippy">Angular frequency</mark> (rad/s) is the rate of rotation (or oscillation) measuring how fast something spins (or vibrates) in radians per second.
- It quantifies the change in angle over time.

Angular frequency (of a circular motion) is defined as :

$$
\omega = \frac{2\pi}{T} = 2\pi f
$$

Where $T$ is period and $f$ is frequency.

![[Pasted image 20260108171123.png | center]]

> [!important] We had defined the general transformation of a sine function to be $y = A \sin(Bx-C)+D$
> In physics and engineering, it is defined as $$x(t) = A \sin(\omega t + \phi)$$

<center>. . .</center>

Phase $\phi$ determines the initial angle on the circle. Any shift in phase shifts the wave horizontally in time.

Two harmonic systems can have same frequency and same amplitude, but they can be *out of phase* with each other.

<center>. . .</center>

Harmonic motions deal with **velocity** and **acceleration**.

Velocity is *largest at equilibrium* and *zero at the extremes*.

Acceleration always *points toward equilibrium*.

> [!important] Velocity is represented by a tangent line on the wave.
> Looking at the velocity and the changes in velocity (acceleration) is at the heart of calculus.

<center>. . .</center>

What makes a simple harmonic motion "simple" is the fact that it is highly idealized :
- Motion continues forever
- Amplitude is constant
- Frequency is constant
- Perfectly symmetric oscillation

SHM is a *model*, not reality.

<center>. . .</center>

Many real systems behave approximately harmonically near equilibrium.

Even complicated systems become harmonic when disturbances are *small*, and can be modeled with sine/cosine *locally*.

This is why harmonic motion is called the "first approximation of nature".

<center>. . .</center>

Damped

Driven
Nonlinear
Quasi-harmonic

<center>. . .</center>

Read more about simple harmonic motion at university physics level :
- https://openstax.org/books/university-physics-volume-1/pages/15-1-simple-harmonic-motion

## Damped Harmonic Motion



Underdamped
Critically damped
Overdamped





