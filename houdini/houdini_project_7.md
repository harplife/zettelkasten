# Houdini Project 7 : Exploding Bomb
간단히 폭탄이 터지는 장면을 구성함 - Modeling (폭탄, 퓨즈), VFX (Spark, Fracture, Explosion), Staging (라이팅, 카메라), Shading, 그리고 Rendering 까지 작업.

## Step 1 : 폭탄 Modeling
1. 네트워크 뷰 > /obj > Geometry 노드 생성 (bomb_geo) > Sphere 노드 생성 (sphere1)
2. sphere1 > Edge Selection > Delete (Dissolve 노드 생성, dissolve1)
	- ![[Pasted image 20230427100439.png|200]]
	- ![[Pasted image 20230427100517.png|200]]
3. dissolve1 > Face Selection > Poly Extrude 노드 생성 (polyextrude1) > Distance 속성 0.075 로 조정 > Extrusion :: Output Geometry and Groups :: Output Front 속성 비활성화
	- ![[Pasted image 20230427100819.png|200]]
	- ![[Pasted image 20230427101003.png|200]]
4. polyextrude1 > Face Selection > Delete (Blast 노드 생성, blast1)
	- ![[Pasted image 20230427101545.png|200]]
5. blast1 > Edge Selection > Poly Fill 노드 생성 (polyfill1) > Fill Mode 속성 Quadrilateral Grid, Smooth 속성 270
	- ![[Pasted image 20230427101738.png|200]]
	- ![[Pasted image 20230427101846.png|200]]
6. polyfill1 > Poly Extrude 노드 생성 (polyextrude2) > Distance 속성 -0.07, Extrusion :: Output Geometry and Groups :: Output Back 속성 활성화
	- ![[Pasted image 20230427102420.png|200]]
	- ![[Pasted image 20230427102554.png|200]]
	- #참고 따로 Selection 을 하지 않은 경우 Poly Extrude 노드는 도형 전체에 두께를 주는 효과를 줌
	- #참고 Poly Extrude 노드를 사용할 때 Distance 속성이 음수인 경우 (안쪽 방향으로 두께를 준 경우), 겉면 Primitive 들의 Normal 이 안쪽 방향으로 됨 - 따라서, Reverse 노드를 적용 해주는게 좋음
7. polyextrude2 > Reverse 노드 생성 (reverse1)
	- ![[Pasted image 20230427104701.png|100]]
	- ![[Pasted image 20230427104719.png|100]]
8. reverse1 > Edge Selection > Poly Bevel 노드 생성 (polybevel1) > Offsetting :: Distance 속성 0.005, Fillet :: Divisions 속성 5
	- ![[Pasted image 20230427105008.png|200]]
	- ![[Pasted image 20230427105130.png|200]]
9. polybevel1 > Edge Selection > Poly Bevel 노드 생성 (polybevel2) > Offsetting :: Distance 속성 0.01, Fillet :: Divisions 속성 5
	- ![[Pasted image 20230427105410.png|200]]
10. polybevel2 > Transform 노드 생성 (transform1) > Rotate 속성 X축 값 27
	- ![[Pasted image 20230427110030.png|200]]
11. transform1 > Match Size 노드 생성 (matchsize1) > Matching :: Justify Y 속성 첫번째 칸 Min
12. matchsize1 > Null 노드 생성 > 이름 변경 BOMB_OUT
13. 밑에 같이 나오면 `OK!`

![[Pasted image 20230427110336.png|500]]

## Step 2 : 퓨즈 Modeling

## Step 3 : 퓨즈 Spark VFX

## Step 4 : 폭탄 Fracture VFX

## Step 5 : 폭탄 Explosion VFX

## Step 6 : Staging

## Step 7 : Rendering

## 참고 자료
- [Houdini Foundations : Destruction FX | Houdini (SideFX) | Youtube Playlist](https://youtube.com/playlist?list=PLXNFA1EysfYkaso5T6Oddp3cnnmPs9itt)
	- SideFX 강의 소개 페이지 - [링크](https://www.sidefx.com/tutorials/foundations-destruction-fx/)
	- PDF 자료 - [[hfoundations19_5_05_destructionfx.pdf]]