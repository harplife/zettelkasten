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

Here are some examples :
- $\sqrt{ 25 } = 5$  since  $5^2 = 25$
- $\sqrt[3]{ 8 } = 2$  since $2^3 = 8$
- $\sqrt[4]{ 81 } = 3$  since  $3^4 = 81$


### Index : Even or Odd

If the index $n$ is even (square root, 4th root, etc.) :
- The radicand must be non-negative (if working in real numbers)
-                                                                                                       For example, $\sqrt{ -9 }$  is undefined in $\mathbb{R}$.

If the index $n$ is odd (cube root, 5th root, etc.) :
- The radicand can be any real number, including a negative value
- For example, $\sqrt[3]{ -27 } = 3$


### Fractional Exponent

Radicals are another way to write fractional exponents :

$$
\sqrt[n]{ a^m } = a^{m/n}
$$

Here are some examples :
- $\sqrt{ a } = a^{1/2}$
- $\sqrt[3]{ a^2 } = a^{2/3}$
- $\sqrt[4]{ 16 } = 16^{1/4} = 2$

