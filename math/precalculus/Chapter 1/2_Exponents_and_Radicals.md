# 1.2 Exponents and Radicals

## Key Points

- Integer Exponents
- Rules for Working with Exponents
- Scientific Notation
- Radicals
- Rational Exponents
- Rationalizing the Denominator; Standard Form

## Integer Exponents

A product of identical numbers is usually written in *exponential notation*.

<mark class="hltr-trippy">Exponential Notation</mark> is defined as follows :

---

If $a$ is any real number and $n$ is a positive integer, then the $n$th power of $a$ is
$$
a^n = a \times a \times \dots \times a
$$

The number $a$ is called the <mark class="hltr-trippy">base</mark>, and $n$ is called the <mark class="hltr-trippy">exponent</mark>.

---

> [!note] The number of times the base repeats is called the $n$ *factor*.
> For example, $(5 \times 5 \times 5)$ has 3 factors.


### Laws of Exponents

| Property            | Rule                                                       | Example                                        |
| ------------------- | ---------------------------------------------------------- | ---------------------------------------------- |
| Product             | $a^m \cdot a^n = a^{m+n}$                                  | $2^3 \cdot 2^2 = 2^5$                          |
| Quotient            | $\frac{a^m}{a^n} = a^{m-n}, a \neq 0$                      | $\frac{5^6}{5^2} = 5^4$                        |
| Power of a Power    | $(a^m)^n = a^{mn}$                                         | $(3^2)^3 = 3^6$                                |
| Power of a Product  | $(ab)^n = a^n \cdot b^n$                                   | $(2 \cdot 3)^2 = 2^2 \cdot 3^2$                |
| Power of a Quotient | $\left( \frac{a}{b} \right)^n = \frac{a^n}{b^n}, b \neq 0$ | $\left( \frac{4}{5} \right)^2 = \frac{16}{25}$ |
| Zero Exponent       | $a^0 = 1, a \neq 0$                                        | $10^0 = 1$                                     |
| Negative Exponent   | $a^{-n} = \frac{1}{a^n}, a \neq 0$                         | $2^{-4} = \frac{1}{16}$                        |
| Rational Exponent   | $a^{\frac{m}{n}} = \sqrt[n]{ a^m } = (\sqrt[n]{ a })^m$    | $16^{3/4} = (\sqrt[4]{ 16 })^3 = 2^3 = 8$      |

> [!example] Negative Exponent Rule applied to a fraction
> Raising a fraction to a negative power inverts the fraction and changes the sign of the exponent :
> 
> $$\left( \frac{a}{b} \right)^{-n} = \left( \frac{b}{a} \right)^n$$
> 
> Negative exponents on both numerator and denominator can invert the fraction as well :
> 
> $$\frac{a^{-n}}{b^{-m}} = \frac{b^m}{a^n}$$


## Scientific Notation

<mark class="hltr-trippy">Scientific Notation</mark> is a way to handle very large or very small numbers conveniently. A number is in scientific notation if it is written in the form :

$$
a \times 10^n
$$

Where $a$ is a decimal number (called the **coefficient** or **mantissa**) such that

$$
1 \leq |a| < 10
$$

and $n$ is an integer (positive, negative, or zero).

> [!note] The coefficient must be exactly one nonzero digit to the left of the decimal point.

Here are some examples :
- $5,600$ = $5.6 \times 10^3$
- $0.00032$ = $3.2 \times 10^{-4}$
- $1.23 \times 10^7$ = $12,300,000$


## Radicals

A <mark class="hltr-trippy">Radical</mark> is an expression that uses the radical symbol $\sqrt[n]{ a }$ to represent the *nth root* of a number.

$\sqrt[n]{ a } = b$  means that   $b^n = a$  where :
- $n$ is the **index** of the radical (must be a positive integer)
- $a$ is the **radicand** (the number inside the radical)
- The symbol $\sqrt{  }$ is called the **radical sign**

> [!note] When the index is not explicit, it means $n = 2$  (square root)

> [!important] If $n$ is *even* and $a>0$, there are two real nth roots - one positive and one negative. For example, the fourth roots of $16$ are $2$ and $-2$.
> By convention, the positive nth root is called the <mark class="hltr-trippy">principal nth root</mark>. If it's not clear whether radicand should be positive or negative, absolute value is used to express the nth root (e.g. $\sqrt{ x^2 } = |x|$). Otherwise, the positive value is used (e.g. $\sqrt{ 9 } = 3$).
> 
> By convention (especially in Computer Science), the radical is defined to mean the principal root only.
> 
> For further clarification, take $\sqrt[4]{ (-3)^4 }$. While at glance the answer could to be $-3$, the correct answer is $3$.

Here are some examples :
- $\sqrt{ 25 } = 5$  since  $5^2 = 25$
- $\sqrt[3]{ 8 } = 2$  since $2^3 = 8$
- $\sqrt[4]{ 81 } = 3$  since  $3^4 = 81$


> [!warning] 



### Index : Even or Odd

