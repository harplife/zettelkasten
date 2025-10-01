# 1.7 Modeling with Equations

## Key Points

- Making and Using Models
- Problems About Interest
- Problems About Area or Length
- Problems About Mixtures
- Problems About the Time Needed to Do a Job
- Problems About Distance, Rate, and Time


## Making and Using Models

A <mark class="hltr-trippy">Mathematical Model</mark> is an equation that describes a real-world object or process.

A simple guideline for modeling with equations :
1. Identify the Variable
2. Translate from Words to Algebra
3. Set Up the Model
4. Solve the Equation (and Check your Answer)


## Problems About Interest

When you borrow money from a bank or when a bank “borrows” your money by keeping it for you in a savings account, the borrower in each case must pay for the privilege of using the money. The fee that is paid is called **interest**.

The most basic type of interest is **simple interest**, which is just an annual percentage of the total amount borrowed or deposited.

The amount of a loan or deposit is called the **principal** $P$.

The annual percentage paid for the use of this money is the **interest rate** $r$.

We will use the variable $t$ to stand for the number of years that the money is deposited (or borrowed) and the variable $I$ to stand for the total interest earned (or paid).

The following simple interest formula gives the amount of interest $I$ when a principal $P$ is deposited (or borrowed) for $t$ years at an interest rate $r$ :

$$
I = Prt
$$

> [!warning] Remember to convert $r$ from a percentage to a decimal.


### Example : Interest on an Investment

An amount of \$100,000 is invested in two certificates of deposit. One certificate pays 6% and the other pays 4.5% simple interest annually. If the total interest is \$5,025 per year, how much money is invested at each rate?

---

1. Identify the variable

Let $x$ be the amount invested at 6%.

---

2. Translate from words to algebra

| In Words                | In Algebra        |
| ----------------------- | ----------------- |
| Amount invested at 6%   | $x$               |
| Amount invested at 4.5% | $100000-x$        |
| Interest earned at 6%   | $0.06x$           |
| Interest earned at 4.5% | $0.045(100000-x)$ |

---

3. Set up the model

$$
0.06x + 0.045(100000-x) = 5025
$$

---

4. Solve for $x$

$$
\begin{align}
  0.06x + 4500 - 0.045x &= 5025 \\
  0.015x + 4500 &= 5025 \\
  0.015x &= 525 \\
  x &= \frac{525}{0.015} \\
  x &= 35000
\end{align}
$$

So $35,000 is invested at 6% and the remaining $65,000 at 4.5%.


## Problems About Area or Length

Basic formulas from geometry comes handy when it comes to dealing with problems such solving for an area, a perimeter, or length of a side.

### Example : Dimensions of a Garden

A square garden has a walkaway 3 ft wide around its outer edge. If the area of the entire garden, including the walkway, is 18,000 ft², what are the dimensions of the planted area?

![[Pasted image 20250929155112.png| center | 400]]


---

1. Identify the variable

Let $x$ be the length of the planted area.

---

2. Translate from words to algebra


| In Words                | In Algebra |
| ----------------------- | ---------- |
| Length of planted area  | $x$        |
| Length of entire garden | $x+6$      |
| Area of entire garden   | $(x+6)^2$  |

---

3. Set up the model

$$
(x+6)^2 = 18000
$$

---

4. Solve for $x$

$$
\begin{align}
  x + 6 &= \sqrt{ 18000 } \\
  x &= \sqrt{ 18000 } - 6 \\
  x &\approx 128
\end{align}
$$

The planted area of the garden is about $128$ ft by $128$ ft.


### Example : Dimensions of a Building Lot

A rectangular building lot is 8 ft longer than it is wide and has an area of 29000 ft². Find the dimensions of the lot.

---

1. Identify the variable

Let $w$ be the width of lot

---

2. Translate from words to algebra

| In Words      | In Algebra |
| ------------- | ---------- |
| Width of lot  | $w$        |
| Length of lot | $w+8$      |

---

3. Set up the model

$$
w(w+8) = 2900
$$

---

4. Solve for $w$

$$
\begin{align}
  w^2 + 8w &= 2900 \\
  w^2 + 8w - 2900 &= 0 \\
  (w-50)(w+58) &= 0 \\
  w &= 50, -58
