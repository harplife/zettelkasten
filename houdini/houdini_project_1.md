<mark style="background: #ADCCFFA6;">저자 : 김우빈</mark>
<mark style="background: #FFF3A3A6;">작성 일자 : 2023-04-17</mark>
<mark style="background: #FF5582A6;">버전 : v02_20230420</mark>

---
# Houdini Project 1 : Random Scatter Spheres
스피어의 형태에 따라 작은 스피어들이 난수적으로 흩어져 있는 형태 구성

![[Pasted image 20230417203417.png|500]]

> [!info]
> 후디니 19 버전 이상 (18 버전은 인터페이스가 좀 달라요)

> [!info] 용어 정의
> Parameters 는 "속성"이라 부를게요~ 따라서, Parameters 패널은 속성 패널이라 부를것임

## 목차
- [[#시작 전]]
- [[#Step 1 : 큰 스피어의 겉면(포인트)에 따라 작은 스피어 생성하기]]
- [[#Step 2 : 작은 스피어 랜덤하게 흩어지게 해주기]]
- [[#Step 3 : 큰 스피어 안에도 작은 스피어로 채워주기]]
- [[#Step 4 : 작은 스피어 크기를 랜덤하게 해주기]]
- [[#Step 5 : 작은 스피어의 색을 랜덤하게 해주기]]
- [[#참고 자료]]
- [[#끝~]]

## 시작 전
- 네트워크 뷰 패널 > `/obj` 탭 > `Geometry` 노드 생성 (`Geo1`) 및 들어가기 (`I`, `Dbl.LMB`, 또는 `Enter`)

![[Pasted image 20230417210149.png]]

## Step 1 : 큰 스피어의 겉면(포인트)에 따라 작은 스피어 생성하기

1. `Sphere` 노드 생성 및 선택 (`sphere1`)
	- 속성 패널 > `Primitive Type`을 `Polygon` 으로 설정
	- 속성 패널 > `Uniform Scale` 을 `0.1` 정도로 설정
	- 속성 패널 > `Frequency` 를 `10` 정도로 조정
	- ![[Pasted image 20230420193635.png]]
2. `Sphere` 노드 생성 및 선택 (`sphere2`)
	- 속성 패널 > `Primitive Type`을 `Polygon` 으로 설정
	- 속성 패널 > `Frequency` 를 `6` 정도로 설정
	- ![[Pasted image 20230420193649.png]]
3. `copytopoints` 노드 생성 (`copytopoints1`) > `sphere1` 를 왼쪽 인풋에 연결 > `sphere2` 을 오른쪽 인풋에 연결 > copytopoints 노드 디스플레이 활성화
	- ![[Pasted image 20230420193701.png]]
4. 밑에 같이 나오면 `OK!`

![[Pasted image 20230420194010.png]]

> [!info]
> 결과적으로 큰 스피어의 표면에 있는 포인트 마다 작은 스피어를 클론하는 것임

## Step 2 : 작은 스피어 랜덤하게 흩어지게 해주기
1. `scatter` 노드 생성 및 선택 (`scatter1`) > 속성 패널 >  `Force Total Count` 를 `92` 정도로 설정
2. `sphere2` 노드와 `copytopoints1` 노드 사이에 연결
	- ![[Pasted image 20230420194235.png]]
3. 밑에 같이 나오면 `OK!`

![[Pasted image 20230420194307.png]]

> [!info]
> 큰 스피어 겉면에 있는 포인트를 랜덤하게 흩어지게 함으로서, 각 포인트에 놓여진 작은 스피어들도 마찬가지로 흩어지게 됨

## Step 3 : 큰 스피어 안에도 작은 스피어로 채워주기
1. `IsoOffset` 노드 생성 및 선택 (`isooffset1`) > 속성 패널 > `Dimensions` :: `Uniform Sampling Divs` 를 `50` 정도로 설정
	- `Output Type` 의 기본 값이 `Fog Volume` 으로 되어있을 것임 (혹시 아니면 수정)
2. `sphere2` 노드와 `scatter1` 노드 사이에 연결
	- ![[Pasted image 20230420194535.png]]
3. 밑에 같이 나오면 `OK!`

![[Pasted image 20230420194548.png]]

> [!info]
> `Output Type` 이 `Fog Volume` 인 `IsoOffset` 노드는 인풋으로 들어온 도형의 형태에 따라 포그를 만들어 줌. 포그 안에 여러 포인트가 생기기 때문에, 이러한 특징을 사용하여 작은 스피어들이 큰 스피어 안에도 클론되게 할 수 있음.

## Step 4 : 작은 스피어 크기를 랜덤하게 해주기
1. `Attribute Randomize` 노드 생성 및 선택 (`attribrandomize1`) > 속성 패널 > `Attribute Name` 에 `pscale` 입력 > `Distribution`:: `Min Value` 를 `0.3` , `Max Value` 를 `1.5` 정도로 설정
	- ![[Pasted image 20230421103450.png]]
2. `attribrandomize1` 노드를 `scatter1` 노드와 `copytopoints1` 노드 사이에 연결
	- ![[Pasted image 20230420200346.png]]
3. 밑에 같이 나오면 `OK!`

![[Pasted image 20230421103508.png]]

> [!info]
> `Attribute Randomize` 노드는 인풋으로 들어온 객체의 특정 속성에 대하여 랜덤으로 값을 변경함. 대상이 될 속성을 `Attribute Name` 속성에 지정하면 됨. 여기에 `pscale` 을 지정함으로서 큰 스피어의 각 포인트의 크기가 난수화가 됨; 각 포인트의 사이즈로 인해 포인트 위에 클론된 작은 스피어의 사이즈도 마찬가지로 변형됨 (포인트의 속성을 작은 스피어가 상속 받음).

## Step 5 : 작은 스피어의 색을 랜덤하게 해주기
1. `Attribute Randomize` 노드 생성 및 선택 (`attribrandomize2`) > 속성 패널 > `Attribute Name` 에 `Cd` 입력
2. `attribrandomize2` 노드를 `attribrandomize1` 노드와 `copytopoints1` 노드 사이에 연결
	- ![[Pasted image 20230421103744.png|250]]
3. 밑에 같이 나오면 `OK!`

![[Pasted image 20230421103816.png]]

## 참고 자료
- [Houdini In Five Minutes 02: Your First Node Tree | Entagma | Youtube](https://youtu.be/7Jg189FyFWs)

## 끝~
- 모든 도형 노드의 마무리는 `Null` 노드로 끝냅니다.
	- ![[Pasted image 20230421103908.png]]
- 언제든지 문의 주세요!