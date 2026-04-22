# Exponents and Logarithms

## Exponents

#define An <mark class="hltr-trippy">Exponentiation</mark> is a mathematical operation, denoted as $b^n$, that represents repeated multiplication of a base number $b$ by itself a specified number of times $n$, known as the *exponent* or *power*.

$$
b^n
$$

It is read as "b raised to the power of n".

#example A simple exponent $5^3$ :

$$
5^3 = 5 \times 5 \times 5 = 125
$$


### Exponent Rules/Laws

| Name                     | Equation                                       |
| ------------------------ | ---------------------------------------------- |
| Product Rule             | $a^m \times a^n = a^{m+n}$                     |
| Quotient Rule            | $\frac{a^m}{a^n}=a^{m-n}$                      |
| Power of a Power Rule    | $(a^m)^n=a^{mn}$                               |
| Power of a Product Rule  | $(ab)^m=a^mb^m$                                |
| Power of a Quotient Rule | $\left( \frac{a}{b} \right)^m=\frac{a^m}{b^m}$ |
| Zero Exponent Rule       | $a^0=1$                                        |
| Negative Exponent Rule   | $a^{-m}=\frac{1}{a^m}$                         |
| Fractional Exponent Rule | $a^{m/n}=\sqrt[n]{ a^m }$                      |


### Exponent Problem Traps

#### Hidden Exponent Splitting/Combination Trap

Trap : Forgetting to use product/quotient rule

#example Hidden exponent splitting in $\frac{8^{x-1}x}{3}$ :

$$
\begin{align}
  \text{Rewrite } &: 8^{x-1} = 8^x \cdot 8^{-1} \to \frac{8^x \cdot 8^{-1} \cdot x}{3} \\
  \text{Simplify } &: \frac{8^x \cdot x}{24}
\end{align}
$$

#example Hidden exponent combination in $\frac{4^{x-1}}{2}$ :

$$
\begin{align}
  \text{Rewrite } &: 4^{x-1} = (2^2)^{x-1} = 2^{2x-2} \to \frac{2^{2x-2}}{2} \\
  \text{Simplify } &: \frac{2^{x-2}}{2} = 2^{x-2-1} = 2^{x-3}
\end{align}
$$


#### Hidden Base Conversion Trap

Trap : Two exponents with different bases, but they turn out to be powers of the same base.

#example Hidden base conversion trap in $\frac{16^x}{8}$ :

$$
\begin{align}
  \text{Common Mistake } &: \frac{16^x}{8} \neq 2^x\\
  \text{Rewrite } &: \frac{16}{8} = \frac{2^4}{2^3} \\
  \text{Simplify } &: \frac{2^{4x}}{2^{3}} = 2^{4x-3}
\end{align}
$$


#### Hidden Exponent Factoring Trap

Trap : Exponents with different powers can be factored.

#example Hidden exponent factoring trap in $3^{2x}+3^{2x+1}$ :

$$
\begin{align}
  \text{Rewrite } &: 3^{2x+1} = 3^{2x} \cdot 3 \to 3^{2x}+3^{2x} \cdot 3 \\
  \text{Factor } &: 3^{2x}(1+3) = 4 \cdot 3^{2x}\\
  \text{Simplify } &: 4 \cdot 3^{2x} = 4 \cdot 9^x
\end{align}
$$


#### Hidden Cancellation Trap

Trap : Expressions are written so that cancellation is not immediately obvious, often covered by other traps.

#example Hidden cancellation trap in $\frac{4^{x+1}}{2^{2x}}$ :

$$
\begin{align}
  \text{Rewrite } &: 4^{x+1} = (2)^{2x+2} \to \frac{2^{2x+2}}{2^{2x}} \\
  \text{Simplify } &: \frac{2^{2x+2}}{2^{2x}}=2^{2x+2-2x}=2^2=4
\end{align}
$$

> [!important] Matching bases (avoiding hidden base conversion trap) often help identifying the hidden cancellation trap.


#### Hidden Exponent Isolation Trap

Trap : When solving exponential equations, matching bases allows exponent comparison.

#example Exponent isolation trap in $2^{x+1}=8^x$ :

$$
\begin{align}
  \text{Rewrite } &: 8=2^3 \to 2^{x+1} = 2^{3x} \\
  \text{Equate exponents } &: x+1 = 3x \\
  \text{Solve } &: x=\frac{1}{2}
\end{align}
$$


#### Fractional Exponent Trap

Trap : Fractional exponents can sometimes be cancelled out.

#eaxmple Fractional exponent trap in $16^{3x/4}$ :

$$
\begin{align}
  \text{Rewrite } &: 16 = 2^4 \to (2^4)^{3x/4} \\
  \text{Simplify } &: (2^4)^{3x/4} = 2^{4 \cdot 3x/4} = 2^{3x}
\end{align}
$$


## Logarithms

#define A <mark class="hltr-trippy">Logarithm</mark> is the **inverse** operation of **exponentiation**, representing the exponent to which a base number must be raised to produce a given value.

