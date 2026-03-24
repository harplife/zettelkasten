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


## Reciprocal Derivatives of Inverses

Two functions $f$ and $g$ are inverse functions if :
$$
g(f(x)) = x \quad \text{ and } \quad f(g(x)) = x
$$

> [!warning] Don't get inverse function confused with *multiplicative inverse* (reciprocal) or the *additive inverse* (opposite).
> The inverse of $f(x)=x$ is $x$ ; NOT $\frac{1}{x}$ or $-x$.

Let $f$ and $g$ be inverses :
$$
g = f^{-1} \implies g(f(x)) = x
$$

Differentiate both sides :
$$
\frac{d}{dx}[g(f(x))] = 1
$$

For the left side, apply the chain rule :
$$
\frac{d}{dx}[g(f(x))] = g'(f(x)) \cdot f'(x)
$$

Thus, we have :
$$
g'(f(x)) \cdot f'(x) = 1
$$

Isolate :
$$
g'(f(x)) = \frac{1}{f'(x)}
$$

Let $u=f(x)$. This means :
- $x=f^{-1}(u)=g(u)$
- $g'(f(x)) = g'(u)$

Substitute :
$$
g'(u) = \frac{1}{f'(g(u))}
$$

Rename the dummy variable $u \to x$ :
$$
\boxed{g'(x) = \frac{1}{f'(g(x))}}
$$

Or more accurately :

