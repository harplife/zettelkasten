# 후디니로 구현하는 알고리즘 디자인
![[Pasted image 20230416202106.jpg|200]]
- 원본 일본어 제목 : ではじめる自然現象のデザイン
- 한국어 제목 : 후디니로 구현하는 알고리즘 디자인
- 영어 제목 : Algorithmic Design with Houdini
- [아마존 링크](https://a.co/d/20Ih2yZ)
- 2023년 기준 시세 : $88.14 (일본어 종이 책)
- ISBN-10 : 4802511027
- ISBN-13 : 978-4802511025

## 저자 소개
![[Pasted image 20230416200454.jpg|75]]
- 저자 : 호리카와 준이치로 (Junichiro Horikawa)
- 개인 사이트 : https://jhorikawa.com/
- 유투브 : [@JunichiroHorikawa](https://www.youtube.com/c/JunichiroHorikawa)
	- [[junichiro_horikawa_youtube_channel.pdf]]
- 인스타그램 : [horikawa.j](https://www.instagram.com/horikawa.j/?hl=en)
- Patreon : https://www.patreon.com/junichirohorikawa

> [!info] Patreon 소개글
> Hello everyone! My name is Junichiro Horikawa.
> I'm an algorithmic designer / architectural programmer who loves anything related to creating geometrical shapes using computational methods including a method for digital fabrication. I am especially into designs using an algorithmic and mathematical approach. I'm always excited founding out new methods to realize new types of geometrical forms.
> I'm currently creating tutorials for Houdini, Rhino / Grasshopper, Unity, and other computational design related software to teach you various aspects of algorithmic design to share my approach I built through years of exploration. To continue sharing my knowledge I would love to have your support if you find my activity worthwhile :D


## 번역자
- 박민수
- 송창현
- 곽민경

## 목차
0) 소개
1) 알고리즘 디자인 (Algorithmic Design)
2) 알고리즘 디자인을 위한 후디니 기초 지식
3) 레시피 (Recipe)

## 소개
### 왜 후디니?
- 비주얼 생성 프로그래밍 언어인 Processing을 시작으로 다양한 언어와 CG 툴을 사용해본 결과, '자연계의 물리 현상을 구현하는 시스템 제작'이란 목적에 제일 부합한 것은 후디니 였음
	- Processing은 다이나믹 시뮬레이션과 2차원 영상 제작이 가능하지만, 3차원 모델링은 어려움
	- Maya는 복잡하고 자유로운 3차원 모델링은 가능하지만, 수학적으로 정확하게 제어해야 하는 다이나믹 시뮬레이션 또는 수리적인 컨트롤이 어려움
	- Houdini는 메쉬를 다루는 3D 범용 도구이면서 노드 기반의 비주얼 프로그래밍 도구이기에, 진행 과정의 이력을 쉽게 제어할 수 있고, 순차적인 절차를 간단하게 재조합 할 수 있음; 따라서, 알고리즈믹 디자인에 적합함.
		- 더불어, 후디니 에서는 메쉬의 포인트마다 데이터를 저장하는 속성이란 것이 있기 때문에 시뮬레이션 데이터를 손쉽게 관리할 수 있음

### 레시피(예제) 다운로드
- https://vielbooks.tistory.com/294

## 알고리즘 디자인 (Algorithmic Design)
**목차**
1. 알고리즘 디자인이란
2. 디자인 모티브를 찾는 방법
3. 알고리즘을 찾는 방법
4. 알고리즘의 이해
5. 후디니로 알고리즘 구현

### 알고리즘 디자인이란
- 알고리즘 디자인(Algorithmic Design) : 수리적(Mathematical) 절차로 재현 되는 기하학적(Geometric) 모양/현상을 디자인하는 것
	- 절차적 프로그래밍(Procedural Programming)으로서 비교적 적은 양의 데이터로 복잡한 형태를 재현할 수 있음
	- 자연계에서 보이는 복잡한 형태나 형상으로부터 규칙을 찾아내고, 이를 재현할 수 있음
