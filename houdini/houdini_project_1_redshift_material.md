<mark style="background: #ADCCFFA6;">저자 : 김우빈</mark>
<mark style="background: #FFF3A3A6;">작성 일자 : 2023-04-18</mark>
<mark style="background: #FF5582A6;">버전 : v02_20230421</mark>

---
# Houdini Project 1.1 : Redshift로 재질 입히기
[[houdini_project_1|"Houdini Project 1 : Random Scatter Sphere"]] 에 Redshift 재질을 입히고 렌더 해보기!

![[20230421_houdini_redshift_scatter_balls_glass_mat_final_2.png|500]]

> [!warning]
> Houdini 와 Redshift 연동하는 방법은 [[houdini_redshift_render|"Houdini + Redshift 연동 가이드"]] 참고 해주세요!

## 목차
- [[#Step 1 : Redshift Material 생성]]
- [[#Step 2 : 랜덤 색상 속성 "참고"하기]]
- [[#Step 3 : 유리 구슬 만들기]]
- [[#참고 자료]]
- [[#끝]]

## Step 1 : Redshift Material 생성
1. 네트워크 뷰 패널 > `/mat` 탭 > `RS Material Builder` 노드 생성 및 들어가기 (`redshift_vopnet1`) > `StandardMaterial1` 노드 선택 > 속성 패널
	- `Base` :: `Color` 에서 기본 색상 선택 (예: `1 // 0.5 // 0`)
	- `Reflection` :: `Weight`는 `1`, `Roughness`는 대략 `0.033`
	- ![[Pasted image 20230418173226.png|300]]
2. Redshift 렌더 돌려서 밑에 같이 나오면 `OK!`

![[Pasted image 20230421154908.png|500]]
(상단 출력 화면은 뷰포트, 하단 출력 화면은 Redshift 렌더뷰 )

## Step 2 : 랜덤 색상 속성 "참고"하기
1. Redshift 재질의 색상이 `Attribute Randomize` 노드로 설정한 랜덤 색상을 덮어버림! 따라서, 뷰포트에는 여러 색상이 보이지만 Redshift 렌더뷰에서는 색상 하나만 보임. 이 문제를 해결하기 위해서 Redshift 재질이 도형의 `Cd` 속성을 참고 할 수 있도록 해줘야 함.
2. 네트워크 뷰 패널 > `/mat/redshift_vopnet1` 탭 > `RS Point Attribute` 노드 생성 (`ParticleAttributeLookup1`) > outColor 속성 아웃풋을 StandardMaterial1 노드의 base_color 속성 인풋으로 연결
	- ![[Pasted image 20230421155303.png]]
3. `ParticleAttributeLookup1` 노드 선택 > 속성 패널 > `Attribute Name` 값에 `Cd` 입력
	- ![[Pasted image 20230418173707.png]]
4. Redshift 렌더 돌려서 밑에 같이 나오면 `OK!`

![[Pasted image 20230421155555.png|500]]
![[20230421_houdini_scatter_balls_redshift_render.png]]

## Step 3 : 유리 구슬 만들기
1. 네트워크 뷰 패널 > `/mat/redshift_vopnet1` 탭 > `StandardMaterial1` 노드 선택 > 속성 패널 > `Transmission` :: `Weight` 속성은 `0.75`, `Dispersion (Abbe)` 속성은 `21.2`
2. 밑에 같이 나오면 `OK!`

![[20230421_houdini_redshift_scatter_balls_glass_mat_final.png]]
![[20230421_houdini_redshift_scatter_balls_glass_mat_final_2.png]]

## 참고 자료
- [Use Point Attributes Inside Redshift for Houdini | Inside The Mind | Youtube](https://youtu.be/p218-2TmJc4)

## 끝
언제든지 문의~