# Renderer Comparison
- V-Ray는 전체적으로 차가운 느낌이 듬
- Redshift는 전체적으로 어두운 느낌이 남
- Octane은 대충 해도 잘나오는 편
	- 따뜻하고 부드러운 품질이 잘 나옴
	- 극실사 같은 느낌은 아님


## Corona vs. Cycles
![[max_corona_vs_blender_cycles.jpg]]
- Corona 는 빛과 그림자가 좀 더 부각되고 디테일이 높은것 같음
	- 라이트 소스에서 오는 빛과, HDRI, 캐릭터 자체에서 나오는 반사의 영향이 좀 더 잘 보임
	- 바닥에 HDRI 반사되는 부분들 보임
	- Spectral Refleciton이 좀 더 부각된 듯?
	- 빛이 너무 강해서 약간 뿌여서 보이는 부분이 있어서, 이게 좋은건지 모르겠음?
	- 검은색 부위 부분들이 좀 더 반사가 높은 플라스틱으로 보임
		- 손 부분에 특히 빛 관련 디테일이 많이 보임
		- 어깨 부분의 블랙 조인트 파트 디테일이 확실히 더 잘 보임
	- 빛/그림자가 부각되기 때문에, 모서리가 좀 더 부각되어 보임
		- 대신에, 대비 효과로 인해 배 부분에 튀어나온 부분이 좀 더 튀어나온 것처럼 보임
	- 후광이 좀 퍼져서 보임
		- 캐릭터 머리 뒤에 특히
- Cycles는 뒤에 후광이 좀 더 부각되는 듯?
	- 바닥에 반영되는 그림자가 좀 더 흐려보이는데, 이게 좀 더 심도가 있어보여서 좋은듯?
	- 눈 부분의 초록색 빛이 좀 더 진해보임
	- 후광으로 인해, 갑옷 안에 비쳐보이는 부분이 좀 더 부각됨
- 전체적으로 Corona가 좀 더 현실감을 구현하는 듯함
	- 스타워즈 스톰트루퍼 느낌하고 유사한듯
		- [Star Wars UE4 Real-Time RT Cinematic Demo | Epic | ILMxLAB | NVIDIA | Youtube](https://youtu.be/lMSuGoYcT3s)
			- ![[Pasted image 20230405182938.png]]

## 문의 사항
- 3D 모델링 소프트웨어에 따라 렌더링이 다를 수 있을까?


## Resources & Related



https://renderman.pixar.com/resources/RenderMan_20/attributes.html

https://renderman.pixar.com/resources/RenderMan_20/rfhGettingStarted.html

https://openmoonray.org/index

https://github.com/dreamworksanimation/openmoonray/discussions/27

https://github.com/dreamworksanimation/moonray_dcc_plugins

https://www.sidefx.com/forum/topic/85831/?page=1#post-371285

https://www.youtube.com/watch?v=RgVbXwfCy3w&ab_channel=DreamWorks

https://www.redsharknews.com/siggraph-2022-a-tale-of-usd-hydra-and-the-sheer-power-of-dreamworks-moonray