\end{align}
$$

Since the width of the lot must be a positive number, $w = 50$. The length of the lot is $w+8=58$.


### Example : Dimensions of a Building

A person needs to find the height of a certain four-story building and observes that the shadow of the building is 28 ft long. The person is 6 ft tall and has a shadow 3.5 ft long when standing next to the building. How tall is the building?

![[Pasted image 20250929161113.png| center | 500]]

---

1. Identify the variable

Let $h$ be the height of the building.

---

2. Translate from words to algebra

| In Words                                  | In Algebra      |
| ----------------------------------------- | --------------- |
| Height of building                        | $h$             |
| Ratio of height to shadow of the building | $\frac{h}{28}$  |
| Ratio of height to shadow of the person   | $\frac{6}{3.5}$ |

---

3. Set up the model

$$
\frac{h}{28} = \frac{6}{3.5}
$$

---

4. Solve for $h$

$$
h = \frac{6 \cdot 28}{3.5} = 48
$$

The building is 48 ft tall.


## Problems About Mixtures

Problems involving mixtures and concentrations make use of the fact that if an amount $x$ of a substance is dissolved in a solution with volume $V$, then the concentration $C$ of the substance is given by :

$$
C = \frac{x}{V}
$$

Note that in many mixture problems the concentration $C$ is expressed as a percentage. It is important to convert it to decimal form in order to make calculations.


### Mixtures and Concentration

A manufacturer of soft drinks advertises their orange soda as "naturally flavored", although it contains only 5% orange juice. A new federal regulation stipulates that to be called "natural", a drink must contain at least 10% fruit juice. How much pure orange juice must this manufacturer add to 900 gal of orange soda to conform to the new regulation?

---

1. Identify the variable

Let $x$ be the amount (in gallons) of pure orange juice to be added.

---

2. Translate from words to algebra

| In Words                                    | In Algebra     |
| ------------------------------------------- | -------------- |
| Amount of orange juice to be added          | $x$            |
| Amount of orange juice in the original soda | $0.05(900)=45$ |
| Amount of the new mixture                   | $900 + x$      |
| Amount of orange juice in the new mixture   | $0.1(900+x)$   |

---

3. Set up the model

$$
45 + x = 0.1(900+x)
$$

---

4. Solve for $x$

$$
\begin{align}
  45 + x &= 90 + 0.1x \\
  0.9x &= 45 \\
  x &= \frac{45}{0.9} = 50
\end{align}
$$

The manufacturer should add 50 gallons of pure orange juice to the soda.


## Problems About the Time Needed to Do a Job

When solving a problem that involves determining how long it takes several workers to complete a job, we use the fact that if a person or machine takes $H$ time units to complete the task, then in one time unit the fraction of the task that has been completed is $\frac{1}{H}$.


### Time Needed to Do a Job

Because of an anticipated heavy rainstorm, the water level in a reservoir must be lowered by 1 ft. Opening spillway A lowers the level by this amount in 4 hours, whereas opening the smaller spillway B does the job in 6 hours. How long will it take to lower the water level by 1 ft if both spillways are opened?

---

1. Identify the variable

Let $x$ be the time (in hours) it takes to lower the water level by 1 ft if both spillways are opened.

---

2. Translate from words to algebra

| In Words                                                      | In Algebra    |
| ------------------------------------------------------------- | ------------- |
| Time it takes to lower level $1$ ft with $A$ and $B$ together | $x$           |
| Distance $A$ lowers level in $1$ hour                         | $\frac{1}{4}$ |
| Distance $B$ lowers level in $1$ hour                         | $\frac{1}{6}$ |
| Distance $A$ and $B$ together lower levels in $1$ hour        | $\frac{1}{x}$ |

---

3. Set up the model

$$
\frac{1}{4} + \frac{1}{6} = \frac{1}{x}
$$

---

4. Solve for $x$

$$
\begin{align}
  \frac{1}{4} + \frac{1}{6} &= \frac{1}{x} \\
  3x + 2x &= 12 \\
  5x &= 12 \\
  x &= \frac{12}{5}
\end{align}
$$

It will take $2 \frac{2}{5}$ hours (2 hours 24 minutes) to lower the water level by 1 ft if both spillways are opened.


