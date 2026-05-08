# Calculus - Quick Reference

## Pre-Calc

Quadratic Formula
$$
-b \pm \frac{\sqrt{ b^2-4ac }}{2a}
$$


Volumes of 3D Shapes
- Cuboid : $whl$
- Cone : $\frac{1}{3} \pi r^2 h$
- Cylinder : $\pi r^2 h$
- Sphere : $\frac{4}{3} \pi r^3$


Trig Values of Special Angles

| Radians         | Sine                   | Cosine                 | Tangent                |
| --------------- | ---------------------- | ---------------------- | ---------------------- |
| $0$             | $0$                    | $1$                    | $0$                    |
| $\frac{\pi}{6}$ | $\frac{1}{2}$          | $\frac{\sqrt{ 3 }}{2}$ | $\frac{\sqrt{ 3 }}{3}$ |
| $\frac{\pi}{4}$ | $\frac{\sqrt{ 2 }}{2}$ | $\frac{\sqrt{ 2 }}{2}$ | $1$                    |
| $\frac{\pi}{3}$ | $\frac{\sqrt{ 3 }}{2}$ | $\frac{1}{2}$          | $\sqrt{ 3 }$           |
| $\frac{\pi}{2}$ | $1$                    | $0$                    | DNE                    |
| $-\pi$          | $0$                    | $-1$                   | $0$                    |


Distance Formula
$$
d = \sqrt{ (x_{2}-x_{1})^2 + (y_{2}-y_{1})^2 }
$$


## Limit Laws

| Limit Law                    | General Form                                                                                         |
| ---------------------------- | ---------------------------------------------------------------------------------------------------- |
| Constant Law                 | $\lim_{x \to a} c = c$                                                                               |
| Identity Law                 | $\lim_{x \to a} x = a$                                                                               |
| Sum Law                      | $\lim_{x \to a}[f(x)+g(x)] = \lim_{x \to a}f(x)+\lim_{x \to a}g(x)$                                  |
| Difference Law               | $\lim_{x \to a}[f(x)-g(x)] = \lim_{x \to a}f(x)-\lim_{x \to a}g(x)$                                  |
| Constant Multiple Law        | $\lim_{x \to a}[c,f(x)] = c\lim_{x \to a}f(x)$                                                       |
| Product Law                  | $\lim_{x \to a}[f(x)g(x)] = \left(\lim_{x \to a}f(x)\right)\left(\lim_{x \to a}g(x)\right)$          |
| Quotient Law                 | $\lim_{x \to a}\frac{f(x)}{g(x)} = \frac{\lim_{x \to a}f(x)}{\lim_{x \to a}g(x)}$                    |
| Power Law                    | $\lim_{x \to a}[f(x)]^n = \left(\lim_{x \to a}f(x)\right)^n$                                         |
| Root Law                     | $\lim_{x \to a}\sqrt[n]{f(x)} = \sqrt[n]{\lim_{x \to a}f(x)}$                                        |
| Composition / Continuity Law | $\lim_{x \to a}f(g(x)) = f\left(\lim_{x \to a}g(x)\right)$                                           |
| Squeeze Theorem              | If $f(x)\le g(x)\le h(x)$ and $\lim_{x \to a}f(x)=\lim_{x \to a}h(x)=L$, then $\lim_{x \to a}g(x)=L$ |
| Absolute Value Law           | $\lim_{x \to a}\lvert f(x)\rvert = \left\lvert\lim_{x \to a}f(x)\right\rvert$                        |


## Derivative Laws

