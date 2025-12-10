# 4.4 Laws of Logarithms

## Key Concepts

- Laws of Logarithms
- Expanding and Combining Logarithmic Expressions
- Change of Base Formula


## Laws of Logarithms

There are three fundamental <mark class="hltr-trippy">Laws of Logarithms</mark> to note :

| Law           | Equation                                 | Description                                                                    |
| ------------- | ---------------------------------------- | ------------------------------------------------------------------------------ |
| Product Rule  | $\log_{a}(xy) = \log_{a}(x)+\log_{a}(y)$ | The log of a product of numbers is the sum of the logs of the numbers.         |
| Quotient Rule | $\log_{a}(x/y)=\log_{a}(x)-\log_{a}(y)$  | The log of a quotient of numbers is the difference of the logs of the numbers. |
| Power Rule    | $\log_{a}(x^c)=c \cdot \log_{a}(x)$      | The log of a power of a number is the exponent times the log of the number.    |

### Proof : Product Rule of Logarithm

Let $\log_{a}(x)=u$ and $\log_{a}(y)=v$. When written in exponential form, these equations become :

$$
a^u=x \quad \text{and} \quad a^v=y
$$

Thus,

$$
\begin{align}
  \log_{a}(xy) &= \log_{a}(a^{u}a^{v}) \\
  &= \log_{a}(a^{u+v}) \\
  &= u+v \\
  &= \log_{a}(x) + \log_{a}(y)
\end{align}
$$


### Proof : Quotient Rule of Logarithm

Using the Product Rule, we have :

$$
\begin{align}
  \log_{a}(x) &= \log_{a}\left[\left(\frac{x}{y}\right)y\right] \\
  &= \log_{a}\left( \frac{x}{y} \right) + \log_{a}(y)
\end{align}
$$

Thus,

$$
\log_{a}\left( \frac{x}{y} \right) = \log_{a}(x) - \log_{a}(y)
$$


### Proof : Power Rule

Let $\log_{a}(x)=u$. Its exponential form is $a^u=x$, thus :

$$
\begin{align}
  \log_{a}(x^c) &= \log_{a}(a^u)^c \\
  &= \log_{a}(a^{uc}) \\
  &= uc \\
  &= c \cdot \log_{a}(x)
\end{align}
$$


## Expanding and Combining Logarithmic Expressions

The process of using the Laws of Logarithms to write the logarithm of a product or a quotient as the sum or difference of logarithms is called <mark class="hltr-trippy">Expanding a Logarithmic Expression</mark>.

For example :

$$
\begin{align}
  \ln\left( \frac{ab}{\sqrt[3]{ c }} \right) &= \ln(ab) - \ln(\sqrt[3]{ c }) \\
  &= \ln(a) + \ln(b) - \ln(c^{1/3}) \\
  &= \ln(a) + \ln(b) - \frac{1}{3} \ln(c)
\end{align}
$$

The opposite of expanding is called <mark class="hltr-trippy">Combining Logarithmic Expressions</mark>.

For example :

$$
\begin{align}
  3\log(x)+\frac{1}{2}\log(x+1) &= \log(x^3) + \log(x+1)^{1/2} \\
  &= \log(x^3(x+1)^{1/2})
\end{align}
$$


## Change of Base Formula

Let $y=\log_{a}(x)$ and consider the following :
1. Its exponential form is $a^y=x$
2. Take $\log_{b}$ of each side to get $\log_{b}(a^y) = \log_{b}(x)$
3. By the quotient rule, we get $y \log_{b}(a)=\log_{b}(x)$
4. Divide both sides by $\log_{b}(a)$ to get $y = \frac{\log_{b}(x)}{\log_{b}(a)}$

Thus, we get the <mark class="hltr-trippy">Change of Base Formula</mark> :

$$
\log_{a}(x) = \frac{\log_{b}(x)}{\log_{b}(a)} \quad (a>0,b>0)
$$

Additionally, if we let $x=b$, then $\log_{b}(x)=1$. Thus, this formula becomes :

$$
\log_{a}(b) = \frac{1}{\log_{b}(a)}
$$

> [!important] This allows us to evaluate a logarithm to *any* base. Particularly, we can express a logarithm in terms of *common logarithms* or *natural logarithms*.

Example of expressing a logarithm in terms of common logarithms :

$$
\log_{8}(5) = \frac{\log_{5}}{\log_{8}} \approx 0.77398
$$

Example of expressing a log in terms of natural logs :

$$
\log_{9}(20) = \frac{\ln(20)}{\ln(9)} \approx 1.36342
$$

### Extra : Converting between bits and natural logs

Binary logarithms (base 2) are used in :
- Algorithm complexity : $O(\log_{2}(n))$
- Entropy and information content
- Compression and coding theory

But most math software uses natural log $\ln$ by default.

You can compute the number of bits required to represent a number $N$ :

$$
\log_{2}(N) = \frac{\ln(N)}{\ln(2)}
$$


### Extra : Conversion for compound interest

Solving for time to double your money :

$$
2 = (1+r)^t
$$

We can convert it to its exponential form :

$$
\log_{(1+r)}(2)=t
$$

Using the change of base formula, we can convert the log to common logs :

$$
t = \frac{\log(2)}{\log(1+r)}
$$