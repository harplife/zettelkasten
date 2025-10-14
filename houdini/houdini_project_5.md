# Houdini Project 5 : Colored Pyro Smoke
후디니 Pyro 기능을 활용한 간단 연기 구현

> [!info]
> Redshift 로 렌더함

> [!important]
> 기본적으로 Pyro 와 같은 시뮬레이션은 시뮬레이션을 계산할 때는 CPU/RAM 성능에 많은 영향을 받지만, 시뮬레이션 데이터 캐싱(저장) 후 스토리지 드라이브의 Read 속도에 많은 영향을 받음.

![[20230427_color_smoke.mp4]]

## Step 1 : 연기가 될 도형 만들기
1. <mark style="background: #BBFABBA6;">네트워크 뷰 /obj</mark> > Geometry 노드 (geo1) > Sphere 노드 (sphere1) > {Primitive Type: Polygon, Uniform Scale: 0.25, Frequency: 4}
2. sphere1 > Transform 노드 (transform1) > {Translate: 0.25}
3. transform1 > Color 노드 (blue) > {Color: (0,0,1)}
4. blue > Mountain 노드 (mountain1) > {Animation : {Animate Noise: True}}
5. 노드 선택 (transform1, blue, mountain1) > 복붙 (Alt + LMB.Drag) == transform2, red (Color노드), mountain2 > sphere1 에 transform1, transform2 가 연결된 상태
6. transform2 {Translate: -0.25} > red {Color: (1,0,0)} > mountain2 {Noise Pattern: {Offset: 36.6}}
7. 노드 선택 (mountain1, mountain2) > Merge 노드 (merge1)
8. 여기까지 됐으면 `OK!`

![[Pasted image 20230428173106.png|300]]

## Step 2 : Pyro 기능 활용
1. 각 포인트에 속도 속성을 부여하기 : merge1 > Point Velocity 노드 (pointvelocity1)
2. pointvelocity1 > Pyro Source 노드 (pyrosource1) >
```json
{
	Mode: Surface_Scatter, // 도형 표면에 여러 포인트가 생성되게 함
	Particle_Separation: 0.01,
	Attributes: { // 각 포인트에 지정된 속성들이 있도록 함
		0: {Attribute: Density},
		1: {Attribute: Color},
		2: {Attribute: Alpha}
	}
}
```
![[Pasted image 20230428181416.png|300]]
3. Particle (Point) 을 기준으로 Voxel 생성 (볼륨을 넣어줌) : pyrosource1 > Volume Rasterize Attributes 노드 (volumerasterizeattributes1) > {Attributes: "density Cd Alpha v", Voxel_Size: 0.01}
	-  ![[Pasted image 20230428181638.png|300]]
4. Particle, Voxel 을 기준으로 연기 시뮬레이션 계산 및 데이터 생성 : volumerasterizeattributes1 > Pyro Solver 노드 (pyrosolver1) >
```json
{
	Setup: {General: {Voxel_Size: 0.01}},
	Sourcing: {
		Source_Volumes: {
			0: {
				Operation: (Add, Scalar),
				Source_Volume: density,
				Target_Field: density
			},
			1: {
				Operation: (Add, Vector),
				Source_Volume: v,
				Target_Field: vel
			},
			2: {
				Operation: (Blend, Vector),
				Source_Volume: Cd,
				Target_Field: Cd,
				Source_Weight: Alpha,
				Target_Weight: Alpha
			}
			// 이외 Source 는 모두 제거
		}
	},
	Fields: {Dissipation: 0.05},
	Shape: {Disturbance: True},
	Output: {Export_Fields:
		{0: (Density, Smoke), 1: (vel, Invisible), 2: (Cd, Invisible)}
	}
}
```
5. 시뮬레이션 데이터를 VDB 형식으로 변환 : pyrosolver1 > Convert 노드 (convert1) > {Convert_To: VDB}
6. VDB 변환 중 각 축(x, y, z)으로 분리된 속성(float)을 다시 하나의 속성(vector)으로 합쳐주기 : convert1 > VDB Vector from Scalar 노드 (vdbvectormerge1)
	- ![[Pasted image 20230428202618.png]]
	- ![[Pasted image 20230428202629.png]]
7. vdbvectormerge1 > File Cache 노드 (filecache1) > {Base_Name: ("아무런이름", vdb)} > Caching :: Save to Disk 버튼 클릭 > 저장 끝난 후 Load from Disk 속성 활성화
8. filecache1 > Null 노드 (PYRO_OUT)
9. 밑에 같이 나오면 `OK!`

![[Pasted image 20230428203327.png|500]]

> [!info] VDB 이란?
> VDB 는 [Volumetric Data (Voxel)](https://en.wikipedia.org/wiki/Voxel) 을 처리하기 위한 소프트웨어 라이브러리 또는 이러한 라이브러리에 최적화된 데이터 포맷으로 이해하면 됨. 원래는 [OpenVDB](https://en.wikipedia.org/wiki/OpenVDB) 라 불렸으며, DreamWorks 에서 오픈소스로 공유해준 도구였음. VDB 가 정확히 어떤 약자인지는 모름 - Voxel Data Base, Volumetric Data Blocks, Volumetric Dynamic B+tree 등 다양한 해석이 있었음.

## Step 3 : 장면 구성
재질 입히기 전에 간단히 라이팅과 카메라를 셋업해줌

1. <mark style="background: #BBFABBA6;">네트워크 뷰 /obj</mark> > RSLightDome 노드 (rslightdome1), RSLight 노드 (rslight1) > {Contribution: {Volume: 1}}
2. HDRI 이미지 선택해주고 적당히 라이팅 조절
3. Camera 노드 (cam1) > 적당히 구도 조절
4. 대강 밑에 같이 나오면 `OK!`

![[Pasted image 20230428204252.png|500]]

## Step 4 : 렌더 1차
한번 렌더해서 중간 점검 해볼 것!

![[Pasted image 20230428205415.png|500]]

> [!info]
> 렌더해보면 뷰포트와 달리 연기에 아무런 색상이 없음. 이는 재질을 입힘으로서 해결됨.

## Step 5 : 재질 입히기
1. <mark style="background: #ADCCFFA6;">네트워크 뷰 /mat</mark> > RS Material Builder 노드 (redshift_vopnet1) > 노드 안에 StandardMaterial1 노드 제거 > RS Volume 노드 (Volume1) > Volume1.outColor ~ redshift_material1.Volume
2. Volume1 속성 설정
```JSON
{
	Scatter: {
		Scatter_Coefficient: 20,
		Color_Channel: Cd
	},
	Absorption: {
		Absorption_Coefficient: 30,
	}
}
```
3. <mark style="background: #BBFABBA6;">네트워크 뷰 /obj</mark> > geo1 {Render: {Material: "/mat/redshift_vopnet1"}}
4. Pyro Solver 노드에 자동 생성된 shop_materialpath 속성 제거해주기 : geo1 > pyrosolver1, convert1 사이 Attribute Delete 노드 (attribdelete1) > {Primitive_Attributes: "shop_materialpath"}
5. 

## Step 5 : 장면 구성 및 렌더링


## 참고 자료
- [Coloured Pyro Smoke with Houdini & Redshift | helloluxx | Youtube](https://youtu.be/yVIlPQO_p2I)
- 