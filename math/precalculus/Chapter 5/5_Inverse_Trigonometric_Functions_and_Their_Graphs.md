# 5.5 Inverse Trigonometric Functions and Their Graphs

## Key Concepts

- The Inverse Sine Function
- The Inverse Cosine Function
- The Inverse Tangent Function
- The Inverse Secant, Cosecant, and Cotangent Functions


## The Inverse Sine Function

> [!important] Reminder : An inverse function, denoted as $f^{-1}(x)$, is a function that "undoes" the original function $f(x)$, effectively reversing the input and output.
> If $f(x)$ turns input $a$ into output $b$, then $f^{-1}(b)$ turns $b$ back into $a$.

Given a base sine function :

$$
y = \sin x
$$

Its inverse is defined as :

$$
y = \sin^{-1}(x) \quad \text{where } -1\leq x \leq 1
$$

> [!important] Inverse sine is also denoted as $\arcsin$.

The inverse answers :
> "Given the value of $\sin x$, what was the angle $x$?"

> [!warning] Inverse does *NOT* mean reciprocal.

The problem with trig functions is that they are not one-to-one functions - which is the requirement for there to be inverse functions.

For example, for $\sin x = \frac{1}{2}$, there are infinitely many angles that gives that value.

> [!important] In order for trig functions to have an inverse, the domain has to be *restricted*.

For sine, its restricted domain is $\left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$.

![[Pasted image 20260102131309.png | center | 500]]

The restricted domain becomes the **range** for inverse sine.

We know that the range of sine is $[-1,1]$, which then becomes the **domain** of inverse sine.

> [!important] The restricted range of inverse sine raises the question of "what if actual angle is outside the range?"
> Note that inverse sine only gives the "reference" angle, and it does not give the full orientation. For example, the angle that satisfies $\sin x = \frac{1}{2}$ is $\frac{\pi}{6}$ (according to inverse sine), but it could also be $\frac{5\pi}{6}$ or infinitely many other angles.
> 
> In such a case where the "actual" angle is outside the range, the actual angle can be solved only by maintaining the context. Meaning, additional information about direction is needed - which can simply be "left or right" or "forward or backward", but it can be within the equation by using the supplementary angle.
> 
> For example, $\sin(\pi-x)=\frac{1}{2}$ gives enough context that the we are facing the other way. It can be solved with $\pi-x = \arcsin\left( \frac{1}{2} \right)$, which gives us $\frac{5\pi}{6}$; which is the "actual" angle we are looking for.

Inverse trig graphs are reflections across the line :

$$
y = x
$$

Thus, the graph of inverse sine looks like this :

![[Pasted image 20260102132213.png | center | 500]]
> Red solid line is inverse sine. Blue dotted line is sine.

<center>. . .</center>

The relationship between sine and inverse sine is summed up as :

$$
\begin{align}
  \sin(\arcsin x) &= x \quad \text{only if } x \in [-1,1] \\
  \arcsin(\sin x) &= x \quad \text{only if } x \in \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]
\end{align}
$$


## The Inverse Cosine Function

Given the base cosine function :

$$
y = \cos x
$$

Its inverse is defined as :

$$
y = \cos^{-1} (x) \quad \text{where } -1\leq x \leq 1
$$

> [!important] Inverse cosine is also denoted as $\arccos$.

Because cosine is not a one-to-one function, its domain has to be restricted to :

$$
[0, \pi]
$$

![[Pasted image 20260104141028.png | center | 500]]

The restricted domain then becomes the **range** for inverse cosine.

We know that the range of cosine is $[-1,1]$, which then becomes the **domain** for inverse cosine.

The graph of inverse cosine looks like this :

![[Pasted image 20260104141816.png | center | 500]]
> Blue solid line is inverse cosine. Green dotted line is cosine. Orange dotted line shows where the reflection occurs.

<center>. . .</center>

The relationship between cosine and inverse cosine is summed up as :

$$
\begin{align}
  \cos(\arccos x) &= x \quad \text{only if } x \in [-1,1]\\
  \arccos(\cos x) &= x \quad \text{only if } x \in \left[ 0, \pi \right]
