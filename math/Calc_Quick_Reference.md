# Calculus - Quick Reference

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
| Constant Rule            | $\frac{d}{dx}[c] = 0$                                                               |
| Power Rule               | $\frac{d}{dx}[x^n] = nx^{n-1}$                                                      |
| Constant Multiple Rule   | $\frac{d}{dx}[cf(x)] = cf'(x)$                                                      |
| Sum Rule                 | $\frac{d}{dx}[f(x)+g(x)] = f'(x)+g'(x)$                                             |
| Difference Rule          | $\frac{d}{dx}[f(x)-g(x)] = f'(x)-g'(x)$                                             |
| Product Rule             | $\frac{d}{dx}[f(x)g(x)] = f'(x)g(x)+f(x)g'(x)$                                      |
| Quotient Rule            | $\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x)-f(x)g'(x)}{[g(x)]^2}$ |
| Chain Rule               | $\frac{d}{dx}[f(g(x))] = f'(g(x))g'(x)$                                             |
| General Power Rule       | $\frac{d}{dx}[u(x)]^n = n[u(x)]^{n-1}u'(x)$                                         |
| Reciprocal Rule          | $\frac{d}{dx}\left[\frac{1}{f(x)}\right] = -\frac{f'(x)}{[f(x)]^2}$                 |
| Exponential Rule         | $\frac{d}{dx}[e^x] = e^x$                                                           |
| General Exponential Rule | $\frac{d}{dx}[a^x] = a^x\ln(a)$                                                     |
| Natural Log Rule         | $\frac{d}{dx}[\ln(x)] = \frac{1}{x}$                                                |
| General Log Rule         | $\frac{d}{dx}[\log_a(x)] = \frac{1}{x\ln(a)}$                                       |
| Sine Rule                | $\frac{d}{dx}[\sin(x)] = \cos(x)$                                                   |
| Cosine Rule              | $\frac{d}{dx}[\cos(x)] = -\sin(x)$                                                  |
| Tangent Rule             | $\frac{d}{dx}[\tan(x)] = \sec^2(x)$                                                 |
| Cotangent Rule           | $\frac{d}{dx}[\cot(x)] = -\csc^2(x)$                                                |
| Secant Rule              | $\frac{d}{dx}[\sec(x)] = \sec(x)\tan(x)$                                            |
| Cosecant Rule            | $\frac{d}{dx}[\csc(x)] = -\csc(x)\cot(x)$                                           |
| Inverse Sine Rule        | $\frac{d}{dx}[\arcsin(x)] = \frac{1}{\sqrt{1-x^2}}$                                 |
| Inverse Cosine Rule      | $\frac{d}{dx}[\arccos(x)] = -\frac{1}{\sqrt{1-x^2}}$                                |
| Inverse Tangent Rule     | $\frac{d}{dx}[\arctan(x)] = \frac{1}{1+x^2}$                                        |
| Inverse Secant Rule      | $\frac{d}{dx}[\sec^{-1}(x)] = \frac{1}{\lvert x \rvert \sqrt{ x^2 -1 }}$            |