- 알고리즘 디자인의 시작 : 건축 디자인으로부터 시작됨
	- 활용 케이스 1 : Greg Lynn이 생체 유기적인 건축 디자인을 구축하기 위해 알고리즘 디자인을 활용함
	- 활용 케이스 2 : Kostas Terzdis가 형태에 국한되지 않는 건축 디자인을 구축하기 위해 알고리즘 디자인을 활용함
- 알고리즘 디자인의 범주
	- 특정 자연 현상을 재현하기 위해 필요한 시뮬레이션 알고리즘 데이터 생성
	- 지형을 만들 때 산맥, 강, 그리고 숲 등의 관계를 설정하여 다양한 패턴 구축
- 알고리즘 디자인의 흥행 : Siggraph에서 수많은 알고리즘이 발표되고 있음

### 디자인 모티브를 찾는 방법
#### 모티브
- 자연 현상
	- 물의 파장
	- 지표면의 균열
	- 생물의 골격
	- 껍질의 모양
	- 식물의 줄기
	- 산맥의 형태
- 자연 현상을 변형한 기하학적 도형

#### 저자의 모티브 찾기 프로세스
- 무엇을 만들까?
	- 시작점 옵션 1 : 이미지
		- 책
			- 과학계
			- 자연 사진집
		- 인터넷
			- 이미지
				- Pinterest
			- 동영상
				- 과학계열 채널
				- Youtube
	- 시작점 옵션 2 : 알고리즘
		- Siggraph 논문
		- Wikipedia

