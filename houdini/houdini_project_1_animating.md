<mark style="background: #ADCCFFA6;">저자 : 김우빈</mark>
<mark style="background: #FFF3A3A6;">작성 일자 : 2023-04-20</mark>

---
# Houdini Project 1.3 : Animating
작은 스피어들을 움직이게 해주죠!

![[20230421_scatter_balls_grid_paint_relax_diffuse_rough_noise.png|500]]

> [!warning]
> "Houdini Project 1.2 : Directing" 가이드 + "Houdini Project 2 : Terrain Generation" 가이드 모두 따라왔어야 진행 가능 (1.1 제외)

> [!info]
> 렌더는 Redshift 로 했습니다~

## Step 1 : 그리드 페인트에 노이즈 넣기
아는 내용이니 말 대신 이미지로 설명 할께요~

- ![[Pasted image 20230421180623.png|200]]
- ![[Pasted image 20230421180729.png|400]]
- ![[Pasted image 20230421180842.png]]
- ![[Pasted image 20230421180918.png]]
- 밑에 같이 나오면 `OK!`

![[Pasted image 20230421180949.png|500]]
![[20230421_scatter_balls_grid_paint_relax_diffuse_rough_noise.png]]

## Step 2 : 렌더 및 시퀀스 출력
1. 네트워크 뷰 패널 > `/out` 탭 > `Redshift_ROP1` 노드 선택 > 파라미터 패널 > `Valid Frame Range` 속성 `Render Frame Range` 선택 > `Start`/`End`/`Inc` 속성 `1`, `240`, `1` (프레임1에서 240까지 1단위로 렌더한다는 뜻) > `Render to Disk` 버튼 클릭 > `MPlay` 창이 뜨면서 바로 렌더가 시작됨
	- ![[Pasted image 20230421192741.png]]
2. 렌더 끝난 후 `MPlay` 창 상단 메뉴 `File` > `Save Sequences As...` 클릭 > 위치 지정 > 저장 완료!
	- ![[Pasted image 20230421193016.png]]
	- ![[Pasted image 20230421193051.png]]

## 참고 자료
- [Houdini In Ten Minutes 07: Animating The Spheres | Entagma | Youtube](https://youtu.be/9Agq4ZOm2rc)

## 끝
언제든지 문의!

참고로 저장된 시퀀스는 에펙에 가져가서 영상으로 출력하면 됩니다~