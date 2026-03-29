# Essence of Trigonometry

A collection of visual aids and other stuffs to understand trigonometry.

---
![[Trigonometric_functions_derivation_animation.svg | center | 600]]

---
https://www.technologyuk.net/mathematics/trigonometry/trigonometric-identities.shtml

---
![[Pasted image 20260102124150.png]]
> [All 6 Trig Functions on the Unit Circle - Schattman Math - Youtube](https://www.youtube.com/watch?v=Dsf6ADwJ66E)


---
![[Pasted image 20260102124302.png]]
> [Trig Visualized: One Diagram to Rule them All - Mathematical Visual Proofs - Youtube](https://www.youtube.com/watch?v=dUkCgTOOpQ0)


![[Trig_Functions.svg]]

![[Unit-circle_sin_cos_tan_cot_exsec_excsc_versin_vercos_coversin_covercos.svg]]


Note : [Trigonometry playlist on the same channel](https://www.youtube.com/playlist?list=PLZh9gzIvXQUvc6SufrIpkVrVLdhcGthSy)


## Unit Circle

![[Unit_circle_angles_color.svg | center | 500]]



## Trigonometric Identities

### Pythagorean Identities



### Angle Sum and Diff Identities

![[angle_sum_diff_identities_fig.svg| center | 500]]

![[Pasted image 20260329083236.png]]
#todo work on transcribing this to a real table



## Inverse Trigonometric Identities



## Relationships between trig functions and inverses

| $\theta$       | $\sin(\theta)$                                             | $\cos(\theta)$                                              | $\tan(\theta)$                                    |
| -------------- | ---------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------- |
| $\sin^{-1}(x)$ | $\sin(\sin^{-1}(x))=x$                                     | $\cos(\sin^{-1}(x))=\sqrt{ 1-x^2 }$                         | $\tan(\sin^{-1}(x))=\frac{x}{\sqrt{ 1-x^2 }}$     |
| $\cos^{-1}(x)$ | $\sin(\cos^{-1}(x))=\sqrt{ 1-x^2 }$                        | $\cos(\cos^{-1}(x))=x$                                      | $\tan(\cos^{-1}(x))=\frac{\sqrt{ 1-x^2 }}{x}$     |
| $\tan^{-1}(x)$ | $\sin(\tan^{-1}(x))=\frac{x}{\sqrt{ 1+x^2 }}$              | $\cos(\tan^{-1}(x))=\frac{1}{\sqrt{ 1+x^2 }}$               | $\tan(\tan^{-1}(x))=x$                            |
| $\cot^{-1}(x)$ | $\sin(\cot^{-1}(x))=\frac{1}{\sqrt{ 1+x^2 }}$              | $\cos(\cot^{-1}(x))=\frac{x}{\sqrt{ 1+x^2 }}$               | $\tan(\cot^{-1}(x))=\frac{1}{x}$                  |
| $\sec^{-1}(x)$ | $\sin(\sec^{-1}(x)=\frac{\sqrt{ x^2-1 }}{\lvert x \rvert}$ | $\cos(\sec^{-1}(x))=\frac{1}{x}$                            | $\tan(\sec^{-1}(x))=\pm \sqrt{ x^2-1 }$           |
| $\csc^{-1}(x)$ | $\sin(\csc^{-1}(x))=\frac{1}{x}$                           | $\cos(\csc^{-1}(x))=\frac{\sqrt{ x^2-1 }}{\lvert x \rvert}$ | $\tan(\csc^{-1}(x))=\pm \frac{1}{\sqrt{ x^2-1 }}$ |

> [!important] For relationships between $\cot$, $\csc$, $\sec$ and their inverses, just find the reciprocals from the chart above.

> [!important] The inner functions (inverses) set the context for the lengths, then the outer functions (trig functions) finds the length of a side as a proportion of the other two sides.
> For example, $\sin(\tan^{-1}(x))$ describes the length of opposite side as opposite over hypotenuse, and given that the opposite side is $x$ and the hypotenuse is $\sqrt{ 1+x^2 }$, it is $\frac{x}{\sqrt{ 1+x^2 }}$ .

| Sides          | Opposite         | Adjacent         | Hypotenuse       | Diagram                              |
| -------------- | ---------------- | ---------------- | ---------------- | ------------------------------------ |
| $\sin(\theta)$ | $x$              | $\sqrt{ 1-x^2 }$ | $1$              | ![[trig_sine_lengths.svg\|150]]      |
| $\cos(\theta)$ | $\sqrt{ 1-x^2 }$ | $x$              | $1$              | ![[trig_cosine_lengths.svg\|150]]    |
| $\tan(\theta)$ | $x$              | $1$              | $\sqrt{ 1+x^2 }$ | ![[trig_tangent_lengths.svg\|150]]   |
| $\cot(\theta)$ | $1$              | $x$              | $\sqrt{ 1+x^2 }$ | ![[trig_cotangent_lengths.svg\|150]] |
| $\sec(\theta)$ | $\sqrt{ x^2-1 }$ | $1$              | $x$              | ![[trig_secant_lengths.svg\|150]]    |
| $\csc(\theta)$ | $1$              | $\sqrt{ x^2-1 }$ | $x$              | ![[trig_cosecant_lengths.svg\|150]]  |


