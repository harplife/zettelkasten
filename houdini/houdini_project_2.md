<mark style="background: #ADCCFFA6;">저자 : 김우빈</mark>
<mark style="background: #FFF3A3A6;">작성 일자 : 2023-04-20</mark>

---
# Houdini Project 2 : Terrain Generation
후디니에서 2 가지 방식으로 간단한 지형(Terrain)을 생성해봅니다!
- 방식 1) `Mountain` 노드 활용
- 방식 2) `Normal` 노드 + `Noise` 노드 활동

> [!info]
> 지형을 생성하는데 두 가지 방식으로 나눈 이유는 나중에 애니메이션 가이드에서 설명 드리겠습니다! 두번째 방식이 복잡하지만 나중에 더 용이하게 사용할 수 있다는 것만 알아두시길~

> [!info]
> 렌더는 Redshift 로 했습니다~

![[20230420_terrain_gen_2.png|500]]

## 방식 1) Mountain 노드 활용
이 방식은 아주 간단합니다!

1. 언제나 시작은  네트워크 뷰 패널 > `Geometry` 노드 생성 (`geo1`) > `Enter`
2. `Grid` 노드 생성 및 선택 (`grid1`) > `grid1` 의 `Rows`, `Columns` 속성 둘 다 `100` 으로 설정
3. `Mountain` 노드 생성 및 선택 (`mountain1`) > 속성 패널 > `Noise Value` :: `Amplitude` 조절 (예: `3.76`) > `Noise Pattern` :: `Element Size` 조절 (예: `5.34`)
4. `grid1` 아웃풋을 `mountain1` 인풋에 연결
5. `Null` 노드 생성 (`null1`) > `mountain1` 아웃풋을 `null1` 인풋에 연결
6. 재질, 라이팅, 카메라, 렌더 설정하고 출력! 밑에 같이 나오면 `OK!`

![[Pasted image 20230419170944.png|500]]
![[20230419_houdini_redshift_terrain_gen_1.png]]


## 방식 2) Normal 노드 + Noise 노드 활용
이 방식은 좀.. 많이 복잡합니다!

### Step 1 : "표면" 꺼내주기
1. 언제나 시작은  네트워크 뷰 패널 > `Geometry` 노드 생성 (`geo1`) > `Enter`
2. `Grid` 노드 생성 (`grid1`) > `Normal` 노드 생성 (`normal1`) > `grid1` 에서 `normal1` 로 연결
3. `normal1` 노드 선택 > 파라미터 패널 > `Construct` :: `Add Normals to` 속성 값을 `Points` 로 변경
4. `Point VOP` 노드 생성 (`pointvop1`) > `normal1` 에서 `pointvop1` 로 연결
	- `Point VOP` 노드는 포인트에 변형을 주는 노드로, 여기 안에서 노이즈 줄 것임! 
5. 밑에 같이 나오면 `OK!`

![[Pasted image 20230420171234.png]]

> [!info] Normal 이란?
> 여기서 Normal 은 기하학(Geometry) 용어로 평면에 수직인 벡터(선)을 뜻합니다. 대강 "표면이 바라보는 방향" 또는 "표면에서 직각(90도)로 나오는 선"으로 이해하면 될 듯.. 한국어로 법선/노멀/수직 벡터로 불림. 
> ![[Surface_normal_illustration.svg|300]]

> [!important] Normal 노드를 사용하는 이유
> Normal 은 무조건 한 방향으로 가기 때문에, 사방대가 아닌 한 방향으로만 노이즈를 넣기 위해서는 Normal 을 사용하면 편리함. 여기서 `grid1` 노드는 ZX 축 기준 평면이기 때문에,  `grid1` 의 Normal 은 Y 축 방향으로 가는 것임.

### Step 2 : 표면에 노이즈 주기
여기서 작동 원리 좀 어려움으로, 일단 따라할 것!

1. `pointvop1` 안으로 이동 (`I` 또는 더블클릭)
	- `geometryvopglobal1` 노드와 `geometryvopoutput1` 노드가 보여야 함
