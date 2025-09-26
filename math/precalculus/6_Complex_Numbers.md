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

It's best to simplify $i$ when the power of $i$ is greater than $1$. For example, $i^2=-1$. Any power in multiples of $2$ can then be simplified. For example,

$$
\begin{align}
  i^{23} &= i^{22}i \\
  &= (-1)i \\
  &= -i
\end{align}
$$

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

