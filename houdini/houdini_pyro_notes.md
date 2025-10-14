# Houdini Pyro Notes
- 일반적으로 `Pyro Source` -> `Attribute Adjust Vector (Velocity)` -> `Volume Rasterize Attributes` -> `Pyro Solver` 조합으로 간단한 불을 구현함
	- `Pyro Source` 노드는 인풋 도형을 `Pyro Solver` 가 처리할 수 있는 파티클로 변환하는 동시에 연기/불과 관련된 속성 (`Density`, `Temperature`, `Burn` 외 4가지)을 부여해줌
		- ![[Pasted image 20230515104535.png|300]]
		- ![[Pasted image 20230515104601.png|300]]
	- `Attribute Adjust Vector` 노드는 객체의 속성에 애니메이션, 노이즈 등 여러 이펙트를 넣어주는 기능을 구현하며, `Pyro` 용도로서는 `Velocity` 속성을 추가해서 연기/불의 움직임을 조절하는 기능을 구현함 (밑에 이미지는 info 에서 `v` 속성 클릭해서 본 것)
		- ![[Pasted image 20230515105458.png|300]]
	- `Volume Rasterize Attributes` 노드는 파티클+속성을 볼륨(Voxel)으로 변환해줌;
- `Pyro Source` 에서 간단한 연기는 `Density` + `v` 속성만 있어도 되는 듯
- `Pyro Source` 에서 간단한 불은 `Density`+`Temperature`+`v` 에 더불어 `Burn` 속성이 있어야함
	- Pyro Source 에서 Burn 속성 추가 해줄 것
	- Volume Rasterize Attributes 에서 Burn 속성 추가 해줄 것
	- `Pyro Solver` 의 `Sourcing` 에서 `burn (flame)` 소스를 추가해줄 것 (`Quick Setups` -> `Initialize Fire`)
- `Pyro Source` 에서 `Mode` 속성이 인풋으로 들어오는 객체와 제대로 매칭되어야 함
	- 닫혀있는 도형인 경우 `Volume Scatter`; 도형 안을 포인트로 채우며, 이 포인트들이 소스가 됨
	- 납작한 면인 경우 `Surface Scatter`; 도형 겉면에 있는 포인트들이 소스가 됨
- `Volume Rasterize Attributes` 노드의 `Voxel Size` 속성은 시뮬레이션이 되기 전 처음 연기/불 사이즈에 영향을 주는 듯 함. `Pyro Solver` 노드의 `Setup :: General :: Voxel Size` 속성은 시뮬레이션이 적용되어 퍼져나가는 연기/불 사이즈에 영향을 줌 (밑에 이미지는 `voxel size`를 Rasterizer-하얀 바운딩 박스 0.075, Solver-노란 바운딩 박스 0.1 로 적용해서 본 것임)
	- ![[Pasted image 20230515111626.png|300]]
	- 계단 현상이 일어나면 `Pyro Solver` 노드의 `Voxel Size` 를 줄여보는게 좋음
- `Pyro Solver` 에서 `Voxel Size` 는 낮을수록 시뮬레이션이 되는 연기/불의 디테일을 섬세하게 해주며, 대신에 시뮬레이션 연산이 많아지며 속도가 느려짐; 연기/불에 계단 현상이 일어나는 경우 `Voxel Size` 를 낮춰보는게 좋음
- `Attribute Adjust Vector` 노드
	- `Pre-Process` 를 활성하고 `Initial Vector` 를 조정함으로서 `velocity` 의 방향을 초기화 할 수 있음 (`wind`, `gravity` 등이 계산되기 전에 우선적으로 구현되는 듯)
	- `Adjustment Value :: Amplitude` 속성으로 velocity 에 부여되는 노이즈를 조정함; 이는 `Pyro Solver` 노드의 `Shredding`/`Disturbance`/`Turbulence` 에 영향을 주는 듯 함
