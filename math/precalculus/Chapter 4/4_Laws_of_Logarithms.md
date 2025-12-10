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