2. `Add` 노드 생성 (`add1`) > `geometryvopglobal1` 노드의 `P` 와 `N` 아웃풋을 `add1` 노드의 인풋으로 각각 연결 > `add1` 아웃풋을 `geomtryvopoutput1` 노드 `P` 인풋으로 연결
3. `Unified Noise` 노드 생성 (`unifiednoise1`) > `geometryvopglobal1` 노드의 `P` 아웃풋을 `unifiednoise1` 노드의 `pos` 인풋으로 연결
4. `Multiply` 노드 생성 (`multiply1`) > `geometryvopglobal1` 노드의 `N` 아웃풋과 `unifiednoise1` 노드의 `noise` 아웃풋을 `multiply1` 노드의 인풋으로 각각 연결 > `multiply1` 노드의 `product` 아웃풋을 `add1` 노드의 `input2` 인풋으로 연결
5. 밑에 같이 나오면 `OK!`

![[Pasted image 20230420171134.png]]

> [!info] 작동 원리??
> **첫째**, `geometryvopglobal1` 노드는 `pointvop1` 노드 인풋으로 들어오는 모든 값을 정리해준 노드로 이해하면 됨. `P` 아웃풋은 Point, `N` 아웃풋은 Normal 을 뜻함. 유사하게, `geomtryvopoutput1` 노드는 아웃풋을 정리해줌.
> **둘째**, `P` 값과 `N` 값을 Add 노드로 더해주면, 모든 포인트 위치에 Y 축 기준으로 1 을 더한 효과가 나옴. 뷰포트에서 보면 grid1 도형이 위로 약간 올라간 것이 보임.
> **셋째**, `P` 값을 기준으로 `Unified Noise` 노드로 노이즈를 생성하고, 이 노이즈를 `N` 값에 곱(`Multiply`)한 결과를 `P` 값에 더한(`Add`) 후 `P` 아웃풋으로 연결함으로서 `grid1` 의 각 포인트에 랜덤한 값을 더한 결과가 나옴.

### Step 3 : 뷰포트 출력 및 노이즈 설정
1. `pointvop1` 노드에서 나가기 (`U` 또는 네비게이션에서 `geo1` 클릭)
2. `Edit` 노드 생성 (`edit1`) > `pointvop1` 아웃풋을 `edit1` 인풋으로 연결
	- #참고 이 가이드를 만들기 위해 참고한 영상에서는 Edit 노드를 사용하지 않음; 버전이 달라서 그런지, 이 노드가 없으면 렌더가 제대로 안 됨.
3. `Null` 노드 생성 (`null1`) > `edit1` 아웃풋을 `null1` 인풋으로 연결
4. `null1` 렌더 플래그 클릭하면 전체적인 결과가 뷰포트에 보임
	- ![[Pasted image 20230420190246.png|150]]
5. `pointvop1` 노드에 들어가기 > `unifiednoise1` 노드의 `cc_amp` 인풋에 스크롤 클릭 > `Promote Parameter` 선택 > `freq`, `offset` 인풋에도 마찬가지로 적용
	- #참고 Promote Parameter 는 특정 객체의 속성을 해당 객체를 담고 있는 상위 객체에서 직접 조절할 수 있도록 속성을 "승진"해주는 기능임
6. `geo1` 노드로 돌아가서 `pointvop1` 노드 선택 > 파라미터 패널에서 `Frequency` 값 모두 `0.5` 로 입력, `Final Amplitude` 값 모두 `3` 으로 입력
	- `Offset` 은 두번째 칸에 `$FF * 0.02` 로 입력
		- ^ 그냥 `0.02` 입력해도 됨; `$FF` 는 프레임 값을 받는 것이고, `Play` 버튼 누르면 노이즈가 프레임마다 변형되는 것을 뷰포트에서 확인할 수 있음
	- ![[Pasted image 20230420191320.png]]
7. 렌더 엔진(e.g. Redshift) 설정하고 렌더하면 끝! 밑에 같이 나오면 `OK!`

![[Pasted image 20230420170946.png|500]]
![[20230420_terrain_gen_2.png]]


## 참고 자료
- [Houdini In Ten Minutes 07: Animating The Spheres | Entagma | Youtube](https://youtu.be/9Agq4ZOm2rc)

## 끝
언제든지 문의해주세요..

밑에는 `fbx` 포맷으로 뽑아서 C4D + Octane 으로 렌더해본 것! 자세한 사항은 나중에~
![[20230420_moon_waves_DeMain_0000.png]]
![[20230420_moon_waves_DeMain_0000 1.png]]