- #PyroLook `Pyro Solver` 노드에 `Sourcing` 에서 `density` 의 `Source Scale` 을 줄임으로서 연기 량을 조절함; 연기 량을 조절함으로서 연기 크기도 영향을 받음.
- #PyroLook Transparent & Wispy 한 Pyro 룩을 만들기 위해서는 Pyro 의 인풋 도형의 "두께"가 얇은게 좋음;
- #PyroLook `Attribute Noise` 로 `Density`, `Temperature`, `Burn` 등 속성을 조절하면 좀 더 자연스러워 보임 (밑에 상세한 설명)
	- #todo `Temperature` 와 `Burn` 은 확실히 변화가 큰데 `Density` 는 잘 모르겠음; 이론적으로는 좀 더 투명한 룩이 나와야 할 듯?
	- `Temperature` 에 노이즈가 부여되면 온도가 높은 부분(빨간 부분)은 불이 높게 오르고, 반대로 낮은 부분(파랑 부분)은 불이 낮게 오름
	- `Burn` 에 노이즈가 부여되면 Pyro 가 전체 도형이 아닌 랜덤한 부분들로서 생김; 빨간 부분은 불이 생기고 파랑 부분은 불이 안 생김
- Pyro Solver 의 Voxel Size 는 0.01 미만으로 내려가지 않도록 할 것; 밑으로 내려가 봤자 룩에 큰 차이가 없으며 연산만 느려질 뿐임
- #PyroLook Pyro Bake Volume 에서 Fire :: Source Range 를 조정하면 좀 더 투명하고 "날카로운" 불을 구현할 수 있음
	- Source Range 0.1 ~ 1 에서 0.1 ~ 0.4 차이
		- ![[20230517_bonfire_fire_source_range_before.jpg|300]]
		- ![[20230517_bonfire_fire_source_range_after.jpg|300]]
- #PyroLook Pyro Bake Volume 에서 Fire :: Masking 을 조절하면 좀 더 "Crunchy"한 룩을 만들 수 있음
	- 활성화하고 불이 갑자기 얕아진 경우 Intensity Scale 을 많이 올려야 할 수 있음
- 

## 렌더 설정
### Mantra
- Sampling :: Pixel Samples 의 크기는 너무 높게 하지 말 것? 4, 4 로 맞추고 노이즈가 너무 높으면 따로 노이즈 처리 해주면 된다고 함; <-- 이는 언제나 그런것인지? 확인 필요
- 

## 계단 현상이 생기는 경우
- Pyro Solver 의 Setup :: General :: Voxel Size 조절
	- Emitter (인풋 도형) 의 모양이 이상한 경우 Volume Rasterize Attributes 노드의 Voxel Size 를 조절
- Pyro Solver 의 Setup :: Simulation :: Global Substeps 조절

## Pyro Attributes
### Fields
#### Density :: Dissipation
흩어진 연기/불이 사라지는 속도/량을 조절하는 듯함 (burn/flame 이 있는 경우 연기만 영향을 주는 듯함)
![[Pasted image 20230515124248.png]]
![[dissipation.jpg|500]]

#### Temperature :: Diffusion
Diffusion 은 Temperature 에 블러를 넣어주는 요소로서, 전체적으로 온도가 좀 더 균일하게 퍼지도록 함; 룩 적으로는 좀 더 통통한 느낌.
![[Pasted image 20230517142637.png]]

Diffusion 0 (No Wind, No Velocity, Buoyancy 0.1)
![[Pasted image 20230517143042.png|400]]
Diffusion 5 (No Wind, No Velocity, Buoyancy 0.1)
![[Pasted image 20230517143156.png|400]]

#### Temperature :: Cooling Rate
온도가 낮아지는 속도를 조절하며, 속도가 높아질수록 흩어지는 온도의 양이 줄어들음.

#PyroLook Wind, Velocity, Buoyancy 를 모두 비활성화 하고 Bound 바닥을 닫힌 것으로 설정하면 바닥 위에 얕게 흩어지는 연기 이펙트를 만들 수 있음; 어떻게 보면 Hot Spring 또는 Witch's Brew 느낌도 가능할 듯.
![[Pasted image 20230517144434.png]]


#### Flame
흩어진 불이 사라지는 속도를 조절함; 불의 크기에 영향을 줌.


### Shape
#### Buoyancy
연기/불이 올라가는 가속(acceleration)에 영향을 주는 요소
![[Pasted image 20230515123205.png]]

> [!important]
> Buoyancy 는 Temperature 에 직접적으로 영향을 받음; Temperature 가 없으면 Buoyancy 도 마찬가지로 없음. 더불어, Buoyancy 는 Velocity 에 영향을 받지 *않기* 때문에, Velocity 가 없어도 Temperature 가 있는 이상 연기/불은 Buoyancy 에 영향을 받아 위로 올라가게도 됨;

#### Wind
연기/불 흩어지는 방향