If the index $n$ is even (square root, 4th root, etc.) :
- The radicand must be non-negative (if working in real numbers). For example, $\sqrt{ -9 }$  is undefined in $\mathbb{R}$.

If the index $n$ is odd (cube root, 5th root, etc.) :
- The radicand can be any real number, including a negative value
- For example, $\sqrt[3]{ -27 } = 3$


### Fractional Exponent

Radicals are another way to write <mark class="hltr-trippy">Fractional Exponents</mark>  (aka **Rational Exponents**):

$$
\sqrt[n]{ a^m } = a^{m/n}
$$

Here are some examples :
- $\sqrt{ a } = a^{1/2}$
- $\sqrt[3]{ a^2 } = a^{2/3}$
- $\sqrt[4]{ 16 } = 16^{1/4} = 2$

### Properties of nth Roots

| Property         | Rule                                                                     | Example                                                                         |
| ---------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| Product          | $\sqrt[n]{ ab } = \sqrt[n]{ a } \cdot \sqrt[n]{ b }$                     | $\sqrt{ 36 } = \sqrt{ 9 \cdot 4 } = 3 \cdot 2 = 6$                              |
| Quotient         | $\sqrt[n]{ \frac{a}{b} } = \frac{\sqrt[n]{ a }}{\sqrt[n]{ b }}$, $b > 0$ | $\sqrt[3]{ \frac{8}{27} } = \frac{\sqrt[3]{ 8 }}{\sqrt[3]{ 27 }} = \frac{2}{3}$ |
| Power of a Power | $(\sqrt[n]{ a })^m = \sqrt[n]{ a^m } = a^{m/n}$                          | $(\sqrt{ 5 })^4 = (5^{1/2})^4 = 5^{4/2} = 5^2 = 25$                             |
| Nested Radical   | $\sqrt[m]{ \sqrt[n]{ a } } = \sqrt[mn]{ a }$                             | $\sqrt[2]{ \sqrt[3]{ 8 } } = \sqrt[6]{ 8 } = 2^{1/2}$                           |
| Absolute Value   | $\sqrt[n]{ a^n } = \lvert a \rvert$, $n > 0$                             | $\sqrt{ (-7)^2 } = \sqrt{ 49 } = 7 = \lvert -7 \rvert$                          |
| Root of Zero     | $\sqrt[n]{ 0 } = 0$                                                      |                                                                                 |

## Rationalizing the Denominator

<mark class="hltr-trippy">Rationalizing the Denominator</mark> is the process of rewriting a fraction so that its denominator contains no radicals.

For example, $\frac{5}{\sqrt{ 3 }}$ should be converted to its standard form by following this process :

$$
\frac{5}{\sqrt{ 3 }} \cdot \frac{\sqrt{ 3 }}{\sqrt{ 3 }} = \frac{5\sqrt{ 3 }}{3}
$$

### Standard Form

<mark class="hltr-trippy">Standard Form</mark> means that an expression is written in its simplest, most conventional way. This usually involves :
- **No radicals in the denominator** (e.g. $\frac{1}{\sqrt{ 2 }}$ should be written as $\frac{\sqrt{ 2 }}{2}$)
- **No perfects powers inside a radical / Coefficients outside radicals when possible** (e.g. $\sqrt{ 12 }$ should be written as $2\sqrt{ 3 }$)
- **Index minimized** (e.g. $\sqrt[6]{ x^3 }$ should be simplified to $\sqrt{ x }$)
- **No fractions inside a radical** (e.g. $\sqrt{ \frac{9}{16} } = \frac{3}{4}$)


### Higher Roots

In general, if the denominator is of the form $\sqrt[n]{ a^m }$ with $m < n$, then multiplying the numerator and denominator by $\sqrt[n]{ a^{n-m} }$ will rationalize the denominator.

$$
\sqrt[n]{ a^m }\sqrt[n]{ a^{n-m} } = \sqrt[n]{ a^{m + n - m} } = \sqrt[n]{ a^n } = a
$$

For example, $\frac{1}{\sqrt[7]{ a^2 }}$ should be converted to its standard form by following this process :

$$
\frac{1}{\sqrt[7]{ a^2 }} = \frac{1}{\sqrt[7]{ a^2 }} \cdot \frac{\sqrt[7]{ a^5 }}{\sqrt[7]{ a^5 }} = \frac{\sqrt[7]{ a^5 }}{a}
$$


### Binomial Denominator

Rationalizing a denominator with two terms (a binomial) involves multiplying both the numerator and the denominator with the conjugate of the denominator.

For example, rationalizing $\frac{1}{2+\sqrt{ 3 }}$ involves the following process :

$$
\frac{1}{2+\sqrt{ 3 }} \cdot \frac{2-\sqrt{ 3 }}{2-\sqrt{ 3 }} = \frac{2-\sqrt{ 3 }}{(2+\sqrt{ 3 })(2-\sqrt{ 3 })} = \frac{2-\sqrt{ 3 }}{4-3} = 2 - \sqrt{ 3 }
$$

