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

A population that experiences exponential growth increases according to the model

$$
n(t)=n_{0}e^{rt}
$$

where :
- $n(t)$ = population at time $t$
- $n_{0}$ = initial size of the population
- $r$ = relative rate of growth (expressed as a proportion of the population)

> [!important] The formula for population growth is the same as that for continuously compounded interest.

---
<mark class="hltr-green">Example</mark> : Predicting the Size of a Population

The initial bacterium count in a culture is 500. A biologist later makes a sample count of bacteria in the culture and finds that the relative rate of growth is 40% per hour.

The population at time $t$ is modeled by :

$$
n(t) = 500e^{0.4t}
$$

where $t$ is measured in hours.

Using the model, we find that the bacterium count after 10 hours is :

$$
n(10) 500e^{4} \approx 27300
$$

Using the model, we can find the time it takes for the population to reach 80000 :

$$
\begin{align}
  500e^{0.4t} &= 80000 \\
  e^{0.4t} &= 160 \\
  0.4t &= \ln(160) \\
  t &= \frac{\ln(160)}{0.4} \approx 12.68
\end{align}
$$


## Logistic Growth

In the real world, a given environment has limited resources (food, water, living space, and so on) and can support a maximum population $M$ (**carrying capacity**). Populations tend to first increase exponentially and then level off as they approach $M$. Under such conditions, the rate of growth of the population $P(t)$ at any time $t$ is jointly proportional to $P(t)$ and to $M-P(t)$. Under such conditions, the population is modeled by a *logistic function*, as follows.

<mark class="hltr-trippy">Logistic Growth</mark> is a model of population (or resource) growth that starts exponentially, but then slows down and eventually levels off as the population approaches a maximum limit.

> [!important] Exponential growths are appropriate only under ideal conditions that allow for unlimited growth.
> Logistic growth is a realistic growth model used in biology, ecology, epidemiology, chemistry, and social sciences.

The formula for logistic growth (growth with limits) :

$$
n(t) = \frac{M}{1+Ae^{-rt}}
$$

Where :
- $M$ = carrying capacity (maximum sustainable population)
- $A$ = $\frac{M-n_{0}}{n_{0}}$, where $n_{0}$ is the initial population
- $r$ = growth rate