### 알고리즘을 찾는 방법
- SIGGRAPH 와 같은 컴퓨터 그래픽 관련 컨퍼런스/협회에서 발표된 논문 참고
- [Ke-Sen Huang](https://kesen.realtimerendering.com/) 웹사이트에 정리된 컴퓨터 그래픽 분야 논문 참고
- [Computer Graphics Algorithms 관련 위키피디아 참고](https://en.wikipedia.org/wiki/Category:Computer_graphics_algorithms)
- 마음에 드는 자연 현상을 찾은 경우, 이러한 자연 현상의 영어 이름에 "Algorithm"을 추가해서 인터넷 검색
	- 예시 : [Brain Coral](https://en.wikipedia.org/wiki/Brain_coral) (뇌같이 생긴 산호, "뇌 산호")의 형태를 재현하는 알고리즘을 찾기 위해 "Brain Coral Algorithm"을 검색하면 다양한 논문과 포럼이 나옴; 이러한 결과에서 핵심이 되는 키워드를 찾을 수 있음
		- ![[Pasted image 20230416213826.jpg|200]]
		- 여기서 핵심적인 키워드는 **Differential Growth** 임. 이어서 이 키워드만 검색해보면 Differential Line Growth, Differential Mesh Growth 등 디자인 관련된 검색 결과가 나옴
			- #개인노트 저자가 올린 유투브 영상도 검색 결과에 나왔음
				- [Houdini Algorithmic Live 053 - Differential Growth with Vellum Part 1 | Junichiro Horikawa | Youtube](https://www.youtube.com/live/tcckNTS9-Os?feature=share)
				- [Houdini Tutorial 0008 Coral Growth (Slow ver.) | Junichiro Horikawa | Youtube](https://youtu.be/l-rt4jSkhPE)
			- #개인노트 SideFX 갤러리에 Differential Line Growth를 재현한 작품이 있음 - [링크](https://www.sidefx.com/gallery/differential-line-growth/)
				- ![[Pasted image 20230416214032.jpg|200]]
				- 후디니에서 작업하고 [[cinema_4d|C4D]] + [[octane_render|Octane]] 으로 마무리 했다고 함
			- #개인노트 Differential Line Growth - The Quick Way - [Blog Post](https://entagma.com/differential-line-growth/), [Youtube Video](https://youtu.be/SOk5qVXrFQA)
				- ![[Pasted image 20230416215116.jpg|200]]
			- #개인노트 free HDRI from GiantCowFilms - [link](https://giantcowfilms.com/category/hdris/)
			- #개인노트 [ODFORCE](https://forums.odforce.net/) - forum for Houdini users?
			- #개인노트 Differential Growth 은 Differential Evolution 에서 비롯된 디자인 용어인 듯 함.
				- #개인노트 [Differential Evolution | wiki](https://en.wikipedia.org/wiki/Differential_evolution) : a method that optimizes a problem by iteratively trying to improve a candidate solution with regard to a given measure of quality.
					- #개인노트 Differential Evolution is a type of Evolutionary Algorithm
						- #개인노트 [Evolutionary Algorithm | wiki](https://en.wikipedia.org/wiki/Evolutionary_algorithm) : a generic population-based metaheuristic optimization algorithm.
							- #개인노트 Evolutionary Algorithm is a subset of Evolutionary Computation
								- #개인노트 [Evolutionary Computation | wiki](https://en.wikipedia.org/wiki/Evolutionary_computation) : a subfield of AI and Soft Computing that involves developing global optimization algorithms inspired by biological evolution; these algorithms are a family of population-based trial-and-error problem solvers with a metaheuristic or stochastic optimization character.
							- #개인노트 [Metaheuristic | wiki](https://en.wikipedia.org/wiki/Metaheuristic) : a higher-level procedure or heuristic designed to find, generate, tune, or select a heuristic (partial search algorithm) that may provide a sufficiently good solution to an optimization problem or a machine learning problem; especially with incomplete or imperfect information or limited computation capacity.
			- #개인노트 Differential Growth 대신 Reaction Diffusion 이란 용어를 사용하는 경우가 있음
				- #개인노트 [Reaction Diffusion on Triangular Mesh | grasshopper3d.com](https://www.grasshopper3d.com/forum/topics/reaction-diffusion-on-triangular-mesh)
					- ![[Pasted image 20230416223128.png]]
				- #개인노트 [Reaction-Diffusion Systems | wiki](https://en.wikipedia.org/wiki/Reaction%E2%80%93diffusion_system) : mathematical models which correspond to several physical phenomena
					- e.g. The change in space and time of the concentration of one or more chemical substances: local chemical reactions in which the substances are transformed into each other, and diffusion which causes the substances to spread out over a surface in space.
						- A simulation of two virtual chemicals reacting and diffusing on a Torus using [the Gray-Scott model](https://groups.csail.mit.edu/mac/projects/amorphous/GrayScott/)
							- ![[Reaction-Diffusion.gif|150]]
					- #개인노트 [Diffusion | wiki](https://en.wikipedia.org/wiki/Diffusion) : the net movement of anything (e.g. atoms, ions, molecules, energy) generally from a region of higher concentration to a region of lower concentration.
			- #개인노트 P5.js 로 구현한 Differential Growth - [링크](https://www.kaspar.wtf/blog/differential-growth)

### 알고리즘의 이해
- 논문 찾아보고, 설명 영상 찾아보고, 코드 찾아보고.. 그리고 수학 공부할 것!

### 후디니로 알고리즘 구현
- 알고리즘은 계산 횟수를 기준으로 두 가지로 구분됨; 한번 계산으로 끝나는지, 또는 여러 번 계산해야 끝나는지.
- 알고리즘은 계산 순서를 기준으로 두 가지로 구분됨; 계산을 매번 새로 하는 것인지, 또는 한번에 모두 계산되는지.
- 시간 축을 따라 계산하며 형태의 변화를 애니메이션으로 보여 주고 싶은 알고리즘을 구현하기 위해서, 후디니에서 "SOP Solver"라는 타임라인 기반 시뮬레이션을 자체적으로 만들 수 있는 노드 네트워크를 사용해야 함
- 시간 축에 관계 없이 곧바로 최종적인 알고리즘을 구현하기 위해서, (SOP Solver 대신) 단일 프레임 내에서 계산이 끝나는 For-Each 노드로 Loop 중심의 네트워크를 사용
- 알고리즘을 구현하기 위해 어떤 방법을 선택하더라도 , 알고리즘 디자인을 구현할 때는 Wrangle 노드라고 부르는 VEX 언어 노드를 사용해야 함

## 알고리즘 디자인을 위한 후디니 기초 지식
**목차**
1. 파라미터의 등록
2. 속성의 기초
3. VEX의 기초
4. Expression 함수의 기초
5. For-Each 노드의 기초
6. Solver 노드의 기초

## 파라미터 등록
- 각 노드에는 노드의 여러 옵션을 변경할 수 있는 파라미터가 있음
- 각 노드에서 파라미터를 직접 입력하고 제어할 수 있지만, `Null` 노드로서 파라미터를 제어할 수 있도록 함으로서 작업할 때 좀 더 편리하게 할 수 있음; 더불어, 이러한 "파라미터" 노드에 색을 부여함으로 좀 더 시각적으로 쉽게 찾아갈 수 있음

### Sphere 객체 사이즈 조절 Null 노드 생성
1. `Sphere` 노드 생성 (`sphere1`) > `Null` 노드 생성 (`null1`)
	- ![[Pasted image 20230418103408.png]]
2. `null1` 노드 선택 > 기어 아이콘 클릭 > `Edit Parameter Interface` 클릭 > `Create Parameters` :: `Float` 선택 > 오른쪽 화살표 클릭 > `Existing Parameters` :: `Label(newparameter)` 선택 > `Name`, `Label` 변경 (예: `uscale`, `Universal Scale`) > `Apply` & `Accept`
	- ![[Pasted image 20230418103548.png]]
	- ![[Pasted image 20230418103727.png]]
3. `Universal Scale` (새로 생성된 파라미터)의 값 조절 (`0.5`) > `Universal Scale` 우클릭 > `Copy Parameters `클릭
	- ![[Pasted image 20230418103817.png]]
4. `sphere1` 노드 선택 >
	- (opt.1) `Uniform Scale` 우클릭 > `Paste Relative References` 클릭
		- ![[Pasted image 20230418103942.png]]
	- (opt.2) `Uniform Scale` 값에 `ch("../null1/uscale")` 입력
		- ![[Pasted image 20230418104023.png]]
5. `null1` 의 파라미터 값을 조정함으로서 `sphere1` 의 크기를 조절할 수 있음

## 속성의 기초
![[houdini_geo_detail.svg]]
- #기본지식 #후디니 도형 객체(**Geometry Object**)를 구성하는 4가지 도형 요소(**Geometry Components**)는 포인트(**Point**), 버텍스(**Vertex**), 프리미티브(**Primitive**), 그리고 정보(**Detail**) 임.
	- #기본지식 #후디니 도형 속성(**Geometry Attributes**)은 각 도형 요소에 들어있는 위치, 색상 등 여러가지의 정보(**Named Values**)를 뜻함.
		- #기본지식 #후디니 **속성 우선권(Attribute Precedence)** : 도형 요소 간에 중복되는 속성은 다음 순서대로 우선권을 갖는다; 버텍스 > 포인트 > 프리미티브 > 디테일
		- #기본지식 #후디니 #레퍼런스 도형 속성(**Geometry Attributes**)에 대한 자세한 정보는 [SideFX 공식 문서](https://www.sidefx.com/docs/houdini/model/attributes.html) 참고
	- #기본지식 #후디니 다른 3D 프로그램과 달리, 후디니는 도형의 꼭지점을 포인트와 버텍스로 나누어 봄; 포인트는 도형 객체가 기준이 된 모든 꼭지점을 뜻하며, 버텍스는 도형 객체의 프리미티브가 기준이 된 모든 꼭지점을 뜻함 - 서로 붙어있는 여러 프리미티브가 동일한 여러 포인트를 공유할 수 있다는 것이고, 버텍스는 각 프리미티브에 상속되는 유일한(유니크한) 꼭지점이라는 것.
	- #기본지식 #후디니 도형 객체의 정보(**Detail**)는 포인트 목록, 프리미티브 목록, 그룹 목록, 그리고 여러 속성을 담고 있음

## VEX의 기초
- `VEX` 는 후디니에서 사용하는 스크립트 언어 중 하나
	- 일반 노드보다 계산이 빠르다는 것이 특징이며, 다양한 방식으로 후디니의 기능을 확장시킬 수 있음
	- 모델링 부분에서 필수로 사용될 것 임
- `Wrangle` 노드는 `VEX` 를 작성할 수 있는 노드임
	- 모델링을 하는 SOP 네트워크 안에서 도형 요소(포인트, 프리미티브 등)에 따라 다른 `Wrangle` 을 구분하여 사용할 것임
	- 기본 노드만으로는 실현하기 어려운 모델링을 손쉽게 해줌
	- 자주 사용되는 4가지 `Wrangle` 노드
		- `Point Wrangle`
		- `Primitive Wrangle`
		- `Vertex Wrangle`
		- `Volume Wrangle`
- `VOP` 노드로도 `VEX + Wrangle` 의 기능을 재현할 수 있지만, 다음과 같은 이유로 `VEX + Wrangle` 을 사용함
	- `VOP` 으로 만들면 복잡해지고 가독성이 떨어짐
	- `VOP` 로 루프(`Loop`)와 조건부 분기(`Conditional Branch`)를 구현하기 귀찮음
	- ~~VOP에서 오류가 발생하면 디버깅이 어렵다?~~
- `VEX` 에서 변수(`Variable`)는 정해진 데이터 타입(int, float 등)의 값을 넣을 수 있는 컨테이너와 같은 것임
	- 정해진 형식은 다음과 같음
		- `INT`
		- `FLOAT`
		- `VECTOR`
		- `MATRIX`
		- `STRING`
	- 변수 사용 예시
		- `int a = 123;`
		- `float b = 10.25;`
		- `vector c = set(1,2,3); // a vector containing a set of integer values`
		- `matrix d = ident(); // matrix variable d with its value as an identity matrix`
		- `string e = "abc";`
- `VEX` 에서 배열(`Array`)은 동일한 타입의 데이터를 저장하는 컨테이너임
	- 배열 사용 예시
		- `int a [] = {1,2,3}; // array variable containing integers 1,2,3`
		- `push(a, 4); // inserting an integer 4 into an array`
		- `pop(a, 1); // removing a 2nd value from an array`
		- `int size = len(a); // length of an array`
- `VEX` 에서 함수(`Function`)도 있음
	- 자주 사용하는 함수
		- `point()` : 포인트의 속성을 얻기 위한 함수
		- `setpointattrib()` : 포인트의 속성을 설정하는 함수
		- `addpoint(int geohandle, int point_number | vector pos)` : 포인트를 추가하는 함수
			- `geohandle` : 함수가 작업할 대상이 되는 도형(의 핸들); 0는 `geoself` (현재 노드가 속한 도형)을 뜻함
			- `point_number` : 정수형 값이 들어오면, 새로 생성할 포인트가 해당 포인트 번호를 가진 포인트의 속성을 그대로 가지고 생성됨
			- `pos` : 벡터형 값이 들어오면, 지정된 좌표값에 포인트가 생성됨
			- `int pt = addpoint(0, set(1,2,3));`
				- 좌표 1,2,3 에 포인트를 추가하고 (성공시) 포인트 번호(Point Number)를 반환함
			- [addpoint VEX function | SideFX](https://www.sidefx.com/docs/houdini/vex/functions/addpoint.html)
		- `npoints()` : 전체 포인트의 개수를 반환하는 함수
		- `chf()` : 지정된 float 속성의 값을 반환하는 함수
	- #개인노트 [List of VEX Functions | SideFX](https://www.sidefx.com/docs/houdini/vex/functions/index.html)
- 

## Expression 함수의 기초

## For-Each 노드의 기초

## Solver 노드의 기초