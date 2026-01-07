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
y = \sin^{-1}(x) \quad \text{ or } \quad \arcsin x
$$

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
\arcsin(\sin x) = x \quad \text{only if } x \in \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]
$$


## The Inverse Cosine Function

Given the base cosine function :

$$
y = \cos x
$$

Its inverse is defined as :

$$
y = \cos^{-1} (x) \quad \text{ or } \quad \arccos (x)
$$

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


## The Inverse Tangent Function

Given the base tangent function :

$$
\tan \theta = \frac{\text{opposite}}{\text{adjacent}} = \frac{y}{x}
$$

Its inverse is defined as :

$$
\theta = \tan^{-1} \left( \frac{y}{x} \right) \quad \text{ or } \quad \arctan\left( \frac{y}{x} \right)
$$

The inverse tangent answers :
> "Given a slope y/x, what angle has that slope?"

<center>. . .</center>

Tangent is not a one-to-one function, and thus its domain has to be restricted for it to have an inverse. In this case, the interval where the "branch" that sits on the origin exists does the job. meaning, the **range** for inverse tangent is :

$$
\left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]
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

Given a point $(x,y)$, $\arctan\left( \frac{y}{x} \right)$ gives the angle the line from the origin makes with the x-axis - but only in Quadrants I and IV. This is where problems arise.

There is an ambiguity problem with inverse tangent - where slope $1$ ($\theta=\frac{\pi}{4}$) could mean that the point is either at $(1,1)$ or $(-1,-1)$. Same thing happens with slope $-1$.

> [!warning] Basically, inverse tangent *cannot* tell which quadrant the point is in.

