# 4.6 Modeling with Exponential Functions

## Key Concepts

- Exponential Growth (Doubling Time)
- Exponential Growth (Relative Growth Rate)
- Logistic Growth
- Radioactive Decay
- Newton's Law of Cooling


## Exponential Growth (Doubling Time)

If the initial size of a population is $n_{0}$ and the doubling time is $a$, then the size of the population at time $t$ is

$$
n(t) = n_{0}2^{t/a}
$$

where $a$ and $t$ are measured in the same time units (minutes, hours, days, years, and so on).

---
<mark class="hltr-green">Example</mark> : Bacteria Population

Let's say a certain bacteria population doubles every four hours, and there are 1000 bacteria in a colony at the moment.

The population at time $t$ is modeled by :

$$
n(t) = 1000 \cdot 2^{0.25t}
$$

where $t$ is measured in hours.

After 24 hours, the number of bacteria is :

$$
n(24) = 1000 \cdot 2^{0.25(24)}=64000
$$

We can calculate how long it takes for the bacteria count to reach one million :

$$
\begin{align}
  1000 \cdot 2^{0.25t} &= 1000000 \\
  2^{0.25t} &= 1000 \\
  \log(2^{0.25t}) &= \log(1000) \\
  (0.25t)\log(2) &= 3 \\
  t &= \frac{3}{0.25\log(2)} \approx 39.86
\end{align}
$$

The bacteria level reaches one million in about 40 hours.


## Exponential Growth (Relative Growth Rate)

