# Houdini Project 6 : Flower Blossom
간단한 꽃을 피우고 꽃잎이 날아오르게 함

```embed
title: 'Trippy Nature Tutorial 08: Blooming Flowers'
image: 'https://img.youtube.com/vi/WQSdMX-z7U4/maxresdefault.jpg'
description: 'In this tutorial I show you how to use Houdini with MOPs to procedurally create and animate blooming flowers.'
url: 'https://youtu.be/WQSdMX-z7U4'
```
^ 위에꺼랑 좀 더 합쳐주는것이 더 좋을듯. 벤드 등 좀 더 상세하게 작업 가능

## Step 1 : 꽃잎 모델 호출
참고 자료에서 제공된 꽃잎 모델을 가져오고 텍스처를 붙여줍니다.

1. `/obj/geo1` > `File` 노드 (`file1`) > `{ Geometry_File:'$HIP/geo/petal.bgeo' }`
2. `file1` > `UV Quick Shade` 노드 (`uvquickshade1`) > `{ Texture_Map:'$HIP/tex/petal_tex_01-01.png' }`
3. `uvquickshade1` > `Null` 노드 (`IN_Geo`)

![[Pasted image 20230504151608.png|300]]
![[Pasted image 20230504151543.png|300]]

## Step 2 : 꽃잎 오므려주기
최종 목표는 꽃을 피게하는 것으로, 꽃이 오므려진 상태로 시작하도록 합니다.

1. 꽃잎의 옆 부분을 구부려주기 : `IN_Geo` > `Bend` 노드 (`bend1`) >
```json
{
	Bend: { Bend:200, Up_Vector_Control:'Y Axis' },
	Capture: { Capture_Length: 0.4 } // Bend가 적용되는 영역의 길이
}
```
2. Reference Copy (카피본의 속성이 원본을 바라보게 된 것) 만들기 : `bend1` > `Shft + Ctrl + Alt + LMB.Drag` (`bend2`)
3. 카피본 방향 반대로 만들기 : `bend2` > `{ Capture : { Capture_Direction:(.., .., '-ch("../bend1/dirz")') } }` (이전 값을 마이너스 값으로 변환)
	- ![[Pasted image 20230504154731.png|300]]
4. 꽃 가운데 방향으로 구부려 주기 : `bend2` > `Bend` 노드 (`bend3`) >
```json
{
	Bend: { Bend:190, Up_Vector_Control:'Custom' },
	Capture: { Capture_Direction:(1,0,0) }
}
```

![[Pasted image 20230504155717.png|300]]
![[Pasted image 20230504155703.png|300]]

