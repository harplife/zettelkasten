# Octane 설정 노트

## Kernels
### Direct Lighting
- Direct Lighting은 직접광을 뜻하며, 광선이 있는 영역만 보여주는 성질이 있음
	- DL은 일반적으로 GI (Global Illumination) / Indirect Illumination 사용하지 않는 설정이라고 이해하면 됨
	- `GI mode > GI_NONE` : 박스 안에서 구멍을 통해 광원을 볼 수 있되, 박스 안에 실제로 빛이 들어오지 않음
		- ![[Pasted image 20230412162151.png]]
	- `GI mode > GI_AMBIENT_OCCLUSION` : 박스 안에서 광원을 볼 수 있고, 박스 안에 빛이 들어오는 것처럼 보임
		- [[ambient_occlusion|Ambient Occlusion]] 은 GI 와 "근접"한 설정이라 볼 수 있지만, GI는 아님
		- 실내 환경인 경우, "벽"이 광원처럼 작용해서 실내에 빛이 비추어짐
		- 일반적으로 AO는 그림자가 흐리게 보이는 속성이 있음; 흐린 날씨 톤이라 볼 수 있음
		- ![[Pasted image 20230412164304.png]]
	- GI mode > GI Diffuse : 
		- ![[Pasted image 20230412164844.png]]
- 