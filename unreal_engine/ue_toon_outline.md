# Toon Outline 만들기 - Evans Bohl
https://youtu.be/9KvUfnrHcqM

ue5_202306

만화(Toon)처럼 모델에 외각선을 그려주는 Post Processing Material 을 만들어 줄거임.

## 관련 내용
- [[ue_toon_shading]] : Post Processing 방식으로 툰 셰이딩 하는 방법

## 원리
모서리 감지(Edge Detection)는 컴퓨터 비전 분야에 많이 연구되고 있는 알고리즘 중 하나임.

단순한 모서리 감지 알고리즘은 각 픽셀마다 해당 픽셀(가운데)의 좌/우/상/하 픽셀의 값을 가져와서 해당 픽셀의 값과 비교하여, 차이(Variation)가 임의의 값(Threshold)보다 큰 경우에 해당 부분을 모서리로 취급하는 원리로 작동함.

$V = |(D_{left} + D_{right} + D_{up} + D_{down}) - 4 * D_{center}|$

여기서 픽셀의 "값"은 색, 거리, 노멀 등이 사용될 수 있음.

![[Pasted image 20230614122735.png|500]]
![[Pasted image 20230614123538.png]]
(왼쪽: Var = 0, 오른쪽: Var = 1000)

각 픽셀과 해당 픽셀의 좌우상하 픽셀을 하나의 커널(Kernel)이라고 부름.

일반적으로 2D 환경에서는 모서리 감지/객체 감지 알고리즘을 구현할 때 색 정보를 사용하지만, 3D 환경에서는 픽셀과 카메라 사이의 거리가 사용됨.

거리에 더불어 노멀도 같이 사용하여 좀 더 알고리즘을 보강함 - 단순한 거리 기준 모서리 감지는 객체 자체에 있는 모서리를 감지하지 못 하는 경우가 있기 때문.

![[Pasted image 20230619102117.png|300]] (거리 기준 모서리 감지)
![[Pasted image 20230619102343.png]]
![[Pasted image 20230619102430.png|300]] (노멀 기준 모서리 감지)
![[Pasted image 20230619102446.png|300]] (거리 + 노멀 기준 모서리 감지)


## Post Processing 설정
- Material 생성 > 이름 "PP_OutlineShader"
- PP_OutlineShader > Material Edit >
	- Details > Material :: Material Domain : Post Process
	- Details > Post Process Material :: Blendable Location : Before Tonemapping
- PP_OutlineShader > RMB > Create Material Instance > 이름 "PPI_OutlineShader"
- PostProcessVolume 생성 > Details >
	- Post Process Materials :: Array Elements : + Button 클릭 > 목록에서 PPI_OutlineShader 선택
		- ![[Pasted image 20230613194544.png]]
	- Post Process Volume Settings :: Infinite Extent (Unbound) 옵션 활성화

## Kernel 함수 재작
- Material Function 생성 > 이름 "MF_GetKernel" > MF_GetKernel > Material Edit

### 아웃풋 준비
가운데 픽셀과 좌우상하 픽셀들의 위치 값을 리턴할 수 있도록 준비

- Output Result 노드 > Output Name : Center
- Output Center (Result) 노드 복붙 x 4
	- Output Name 값을 Left, Right, Up, Down 순서대로 변경
	- Sort Priority 값을 1, 2, 3, 4 순서대로 변경

### 인풋 준비
가로(Horizontal) 좌표 오프셋 (1,0 과 -1,0), 세로(Vertical) 좌표 오프셋 (0,1 과 0,-1) 으로 좌우상하 픽셀을 잡을 수 있도록 하며, 인풋으로 받은 값으로 위치 오프셋을 곱할 수 있도록 함.

- FunctionInput 노드 생성 > Input Name : Width, Input Type : Function Input Scalar
	- Preview 인풋 Constant (값 1) 노드 생성 및 연결
