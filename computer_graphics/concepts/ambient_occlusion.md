# Ambient Occlusion
## Definition
- [Ambient Occlusion | wiki](https://en.wikipedia.org/wiki/Ambient_occlusion) : [[shading]] / [[rendering]] technique used to calculate how exposed each point in a scene is to ambient lighting.

## Research
- Ambient occlusion can be seen as an accessibility value that is calculated for each surface point.
	- In scenes with **open sky**, this is done by estimating the amount of visible sky for each point.
	- In **indoor environments**, only objects within a certain radius are taken into account and *the walls are assumed to be the origin of the ambient light*.
		- The result is a diffuse, non-directional shading effect that casts no clear shadows, but that darkens enclosed and sheltered areas and can affect the rendered image's overall tone.
		- It is often used as a post-processing effect. 

## References
- [[octane_settings|C4D Octane 렌더 설정]]에서 `Kernels > Direct Lighting > GI_AMBIENT_OCCLUSION` 설정이 있음
	- ![[Pasted image 20230412164304.png|500]]
- 

## Resources