$$
\boxed{(f^{-1})'(u) = \frac{u'}{f'(f^{-1}(u))}}
$$

---
We can see that this relationship holds true with $f(x)=e^x$ and its inverse $g(x)=\ln x$.

$$
g'(x)=\frac{1}{f'(g(x))}=\frac{1}{f'(\ln x)} = \frac{1}{e^{\ln x}} = \frac{1}{x}
$$

Note that :
$$
f'(x) = e^x \implies f'(\ln x) = e^{\ln x} = x
$$


## Derivative of Exponential Functions

| Name                     | Equation                                                                         |
| ------------------------ | -------------------------------------------------------------------------------- |
| Special Exponential Rule | $\frac{d}{dx}(e^{g(x)})=e^{g(x)}g'(x)$<br>or $\frac{d}{dx}(e^x)=e^x$             |
| General Exponential Rule | $\frac{d}{dx}(a^{g(x)})=\ln(a)a^{g(x)}g'(x)$<br>or $\frac{d}{dx}(a^x)=\ln(a)a^x$ |

### Derivative of $e^x$

Recall that the the fundamental property of $e$ is that the slope of the tangent line at $x=0$ for $e^x$ is $1$ :
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


#### Derivative of e^{g(x)}

Let $g(x)$ be any function differentiable at $x$.

We can differentiate $e^{g(x)}$ by using the chain rule.

Outside function is $e^u$ and the inside function is $u=g(x)$ :
$$
\begin{align}
  \frac{d}{dx} e^{g(x)} &= \frac{d}{dx} e^u \cdot u' \\
  &= e^u \cdot u'
\end{align}
$$

Plug the original numbers back in  :
$$
\boxed{\frac{d}{dx} e^{g(x)} = e^{g(x)} \cdot g'(x)}
$$


### Derivative of $a^x$

Recall the fundamental property of $e$ :
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

Recall the inverse rule :
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


#### Derivative of a^{g(x)}

Let $g(x)$ be any function differentiable at $x$.

We use the chain rule to find the derivative of $a^{g(x)}$.

The outside function is $a^u$ and the inside function is $u=g(x)$ :
$$
\begin{align}
  \frac{d}{dx} a^{g(x)} &= \frac{d}{dx} a^u \cdot \frac{d}{dx} u \\
  &= a^u \cdot \ln(a) \cdot u'
\end{align}
$$

Substitute the original numbers back in and we get :
$$
\boxed{\frac{d}{dx} a^{g(x)} = a^{g(x)} \cdot \ln(a) \cdot g'(x)}
$$


## Derivative of Logarithmic Functions

| Name                                             | Equation                                             |
| ------------------------------------------------ | ---------------------------------------------------- |
| Derivative of Natural Log of $x$                 | $\frac{d}{dx}(\ln x)=\frac{1}{x}, x>0$               |
| Derivative of Natural Log of any function of $x$ | $\frac{d}{dx}\ln(g(x))=\frac{g'(x)}{g(x)}$           |
| Derivative of log of $x$                         | $\frac{d}{dx}(\log_{a}x)=\frac{1}{x \ln a}, x>0$     |
| Derivative of log of any function of $x$         | $\frac{d}{dx}(\log_{a}g(x))=\frac{g'(x)}{g(x)\ln a}$ |

> [!important] Logarithms measure multiplicative growth.
> This means that if $x$ doubles :
> $$\ln(2x)-\ln(x)=\ln 2$$
> 
> The change depends on **ratios**, not absolute differences. Because of this, the rate of change scales as $\frac{1}{x}$. Meaning, the change is slower for larger $x$ whereas it is faster for smaller $x$.


### Derivative of Natural Log

Recall the limit definition of derivative :
$$
f'(x) = \lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}
$$

For derivative of $\ln x$, we define it this way :
$$
\frac{d}{dx} \ln x = \lim_{ h \to 0 } \frac{\ln(x+h)-\ln x}{h}
$$

By the quotient rule of logs :
$$
\ln (x+h)-\ln x = \ln\left( \frac{x+h}{x} \right)
$$

We simplify :
$$
\ln \left( \frac{x+h}{x} \right) = \ln \left( 1+\frac{h}{x} \right)
$$

The derivative then becomes :
$$
\lim_{ h \to 0 } \frac{\ln\left( 1 + \frac{h}{x} \right)}{h}
$$

We let :
$$
u = \frac{h}{x}
$$

Substitute $u$ in :
$$
\lim_{ u \to 0 } \frac{\ln (1+u)}{xu}
$$

> [!important] Note that limit as $xu \to 0$ is the same thing as limit as $u \to 0$.
> $x$ in this case is treated as a constant, and it is inconsequential to how $u$ approaches $0$.

Factor out the constant and then use the constant multiple rule :
$$
\lim_{ u \to 0 } \frac{1}{x} \cdot \frac{\ln(1+u)}{u} = \frac{1}{x} \lim_{ u \to 0 } \frac{\ln(1+u)}{u}
$$

Recall the fundamental property of natural log :
$$
\lim_{ h \to 0 } \frac{\ln(1+h)}{h} = 1
$$

It follows that :
$$
\frac{1}{x} \lim_{ u \to 0 } \frac{\ln(1+u)}{u} = \frac{1}{x} (1) = \frac{1}{x}
$$

Therefore :
$$
\boxed{\frac{d}{dx} \ln x = \frac{1}{x}}
$$


#### The Inverse Function Approach

Let :
$$
y = \ln x \iff e^y = x
$$

Take the derivative on both sides of $e^y=x$ :
$$
e^y \cdot y' = 1
$$

Isolate $y'$ to one side :
$$
y' = \frac{1}{e^y}
$$

Finally, use substitution :
$$
\boxed{y' = \frac{1}{x}}
$$


#### Derivative of Natural Log of any function of $x$

Let $g(x)$ be any differentiable function of $x$.

In order to get derivative of natural log of $g(x)$, we use the chain rule.

The outside function is $\ln u$, and the inside function is $u = g(x)$. Thus :
$$
\begin{align}
  \frac{d}{dx} \ln(g(x)) &= \frac{d}{dx} \ln u \cdot u' \\
  &= \frac{1}{u} \cdot u' \\
  &= \frac{1}{g(x)} \cdot g'(x)
\end{align}
$$

Simplify and we get :
$$
\boxed{\frac{d}{dx} \ln(g(x)) = \frac{g'(x)}{g(x)}}
$$


### Derivative of Log

Consider logarithm with base $a$ :
$$
\log_{a} x
$$

By the change-of-base rule of logs :
$$
\log_{a} x = \frac{\ln x}{\ln a}
$$

This means that :
$$
\frac{d}{dx} \log_{a} x = \frac{d}{dx} \frac{\ln x}{\ln a}
$$

Take out the constant :
$$
\begin{align}
  \frac{d}{dx} \left( \frac{\ln x}{\ln a} \right) &= \frac{d}{dx} \left( \frac{1}{\ln a} \cdot \ln x \right) \\
  &= \frac{1}{\ln a} \cdot \frac{d}{dx} \ln x
\end{align}
$$

We know that :
$$
\frac{d}{dx} \ln x = \frac{1}{x}
$$

Substitute :
$$
= \frac{1}{\ln a}\left( \frac{1}{x} \right) = \frac{1}{x \ln a}
$$

Therefore :
$$
\boxed{\frac{d}{dx} \log_{a} x = \frac{1}{x\ln a}}
$$


#### Derivative of Log of any function of $x$

Let $g(x)$ be any function differentiable at $x$.

We can use the chain rule to find the derivative of $\log(g(x))$.

The outside function is $\log_{a} u$, inside function is $u=g(x)$ :
$$
\begin{align}
  \frac{d}{dx}(\log_{a}g(x)) &= \frac{d}{dx} \log_{a} u \cdot u' \\
  &= \frac{1}{u \ln a} \cdot u' \\
  &= \frac{u'}{u \ln a}
\end{align}
$$

Plug the original numbers back in :
$$
\frac{u'}{u \ln a} = \frac{g'(x)}{g(x) \ln a}
$$

Therefore :
$$
\frac{d}{dx}(\log_{a}g(x)) = \frac{g'(x)}{g(x) \ln a}
$$


## Derivative of Trigonometric Functions

| Name                    | Equation                              |
| ----------------------- | ------------------------------------- |
| Derivative of Sine      | $\frac{d}{dx}(\sin x)=\cos x$         |
| Derivative of Cosine    | $\frac{d}{dx}(\cos x)=-\sin x$        |
| Derivative of Tangent   | $\frac{d}{dx}(\tan x)=\sec^2 x$       |
| Derivative of Cotangent | $\frac{d}{dx}(\cot x)=-\csc^2 x$      |
| Derivative of Secant    | $\frac{d}{dx}(\sec x)=\sec x \tan x$  |
| Derivative of Cosecant  | $\frac{d}{dx}(\csc x)=-\csc x \cot x$ |


### Inverse Trig Functions

| Name                            | Equation                                                              | RDI\*                                          |
| ------------------------------- | --------------------------------------------------------------------- | ---------------------------------------------- |
| Derivative of Inverse Sine      | $\frac{d}{dx}(\sin^{-1}u)=\frac{u'}{\sqrt{ 1-u^2 }}$                  | $\frac{u'}{\cos(\sin^{-1} u)}$                 |
| Derivative of Inverse Cosine    | $\frac{d}{dx}(\cos^{-1}u)=-\frac{u'}{\sqrt{ 1-u^2 }}$                 | $-\frac{u'}{\sin(\cos^{-1}u)}$                 |
| Derivative of Inverse Tangent   | $\frac{d}{dx}(\tan^{-1}u)=\frac{u'}{1+u^2}$                           | $\frac{u'}{\sec^2(\tan^{-1}u)}$                |
| Derivative of Inverse Cotangent | $\frac{d}{dx}(\cot^{-1}u)=-\frac{u'}{1+u^2}$                          | $-\frac{u'}{\csc^2(\cot^{-1}u)}$               |
| Derivative of Inverse Secant    | $\frac{d}{dx}(\sec^{-1}u)=\frac{u'}{\lvert x \rvert \sqrt{ x^2-1 }}$  | $\frac{u'}{\sec(\sec^{-1}u) \tan(\sec^{-1}u)}$ |
| Derivative of Inverse Cosecant  | $\frac{d}{dx}(\csc^{-1}u)=-\frac{u'}{\lvert x \rvert \sqrt{ x^2-1 }}$ | $-\frac{u'}{\csc(\csc^{-1}u)\cot(\csc^{-1}u)}$ |

\*Reciprocal Derivatives of Inverses :
$$
\boxed{(f^{-1})'(u) = \frac{u'}{f'(f^{-1}(u))}}
$$

> [!important] Check out [[Essence_of_Trigonometry#Relationships between trig functions and inverses]] to get a better understanding how derivatives of inverse functions work.



$$
f'(x) = \frac{35x^4}{\sqrt{ 1-7x^5 }}
$$



### Hyperbolic Functions


### Inverse Hyperbolic Functions



## Implicit Differentiation



