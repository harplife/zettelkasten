# Canny Edge Detection

<mark class="hltr-trippy">Canny Edge Detection</mark> is a multi-stage algorithm that identifies edges in images by first reducing noise with a Gaussian filter, then finding the intensity gradients and suppressing non-maximum pixels to thin edges, and finally using hysteresis thresholding to link strong edges and discard weak ones.

## Stage 1 : Noise Reduction

- A Gaussian filter is applied to the image to smooth out noise, as edge detection is sensitive to it.
- The extent of smoothing is adjustable; a larger Gaussian kernel is used for noisier images.


## Stage 2 : Finding Intensity Gradients

- A Sobel Filter is applied to the smoothed image to find the first derivatives in both the horizontal $G_{x}$ and vertical $G_{y}$ directions.
- The gradient magnitude $G$ and direction $\theta$ are calculated for each pixel using the following formulas :
	- $G=\sqrt{ G_{x}^2+G_{y}^2 }$
	- $\theta = \tan^{-1}\left( \frac{G_{y}}{G_{x}} \right)$


## Stage 3 : Non-maximum Suppression

- The algorithm thins the edges by removing any pixel that is not a local maximum in its neighborhood along the gradient direction.
- This process results in a set of "ridges" or potential edges that are typically only one pixel wide.


## Stage 4 : Hysteresis Thresholding

- Two thresholds, a high and a low, are used to determine the final edges.
- Strong edges : Pixels with a gradient magnitude greater than the high threshold are always considered edges.
- Weak edges : Pixels with a gradient magnitude between the high and low thresholds are only considered edges if they are connected to a strong edge.
- Discarded edges : Pixels with a gradient magnitude below the low threshold are discarded.