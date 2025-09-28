# 1.6 Complex Numbers

## Key Points

- Arithmetic Operations on Complex Numbers
- Square Roots of Negative Numbers
- Complex Solutions of Quadratic Equations

## Arithmetic Operations on Complex Numbers

In real number system, square root (or any even index root) of a negative number is **undefined**. However, in the <mark class="hltr-trippy">Complex Number System</mark>, it is possible to do so by defining a new number :

$$
i = \sqrt{ -1 }
$$

A <mark class="hltr-trippy">Complex Number</mark> is an expression of the form

$$
a + bi
$$

where $a$ and $b$ are real numbers and $i^2=-1$. The **real part** of this complex number is $a$, and the **imaginary part** is $b$.

Two complex numbers are equal if and only if their real parts are equal and their imaginary parts are equal.

Examples of complex numbers :
- $3+4i$ (imaginary part is $4$)
- $\frac{1}{2}-\frac{2}{3}i$ (imaginary part is $-\frac{2}{3}$)
- $6i$ (imaginary part is $6$)

> [!important] In a complex number system, a number without any imaginary part is still a complex number.
> For example, $-7$ is still a complex number, its imaginary part is $0$.

> [!important] A complex number without any real part is called a **Pure Imaginary Number**.
> For example, $6i$ is a pure imaginary number, its real part $0$.

Arithmetic with complex numbers works just like dealing with binomials.

It's easy to think about addition/subtraction with complex numbers. Add/subtract the real parts and add/subtract the imaginary parts.

For example,

$$
\begin{align}
  \text{Addition : } &\quad (a+bi) + (c+di) = (a+c)+(b+d)i \\
  \text{Subtraction : } &\quad (a+bi) - (c+di) = (a-c) + (b-d)i
\end{align}
$$

With multiplication, just keep in mind that $i^2=-1$.

For example,

$$
\begin{align}
  (a+bi) \cdot (c+di) &= ac + adi + bci + bdi^2 \\
  &= ac + adi + bci - bd \\
  &= (ac-bd)+(ad+bc)i
\end{align}
$$


### Powers of i

The trick to simplifying (evaluating) the powers of $i$ comes down to understanding that the powers of $i$ goes through a cycle for every 4th power :
- $i^1=1$
- $i^2=-1$
- $i^3=-i$
- $i^4=1$
- and cycle repeats at $i^5=1$

For $i^n$, divide $n$ by $4$ and look at the remainder :
- If $n \equiv 0 \text{ (mod 4)}$, then $i^n=1$
- If $n \equiv 1 \text{ (mod 4)}$, then $i^n=i$
- If $n \equiv 2 \text{ (mod 4)}$, then $i^n=-1$
- If $n \equiv 3 \text{ (mod 4)}$, then $i^n=-i$


### Complex Conjugate

Division of complex numbers is much like rationalizing the denominator of a radical expression.

For the complex number $z = a+bi$, we define its <mark class="hltr-trippy">Complex Conjugate</mark> to be :

$$
\overline{z} = \overline{a+bi} = a - bi
$$

The product of a complex number and its conjugate is always a non-negative real number :

$$
z \cdot \overline{z} = (a+bi)(a-bi) = a^2 + b^2
$$

To simplify the quotient $\frac{a+bi}{c+di}$, multiply the numerator and the denominator by the complex conjugate of the denominator :

$$
\begin{align}
  \frac{a+bi}{c+di} &= \left( \frac{a+bi}{c+di} \right)\left( \frac{c-di}{c-di} \right) \\
  &= \frac{ac - adi + bci + bd}{c^2-d^2} \\
  &= \frac{(ac+bd) + (bc-ad)i}{c^2 + d^2}
\end{align}
$$

Example :

$$
\begin{align}
  \frac{3+5i}{1-2i} &= \left( \frac{3+5i}{1-2i} \right)\left( \frac{1+2i}{1+2i} \right) \\
  &= \frac{3 + 6i + 5i - 10}{1+4} \\
  &= \frac{-7+11i}{5} \\
  &= -\frac{7}{5} + \frac{11}{5}i
\end{align}
$$

> [!important] I guess it's important to write complex numbers with its real part and imaginary part separately even if they share the same denominator.


## Square Roots of Negative Numbers

Just as every positive real number $r$ has two square roots ($\sqrt{ r }$ and $-\sqrt{ r }$), every negative number has two square roots. If $-r$ is a negative number, then its square roots are $\pm i\sqrt{ r }$.

$$
\begin{align}
  (i\sqrt{ r })^2 &= (-1)(r) = -r \\
  (-i\sqrt{ r })^2 &= (1)(-1)(r) = -r
\end{align}
$$

If $-r$ is a negative, then the **principal square root** of $-r$ is $i\sqrt{ r }$.

Examples :
- $\sqrt{ -1 } = i\sqrt{ 1 } = i$
- $\sqrt{ -16 } = i\sqrt{ 16 } = 4i$
- $\sqrt{ -3 } = i\sqrt{ 3 }$


## Complex Solutions of Quadratic Equations

In the previous section, we learned about how to solve a quadratic equation

$$
ax^2 + bx + c = 0
$$

using a quadratic formula :

$$
x = \frac{-b \pm \sqrt{ b^2 -4ac }}{2a}
$$

We also learned how to use the discriminant

$$
D = b^2-4ac
$$

to determine whether there are two real solutions ($D>0$), one real solution ($D=0$), or no real solutions ($D<0$).

Of course, in the complex number system, any quadratic equation will always have solutions.

The quadratic equation $x^2+9=0$ has a real solution in the complex number system :

$$
\begin{align}
  x^2 +9 &= 0 \\
  x^2 &= -9 \\
  x &= \pm \sqrt{ -9 } \\
  x &= \pm i\sqrt{ 9 } \\
  x &= \pm 3i
\end{align}
$$

Another example :

$$
\begin{align}
  x^2 + 4x + 5 &= 0 \\
  x &= \frac{-4 \pm \sqrt{ 4^2 - 4(5) }}{2} \\
  x &= \frac{-4 \pm \sqrt{ -4 }}{2} \\
  x &= \frac{-4 \pm 2i}{2} \\
  x &= -2 \pm i
\end{align}
$$

> [!important] In the complex system, we see that the solutions are complex conjugates of each other.
> In the example above, the solutions are $-2+i$ and $-2-i$. These are complex conjugates of each other.


## Extra : imaginary in the real world

While the imaginary number $i$ itself is not a "measurable" quantity in the real world, it still has real consequences, as $i$ encodes :
- Rotations
- Oscillations/Waves
- Quantum states
- Phase information
