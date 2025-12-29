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

> [!important] A <mark class="hltr-trippy">Periodic Function</mark> is a function that repeats its values and pattern at regular intervals, meaning its graph shows a repeating wave or cycle.
> The sine and cosine functions are periodic functions.

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

<mark class="hltr-trippy">Secant</mark> is reciprocal to Cosine (*undefined* when $\cos(\theta)=0$) :

$$
\sec(\theta) = \frac{1}{\cos(\theta)} = \frac{1}{x}
$$

<mark class="hltr-trippy">Cosecant</mark> is reciprocal to Sine (*undefined* when $\sin(\theta)=0$) :

$$
\csc(\theta) = \frac{1}{\sin(\theta)} = \frac{1}{y}
$$

<mark class="hltr-trippy">Cotangent</mark> is reciprocal to Tangent (*undefined* when $\sin(\theta)=0$) :

$$
\cot(\theta) = \frac{\cos(\theta)}{\sin(\theta)} = \frac{x}{y}
$$

---
Below is a table of special values of the trigonometric functions :

| Functions / $\theta$ | $0$       | $\frac{\pi}{6}$         | $\frac{\pi}{4}$        | $\frac{\pi}{3}$         | $\frac{\pi}{2}$ | $\pi$     | $\frac{3\pi}{2}$ |
| -------------------- | --------- | ----------------------- | ---------------------- | ----------------------- | --------------- | --------- | ---------------- |
| $\sin(\theta)$       | $0$       | $\frac{1}{2}$           | $\frac{\sqrt{ 2 }}{2}$ | $\frac{\sqrt{ 3 }}{2}$  | $1$             | $0$       | $-1$             |
| $\cos(\theta)$       | $1$       | $\frac{\sqrt{ 3 }}{2}$  | $\frac{\sqrt{ 2 }}{2}$ | $\frac{1}{2}$           | $0$             | $-1$      | $0$              |
| $\tan(\theta)$       | $0$       | $\frac{\sqrt{ 3 }}{3}$  | $1$                    | $\sqrt{ 3 }$            | undefined       | $0$       | undefined        |
| $\csc(\theta)$       | undefined | $2$                     | $\sqrt{ 2 }$           | $\frac{2\sqrt{ 3 }}{3}$ | $1$             | undefined | $-1$             |
| $\sec(\theta)$       | $1$       | $\frac{2\sqrt{ 3 }}{3}$ | $\sqrt{ 2 }$           | $2$                     | undefined       | $-1$      | undefined        |
| $\cot(\theta)$       | undefined | $\sqrt{ 3 }$            | $1$                    | $\frac{\sqrt{ 3 }}{3}$  | $0$             | undefined | $0$              |


### (Extra) Summary table

| Function  | Relationship                                                                                                    |
| --------- | --------------------------------------------------------------------------------------------------------------- |
| Sine      | $\sin(\theta)=\cos\left( \frac{\pi}{2}-\theta \right)=\frac{1}{\csc(\theta)}$                                   |
| Cosine    | $\cos(\theta)=\sin\left( \frac{\pi}{2}-\theta \right)=\frac{1}{\sec(\theta)}$                                   |
| Tangent   | $\tan(\theta)=\frac{\sin(\theta)}{\cos(\theta)}=\cot\left( \frac{\pi}{2}-\theta \right)=\frac{1}{\cot(\theta)}$ |
| Cotangent | $\cot(\theta)=\frac{\cos(\theta)}{\sin(\theta)}=\tan\left( \frac{\pi}{2}-\theta \right)=\frac{1}{\tan(\theta)}$ |
| Secant    | $\sec(\theta)=\csc\left( \frac{\pi}{2}-\theta \right)=\frac{1}{\cos(\theta)}$                                   |
| Cosecant  | $\csc(\theta)=\sec\left( \frac{\pi}{2}-0 \right)=\frac{1}{\sin(\theta)}$                                        |

> [!important] The trigonometric functions are sometimes called the **Circular Functions** because they can be defined in terms of the unit circle.


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
\cos(\theta) = \sin\left( \frac{\pi}{2}-\theta \right)
$$

All this supports the fact that the sine function represents the y-axis coordinate of a terminal point, while the cosine function represents the x-axis coordinate.

<center>. . .</center>

The significance of the secant function is not that it is the reciprocal of the cosine function, but rather the fact that it is the length of the line that "cuts through" the circle and extends to the point $(1, \tan(\theta))$ on the tangent line $x=1$.

![[TrigFunctionDiagram.svg|center|500]]

The "co-" prefix in the cosecant function denotes the fact that it is a *co-function* (paired function) of the secant function. Similar to the secant function, the cosecant function represents the length of the line that "cuts through" the circle - however, it extends to the point $(\cot(\theta), 1)$ on the cotangent line $y=1$.

> [!important] In a way, the cosecant function is also the secant function of the complementary angle.
> $$\csc(\theta)=\sec\left( \frac{\pi}{2}-\theta \right)$$

<center>. . .</center>

The diagram below represents the *numeric* value of the trigonometric functions.

![[Circle-trig6.svg | center | 500]]

> [!warning] The diagram is not labeling rays, but specific line segments, often projected or truncated in ways that aren't obvious.
> Be mindful that it may conflict with the understanding of the trigonometric functions.


## Values of the Trigonometric Functions

### Even-Odd Properties

Sine, cosecant, tangent, and cotangent are <mark class="hltr-trippy">Odd Functions</mark>. Meaning, negative input means negative output. For example :
- $\sin(-\theta)=-\sin(\theta)$
- $\csc(-\theta)=-\csc(\theta)$
- $\tan(-\theta)=-\tan(\theta)$
- $\cot(-\theta)=-\cot(\theta)$

Cosine and secant are <mark class="hltr-trippy">Even Functions</mark>, where negative inputs are inversed. For example :
- $\cos(-\theta)=\cos(\theta)$
- $\sec(-\theta)=\sec(\theta)$

> [!important] <mark class="hltr-trippy">Parity</mark> refers to the fact of being *even* or *odd*.


## Fundamental Identities

### Reciprocal Identities

We already covered this.


### Pythagorean Identities

1.

$$
\sin^2(\theta) + \cos^2(\theta) = 1
$$

2.

$$
\tan^2(\theta) + 1 = \sec^2(\theta)
$$

3.

$$
1 + \cot^2(\theta)=\csc^2(\theta)
$$