- 인풋 값에 줄 좌우, 상하 오프셋을 입력하도록 설정
	- Constant2Vector 노드 생성 x2
		- Desc : Horizontal Offset, R 1, G 0
		- Desc : Vertical Offset, R 0, G 1
- Multiply 노드 생성 x2
	- 각 Multiply 노드의 A 인풋에 Constant2Vector 노드 연결
	- 각 Multiply 노드의 B 인풋에 Input Width (Scalar) 노드 연결

### 픽셀 정보 호출
좌표 단위 값으로 사용할 픽셀 사이즈 호출

- SceneTexelSize 노드 생성 (화면에서의 픽셀 사이즈를 호출함)

### 인풋 값 처리 및 아웃풋 연결
좌우상하 픽셀의 위치를 리턴하기 위해 인풋 - 픽셀 사이즈 - 아웃풋 연결

- 인풋 부분에 각 Multiply 노드에 새로 Multiply 노드 생성해서 A 인풋에 연결
- 새로 생성한 Multiply 노드들의 B 인풋에 SceneTexelSize 노드 아웃풋 연결
- Multiply 노드 새로 생성 x2 > A 인풋 값 -1 로 설정 > B 인풋 값 이전 Multiply 노드에 연결
- TextureCoordinate 노드 생성
- Add 노드 4개 생성 > 각 노드의 A 인풋을 TexCoord 노드 아웃풋에 연결
- 각 Add 노드의 아웃풋을 각 Output 노드 (Left, Right, Up, Down) 에 연결
- TexCoord 노드 아웃풋을 Output (Center) 노드에 연결
- 각 Multiply (-1,) 노드를 각 Output Left, Up 노드에 연결된 Add 노드 B 인풋에 연결
- SceneTexelSize 노드에 연결된 각 Multiply 의 아웃풋을 각 Output Right, Down 노드에 연결된 Add 노드 B 인풋에 연결

### 노드 에디터 - MF_GetKernel
![[Pasted image 20230619102708.png]]

## 거리 기반 모서리 감지 함수 재작
MF_GetKernel 로 커널 픽셀 위치들을 가져오고, 각 픽셀의 거리(깊이) 정보를 호출 한 후 거리 기반 모서리 감지 알고리즘을 구현.

- Material Function 생성 > 이름 "MF_DetectEdges_Depth" > MF_DetectEdges_Depth > Material Edit

### 커널 준비
- FunctionInput 노드 생성 > Input Name : Thickness, Input Type : Function Input Scalar
	- Preview 인풋 값 Constant 노드 (1)
- MF_GetKernel 함수 노드 Drag & Drop > 인풋을 Input Thickness (Scalar) 아웃풋에 연결

### 거리 값 호출
- SceneDepth 노드 5개 생성
	- 각 UVs 인풋을 각 MF_GetKernel 아웃풋에 연결

### 알고리즘 구현
가운데 픽셀의 거리 값(x4)과 좌우상하 픽셀의 거리 값의 합의 차이(Variation)가 특정 값(Threshold) 보다 큰 경우 True, 아닌 경우 False 를 리턴하도록 구현

$V = |(D_{left} + D_{right} + D_{up} + D_{down}) - 4 * D_{center}|$

- Center 노드에 연결된 SceneDepth 노드 아웃풋에 Multiply 4
- Left & Right 노드에 연결된 SceneDepth 노드 아웃풋들을 Add
- Up & Down 노드에 연결된 SD 노드 아웃풋들을 Add
- Left + Right & Up + Down 에 연결된 Add 노드들을 또 Add
- Subtract 노드 생성
	- A 인풋을 좌우상하를 합친 Add 노드 아웃풋에 연결
	- B 인풋을 Center 노드에 연결된 Multiply 노드 아웃풋에 연결
