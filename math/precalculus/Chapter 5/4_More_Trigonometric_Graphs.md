# 5.4 More Trigonometric Graphs

## Key Concepts

- Graphs of Tangent, Cotangent, Secant, and Cosecant
- Graphs of Transformations of Tangent and Cotangent
- Graphs of Transformations of Secant and Cosecant


## Graphs of Tangent, Cotangent, Secant, and Cosecant

### Tangent

The graph of tangent $y=\tan x$ looks like this :

![[Pasted image 20251229231955.png | center | 500]]

Reminder that :

$$
\tan x = \frac{\sin x}{\cos x}
$$

and tangent represents **slope** of the unit vector pointing at the terminal point.

The slope of the unit vector becomes exponentially steeper as the terminal point moves along the circle counter-clockwise until it the unit vector becomes vertical (where tangent becomes undefined).
- Past that point, it starts at negative slope and goes toward $0$, where it becomes steep again.
- Note that slope is *always increasing*.

Tangent becomes undefined when $\cos x = 0$, which happens at :

$$
x = \frac{\pi}{2} + n\pi
$$

Where $n$ is an integer. These become **vertical asymptotes** in the graph of tangent.

The **period** of tangent is $\pi$. We know this because a slope repeats every half rotation. For example, the unit vector tilted at $\frac{\pi}{6}$ and another at $\frac{7\pi}{6}$ has the same slope.

Tangent is an **odd function**, and so it is symmetric about the origin :

$$
\tan(-x) = -\tan x
$$

Key points of tangent :
- When $x=0$, then $\tan x=0$
- When $x=\pm \frac{\pi}{4}$, then $\tan x=\pm 1$
- When $x$ approaches $\pm \frac{\pi}{2}$, $\tan x$ approaches $\pm \infty$

> [!important] One continuous, non-repeating segment on the graph of tangent is referred to as the <mark class="hltr-trippy">Branch</mark>.
> In other words, each segment of the curve between two consecutive vertical asymptotes is considered a single branch. The range of each branch spans all real numbers from $-\infty$ to $\infty$.


### Cotangent

The graph of cotangent $y = \cot x$ looks like this :

![[Pasted image 20251229232513.png | center | 500]]

Reminder that :

$$
\cot x = \frac{\cos x}{\sin x} = \frac{1}{\tan x}
$$

Cotangent is undefined when $\sin x = 0$, which happens at :

$$
x = n\pi, \quad n \in \mathbb{Z}
$$

This means that cotangent has vertical asymptotes at $0$, $\pi$, $2\pi$, and so on.

Just like tangent, cotangent has period of $\pi$, which means :

$$
\cot(x+\pi) = \cot x
$$

Cotangent is also an odd function, which means it is symmetric about the origin :

$$
\cot(-x) = -\cot x
$$

Just as tangent is always increasing, cotangent is always decreasing.




## Graphs of Transformations of Tangent and Cotangent

### Transformations of Tangent

The general form is :

$$
y = A \cdot \tan B(x-C) + D
$$

| Parameter | Effect                                           |
| --------- | ------------------------------------------------ |
| $A$       | vertical stretch (steeper curve) & vertical flip |
| $B$       | horizontal compression (shortens period)         |
| $C$       | horizontal shift                                 |
| $D$       | vertical shift                                   |

> [!important] Tangent is an odd function, so $\tan(-Bx)$ is the same as $-\tan(Bx)$.
> This would result in vertical flip.