#### Shredding
연기/불이 흩어지는 방향에 영향을 줌으로서 좀 더 흩어지게 보이는 효과를 구현함
![[Pasted image 20230515123406.png]]
![[shredding.jpg|500]]

#### Disturbance
연기/불에 노이즈를 주어 상세한 흩어짐을 부여하는 듯; 특히 불/연기 꼬리 부분에 영향을 많이 줌 (붓의 모서리가 균일함/거칠함의 정도를 조절하는 듯)
![[Pasted image 20230515123003.png]]
![[disturbance.jpg|500]]

#### Turbulence
Disturbance 와 유사하되, 큰 규모의 Pyro 에 적용되는 효과라고 함
![[Pasted image 20230515122945.png]]
![[turbulence.jpg|500]]

#### Viscosity
불을 뭉쳐주게(?) 하는 효과; 높을수록 불이 더 뚱뚱해짐
![[Pasted image 20230515132001.png]]

## Microsolvers
> [!important] merge 관련 주의 사항 : 인풋 순서
> 여러 Microsolver 를 Merge 하는 경우, 좌우 순서로 각 노드가 계산됨; 순서가 바뀌면 전혀 다른 효과가 나올 수 있음

> [!important] Time Scale 속성 묶어주기
> 각 Microsolver 에 Time Scale 속성이 있음으로, Pyro Solver 의 Time Scale 속성 값을 변경하는 경우 같이 변경할 수 있도록 해줘야 함; Copy Parameter > Paste Relative Reference 꼭 해줄 것.

> [!important] 다른 모델이 안 보이는 경우 DOP Network 활용
> Microsolver 로 작업하려고 Pyro Solver 노드 안에 들어가면 다른 모델이 안 보이는 이슈가 생기며, 참고로 하는 모델이 안 보이면 작업할 때 불편함. 이 때 obj 컨텍스에서 DOP Network 노드를 생성하고, 이 안에 원하는 Microsolver 를 생성하면 Microsolver 와 참고 모델이 같이 보임 - 일단 여기서 위치나 크기를 맞춘 후 Microsolver 를 복사해서 Pyro Solver 노드 안에 붙여주면 됨.

> [!important] Voxel Size 관련 주의 사항
> Pyro Solver 에서 Voxel Size 를 조절하는 경우 Microsolver 로 작업한 룩이 크게 변형될 수 있으니 주의할 것!

- Gas Turbulence : Turbulence 효과를 적용해줌
- Gas Disturb : Disturbance 효과를 적용해줌
- Gas Damp : Pyro 의 속도를 줄여줌
	- #개인노트 속도를 줄여서 중력에 더 영향을 받는지 연기가 납작해짐?
- Gas Blur : Field 내에 지정된 Pyro 속성에 대하여 "blur" 효과를 줌;
	- Key Frame 을 적용하는 경우 속성 옆에 키 프레임 아이콘 (동그라미) 클릭하여 Set Always 를 눌러줘야 함
	- Field 속성을 density 로 지정한 경우 연기가 흐려보이는 효과를 주는 듯 한데, 동시에 연기가 몽실몽실/둥글둥글 하게 보임
- Gas Axis Force : 회오리 효과를 적용해줌
- 

## Minimal OpenCL Simulation
- Pyro Solver 노드의 Simulation Type 을 Minimal OpenCL 로 지정하면 CPU 대신에 GPU 를 사용하여 시뮬레이션이 가능함
- 장점
	- 아주 빠름
- 단점
	- Cache 저장을 못 함
	- OpenCL 과 호환되지 않는 Microsolver 가 있음
		- 호환되는 Microsolver 인 경우 Use OpenCL 옵션을 꼭 활성화 해줘야 함
	- 컨테이너(Bounds)에 Resizing 이 불가능함; 연기가 벽에 안 부닥치도록 컨테이너 사이즈를 잘 조정해놔야함

## Resources
- [Introduction to Pyro - SideFX](https://www.sidefx.com/docs/houdini/pyro/intro.html)
- [Smoke and Pyro - cgwiki](https://www.tokeru.com/cgwiki/Smoke_and_Pyro)
	- [[H13_Smoke_solver_basic_cgwiki.hipnc]] 후디니 파일 참고; 19.5 버전에서도 실행되며, 옛날 방식으로 작업하는 것을 보여줌 (이 방식이 더 좋을지도?); #todo 어떤 버전으로 배울지 문의 필요
- [Houdini DOPS - cgwiki](https://www.tokeru.com/cgwiki/HoudiniDops)
- 