- Subtract 노드 생성 > 위에 생성한 Subtract 노드에 연결된 것처럼, 대신 반대로 연결
- StaticSwitchParameter 노드 생성 x2
	- 각 Subtract 노드 아웃풋을 True 인풋에 연결
	- False 인풋을 Constant (0) 노드 생성 후 연결
	- Parameter Name 속성 값을 Inside / Outside Strokes DO (Depth Output) 으로 각각 지정
- Max 노드 생성 > A 인풋을 Inside Strokes DO 스위치 노드, B 인풋을 Outside 스위치 노드에 연결
- FunctionInput 노드 생성 > Input Name : Threshold, Input Type : Scalar > Preview --> 4
- Step 노드 생성 > Input Threshold (Scalar) 노드 아웃풋을 Y 인풋에 연결, Max 노드 아웃풋을 X 인풋에 연결
- Output Result 노드 인풋에 Step 노드 아웃풋 연결

### 노드 에디터 - MF_DetectEdges_Depth
![[Pasted image 20230619132214.png]]

## 1차 결과 확인
PP_OutlineShader 에 MF_DetectEdges_Depth 넣어줘서 결과를 확인

- PP_OutlineShader > Edit Material > MF_DetectEdges_Depth 드래그&드롭
- MF_DetectEdges_Depth 노드 각 인풋 승격 (Promote Parameter)
	- Threshold 기본값 4
	- Thickness 기본값 2
- Linear Interpolation (Lerp) 노드 생성 > Alpha 인풋 --> MF_DetectEdges_Depth 아웃풋
- SceneTexture:PostProcessInput0 노드 생성 > Color 아웃풋 --> Mask (RGB) 노드 생성 및 연결 > 아웃풋을 Lerp 노드 A 인풋에 연결
- VectorParameter 노드 생성 > 검은색 (0,0,0,0) 설정 > Color 아웃풋 --> Lerp 노드 B 인풋
- Lerp 노드 아웃풋 --> PP_OutlineShader 노드 Emissive Color 인풋
- 결과 확인

![[Pasted image 20230619141914.png]]
![[Pasted image 20230619141931.png]]
![[Pasted image 20230619142116.png]]

### 노드 에디터 - PP_OutlineShader (1차)
![[Pasted image 20230619143027.png]]

## 노멀 기반 모서리 감지 함수 재작
노멀 기반 모서리 감지 알고리즘은 픽셀과 픽셀 사이의 거리를 모두 합한 값이 특정 값(Treshold)를 넘은 경우 모서리임을 감지하는 원리로 작동함.

- Material Function 생성 > 이름 "MF_DetectEdges_Normal" > MF_DetectEdges_Normal > Material Edit
- FunctionInput 노드 생성 > Input Name : Thickness, Input Type : Scalar > Preview 인풋 값 1
- MF_GetKernel 드래그&드롭
- SceneTexture:WorldNormal 5개 생성 > MF_GetKernel 노드 각 아웃풋에 연결
- ST:WN 노드 사이사이에 Distance 노드 생성 및 연결 (총 4개)
- Distance 노드 2개씩 Add 노드 생성 및 연결
- Add 노드 2개를 또 Add > Step 노드 생성 및 X 인풋에 연결
- FunctionInput 노드 생성 > Input Name : Threshold, Input Type : Scalar > Preview 값 1 > Step 노드 Y 인풋에 연결
- Step 노드 아웃풋 --> Output Result 인풋

### 노드 에디터 - MF_DetectEdges_Normal
![[Pasted image 20230619145222.png]]

## 거리 + 노멀
PP_OutlineShader 에 노멀 기반 모서리 감지 함수를 합쳐줌.

- PP_OutlineShader > Edit Material
- MF_DetectEdges_Normal 드래그&드롭
	- Thickness 인풋 승격 및 기본값 1.6
	- Threshold 인풋 승격 및 기본값 1
