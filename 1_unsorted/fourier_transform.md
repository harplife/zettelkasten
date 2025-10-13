# Fourier Transform

## Definition
- [Fourier Transform - Mathematics | wiki](https://en.wikipedia.org/wiki/Fourier_transform) : a transform that converts a function into a form that describes the frequencies present in the original function.

## Information
- The output of the transform is a complex-valued function of frequency.
- The term *Fourier transform* refers to both this complex-valued function and the mathematical operation.
	- When a distinction needs to be made, it is sometimes called the **Frequency Domain Representation** of the original function.
- The Fourier transform is analogous to decomposing the sound of a musical chord into terms of the intensity of its constituent pitches.
- Functions that are localized in the time domain have Fourier transforms that are spread out across the frequency domain and vice versa, a phenomenon known as the [[uncertainty_principle|Uncertainty Principle]].
	- Generally speaking, the more concentrated $f(x)$ is, the more spread out its Fourier Transform $\hat{f}(\xi)$ must be.
		- In particular, the scaling property of the Fourier transform may be seen as saying : if we squeeze a function in $x$, its Fourier transform stretches out in $\xi$.
		- It is not possible to arbitrarily concentrate both a function and its Fourier transform.
	- The trade-off between the compaction of a function and its Fourier transform can be formalized in the form of an [[uncertainty_principle|Uncertainty Principle]] by viewing a function and its Fourier transform as [[conjugate_variables|Conjugate Variables]] with respect to the [Symplectic Form](https://en.wikipedia.org/wiki/Symplectic_vector_space) on the [time-frequency domain](https://en.wikipedia.org/wiki/Time%E2%80%93frequency_representation).
		- From the point of view of the Linear Canonical Transformation, the Fourier transform is rotation by 90 degree in the time-frequency domain, and preserves the symplectic form.