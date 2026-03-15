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


### Derivative of $e^x$

Recall that the [[Eulers_Number_e#Key Property of $e$|key property of ]] $e$ is that the slope of the tangent line at $x=0$ for $e^x$ is $1$ :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$

This fact helps proving why the derivative of $e^x$ is equal to itself :
$$
\frac{d}{dx} e^x = e^x
$$

---
**Step 1 - Apply the limit definition of derivative to** $e^x$

The limit definition of derivative :
$$
\frac{d}{dx} f(x) = \lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}
$$

Which, when applied to $f(x)=e^x$ :
$$
\frac{d}{dx} e^x = \lim_{ h \to 0 } \frac{e^{x+h}-e^x}{h}
$$

---
**Step 2 - Use the product rule of the exponents**

$$
e^{x+h} = e^xe^h
$$

Which means :
$$
\lim_{ h \to 0 } \frac{e^{x+h}-e^x}{h} = 
\lim_{ h \to 0 } \frac{e^xe^h-e^x}{h}
$$

From here, we can factor out $e^x$ from the numerator :
$$
\lim_{ h \to 0 } e^x \cdot \frac{e^h-1}{h}
$$

---
**Step 3 - Take the limit**

By the constant multiple law of the limits :
$$
\lim_{ h \to 0 } e^x \cdot \frac{e^h-1}{h} = e^x \cdot \lim_{ h \to 0 } \frac{e^h-1}{h}
$$

Using the property of $e$ which states that :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = 1
$$

We get :
$$
e^x \cdot \lim_{ h \to 0 } \frac{e^h-1}{h} = e^x \cdot 1 = e^x
$$

Therefore,
$$
\boxed{\frac{d}{dx} e^x = e^x}
$$

> [!important] The number $e$ is **specifically chosen** so that the exponential function satisfies :
> *rate of growth = current value* at every point on the curve.


### Derivative of $a^x$

Recall the key property of $e$ :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = 1
$$

We know that natural logarithm is the inverse of the natural exponential function :
$$
\ln(e^x) = x
$$

Which means :
$$
\ln(e) = 1
$$

Thus, we get that :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = \ln(e)
$$

This means that we can replace the base to any number $a$ to get :
$$
\lim_{ h \to 0 } \frac{a^h-1}{h} = \ln(a)
$$

We can use this fact to find the derivative of $a^x$.

---
**Step 1 - Use the limit definition of the derivative**

Recall :
$$
f'(x) = \lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}
$$

That means the derivative of $a^x$ is :
$$
\frac{d}{dx} a^x = \lim_{ h \to 0 } \frac{a^{x+h}-a^x}{h}
$$

---
**Step 2 - Use the product law of exponents and factor**

$$
\lim_{ h \to 0 } \frac{a^{x+h}-a^x}{h}
= \lim_{ h \to 0 } \frac{a^xa^h-a^x}{h}
= \lim_{ h \to 0 } a^x \cdot \frac{a^h-1}{h}
$$

---
**Step 3 - Use the constant multiple law of limits**

$$
\lim_{ h \to 0 } a^x \cdot \frac{a^h-1}{h}
= a^x \cdot \lim_{ h \to 0 } \frac{a^h-1}{h}
$$

---
**Step 4 - Substitute** $\ln(a)$ **and finalize the proof**

Recall that :
$$
\lim_{ h \to 0 } \frac{a^h-1}{h} = \ln(a)
$$

This means we can substitute in $\ln(a)$ :
$$
a^x \cdot \lim_{ h \to 0 } \frac{a^h-1}{h}
= a^x \cdot \ln(a)
$$

Therefore :
$$
\boxed{\frac{d}{dx} a^x = a^x \cdot \ln(a)}
$$


#### The Chain Rule Approach

> [!important] This might be my favorite approach.

Recall the identity rule of exponents :
$$e^{\ln a}=a$$

Raise both sides to the power of $x$ :
$$
e^{x \ln a} = a^x
$$

This means that :
$$
\frac{d}{dx} e^{x \ln a} = \frac{d}{dx} a^x
$$

We can use this fact to find the derivative of $a^x$.

---
**Step 1 - Use the chain rule**

By the chain rule, $f(u)=e^u$ becomes the outside function, whereas $u = x \ln a$ becomes the inside function :
$$
\frac{d}{dx} e^{x \ln a} = \frac{d}{du} e^u \cdot \frac{d}{dx} u
$$

For outside function, we know that derivative of $e^x$ is equal to itself :
$$
\frac{d}{du} e^u = e^u \to e^{x \ln a}
$$

For inside function, since $\ln a$ is just a constant multiple, we get :
$$
\frac{d}{dx} u = \frac{d}{dx} x \ln a = \ln a \frac{d}{dx} x = \ln a
$$

Putting it together, we then get :
$$
\frac{d}{dx} e^{x \ln a} = e^{x \ln a} \cdot \ln a
$$

---
**Step 2 - Substitute back** $a^x$

Since :
$$
e^{x \ln a} = a^x
$$

We get :
$$
\frac{d}{dx} a^x = a^x \ln a
$$


#### The Change of Base Rule Approach

> [!important] This is the way that was taught in class.

> [!warning] This requires knowing ahead of time the derivative of natural log.

By the inverse rule, we can say that :
$$
y=a^x \iff x = \log_{a} y
$$

By the change of base rule, we can also say that :
$$
x = \frac{\ln y}{\ln a}
$$

We can use these facts to find the derivative of $a^x$.

---
**Step 1 - Differentiate both sides**

Given $x=\frac{\ln y}{\ln a}$, differentiate both sides :
$$
\frac{d}{dx} x = \frac{d}{dx} \frac{\ln y}{\ln a}
$$

---
**Step 2 - Compute and finalize the proof**

We use the fact that derivative of $x$ is just one, $\ln a$ is really just a constant multiple, and the fact that derivative of $\ln y$ is derivative of $y$ over $y$. Therefore, we get :
$$
1 = \frac{1}{\ln a} \cdot \frac{y'}{y}
$$

We neatly organize this by isolating the derivative of $y$ :
$$
y' = y \ln a
$$

We then substitute $y$ :
$$
y' = a^x \ln a
$$


#### The General Rule

For any function of the form (where $a$ and $b$ are constants) :
$$
a^{bx}
$$

In order to find the derivative :
$$
\frac{d}{dx} a^{bx}
$$

We can use the chain rule to define the outside and inside functions :
- $f(u)=a^u$
- $g(x)=u=bx$

Therefore :
$$
\begin{align}
  \frac{d}{dx} a^{bx} &= \frac{d}{dx} a^u \cdot \frac{d}{dx} u \\
  &= a^u \cdot \ln(a) \cdot u' \\
  &= a^{bx} \cdot \ln(a) \cdot b
\end{align}
$$


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