\end{align}
$$


## The Inverse Tangent Function

Given the base tangent function :

$$
\tan \theta = \frac{\text{opposite}}{\text{adjacent}} = \frac{y}{x}
$$

Its inverse is defined as :

$$
\theta = \tan^{-1} \quad \text{where } x \in \mathbb{R}
$$

> [!important] Inverse tangent is also denoted as $\arctan$.

The inverse tangent answers :
> "Given a slope y/x, what angle has that slope?"

<center>. . .</center>

Tangent is not a one-to-one function, and thus its domain has to be restricted for it to have an inverse. In this case, the interval where the "branch" that sits on the origin exists does the job. meaning, the **range** for inverse tangent is :

$$
\left( -\frac{\pi}{2}, \frac{\pi}{2} \right)
$$

Since the range of tangent is all real numbers, the **domain** of inverse tangent is :

$$
(-\infty, \infty)
$$

<center>. . .</center>

The graph of inverse tangent looks like this :

![[Pasted image 20260107083704.png | center]]
> Red solid line is inverse tangent. Blue dotted line is tangent (restricted). Orange dotted line shows reflection at $y=x$.

<center>. . .</center>

The relationship between tangent and inverse tangent is summed up as :

$$
\begin{align}
  \tan(\arctan x) &= x \quad \text{only if } x \in \mathbb{R}\\
  \arctan(\tan x) &= x \quad \text{only if } x \in \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]
\end{align}
$$

<center>. . .</center>

Given a point $(x,y)$, $\arctan\left( \frac{y}{x} \right)$ gives the angle the line from the origin makes with the x-axis - but only in Quadrants I and IV. This is where problems arise.

There is an ambiguity problem with inverse tangent - where slope $1$ ($\theta=\frac{\pi}{4}$) could mean that the point is either at $(1,1)$ or $(-1,-1)$. Same thing happens with slope $-1$.

> [!warning] Basically, inverse tangent *cannot* tell which quadrant the point is in.

> [!important] When it comes to programming (specifically CG), a different version of inverse tangent is used to retain direction.
> Generally, the function looks like this : `atan2(y,x)`


## Other inverse functions

> [!important] Inverse secant, cosecant, and cotangent functions are rarely used, and they can be replaced by the three aforementioned inverse functions.


### The Inverse Secant Function

Given the base secant function :

$$
\sec x = \frac{1}{\cos x}
$$

Its inverse function is defined as :

$$
y = \sec^{-1}(x) \quad \text{where } |x| \geq {1}
$$

> [!important] It also goes by the name *arcsec*, but it seems like there's no LaTex symbol for this one.

Inverse secant answers :
> "At what angle has secant equal to this value?"

<center>. . .</center>

Because secant is not a one-to-one function, its domain has to be restricted for there to be an inverse. In this case, the **range** of inverse secant is $\left[ 0, \frac{\pi}{2} \right) \cup \left( \frac{\pi}{2}, \pi \right]$

![[Pasted image 20260107105358.png | center | 500]]
> The graph of secant with the interval $[0,\pi]$ highlighted.

The **domain** of inverse secant is $(-\infty,-1] \cup [1, \infty)$. Note that it skips the values between $-1$ and $1$.

<center>. . .</center>

The graph of inverse secant looks like this :

![[Pasted image 20260107131019.png | center]]
> Red solid line is inverse secant. Blue dotted line is secant (restricted). Orange dotted line shows the reflection at $y=x$.

<center>. . .</center>

The relationship between inverse cosine and inverse secant is :

$$
\sec^{-1}(x) = \cos^{-1}\left( \frac{1}{x} \right)
$$

The relationship is explained by the fact that secant is **reciprocal** to cosine.

> [!important] The range of inverse secant matches with the range of inverse cosine.
> The domain of inverse cosine happens to sit right between the hole in the domain of inverse secant.
> ![[Pasted image 20260107130812.png | center | 500]]

> [!warning] Inverse secant is rarely used (in application) because inverse cosine can easily replace it.

