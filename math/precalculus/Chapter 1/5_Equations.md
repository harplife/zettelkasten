# 1.5 Equations

## Key Points

- Equations and Equalities
- Solving Linear Equations
- Formulas
- Solving Quadratic Equations
- Other Types of Equations

## Equations and Equalities

An <mark class="hltr-trippy">Equation</mark> is a mathematical statement that says two expressions are equal. It always has an equals sign $=$.

Examples :
- $2+3=5$
- $x^2+2x+1=0$
- $\sin{\theta}=\frac{1}{2}$

An equation can be true, false, or conditionally true depending on the value(s) of the variable(s).
- $2+3=5$ --> always true
- $x+2 = 5$ --> true only when $x = 3$
- $x+2 = x+3$ --> never true

The <mark class="hltr-trippy">Solution Set</mark> of an equation is the set of all values of the variable(s) that make the equation true.
- For $x+2 =5$, the solution set is $\{ 3 \}$
- For $x^2=4$, the solution set is $\{ -2, 2 \}$

> [!important] The solution set is also referred to as the **Solutions** or **Roots**.

> [!important] The process of finding the solutions is called **solving the equation**.


### Types of Equations

- Linear Equation : $2x+3=7$
- Quadratic Equation : $x^2-4=0$
- Polynomial Equation : $x^4+x^3-2=0$
- Rational Equation : $\frac{1}{x+1}=\frac{2}{x}$
- Trigonometric Equation : $\sin{\theta}=\cos{\theta}$
- Exponential Equation : $2^x=8$
- Logarithmic Equation : $\log(x)=2$


### Equivalent Equations

The <mark class="hltr-trippy">Equivalent Equations</mark> refer to two equations with exactly the same solutions.

> [!important] Most of precalculus is about *manipulating equations into simpler equivalent forms* so they are solvable.

Equivalent equations has a couple of properties.

| Property                | Equation                           |
| ----------------------- | ---------------------------------- |
| Addition Property       | $A=B \iff A+C=B+C$                 |
| Multiplication Property | $A=B \iff CA=CA$, given $C \neq 0$ |

> [!note] Addition property is basically subtraction property, as multiplication is division.


## Solving Linear Equations

The <mark class="hltr-trippy">Degree</mark> of an equation is determined by the highest power of the variable (with a nonzero coefficient) in the equation, after it's simplified.

The simplest type of equation is a <mark class="hltr-trippy">Linear Equation</mark>, or first-degree equation.

The general form of linear equations :

$$
ax + b = 0, \quad a \neq 0
$$

Both $a$ and $b$ are real numbers, and $x$ is the variable.

Examples of linear equations :
- $4x-5=3$
- $2x=\frac{1}{2}x-7$
- $x-6=\frac{x}{3}$

Solving a linear equation usually involves moving all terms (with variable $x$) to one side and all constant terms on the other.

For example,

$$
\begin{align}
  7x-4 &= 3x+8 \\
  7x &= 3x +8 + 4 \\
  7x &= 3x + 12 \\
  7x - 3x &= 12 \\
  4x &= 12 \\
  4x \cdot \frac{1}{4} &= 12 \cdot \frac{1}{4} \\
  x &= 3
\end{align}
$$


## Formulas

A <mark class="hltr-trippy">Formula</mark> is a special type of equation that shows the relationship between different variables.
- It's not usually meant to be solved for one specific variable (like a normal equation might be).
- Instead, it expresses how one quantity depends on others.

In other words, a formula is an equation that represents a rule or relationship between quantities.

