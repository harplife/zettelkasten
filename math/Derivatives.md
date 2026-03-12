# Derivatives

## Basic Derivative Rules

| Name                   | Equation                                                                            |
| ---------------------- | ----------------------------------------------------------------------------------- |
| Constant Rule          | $\frac{d}{dx}(c)=0$                                                                 |
| Constant Multiple Rule | $\frac{d}{dx}[cf(x)]=cf'(x)$                                                        |
| Power Rule             | $\frac{d}{dx}(x^n)=nx^{n-1}$                                                        |
| Sum Rule               | $\frac{d}{dx}[f(x)+g(x)]=f'(x)+g'(x)$                                               |
| Difference Rule        | $\frac{d}{dx}[f(x)-g(x)]=f'(x)-g'(x)$                                               |
| Product Rule           | $\frac{d}{dx}[f(x)g(x)]=f(x)g'(x)+g(x)f'(x)$                                        |
| Quotient Rule          | $\frac{d}{dx}\left[ \frac{f(x)}{g(x)} \right]=\frac{g(x)f'(x)-f(x)g'(x)}{[g(x)]^2}$ |
| Chain Rule             | $\frac{d}{dx}f(g(x))=f'(g(x))g'(x)$                                                 |


## Derivative of Exponential Functions

| Name                     | Equation                                                                         |
| ------------------------ | -------------------------------------------------------------------------------- |
| Special Exponential Rule | $\frac{d}{dx}(e^{g(x)})=e^{g(x)}g'(x)$<br>or $\frac{d}{dx}(e^x)=e^x$             |
| General Exponential Rule | $\frac{d}{dx}(a^{g(x)})=\ln(a)a^{g(x)}g'(x)$<br>or $\frac{d}{dx}(a^x)=\ln(a)a^x$ |

#todo 2026-03-12
- Why derivative of $e^x$ is $e^x$
- Proof of the derivative of exponents (using chain rule)
- why e matter?
- Why does ln appear for general exponents?
- Implicit differentiations

In the context of calculus, how is Euler's number e defined?

Tell me more about the part where you said we can convert exponentials using logs :
$$
a^x = e^{x \ln a}
$$


### Derivative of $e^x$ - The Limit Approach

The derivative of a function $f(x)$ is defined as :
$$
\frac{d}{dx}f(x) = \lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}
$$

Given $f(x)=e^x$, we can find its derivative using the limit definition.

---
Step 1 - Define the derivative

Let
$$
f(x) = e^x
$$

Then the derivative becomes
$$
\lim_{ h \to 0 } \frac{e^{x+h} - e^x}{h}
$$

---
Step 2 - Use the exponent rule and factor

By the product rule of exponents
$$
e^{x+h} = e^xe^h
$$

Substitute this into the expression
$$
\frac{e^xe^h-e^x}{h}
$$

Factor out $e^x$
$$
e^x \cdot \frac{e^h-1}{h}
$$

Now the derivative becomes
$$
e^x \lim_{ h \to 0 } \frac{e^h-1}{h}
$$

> [!important] Note that $e^x$ comes out of the limit because it does not depend on $h$.

---
Step 3 - Find the value that the limit reaches




## Derivative of Logarithmic Functions

| Name | Equation                                             |
| ---- | ---------------------------------------------------- |
|      | $\frac{d}{dx}(\ln x)=\frac{1}{x}, x>0$               |
|      | $\frac{d}{dx}\ln(g(x))=\frac{g'(x)}{g(x)}$           |
|      | $\frac{d}{dx}(\log_{a}x)=\frac{1}{x \ln a}, x>0$     |
|      | $\frac{d}{dx}(\log_{a}g(x))=\frac{g'(x)}{g(x)\ln a}$ |


## Derivative of Trigonometric Functions

| Name                    | Equation                              |
| ----------------------- | ------------------------------------- |
| Derivative of Sine      | $\frac{d}{dx}(\sin x)=\cos x$         |
| Derivative of Cosine    | $\frac{d}{dx}(\cos x)=-\sin x$        |
| Derivative of Tangent   | $\frac{d}{dx}(\tan x)=\sec^2 x$       |
| Derivative of Cotangent | $\frac{d}{dx}(\cot x)=-\csc^2 x$      |
| Derivative of Secant    | $\frac{d}{dx}(\sec x)=\sec x \tan x$  |
| Derivative of Cosecant  | $\frac{d}{dx}(\csc x)=-\csc x \cot x$ |



### Inverse Trigonometric Functions


### Hyperbolic Functions


### Inverse Hyperbolic Functions



## Implicit Differentiation