## Step 3 : 꽃잎 복사 루프 만들기
꽃잎을 루프로 18개 생성하며, 각 꽃잎이 이전 꽃잎보다 Y축 기준 (XZ 표면) 137.5° (_φ_) 회전된 위치에 생성되게 합니다; Transform 노드 + [Attribute Wrangle 노드](https://www.sidefx.com/docs/houdini/nodes/sop/attribwrangle.html) + For-Each Point 노드 + Copy to Points 노드

1. `/obj/geo1` > `Attribute Wrangle` 노드 (`attribwrangle1`) > `{ Run_Over:Numbers, Number_Count:18 }`
	- `Run Over `속성이 `Numbers` 인 경우, `Number Count` 값만큼 VEX 코드를 반복 수행함
2. `attribwrangle1` > `VEXpression` 속성 값 (VEX 코드) 작성
```C
// addpoint 함수로 좌표 (0,0,0)에 포인트 생성
// addpoint 함수는 point number를 리턴하며, pnt 변수는 이 값을 저장함
int pnt = addpoint(0, {0,0,0});

// roff: Rotation Offset
// chf 함수로 Angle 속성을 "정의"하고 입력받은 값을 리턴함
// 파라미터 패널에서 Angle 속성과 입력칸(+슬라이더)가 생성된게 보임
// @elemnum은 코드가 수행된 횟수(0~17)를 뜻하며,
// 이 값을 Angle 속성값에 곱해줌
float roff = chf("Angle") * @elemnum;

// setpointattrib 함수로 포인트의 속성을 지정된 값으로 변경해줌
// roff 속성이 없는 경우 새로 생성됨
setpointattrib(0, "roff", pnt, roff, "set");
```
3. `attribwrangle1` > 파라미터 생성 및 `Angle` 값 `137.5` 로 조정
	- `VEXpression` 옆에 ![[Pasted image 20230504181501.png]] 클릭 > 밑에 슬라이더 생성된 것 보임
	- ![[Pasted image 20230504181528.png]]
4. 루프 노드 생성 :  `For-Each Point` 노드 (`foreach_begin1`, `foreach_end1`)
5. `attribwrangle1` ~ `foreach_begin1` 연결
6. 꽃잎 회전 (*바로 반영되지 않음*) : `bend3` > `Transform` 노드 (`transform1`) >
```json
{ Rotate:(0, 'point("../foreach_begin1/", 0, "roff", 0)', 0) }
```
> [!info] point 함수?
> `float point(string surface_node, float point_number, string attribute, float index)`
> point 함수는 특정 노드(surface_node)에서 처리되는 객체(point_number)의 속성(attribute)에서 n번째(index) 값을 가져오는 함수임; 
7. `Copy to Points` 노드 (`copytopoints1`) > 왼쪽 인풋을 `transform1` 아웃풋과 연결 > 오른쪽 인풋을 `foreach_begin1` 아웃풋과 연결 > 아웃풋을 `foreach_end1` 왼쪽 인풋으로 연결

![[Pasted image 20230504180840.png|300]]
![[Pasted image 20230504180858.png|300]]

### 부연 설명
1. `bend3` 노드 선택하고 `Geometry Spreadsheet` 창을 보면 꽃잎에 총 `29`개의 포인트(`0~28`)가 있다는 것을 확인할 수 있음.
	- ![[Pasted image 20230504174053.png|500]]
2. `attribwrangle1` 노드 선택하고 `Geometry Spreadsheet` 창을 보면 총 `18`개의 포인트(`0~17`)가 있다는 것을 확인할 수 있으며, 각 포인트마다 `roff` 속성이 이전 값보다 `137.5` 씩 증가한 것을 확인할 수 있음.
	- ![[Pasted image 20230504174200.png|500]]
3. `foreach_end1` 노드 선택하고 `Geometry Spreadsheet` 창을 보면 총 `522`개의 포인트(`0~521`)가 있다는 것을 확인할 수 있으며, `18`개 포인트의 각 포인트마다 `roff` 속성을 참조하는 `29`개의 포인트가 생성된 것을 알 수 있음.

## Step 4 : 펴지는 꽃잎 애니메이션
1. bend3 > 1 Frame 에서 Bend 속성 190 으로 Key Frame 생성 > 60 Frame 에서 Bend 속성 5 으로 Key Frame 생성
2. bend1 > 1 Frame 에서 Bend 속성 200 으로 Key Frame 생성 > 60 Frame 에서 Bend 속성 50 으로 Key Frame 생성

![[Pasted image 20230504192632.png|300]]
![[Pasted image 20230504192645.png|300]]
![[Pasted image 20230504192654.png|300]]

## Step 5 : 꽃잎 타이밍 조절
꽃잎이 서로 다른 타이밍에 펼치도록 해줍니다.

1. `transform1` > `Time Shift` 노드 (`timeshift1`) > `{ Frame:'$F + point("../foreach_begin1/", 0, "toff", 0)' }`
```C
// foreach_begin1 노드에서 처리되는 포인트 객체의 toff 속성을 가져오며,
// 현재 프레임에 toff 속성값 만큼 더해줌
// toff 속성값은 attribwrangle1 노드에서 음수 값을 넣어줌으로,
// 각 꽃잎들이 이전 꽃잎보다 늦게 펼쳐지는 효과가 생김
$F + point("../foreach_begin1/", 0, "toff", 0)
```
2. `attribwrangle1` 노드 `VEXpression` 코드 수정
```C
int pnt = addpoint(0, {0,0,0});

float roff = chf("Angle") * @elemnum;
// toff : Time Offset
// 지정한 Frames 값과 현재 횟수와 곱해준 값을 저장
float toff = chf("Frames") * @elemnum;

setpointattrib(0, "roff", pnt, roff, "set");
setpointattrib(0, "toff", pnt, toff, "set");
```
3. `attribwrangle1` > 파라미터 생성 및 `Frames` 값 `-2` 로 조정

![[Pasted image 20230504203609.png|300]]
![[Pasted image 20230504203632.png|300]]
![[Pasted image 20230504203708.png|300]]

## Step 6 : 꽃잎 떨어지게 하기
꽃잎이 완전히 펼쳐졌을 때 바로 떨어지게 하는 효과를 넣어줍니다.
1. Cloth 시뮬레이션으로 꽃잎을 부드럽게 만듬
2. Velocity 속성으로 꽃잎을 날아가게 만듬

### 꽃잎에 Cloth 시뮬레이션 적용
1. 객체의 한 순간(프레임)을 하나의 그룹(`toSim`)으로 묶어주기 : `bend3` ~ `transform1` 사이에 `Group Expression` 노드 (`groupexpression1`) >
```json
{
	Group_VEXpressions: [
		{ Group_Name:'toSim', VEXpression:'@Frame == chi("Frame");' }
	]
}
```
> [!important]
> `@Frame`은 객체 기준 프레임으로 `Time Shift` 노드에 영향을 받음.
2. `groupexpression1` > 파라미터 생성 및 `Frame` 속성 `70` 입력
3. `toSim` 그룹만 추려내기 (그룹 외 객체 제거) : `foreach_end1` > `Blast` 노드 (`blast1`) > `{ Group:'toSim', Delete_Non_Selected:True }`
	- `70` 프레임부터 `2` 프레임 단위로 각 꽃잎이 하나씩 보임
4. `blast1` > `Vellum Configure Cloth` 노드 (`vellumcloth1`) > `Null` 노드 2개 생성 (`GEO`, `CON`) > `vellumcloth1` 노드 아웃풋1에 `GEO`, 아웃풋2에 `CON` 연결
5. DOP Network 노드 (dopnet1) > 들어가기 > Vellum Object 노드 (vellumobject1), Vellum Source 노드 (vellumsource1), Vellum Solver 노드 (vellumsolver1) > vellumobject1 노드 아웃풋을 vellumsolver1 노드 아웃풋1에 연결, vellumsource1 노드 아웃풋을 vellumsolver1 아웃풋3에 연결
6. `vellumsource1` > `{ Source: { SOP_Path:'/obj/geo1/GEO', Constraint_SOP_Path:'/obj/geo1/CON' } }`
7. `vellumsolver1` 노드 `Output` 플래그 활성화 후 애니메이션 실행해보면 시뮬레이션이 실행되고 데이터 캐시가 저장됨; 문제는 꽃잎들이 뭉쳐버린다는 것!

![[Pasted image 20230504214323.png|300]]
![[Pasted image 20230504214922.png|300]]

### 꽃잎의 Velocity 속성 조절
#todo this note needs to be finished!!

## VEX 언어 참고 자료
- `geohandle` 값이 `0`인 경우, 이는 `self`를 뜻하며 현재 처리되는 `geometry` 객체를 처리한다는 것을 뜻함.
- `int addpoint(int geohandle, vector pos)` - [링크](https://www.sidefx.com/docs/houdini/vex/functions/addpoint.html)
	- ![[Pasted image 20230504181007.png]]
- `float chf(string channel)` - [링크](https://www.sidefx.com/docs/houdini/vex/functions/chf.html)
	- ![[Pasted image 20230504181030.png]]
- `float point(string surface_node, float point_number, string attribute, float index)`
	- ![[Pasted image 20230504163207.png]]
- setpointattrib
	- ![[Pasted image 20230504181120.png]]
- `@elemnum` - [링크](https://www.sidefx.com/docs/houdini/vex/snippets.html)

## 참고 자료
- [Guest Tutorial (Chris Kopic): Endless Flower Blossoming | Entagma | Youtube](https://youtu.be/J2rDQtsTwzo)