The formal definition of Logarithms :

$$
\text{If } x=b^y, \text{ then } y=\log_{b} x \quad \text{given } x>0
$$

where $b$ is the base, $x$ is the argument, and $y$ is the exponent result.
- $x>0$ because $b^y$ can never produce a negative number.

#define A <mark class="hltr-trippy">Common Logarithm</mark> refers to a logarithm with base $10$, and it is denoted simply as $\log x$ without any indication of the base.

#define A Natural Logarithm refers to a logarithm with base $e$, and it is denoted as $\ln x$.


### Logarithm Rules/Laws

| Name                | Equation                                                                            |
| ------------------- | ----------------------------------------------------------------------------------- |
| Product Rule        | $\log_{b}(xy)=\log_{b}x+\log_{b}y$                                                  |
| Quotient Rule       | $\log_{b}\left(\frac{x}{y} \right)=\log_{b}x-\log_{b}y$                             |
| Power Rule          | $\log_{b}(x^n)=n \log_{b} x$                                                        |
| Change of Base Rule | $\log_{b}x=\frac{\log_{c}x}{\log_{c}b}$<br>or $\log_{b}x \cdot \log_{c}b=\log_{c}x$ |
| Zero Rule           | $\log_{b}(1)=0$                                                                     |
| Identity Rule       | $\log_{b}(b)=1$                                                                     |
| Equality Rule       | $\log_{b}x=\log_{b}y \to x=y$                                                       |
| Inverse Rule        | $b^{\log_{b}x}=x$<br>or $\log_{b}(b^x)=x$                                           |
| Reciprocal Rule     | $\log_{b}\left( \frac{1}{x} \right)=-\log_{b}(x)$                                   |


#### Proof of The Product Rule

Rule :
$$
\log_{b}(xy)=\log_{b}(x)+\log_{b}(y)
$$

---
**Step 1 - Define the logs**

Let
$$
\begin{align}
  \log_{b}(x) &= m \\
  \log_{b}(y) &= n
\end{align}
$$

By definition of logarithm :
$$
\begin{align}
  b^m &= x \\
  b^n &=y 
\end{align}
$$

---
**Step 2 - Multiply the numbers**

$$
xy = (b^m)(b^n)
$$

Using the product rule of exponents :
$$
b^mb^n = b^{m+n}
$$

So
$$
xy = b^{m+n}
$$

---
**Step 3 - Convert back to logarithm form**

If
$$
  b^{m+n} = xy
$$

and
$$
\log_{b}(b^{m+n}) = m+n
$$

then
$$
\log_{b}(xy) = m+n
$$

---
**Step 4 - Substitute back the original numbers**

Recall
$$
\begin{align}
  m = \log_{b}(x) \\
  n = \log_{b}(y)
\end{align}
$$

Plug in the original logs to finalize the proof
$$
\log_{b}(xy) = \log_{b}(x) + \log_{b}(y)
$$


#### Proof of the Power Rule

Rule :
$$
\log_{b}(x^k) = k \log_{b}(x)
$$

---
**Step 1 - Define the logarithm**

Let
$$
\log_{b}(x) = m
$$

By definition of logarithm
$$
x = b^m
$$

---
**Step 2 - Raise both sides to power** $k$

$$
x^k = (b^m)^k
$$

By the power of the product rule of exponents
$$
(b^m)^k=b^{mk}
$$

So
$$
x^k = b^{mk}
$$

---
**Step 3 - Convert back to log**

If
$$
b^{mk} = x^k
$$

and
$$
\log_{b}(b^{mk})=mk
$$

Then
$$
\log_{b}(x^k)=mk
$$

---
**Step 4 - Substitute back the original numbers**

Recall
$$
m = \log_{b}(x)
$$

Substitute the original log and finalize the proof
$$
\log_{b}(x^k) = k \log_{b}(x)
$$


#### Proof of the Change of Base Rule

Rule :
$$
\log_{b}(a) = \frac{\log_{c}(a)}{\log_{c}(b)}
$$

---
Step 1 - Define the logarithm

Let
$$
x = \log_{b}(a)
$$

By definition of logarithm :
$$
b^x=a
$$

---
**Step 2 - Take log base** $c$ **of both sides**

$$
\log_{c}(b^x) = \log_{c}(a)
$$

---
**Step 3 - Apply the power rule**

$$
x \log_{c}(b) = \log_{c}(a)
$$

---
**Step 4 - Isolate** $x$

$$
x = \frac{\log_{c}(a)}{\log_{c}(b)}
$$

---
**Step 5 - Substitute the original number**

Recall
$$
x = \log_{b}(a)
$$

Substitute the original log and finalize the proof
$$
\log_{b}(a) = \frac{\log_{c}(a)}{\log_{c}(b)}
$$





$$
\lim_{ x \to 21 } \frac{2x-42}{2\pi\cos(\pi x)}
$$