Example of formulas :
- $A = \pi r^2$ (area of a circle)
- $V = \pi r^2h$ (volume of a cylinder)
- $F = ma$ (Newton's 2nd law)
- $m = \frac{y_{2}-y_{1}}{x_{2}-x_{1}}$ (slope)


## Solving Quadratic Equations

The <mark class="hltr-trippy">Quadratic Equation</mark>, or second-degree equation, generally takes the following form :

$$
ax^2 + bx + c = 0, \quad a \neq 0
$$

$a$, $b$, and $c$ are real numbers and $x$ is the variable.

Examples of quadratic equation :
- $x^2-2x-8=0$
- $3x+10=4x^2$
- $\frac{1}{2}x^2+\frac{1}{3}x-\frac{1}{6}=0$


Some quadratic equations can be solved by factoring and using the Zero-Product Property of real numbers. Be warned that this only works if the right-hand side of the equation is $0$.

> [!important] Zero-Product Property
> $$AB=0 \quad \text{if and only if} \quad A=0 \quad \text{or} \quad B=0$$

For example :

$$
\begin{align}
  x^2 + 5x &= 24 \\
  x^2+5x-24 &= 0 \\
  (x-3)(x+8) &= 0 \implies x=3 \text{ or } x=-8
\end{align}
$$

The solutions are $x = 3$ and $x = -8$.


Another form of quadratic equation is $x^2-c=0$, where $c$ is a positive constant. This form of equation factors as $(x-\sqrt{ c })(x+\sqrt{ c })=0$, so the solutions are $x=\pm\sqrt{ c }$.


### Completing the Square

<mark class="hltr-trippy">"Completing the Square"</mark> is one of the fundamental techniques in algebra that is used to solve quadratic equations.

Normally, when we have a quadratic formula in its generic form $ax^2+bx+c=0$, we'd factor the equation with a bit of trail and error.

We can take out the guesswork with a neat little trick, which works by adding a special number that would make the left-hand expression into a perfect square trinomial (i.e. $(x+d)^2$).

Given a quadratic expression $x^2+bx=0$ (ignore $c$ for now), that "special" number is $\left( \frac{b}{2} \right)^2$.

This works because :

$$
x^2 + bx + \left( \frac{b}{2} \right)^2 = \left( x+\frac{b}{2} \right)^2
$$

> [!important] The coefficient of $x^2$ has to be $1$ for this to work.
> We are ignoring $a$ for now, but later on when we add $a$ back in, the special number is actually  $\left( \frac{b}{2a} \right)^2$.

---

This can be understood geometrically. Take a look at this figure :

![[Pasted image 20250921223246.png|300]]

The area of the blue region is

$$
x^2 + 2\left( \frac{b}{2} \right)x = x^2 + bx
$$

Adding in the small square area $\left( \frac{b}{2} \right)^2$ to the blue region "completes" the square.

$$
x^2 + bx + \left( \frac{b}{2} \right)^2 = \left( x+\frac{b}{2} \right)^2
$$

---

Now with the constant $c$ back in the picture, completing the square looks like this :

$$
\begin{align}
  x^2+bx+c &= 0 \\
  x^2+bx &= -c \\
  x^2+bx+\left( \frac{b}{2} \right)^2 &= \left( \frac{b}{2} \right)^2-c \\
  \left( x+\frac{b}{2} \right)^2 &= \left( \frac{b}{2} \right)^2 -c \\
  x+\frac{b}{2} &= \pm \sqrt{ \left( \frac{b}{2} \right)^2 - c } \\
  x &= \pm \sqrt{ \left( \frac{b}{2} \right)^2 - c } - \frac{b}{2}
\end{align}
$$

It looks a bit messy, but it makes much more sense in practice. For example :

$$
\begin{align}
  x^2+4x+3 &= 0 \\
  x^2+4x &= -3 \\
  x^2+4x+4 &= -3+4 \\
  (x+2)^2 &= 1 \\
  x+2 &= \pm 1 \text{ (square root of 1 is 1)} \\
  x &= \pm 1 -2
\end{align}
$$

The solutions are $x = -3$ and $x = -1$. We can reach the same solution by factoring the left-hand expression, which would be $(x+3)(x+1) = 0$.

Completing the square may seem like overkill for a simple equation like above, but for equations that are not simple-cut like that, it works wonders :

$$
\begin{align}
  x^2-8x+13 &= 0 \\
  x^2-8x &= -13 \\
  x^2-8x+16 &= -13 + 16 \\
  (x-4)^2 &= 3 \\
  x-4 &= \pm \sqrt{ 3 } \\
  x &= 4 \pm \sqrt{ 3 }
\end{align}
$$


### Quadratic Formula

For any quadratic equation of the form,

$$
ax^2 + bx + c = 0, \quad a \neq 0
$$

the "universal tool" for solving such equation is the <mark class="hltr-trippy">Quadratic formula</mark>, which goes like this :

$$
x = \frac{-b \pm \sqrt{ b^2-4ac }}{2a}
$$

This formula is derived from Completing-the-Square, like so :

$$
\begin{align}
  ax^2+bx+c &= 0 \\
  x^2+\frac{b}{a}x+\frac{c}{a} &= 0\\
  x^2 + \frac{b}{a}x &= -\frac{c}{a} \\
  x^2+\frac{b}{a}x+\frac{b^2}{4a^2} &= -\frac{c}{a}+\frac{b^2}{4a^2} \\
  \left( x+\frac{b}{2a} \right)^2 &= \frac{b^2-4ac}{4a^2} \\
  x + \frac{b}{2a} &= \pm \frac{\sqrt{ b^2-4ac }}{2a} \\
  x &= -\frac{b}{2a} \pm \frac{\sqrt{ b^2-4ac }}{2a} \\
  x &= \frac{-b \pm \sqrt{ b^2-4ac }}{2a}
\end{align}
$$

It follows this process :
1. Start with the general quadratic
2. Divide through by $a$ (so the coefficient of $x^2$ is $1$)
3. Complete the square by adding in $\frac{b^2}{4a^2}$
4. Write the left side as a square
5. Take square root of both sides
6. Isolate $x$


Example of using the quadratic formula :

$$
\begin{align}
  3x^2-5x-1 &= 0 \\
  x &= \frac{5 \pm \sqrt{ 5^2 - 4(3)(-1) }}{2(3)} \\
  x &= \frac{5 \pm \sqrt{ 37 }}{6}
\end{align}
$$


#### The Discriminant

In the quadratic formula, the term under the square root ($b^2-4ac$) is called <mark class="hltr-trippy">the Discriminant</mark>, which shows the nature of the solutions (real vs. complex, distinct vs. repeated).

For discriminant $D = b^2 - 4ac$, the type of solutions for any quadratic equation can be decided by the value of the discriminant :
1. If $D > 0$, there are **two** distinct **real** roots.
2. If $D = 0$, there is **one real** repeated root.
3. If $D<0$, there are **two complex conjugate** roots (no real roots).

Case 1 ) Take $x^2-5x+6=0$. The discriminant is $1$ (bigger than $0$), which means there are two distinct real roots. Indeed, the roots are $x = 2, 3$.

Case 2 ) Take $x^2-4x+4=0$. The discriminant is $0$, which means there is one real repeated root. Indeed, the root is $x = 2$.

Case 3 ) Take $x^2+x+1=0$. The discriminant is $-3$ (less than $0$), which means there are two complex conjugate roots. Indeed, the roots are $x = \frac{-1 \pm i\sqrt{ 3 }}{2}$.

> [!important] When we go further into the lessons, we learn that the discriminants are used to find out whether a parabola $y = ax^2=bx+c$ intersects the x-axis.


## Other Types of Equations

Linear equations and quadratic equations are fairly clean and simple to deal with. However, when equations start to involve fractional expressions, radical expressions, fractional powers, and absolute-value, things get a little bit more complicated.

### Equations involving fractional expression

