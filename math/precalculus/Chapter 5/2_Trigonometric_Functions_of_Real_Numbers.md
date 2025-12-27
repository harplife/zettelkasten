# 5.2 Trigonometric Functions of Real Numbers

## Key Concepts

- The Trigonometric Functions
- Values of the Trigonometric Functions
- Fundamental Identities


## The Trigonometric Functions

Let :
- $\theta$ be the angle measured from the positive x-axis (to the unit vector at the terminal point)
- $(x,y)$ be the coordinates of the terminal point at angle $\theta$

---
The coordinates of each axis can be found by using the two fundamental trigonometric functions :

$$
\begin{align}
  \cos(\theta) &= x \\
  \sin(\theta) &= y
\end{align}
$$

$\cos$ stands for <mark class="hltr-trippy">Cosine</mark>, which represents the *horizontal coordinate* of the terminal point.

$\sin$ stands for <mark class="hltr-trippy">Sine</mark>, which represents the *vertical coordinate* of the terminal point.

> [!warning] Many apps default to *radians* when it comes to angles.
> Be sure to check which unit of measurement (degree/radian) is used before using angle-based functions such as $\sin$ or $\cos$.

<mark class="hltr-green">Example</mark>
Let's say $\theta=45$. The terminal point is then located at $(\cos(45), \sin(45))$, which gives us $(0.707, 0.707)$ (same as $\left( \frac{\sqrt{ 2 }}{2}, \frac{\sqrt{ 2 }}{2} \right)$).

<mark class="hltr-green">Example</mark>
Let's say $\theta=55$. The terminal point is then located at $(\cos(55), \sin(55))$, which gives us $(0.57, 0.82)$.

> [!important] The outputs of Sine and Cosine are bounded to values between $-1$ and $1$.
> Naturally, this is because they are coordinates on a circle of radius $1$.

> [!important] #todo write about Periodicity, how rotating a full circle ($2\pi$) lands at the same terminal point - and how that relates to trigonometric functions $\sin(\theta+2\pi)=\sin(\theta)$.

---
The ratio of the two functions Sine and Cosine creates <mark class="hltr-trippy">Tangent</mark>, which represents the slope of the unit vector pointing to the terminal point.

$$
\tan(\theta) = \frac{\sin(\theta)}{\cos(\theta)}
$$

Note that this is equivalent to how we understand *slope*, that is :

$$
\text{slope} = \text{ rise over run } = \frac{y}{x}
$$

Note that $\tan(\theta)$ becomes undefined when the line is vertical and consequently, $x=0$ and $\cos(\theta)=0$.

> [!important] The Tangent Line Interpretation
> Draw the vertical line at $x=1$. This line is a **Tangent Line**, which is perpendicular to the unit vector that points to the terminal point $P(1,0)$.
> 
> Let's say we move the terminal point to elsewhere (e.g. $\frac{\pi}{4}$). When we extend the unit vector so that the endpoint hits the tangent line, the coordinate of the point where they meet is $$(1, \tan(\theta))$$
> 
> In a sense, Tangent is the *vertical height* where the "ray" from the unit vector hits the tangent line.

---
The three functions, Sine, Cosine, and Tangent, have their reciprocals.

Secant is reciprocal to Cosine (*undefined* when $\cos(\theta)=0$) :

$$
\sec(\theta) = \frac{1}{\cos(\theta)} = \frac{1}{x}
$$

Cosecant is reciprocal to Sine (*undefined* when $\sin(\theta)=0$) :

$$
\csc(\theta) = \frac{1}{\sin(\theta)} = \frac{1}{y}
$$

Cotangent is reciprocal to Tangent (*undefined* when $\sin(\theta)=0$) :

$$
\cot(\theta) = \frac{\cos(\theta)}{\sin(\theta)} = \frac{x}{y}
$$

### (Extra) Special segments in circle

Special segments in a circle include chords, secants, and tangents.

A <mark class="hltr-trippy">Chord</mark> is a segment with both endpoints on the circle

A <mark class="hltr-trippy">Secant</mark> is a line intersecting the circle at two points, and extending beyond the circle.

A <mark class="hltr-trippy">Tangent</mark> is a line touching the circle at exactly one point.

![[special_segments_in_a_circle.svg|center|500]]


### (Extra) More context for better understanding

Historically, the sine function used to be referred to as the *half-chord of a circle*, literally referring to the half the length of a chord.

![[Pasted image 20251227123727.png | center | 300]]

The sine function was the first function of the (fundamental) trigonometric functions to be discovered. Next was the cosine function, "co-" prefix noting the fact that the cosine is the sine of the *complementary* angle (in 90 degrees).

$$
\begin{align}
  \text{If : } &\quad \theta + \phi = 90^\circ \\
  \text{Then : }&\quad \cos(\theta) = \sin(\phi)
\end{align}
$$

All this supports the fact that the sine function represents the y-axis coordinate of a terminal point, while the cosine function represents the x-axis coordinate.

<center>. . .</center>

The significance of the secant function is not that it is the reciprocal of the cosine function, but rather the fact that it is the length of the line that "cuts through" the circle and extends to the point $(1, \tan(\theta))$ on the tangent line $x=1$.

![[TrigFunctionDiagram.svg|center|500]]

The "co-" prefix in the cosecant function denotes the fact that it is a *co-function* (paired function) of the secant function. Similar to the secant function, the cosecant function represents the length of the line that "cuts through" the circle - however, it extends to the point $(\cot(\theta), 1)$ on the cotangent line $y=1$.

<center>. . .</center>

The diagram below represents the *numeric* value of the trigonometric functions.

![[Circle-trig6.svg | center | 500]]

> [!warning] The diagram is not labeling rays, but specific line segments, often projected or truncated in ways that aren't obvious.
> Be mindful that it may conflict with the understanding of the trigonometric functions.



