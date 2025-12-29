# 5.3 Trigonometric Graphs

## Key Concepts

- Graphs of Sine and Cosine
- Graphs of Transformations of Sine and Cosine
- Using Graphing Devices


## Graphs of Sine and Cosine

![[Circle_cos_sin.gif | center]]

The graph of the cosine function $\cos(\theta)$ reflects the *horizontal* movement of the terminal point as it moves along the circle. The graph of the sine function $\sin(\theta)$ reflects the *vertical* movement.

<center>. . .</center>

A <mark class="hltr-trippy">Cycle</mark> describes the *pattern* or *shape* of the repeating wave.

Note that the "starting" point of the sine/cosine graph is at $(1,0)$ where $\theta=0$. Once the terminal point moves all the way along the circle ($\theta=2\pi$), a single cycle of the graph has completed.
- The graph of sine starts its cycle at $0$, and then comes back around to $0$.
- The graph of cosine starts its cycle at $1$, and then comes back around to $1$.

A <mark class="hltr-trippy">Period</mark> describes the specific *horizontal length* or *duration* (along the x-axis) for the repeating wave to complete one full cycle.

The standard period of sine and cosine is $2\pi$. This means that the graph of these functions complete one cycle for every interval $2\pi$. This means that :

$$
\begin{align}
  \sin(\theta+2\pi) &= \sin(\theta) \\
  \cos(\theta+2\pi) &= \cos(\theta)
\end{align}
$$
<center>. . .</center>

We know that the values of $\sin(\theta)$ starts $0$, moves to $1$, back to $0$, moves to $-1$, and then finally comes back around to $0$. The highest value is $1$ and the lowest $-1$. Meaning, the <mark class="hltr-trippy">Range</mark> of the sine graph is $[-1,1]$.
- The range of the cosine graph is $[-1,1]$ as well.

> [!important] Graphs of even or odd functions
> An odd function, such as the sine function, outputs a negative value if the input is negative. On the other hand, an even function, like the cosine function, output is not affected by the sign of the input.
> 
> What this means on the graph is that when the terminal point rotates *clockwise* ($\theta<0$), the graph of the odd function is *flipped*. Meaning, the graph of the sine function goes from $0$ to $-1$ instead of $0$ to $1$. Meanwhile, the graph of the even function is not affected.

---
The sine function

$$
y = \sin(x)
$$

has x-intercepts at $x=n\pi$ where $n$ is an integer.

<center>. . .</center>

The cosine function

$$
y = \cos(x)
$$

has x-intercepts at $x=\frac{\pi}{2}$ where $n$ is an integer.


## Graphs of Transformations of Sine and Cosine

The general wave form (of sine) :

$$
y = A \cdot \sin(Bx-C)+D
$$

| Parameter | Effect                             |
| --------- | ---------------------------------- |
| $A$       | amplitude (vertical stretch)       |
| $B$       | frequency (horizontal compression) |
| $C$       | horizontal (phase) shift           |
| $D$       | vertical shift                     |

<center>. . .</center>

The maximum distance from $0$ (midline on the graph) to the highest/lowest value is called the <mark class="hltr-trippy">Amplitude</mark>. Both the sine and the cosine functions have amplitude of $1$. In essence, the amplitude tells "how far the motion from the center is stretched".

> [!important] Amplitude can also be defined as half the distance between the function's maximum and minimum values (for symmetrical waves).

The graph can be transformed such that the graph is vertically compressed/stretched :

$$
y = A \cdot \sin(x)
$$

In this case, $A$ is directly related to amplitude :

$$
\text{Amplitude} = |A|
$$

For example, for $y=2 \cdot \sin(x)$, the amplitude is $2$; the graph of the function is highest at $2$, and then lowest at $-2$.

> [!important] If $A<0$, the graph of sine/cosine function *flips vertically* - regardless of parity.

<center>. . . </center>

The number of cycles a periodic function (sine and cosine) completes over a set interval (usually $2\pi$) is called <mark class="hltr-trippy">Frequency</mark>.

The standard period of sine/cosine is $2\pi$. However, when the function is transformed such that the graph is horizontally compressed/stretched,

$$
y = \sin(Bx)
$$

The **period** of the transformed function is related to frequency, such that :

$$
P = \frac{2\pi}{B}
$$

For example, given the sine function :

$$
y = \sin(2x)
$$

The period for such function is $\pi$. This means that, compared to the standard sine function whose graph completes one cycle within the interval $2\pi$, the transformed sine function completes its cycle *twice* within the same interval. Meaning, the frequency of the transformed function is $2$.

> [!important] Note that $B$ is directly related to the frequency.
> A larger $B$ value (higher frequency) compresses the graph horizontally; the period is shorter, and the cycles are faster.

> [!important] In physics and engineering, $\omega$ (omega) symbol is used in place of $B$.

Note that **frequency** and **period** are *reciprocals* :

$$
B = \frac{1}{P}
$$

> [!important] If $B<0$, the graph of a sine function flips vertically (being an even function). On the other hand, the graph of a cosine function remains the same.

<center>. . .</center>

<mark class="hltr-trippy">Phase</mark> refers to the *angular* or *horizontal* position of a wave within its cycle.
- **Phase shift** (of a periodic function) is synonymous to *horizontal shift* and *rotation offset*.

The standard sine/cosine function has zero phase shift; the cycle start at phase $0$ - in other words, it starts at $\theta=0$ and ends at $\theta=2\pi$.

The standard function can be transformed, such that :

$$
y = \sin(x-C)
$$

Where $C$ describes the phase shift.
- This means that at $x=0$, the function becomes $y=\sin(-C)$; therefore, the wave starts at $\theta=-C$.
- $(x-C)$ shifts the function ***right*** by $C$.
- $(x+C)$ shifts the function ***left*** by $C$.

For example, given $y=\sin\left( x-\frac{\pi}{2} \right)$, the starting angle is at $-\frac{\pi}{2}$ and $\sin\left( -\frac{\pi}{2} \right)$ is $-1$. Therefore, the wave begins at $-1$, goes up to $1$, and then back down to $-1$.

Cosine happens to be a form of sine where it's shifted by $-\frac{\pi}{2}$. Meaning :

$$
\begin{align}
  \sin(x) &= \cos\left( x-\frac{\pi}{2} \right) \\
  \cos(x) &= \sin\left( x+\frac{\pi}{2} \right)
\end{align}
$$

> [!important] It's important to note that sine and cosine describe the same circular motion, but the only difference is that they are projected onto different axes.

> [!important] Given two or more waves of the same amplitude and period, if those waves have different starting angle, they are said to be "out of phase" with each other.

> [!important] Phase shift vs. horizontal shift
> The angle $\theta$ represents a state of rotation around the unit circle. Phase represents the *current* state of rotation around the unit circle. Graphically speaking, phase shift is the same as horizontal shift - but geometrically, it is understood that the wave is "out of phase" with the original state.

> [!important] In physics and engineering, $\phi$ (phi) symbol is used in place of $C$.

<center>. . .</center>

A periodic function can be vertically shifted :

$$
y = \sin(x)+C
$$

Graphically, $C$ moves the midline $y=0$ to $y=C$. This constant $C$ is called the <mark class="hltr-trippy">Vertical Offset</mark>.

> [!important] In the real world, the vertical offset can be understood as the mean value.
> For example, the temperature outside can oscillate daily but there is an average temperature over the week.


$y=A \cdot \sin B(x-C)+D$