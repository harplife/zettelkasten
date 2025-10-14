<mark style="background: #ADCCFFA6;">저자 : 김우빈</mark>
<mark style="background: #FFF3A3A6;">작성 일자 : 2023-04-19</mark>
<mark style="background: #FF5582A6;">버전 : v02_20230421</mark>

---
# Houdini Project 1.2 : Directing
작은 스피어들이 좀 더 복잡한 모형으로 흩어지게 해봅니다!

![[20230421_scatter_balls_grid_paint_relax_diffuse_rough.png|500]]

> [!warning]
> "Houdini Project 1 : Random Scatter Spheres" 가이드를 따라간 후에 진행해주세요!

> [!info]
> 렌더는 Redshift 로 했습니다~ 관련해서 `Houdini + Redshift 연동` 가이드와 `Houdini Project 1.1 : Redshift로 재질 입히기` 가이드를 참고하세요!

## Step 1 : Grid에 스피어 흩어지게 하기
1. 네트워크 뷰 > `/obj/geo1` > `sphere2` (큰 스피어), `isooffset1` 는 제거해주고 > `Grid` 노드로 대체 (`grid1`)
	- `grid1` 의 `Rows`, `Columns` 속성 값을 `100` 으로 조정
2. `grid1` 에 비해 스피어(`sphere1`)들이 너무 작아 보이고 수도 적어 보이니, 좀 수정해줌
	- `sphere1` (작은 스피어)의 `Uniform Scale` 을 `1`로 수정
	- `attribrandomize1` (사이즈 랜덤 노드)의 `Min Value` 는 `0.25`, `Max Value` 는 `0.5` 로 수정
	- `scatter1` 의 `Force Total Count` 를 `500` 정도로 수정
3. 밑에 같이 나오면 `OK!`

![[Pasted image 20230421171011.png|500]]
![[20230421_scatter_balls_grid.png]]

## Step 2 : Grid에 그림 그리기
> [!info] 작동 원리 설명
> 납작한 평면(Grid)에 "가상"의 두께(Density)라는 속성을 추가하고, 페인트 도구로 이 평면에 두께를 그릴 것임. 그려진 두께에 여러 포인트가 생성될 것이고, 최종적으로 각 포인트에 공(Sphere)이 그려질 것임.

1. `scatter1` 노드의 `Density Attribute` 속성 활성화
	- 네트워크 뷰 패널에서 빨간 경고가 뜰 것임. 이유는, density 라는 속성이 `scatter1` 노드에 전달되고 있지 않기 때문임
		- ![[Pasted image 20230419105354.png]]
		- ![[Pasted image 20230419105419.png]]
2. `grid1` & `scatter1` 노드 사이 `Attribute Paint` 노드 생성 및 선택 (`attribpaint1`) > 속성 패널 > `Attributes` 탭 > `Attribute Name` 속성에 `density` 입력
	- 여기까지 제대로 했으면 경고 없어짐
		- ![[Pasted image 20230419110300.png]]
	- 그림 그리기 위해 브러시 설정 해주기 : `Brush` 탭 > `FG Float` 을 `1`, `Soft Edge` 를 `1` 로 맞춰줌
		- ![[Pasted image 20230419111049.png]]
3. `attribpaint1` 노드를 뷰포트에 출력 > `Attribute Paint tool` 선택 (화살표 3개, 삼각형처럼 생긴 아이콘 클릭)
	- ![[Pasted image 20230419110539.png|75]]
	- ![[Pasted image 20230421171627.png]]
	- `MMB`(마우스 스크롤)로 `Radius`(브러시 사이즈) 조정하고 원하는 그림 그리기
		- ![[Pasted image 20230421171922.png]]
4. `null1` 노드 뷰포트 출력
5. 렌더하고 밑에 같이 나오면 `OK!`

![[Pasted image 20230421172302.png|500]]
![[20230421_scatter_balls_grid_paint.png]]

## Step 3 : 덜 뭉치게 해주기
작은 스피어들이 너무 서로 뭉쳐있다 싶으면 느슨~하게 해줄 수 있음

1. <mark style="background: #FF5582A6;"> !!주의!!</mark> `attribrandomize1` & `attribpaint1` 와 `attribrandmize2` 사이에 `Point Relax` 노드 생성 (`relax1`)
	- ![[Pasted image 20230421173011.png]]
2. `relax1` 노드 선택 > `Point Radius Scale` 속성 적절히 조정 (대략 `0.0984`)
	- 필요시 스피어 크기, 랜덤 크기, 개수 조절
3. 밑에 같이 나오면 `OK!`

![[Pasted image 20230421173320.png|500]]
![[20230421_scatter_balls_grid_paint_relax.png|500]]
![[20230421_scatter_balls_grid_paint_relax_diffuse_rough.png]]
(전체적으로 너무 밝게 보여서 Diffuse Roughness 0.76 으로 조정했음)

## 참고 자료
- [Houdini In Five Minutes 06: Art Directing Your Scattered Spheres | Entagma | Youtube](https://youtu.be/3wqpHCgrS8g)

## 끝
언제든지 문의~