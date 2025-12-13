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

---
<mark class="hltr-green">Example</mark> : Expressing a Model in Terms of $e$

A population of a certain species of fish starts with 3000 fish and the number doubles every 3.75 years. This gives us the model :

$$
n(t) = 3000 \cdot 2^{t/3.75}
$$

We can convert this model to fit the form $n(t) = n_{0}e^{rt}$, by equating the two models and solving for $r$ :

$$
\begin{align}
  3000e^{rt} &= 3000 \cdot 2^{t/3.75} \\
  e^{rt} &= 2^{t/3.75} \\
  rt &= \ln(2^{t/3.75}) \\
  rt &= \frac{t\ln(2)}{3.75} \\
  r &= \frac{\ln(2)}{3.75} \\
  r &\approx 0.1848
\end{align}
$$

Then we plug $r$ in to get the converted model :

$$
n(t) = 3000 \cdot e^{0.1848t}
$$

> [!important] The graphs of these two models are the same because the two functions are just two different ways of expressing the same model.
> If anything, the conversion process just shows how to find the rate when we model the population growth using the natural growth $e$.


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

---
The graph of a logistic growth is **S-shaped**. It can be described with three levels of population :
- Small population, where growth is fast
- Medium population, where growth is fastest
- Large population, where growth is slow

![[Pasted image 20251211124120.png]]

The **Inflection Point** is where the growth is fastest, but at the same time, where the growth starts slowing down.

---
<mark class="hltr-green">Example</mark>

A population of a certain species of fish starts with 3000 fish and the number doubles every 3.75 years. Let's say this fish population is introduced into a small lake that can support a maximum of 30000 fish.

We first model the double growth :

$$
n(t) = 3000 \cdot 2^{t/3.75}
$$

Which we use to find $r$ and convert to the relative growth model :

$$
n(t) = 3000 \cdot e^{0.1848t}
$$

We calculate $A$ :

$$
A = \frac{30000-3000}{3000} = 9
$$

Then we plug $A$ and $r$ into the logistic growth formula :

$$
n(t) = \frac{30000}{1+9e^{-0.1848t}}
$$

After the first 3.75 years, the population grows to 5353 fish instead of doubling to 6000 fish.

---
When the focus of the logistic function is on more so the *shape of the curve* rather than the growth it self, the formula is written differently :

$$
f(x) = \frac{L}{1+e^{-k(x-x_{0})}}
$$

Where :
- $L$ : maximum value the function approaches (analogous to $M$)
- $k$ : steepness (analogous to growth rate $r$)
- $x_{0}$ : midpoint where $f(x)=\frac{L}{2}$
- $x$ : input (analogous to $t$)

This version emphasizes *shape*, *steepness*, and *midpoint*.

> [!important] The major difference is at the horizontal shift.
> In the other version, $A$ is determined by the initial population. In this version, horizontal shift is controlled by $x_{0}$. The value of $x_{0}$ can be known depending on the process, but generally it is an unknown parameter. In such case, Statistics and Machine Learning is used to solve it from data (so called "Fitting").

Both models are equivalent with substitutions :
- $L=M$
- $x_{0}=-\frac{\ln(A)}{r}$
- $k=r$
- $x=t$

$$
\begin{align}
  \frac{L}{1+e^{-k(x-x_{0})}} &= \frac{M}{1+e^{-r(t+\ln(A)/r)}} \\
  &= \frac{M}{1+e^{-rt+\ln(A)}} \\
  &= \frac{M}{1+Ae^{-rt}}
\end{align}
$$


## Radioactive Decay

Radioactive substances decay by spontaneously emitting radiation. The rate of decay is proportional to the mass of the substance. This is analogous to population growth except that the mass decreases.

### (Continuous) Exponential Decay

<mark class="hltr-trippy">Exponential Decay</mark> is when a quantity decreases at a rate proportional to its current value, represented by the formula :

$$
N(t) = N_{0}e^{-\lambda t}
$$