## Problems About Distance, Rate, and Time

When dealing with distance, rate, and time, the following formula is often used :

$$
\text{Distance} = \text{rate} \times \text{time}
$$

The rate is either the constant speed or average speed of a moving object.


### A Distance-Speed-Time Problem

A jet flew from New York to Los Angeles, a distance of 4200 km. The speed for the return trip was 100 km/h faster than the outbound speed. If the total trip took 13 hours of flying time, what was the jet's speed from New York to Los Angeles?

---

1. Identify the variable

Let $s$ be the speed from New York to Los Angeles

---

2. Translate from words to algebra

| In Words                     | In Algebra           |
| ---------------------------- | -------------------- |
| Distance between NY and LA   | $4200$               |
| Speed from NY to LA          | $s$                  |
| Speed from LA to NY          | $s+100$              |
| Time from NY to LA           | $\frac{4200}{s}$     |
| Time from LA to NY           | $\frac{4200}{s+100}$ |
| Total time of the round trip | $13$                 |

---

3. Set up the model

$$
\frac{4200}{s} + \frac{4200}{s+100} = 13
$$

---

4. Solve for $s$

$$
\begin{align}
  \frac{4200}{s} + \frac{4200}{s+100} &= 13 \\
  4200(s+100) + 4200s &= 13s(s+100) \\
  8400s + 420000 &= 13s^2 + 1300s \\
  0 &= 13s^2 - 7100s - 420000 \\
  s & = \frac{7100 \pm \sqrt{ (-7100)^2 -4(13)(-420000) }}{2(13)} \\
  s &= \frac{7100 \pm 8500}{26} \\
  s &= 600, -53.8
\end{align}
$$

Since $s$ represents speed, we reject the negative answer and conclude that the jet's speed from NY to LA was $600$ km/h.


### Energy Expended in Bird Flight

Ornithologists have determined that some species of birds tend to avoid flights over large bodies of water during daylight hours, because air generally rises over land and falls over water in the daytime, so flying over water requires more energy.

A bird is released from point A on an island, 5 mi from B, the nearest point on a straight shoreline. The bird flies to a point C on the shoreline and then flies along the shoreline to its nesting area D.

![[Pasted image 20250929170218.png| center | 300]]

Suppose the bird has 170 kcal of energy in reserve. It uses 10 kcal/mi flying over land and 14 kcal/mi flying over water.

---

(a) Where should the point C be located so that the bird uses exactly 170 kcal of energy during its flight?

1. Identify the variable

Let $x$ be the distance from $B$ to $C$.

2. Translate from words to algebra

| In Words                                    | In Algebra                              |
| ------------------------------------------- | --------------------------------------- |
| Distance from $B$ to $C$                    | $x$                                     |
| Distance flown over water (from $A$ to $C$) | $\sqrt{ x^2+25 }$ (Pythagorean Theorem) |
| Distance flown over land (from $C$ to $D$)  | $12-x$                                  |
| Energy used over water                      | $14\sqrt{ x^2+25 }$                     |
| Energy used over land                       | $10(12-x)$                              |

3. Set up the model

$$
170 = 14\sqrt{ x^2+25 } + 10(12-x)
$$

4. Solve for $x$

$$
\begin{align}
  170 &= 14\sqrt{ x^2+25 } + 10(12-x) \\
  170 - 10(12-x) &= 14\sqrt{ x^2+25 } \\
  50 + 10x &= 14\sqrt{ x^2+25 } \\
  (50+10x)^2 &= (14)^2(x^2+25) \\
  2500 + 1000x + 100x^2 &= 196x^2 + 4900 \\
  0 &= 96x^2 - 1000x + 2400 \\
  x &= \frac{1000 \pm \sqrt{ (-1000)^2 -4(96)(2400) }}{2(96)} \\
  x &= \frac{1000 \pm 280}{192} = 6 \frac{2}{3} \quad \text{ or } \quad 3 \frac{3}{4}
\end{align}
$$

Point C should be either $6 \frac{2}{3}$ or $3 \frac{3}{4}$ miles from B so that the bird uses exactly 170 kcal of energy during its flight.


---


(b) Does the bird have enough energy in reserve to fly directly from A to D?