| Derivative Law           | General Form                                                                        |
| ------------------------ | ----------------------------------------------------------------------------------- |
| Constant Rule            | $\frac{d}{ \,dx}[c] = 0$                                                               |
| Power Rule               | $\frac{d}{ \,dx}[x^n] = nx^{n-1}$                                                      |
| Constant Multiple Rule   | $\frac{d}{ \,dx}[cf(x)] = cf'(x)$                                                      |
| Sum Rule                 | $\frac{d}{ \,dx}[f(x)+g(x)] = f'(x)+g'(x)$                                             |
| Difference Rule          | $\frac{d}{ \,dx}[f(x)-g(x)] = f'(x)-g'(x)$                                             |
| Product Rule             | $\frac{d}{ \,dx}[f(x)g(x)] = f'(x)g(x)+f(x)g'(x)$                                      |
| Quotient Rule            | $\frac{d}{ \,dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x)-f(x)g'(x)}{[g(x)]^2}$ |
| Chain Rule               | $\frac{d}{ \,dx}[f(g(x))] = f'(g(x))g'(x)$                                             |
| General Power Rule       | $\frac{d}{ \,dx}[u(x)]^n = n[u(x)]^{n-1}u'(x)$                                         |
| Reciprocal Rule          | $\frac{d}{ \,dx}\left[\frac{1}{f(x)}\right] = -\frac{f'(x)}{[f(x)]^2}$                 |
| Exponential Rule         | $\frac{d}{ \,dx}[e^x] = e^x$                                                           |
| General Exponential Rule | $\frac{d}{ \,dx}[a^x] = a^x\ln(a)$                                                     |
| Natural Log Rule         | $\frac{d}{ \,dx}[\ln(x)] = \frac{1}{x}$                                                |
| General Log Rule         | $\frac{d}{ \,dx}[\log_a(x)] = \frac{1}{x\ln(a)}$                                       |
| Sine Rule                | $\frac{d}{ \,dx}[\sin(x)] = \cos(x)$                                                   |
| Cosine Rule              | $\frac{d}{ \,dx}[\cos(x)] = -\sin(x)$                                                  |
| Tangent Rule             | $\frac{d}{ \,dx}[\tan(x)] = \sec^2(x)$                                                 |
| Cotangent Rule           | $\frac{d}{ \,dx}[\cot(x)] = -\csc^2(x)$                                                |
| Secant Rule              | $\frac{d}{ \,dx}[\sec(x)] = \sec(x)\tan(x)$                                            |
| Cosecant Rule            | $\frac{d}{ \,dx}[\csc(x)] = -\csc(x)\cot(x)$                                           |
| Inverse Sine Rule        | $\frac{d}{ \,dx}[\arcsin(x)] = \frac{1}{\sqrt{1-x^2}}$                                 |
| Inverse Cosine Rule      | $\frac{d}{ \,dx}[\arccos(x)] = -\frac{1}{\sqrt{1-x^2}}$                                |
| Inverse Tangent Rule     | $\frac{d}{ \,dx}[\arctan(x)] = \frac{1}{1+x^2}$                                        |
| Inverse Secant Rule      | $\frac{d}{ \,dx}[\sec^{-1}(x)] = \frac{1}{\lvert x \rvert \sqrt{ x^2 -1 }}$            |


## Integral Laws

$\int_a^b f(x)  \,dx$ is read as "the integral from $a$ to $b$ of $f(x)$ with respect to $x$".

| Integral Property / Rule                 | General Form                                                                        |
| ---------------------------------------- | ----------------------------------------------------------------------------------- |
| Constant Multiple Rule                   | $\int cf(x)  \,dx = c\int f(x)  \,dx$                                               |
| Sum Rule                                 | $\int [f(x)+g(x)]  \,dx = \int f(x)  \,dx + \int g(x)  \,dx$                        |
| Difference Rule                          | $\int [f(x)-g(x)]  \,dx = \int f(x)  \,dx - \int g(x)  \,dx$                        |
| Power Rule for Integrals                 | $\int x^n  \,dx = \frac{x^{n+1}}{n+1}+C$ for $n\neq -1$                             |
| Logarithmic Integral Rule                | $\int \frac{1}{x}  \,dx = \ln\lvert x\rvert + C$                                    |
| Exponential Integral Rule                | $\int e^x  \,dx = e^x + C$                                                          |
| General Exponential Rule                 | $\int a^x  \,dx = \frac{a^x}{\ln(a)} + C$                                           |
| Sine Integral Rule                       | $\int \sin(x)  \,dx = -\cos(x)+C$                                                   |
| Cosine Integral Rule                     | $\int \cos(x)  \,dx = \sin(x)+C$                                                    |
| Secant Squared Rule                      | $\int \sec^2(x)  \,dx = \tan(x)+C$                                                  |
| Cosecant Squared Rule                    | $\int \csc^2(x)  \,dx = -\cot(x)+C$                                                 |
| Secant Tangent Rule                      | $\int \sec(x)\tan(x)  \,dx = \sec(x)+C$                                             |
| Cosecant Cotangent Rule                  | $\int \csc(x)\cot(x)  \,dx = -\csc(x)+C$                                            |
| Substitution Rule                        | $\int f(g(x))g'(x)  \,dx = \int f(u) \,du$                                          |
| Integration by Parts                     | $\int u\,dv = uv - \int v\,du$                                                      |
| Definite Integral Linearity              | $\int_a^b [cf(x)+g(x)]  \,dx = c\int_a^b f(x)  \,dx + \int_a^b g(x)  \,dx$          |
| Zero Width Property                      | $\int_a^a f(x)  \,dx = 0$                                                           |
| Reversal Property                        | $\int_a^b f(x)  \,dx = -\int_b^a f(x)  \,dx$                                        |
| Additivity Over Intervals                | $\int_a^c f(x)  \,dx + \int_c^b f(x)  \,dx = \int_a^b f(x)  \,dx$                   |
| Comparison Property                      | If $f(x)\ge g(x)$, then $\int_a^b f(x)  \,dx \ge \int_a^b g(x)  \,dx$               |
| Absolute Value Inequality                | $\left\lvert \int_a^b f(x)  \,dx \right\rvert \le \int_a^b \lvert f(x)\rvert  \,dx$ |
| Fundamental Theorem of Calculus (Part 1) | $\frac{d}{ \,dx}\int_a^x f(t) \,dt = f(x)$                                          |
| Fundamental Theorem of Calculus (Part 2) | $\int_a^b f(x)  \,dx = F(b)-F(a)$                                                   |
