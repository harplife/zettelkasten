---
aliases:
  - photo-realistic rendering
  - Photo-Realistic Rendering
  - unbiased rendering
  - Unbiased Rendering
---

# Photo-Realistic Rendering

- <mark class="hltr-trippy">Photo-Realistic Rendering</mark> or <mark class="hltr-cyan">Unbiased Rendering</mark> is a rendering technique that avoid systematic errors (or statistical biased) in computing an image's radiance.
- "Bias" in this context means inaccuracies like dimmer light or missing effects such as soft shadows, caused by approximations.
- Unbiased methods, such as [[path_tracing|path tracing]] and its derivatives, simulate real-world lighting and shading with full physical accuracy.
	- In contrast, biased methods, including traditional [[ray_tracing|ray tracing]], sacrifice precision for speed by using approximations that introduce errors - often seen as blur. This blur reduces variance (random noise) by averaging light samples, enabling faster computation with fewer samples needed for a clean image.


## Problems with unbiased rendering

### Selecting Ideal Paths within Infinite Paths
- It is important to note that an unbiased technique cannot consider all possible paths (because there is an infinite number of them), and may not select the ideal paths for a given render (because to select certain paths over others introduces bias).
- Path tracing, an unbiased approach at its core, cannot consistently handle caustics generated from a point light source, as it is highly unlikely to randomly generate the singular path that directly reflects into the point.


## Sources

- https://en.wikipedia.org/wiki/Unbiased_rendering