- Lerp 노드 생성
	- 기존 Lerp 노드의 아웃풋을 새 Lerp 노드 A 인풋에 연결
	- Alpha 인풋에 MF_DetectEdges_Normal 노드 아웃풋 연결
	- VectorParameter 노드 생성 > 검은색 (0,0,0,0) > B 인풋에 연결
- Lerp 노드 아웃풋 --> PP_OutlineShader 노드 Emissive Color 인풋

### 노드 에디터 - PP_OutlineShader (2차)
![[Pasted image 20230619145728.png]]

## 2차 결과 확인
![[Pasted image 20230619145910.png]]

사각형 모델의 모서리에 확실히 선이 생긴 것을 확인할 수 있음; 하지만 모델의 모서리에 Bevel 이 있는 경우 (부드럽게 처리된 경우) 선이 애매하게 생김 (좀 더 확대하면 확실히 이런 문제가 보임).

![[Pasted image 20230619150145.png]]
![[Pasted image 20230619150324.png]]

더불어, 자잘한 디테일이 많은 경우 쓸데없이 선들이 생기는 경향이 있는 듯 함.

![[Pasted image 20230619150423.png]]

## 먼거리 처리 문제 해결
거리 기반 알고리즘의 문제점은 멀리 떨어져 있는 픽셀일 수록 픽셀과 픽셀의 거리 차이가 "크게" 처리된다는 것임; 밑에 이미지를 보면 코너에 선들이 그려져서 큰 어두운 영역이 생긴 것이 보임.

MF_DTM_GrazingAngle
![[Pasted image 20230619155101.png]]

PP_OutlineShader
![[Pasted image 20230619155152.png]]

결과
![[Pasted image 20230619151006.png|500]]
![[Pasted image 20230619154808.png|500]]

## 거리에 따른 선 두께 조절

MF_ThicknessModulation
![[Pasted image 20230619163601.png]]

PP_OutlineShader
![[Pasted image 20230619163717.png]]
![[Pasted image 20230619163638.png]]
![[Pasted image 20230619163655.png]]



![[Pasted image 20230619163539.png]]

## 거리 기준 선 두께 일관성 문제 해결
객체가 거리가 먼 곳과 가까운 곳에 둘 다 겹쳐있는 경우 두께가 너무 차이가 나는 문제가 있음.

![[Pasted image 20230619163840.png]]
![[Pasted image 20230619164007.png]]

해결방법 : 카메라에 가장 가까운 픽셀을 기준으로 선 두께를 선정
![[Pasted image 20230619164041.png]]

MF_ThicknessModulation
![[Pasted image 20230619164732.png]]

결과
![[Pasted image 20230619164918.png]]

## 먼거리 객체 제외
아주 먼거리에 있는 모델에는 외각선이 안 그려지도록 해줌;

MF_Mask_Depth
![[Pasted image 20230619165330.png]]

PP_OutlineShader
![[Pasted image 20230619172234.png]]
![[Pasted image 20230619172200.png]]
![[Pasted image 20230619172215.png]]

결과
![[Pasted image 20230619172253.png]]

## 먼거리 객체 제외로 인한 문제 해결
먼거리 객체 제외로 인해 거리 기준 일관성 문제가 다시 발생함.

![[Pasted image 20230619172453.png]]

MF_Mask_Depth
![[Pasted image 20230619173815.png]]

PP_OutlineShader

MF_Mask_Depth 노드 MaxThickness 인풋을 Thickness Modulation 노드 아웃풋과 연결해줄 것; 거리 기준 처리 부분과 노멀 기준 처리 부분 둘 다;

![[Pasted image 20230619173945.png]]
![[Pasted image 20230619173843.png]]
![[Pasted image 20230619174011.png|500]]

결과
![[Pasted image 20230619174055.png]]

## 나머지 부분
1. Custom Depth
2. Custom Depth 겹치는 문제 해결
3. Stencil Buffer : 객체에 따라 외각선 색상 서로 다르게 설정하는 방법