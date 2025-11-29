# Convolution (Image Processing)

## Definition

In mathematics, <mark class="hltr-trippy">Convolution</mark> is an operation on two functions $f$ and $g$ that produces a third function $f * g$, as the integral of the product of the two functions after one is reflected about the y-axis and shifted.
- The integral is evaluated for all values of shift, producing the convolution function.
- The term convolution refers to both the resulting function and to the process of computing it.

Intuitively, convolution is a mathematical operation where a small matrix called a kernel (or filter) slides over an image and compute a weighted sum of the pixels underneath it.

![[2D_Convolution_Animation.gif]]

The formal definition is as follows.

Given :
- An image $I(x,y)$
- A kernel $K(u,v)$

The 2D convolution is :

$$
(I * K)(x,y) = \sum_{u}\sum_{v}I(x-u,y-v)K(u,v)
$$

Convolution is basically a weighted local average, but the kernel decides what *effect* is produced.


## History

Early concept of convolution came from integral transforms in the 1700s~1800s. It was then applied in signal processing. It was then formalized by Joseph Fourier, Oliver Heaviside, and Norbert Wiener.

In 1960s, convolution entered the digital processing field. Key contributions were :
- Lawrence Roberts - first digital edge detector (predecessor to Sobel)
- Russel Kirsch - early digital filters at NIST

In 1970s, convolution became foundational. Major progress were made :
- Sobel Operator - first widely used convolutional edge detector
- Gaussian blurring became standard for noise removal
- Laplacian, Prewitt filters were developed

In 1980s, fast convolution came into the scene.
- Separable filters (e.g. Gaussian split into 1D filters)
- Fast Fourier Transform for large-kernel convolution
- Hardware acceleration using SIMD instructions

In 2000s, convolution became faster with GPUs.
- CUDA and OpenCL enabled massively parallel 2D convolutions.
- Real-time image processing became routine.

In 2012+, convolution becomes part of machine learning.
- Convolutional Neural Networks (CNNs) was made, which apply learnable convolution kernels (as opposed to hand-designed kernels). They revolutionized object recognition, segmentation, denoising, and super-resolution.

Today, convolution is the foundation of modern computer vision.