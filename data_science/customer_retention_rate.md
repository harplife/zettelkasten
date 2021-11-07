---
aliases: [Customer Retention Rate]
tags: [data_science, statistics, e-commerce, business, example, HOW-TO, formula]
status: complete
edited: 2021-11-06
---

# Customer Retention Rate
As informed by [Zendesk Blog](https://www.zendesk.com/blog/calculate-customer-retention-rate/)

Customer Retention Rate (CRR) measures the number of customers a company retains over a given period of time. It's expressed as a percentage of a company's existing customers who remain loyal within that time frame.

For example, if a business has 10 customers at the beginning of the year and loses 2 of them, then the business has an 80% CRR.

## Data
The required information to calculate CRR:
1. Customer ID
2. Order ID (if not, Product ID)
3. Order Date (date of order, purchase, or delivery)
4. Purchase Confirmation (e.g. paid, not-canceled, delivered)

## Formula
If,
1. `S` is the number of existing customers at the start of the time period
2. `E` is the number of total customers at the end of the time period
3. `N` is the number of new customers added within the time period

Then the formula for CRR is
`CRR = ((E-N)/S) * 100`

## Example
Say a company had 100 customers at the start of the period (S), ended the period with 100 customers, and added 10 customers over the period (N). They would have a customer retention rate of 90 percent : ((100-10)/100) x 100 = 90.

## My Thoughts
I tried to implement this formula with [[python|Python]] to calculate CRR for any given year. Then I realized this formula was somewhat misleading.

1. How do you define _Existing_ customers?
2. How do you define _Total_ customers?

Initially, I tried to define these two variables, like so:
1. _Existing_ means all customers from 1st day of business to the start of the target year.
2. _Total_ means all customers from 1st day of the business to end of the target year.

It made sense at first, but the problem with this definition is that _Existing_ customers are included in _Total_ customers, which means CRR would always return 100%. Also, it does not take into account the _Churned_ customers.

In order to fix this, I had to re-define the variables:
1. _Existing_ customers are customers from the previous year.
2. _Total_ customers are customers from the target year.

There are a few benefits with this new definition:
1. _Existing_ customers are not included in _Total_ customers (at least, not _ALL_ of them).
2. It's clear to see that customers from _Total_ customers who are not in _Existing_ customers are _New_ customers.
3. It's also clear to see that customers who are in both _Total_ and _Existing_ customers are _Loyal_ customers.
4. Naturally, if we subtract _New_ customers from _Existing_ customers, we get _Loyal_ customers. This is actually part of the CRR formula, `(E - N)`.

The only downside with this new definition is that the customers from earlier than previous year are _forgotten_, and so even if they come back to make a purchase, they are considered a _New_ customer instead of a _Loyal_ customer.

A solution to this would be to "look ahead" and check if _Existing_ customers have made any purchases for the _n_ years afterwards.

For example, in order to calculate CRR for 2017, we would check if customers from 2016 have made any purchases for the next 3 years (2017~2019). If so, they are _Loyal_.

One might consider, what if instead of _n_ years, we use _rest_ of the years? In other words, if a customer makes a purchase at all later down the line, why not count them as _Loyal_?

A problem with that is the fact that the _rest_ of the years are limited. As the target year progresses towards the latest, the _rest_ of the years decrease - which means, number of _Loyal_ customers would decrease, and so does CRR.

Another version of this "look ahead" solution, is to consider _Existing_ customers as _ALL_ customers from prior to the target year. For example, if we are calculating CRR for 2016, then we would consider all customers from before 2016 to be _Existing_ customers.

This way, no customers are _forgotten_. However, because no customers are _forgotten_, the _churn rate_ is carried over (accumulates). Because _churn rate_ is basically the opposite of _retention rate_, if the _churn rate_ gets higher, then the _retention rate_ gets lower.

I think the customers from last year are worth more than the customers from more than a year ago. It seems hardly fair, or efficient to look at CRR from literally _ALL_ customers. If the point of looking at CRR is to make a business decision to help increase CRR, then the business decision would have to take into account the cost of operation in proportion to the number of customers, and therefore, the target range of customers - _New_, _Loyal_, or _Forgotten_.

Theory : the most elegant solution to this _"Forgotten Customers"_ problem, is to get an average of the time between purchases (excluding outliers). Depending on type of business, it may be _normal_ to have made another purchase within a year's time. If it's groceries, then maybe a month. I have yet to test this theory. #todo

For my script, I've made 2 versions of the CRR calculator.
- Version 1 : _Existing_ customers are from _a year_ before the target year
- Version 2 : _Existing_ customers are from _all years_ before the target year

The script : [[CRR_EXAMPLE.html]]