---
Just FYI, the textbook definition of inverse secant is fucked up.

![[Pasted image 20260107224457.png | center | 700]]


### The Inverse Cosecant Function

Given the base cosecant function :

$$
y = \csc x
$$

Its inverse function is defined as :

$$
y = \csc^{-1}(x) \quad \text{where } |x| \geq {1}
$$

> [!important] It is often written as *arccsc*, but there is no LaTex symbol for this one.

Inverse cosecant answers :
> "What angle has cosecant equal to this value?"

The **domain** of inverse cosecant is $(-\infty, -1] \cup [1,\infty)$.

The **range** of inverse cosecant is $\left[ -\frac{\pi}{2}, 0 \right) \cup \left( 0, \frac{\pi}{2} \right]$.

The graph of inverse cosecant looks like this :

![[Pasted image 20260107132507.png | center]]
> Red solid line is inverse cosecant. Blue dotted line is cosecant (restricted). Orange dotted line shows the reflection at $y=x$.

The relationship between inverse sine and inverse cosecant is as follows :

$$
\csc^{-1}(x) = \sin^{-1}\left( \frac{1}{x} \right)
$$

As such is the case, inverse sine often used in place of inverse cosecant.

---
Just FYI, the textbook definition of inverse cosecant is fucked up.

![[Pasted image 20260107224527.png | center | 700]]


### The Inverse Cotangent Function

Given base cotangent function :

$$
\cot x = \frac{\cos x}{\sin x} = \frac{1}{\tan x}
$$

Its inverse function is defined as :


$$
y = \cot^{-1}(x) \quad \text{where } x \in \mathbb{R}
$$

However, this is *NOT* a complete definition.

> [!warning] The definition of inverse cotangent may *vary* by convention.

<center>. . .</center>

The graph of cotangent looks like :

![[Pasted image 20251229232513.png | center | 500]]

Note here that, in order to have an inverse, we need to restrict the domain of cotangent - but in this case, it's not clear where to set the interval :

$$
\left[ -\frac{\pi}{2}, \frac{\pi}{2} \right] \quad \text{ or } \quad (0, \pi)
$$

---
In one convention (which is used in the textbook), the domain is restricted to $(0, \pi)$. Thus, the definition of inverse cotangent is :

$$
y = \cot x \text{ for } x \in (0, \pi) \iff x = \cot^{-1}(y)
$$

In other words :

$$
y = \cot^{-1}(x) \in (0, \pi)
$$

The domain for inverse cotangent is $(-\infty, \infty)$.

The graph of inverse cotangent looks like this :

![[Pasted image 20260107212208.png | center | 700]]
> Red solid line is inverse cotangent. Blue dotted line is cotangent (restricted). Orange dotted line shows the reflection at $y=x$.

In this convention, the properties of the inverse cotangent are :
- Avoids the vertical asymptotes at $0$ and $\pi$.
- Covers both Quadrant I and Quadrant II.
- Always returns a **positive** angle.
- Covers all real numbers in once.

---
In another convention, the domain is restricted to $\left( -\frac{\pi}{2}, \frac{\pi}{2} \right)$. Thus, the definition of inverse cotangent is :

$$
y = \cot x \text{ for } x \in \left( -\frac{\pi}{2}, \frac{\pi}{2} \right) \iff x = \cot^{-1}(y)
$$

In other words :

$$
y = \cot^{-1}(x) \in \left( -\frac{\pi}{2}, \frac{\pi}{2} \right)
$$

In this convention, inverse cotangent is a reciprocal to inverse tangent :

$$
\cot^{-1}(x) = \tan^{-1}\left( \frac{1}{x} \right)
$$

The domain for inverse cotangent is $(-\infty, \infty)$.

The graph of inverse cotangent looks like this :

![[Pasted image 20260107220158.png | center | 500]]
> Red solid line is inverse cotangent. Blue dotted line is cotangent (restricted). Orange dotted line shows the reflection at $y=x$.

In this convention, the properties of the inverse cotangent are :
- Undefined at $x=0$. In other words, it does not cover all real numbers.
- Loses quadrant information

