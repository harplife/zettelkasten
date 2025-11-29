# Convolution (Image Processing)

In mathematics, <mark class="hltr-trippy">Convolution</mark> is an operation on two functions $f$ and $g$ that produces a third function $f * g$, as the integral of the product of the two functions after one is reflected about the y-axis and shifted.
- The term convolution refers to both the resulting function and to the process of computing it.
- The integral is evaluated for all values of shift, producing the convolution function.

Intuitively, convolution is a mathematical operation where a small matrix called a kernel (or filter) slides over an image and compute a weighted sum of the pixels underneath it.

The formal definition is as follows.

Given :
- An image $I(x,y)$
- A kernel $K(u,v)$

The 2D convolution is :

$$
(I * K)(x,y) = \sum_{u}\sum_{v}I(x-u,y-v)K(u,v)
$$