Where :
- $N(t)$ = amount remaining after time $t$
- $N_{0}$ = initial amount at time $t=0$
- $e^{-\lambda t}$ = decay factor (the fraction left after time $t$)
- $\lambda$ = decay constant (larger means faster decay)

Exponential decay is often used to model radioactive decay.

---
Note that we learned about exponential function back in chapter [[1_Exponential_Functions|4.1 Exponential Functions]]. The simplest form of exponential decay is :

$$
y = a \cdot b^x \quad (0<b<1)
$$

In that form, if $b=0.8$, it meant that the value would be 80% of its value in 1 year ($x=1$).

This formula can be expressed in a different form :

$$
y = a \cdot (1-r)^x \quad (0<r<1)
$$

In that form, if $r=0.2$, it meant that the value would lose 20% of its value in 1 year $(x=1)$.

This formula (and the other one) describes decay in **discrete** context, where the change occurs at each "step" - such as 1 day, 1 month, or 1 year. While this change occurs once per step, we can change the formula so that the change occur $n$ times per step :

$$
A(t) = P\left( 1+\frac{r}{n} \right)^{nt}
$$

> [!note] $-r$ for decay

This is the formula we covered in Chapter 4.1 [[1_Exponential_Functions#Compound Interest|Compound Interest]], where $n=2$ meant the interest occurred at every 6 months (twice per year). Then, we covered in Chapter 4.2 [[2_The_Natural_Exponential_Function#Continuously Compounded Interest|Continuously Compounded Interest]], that we can calculate the change that occur continuously at any given time by setting $n$ to be infinitely large :

$$
A(t) = Pe^{rt}
$$

Now, in terms of radioactive decay, we get the formula :

$$
N(t) = N_{0}e^{-\lambda t}
$$

> [!important] This change from discrete function to continuous function is at the heart of Calculus.
> Calculus is all about 



### Half-Life

Physicists express the rate of decay in terms of <mark class="hltr-trippy">Half-Life</mark>, the time it takes for a sample of the substance to decay to half its original mass.

For example, the half-life of radium-226 is 1600 years, so a 100-gram sample decays to 50-gram in 1600 years, then to 25 g in 3200 years, and so on.

In general, for a radioactive substance with mass $m_{0}$ and half-life $h$, the amount remaining at time $t$ is modeled by :

$$
m(t) = m_{0}2^{-t/h}
$$

where $h$ and $t$ are measured in the same time units.

> [!important] Outside the textbook, the *standard scientific symbol* for half-life is $t_{1/2}$.
> Thus, $$m(t) = m_{0}\left( \frac{1}{2} \right)^{\frac{t}{t_{1/2}}}$$

> [!important] Outside the textbook, capital letter $N$ is used in the radioactive decay function to represent the number of radioactive nuclei (atoms) remaining in a sample at any given time, while $N_{0}$ (N-nought) signifies the initial number of nuclei at the start (time zero).
> Thus, $$N(t)=N_{0}\left( \frac{1}{2} \right)^{\frac{t}{t_{1/2}}}$$

---
An exponential decay can be described by any of the following equivalent formulas :

$$
\begin{align}
  N(t) &= N_{0}2^{-\frac{t}{t_{1/2}}}\\
  N(t) &= N_{0}\left( \frac{1}{2} \right)^{\frac{t}{t_{1/2}}} \\
  N(t) &= N_{0}e^{-\frac{t}{\tau}} \\
  N(t) &= N_{0}e^{-\lambda t}
\end{align}
$$

> [!important] $\tau$ (tau) is the **mean lifetime** of the decaying quantity.

> [!important] $\lambda$ (lambda) is the **decay constant** of the decaying quantity.

The three parameters $t_{1/2}$, $\tau$, and $\lambda$ are directly related in the following way :

$$
t_{1/2} = \frac{\ln(2)}{\lambda} = \tau \ln(2)
$$

---
