# Toon Shader 만들기 - Evans Bohl
https://youtu.be/mzydOmgN7mc

ue5_20230605

![[Pasted image 20230608174454.png|500]]

여기서 구현하려는 Toon 의 특징은 "밝은 영역과 어두운 영역이 (부드러운 Gradient 대신에) 명확하게 구분이 된다"는 것.

이 특징을 구현하기 위해서는 필요한 작업:
1. 라이팅 추출
2. 라이팅 매핑
3. 색상 복구

추가적으로 지정된 객체에만 Toon Shading 이 적용될 수 있도록 설정해줘야 함.

## 라이팅 추출
화면에 그려지는 장면은 색상과 라이팅이 이미 적용된 것이기 때문에, 화면에 그려지기 전의 색상만 따로 가져와서 화면에 그려진 결과물에서 색상을 빼면 라이팅만 따로 추출이 가능함 (아쉽게도 라이팅 정보만 따로 주는 것은 없는 듯).

### 후반 처리 재질 생성
- Material 생성 (PP_ToonShader) > 노드 edit > Material :: Material Domain : PostProcess
	- ![[Pasted image 20230612142024.png|300]]

> [!info] Post Process Material
> [Post Process Material](https://docs.unrealengine.com/4.27/en-US/RenderingAndGraphics/PostProcessEffects/PostProcessMaterials/) 은 화면이 일차적으로 한 번 렌더링 된 후에 적용됨. 인풋/아웃풋이 Emissive Color 만 있으며, 효과는 마치 카메라 앞에 필터를 넣는 것 같음. Toon Shading 은 이러한 기능을 활용하여 일차적으로 그려진 라이팅/그림자/색상을 변형시켜 만화처럼 변환하는 것임.
> ![[o86ahy0p.bmp]]

- SceneTexture 노드 생성 > Scene Texture Id : PostProcessInput0

> [!info] SceneTexture: PostProcessInput0
> SceneTexture 노드는 화면에 있는 정보를 호출해올 수 있는 노드임. 이 노드에서 PostProcessInput0 를 선택하면 화면에 그려지는 모든 정보를 그대로 가져옴.

### 회색 변환 및 1차 결과 확인
- Desaturation 노드 생성 > SceneTexture 노드 Color 아웃풋 --> Desaturation 노드 1번 인풋 > Desaturation 노드 아웃풋 --> PP_ToonShader 노드 Emissive Color 인풋
- PP_ToonShader 노드 > Post Process Material :: Blendable Location : Before Tonemapping
	- #todo 정확히 이게 무엇을 하는지 모르겠음; 일단 화면이 지글거리는 현상을 방지한다는 것으로만 설명됨.
- PP_ToonShader 노드 instance 생성 (PPI_ToonShader)
- Place Actors > Volumes > PostProcessVoume 생성
- PostProcessVoume > Post Process Materials > + > Choose : Asset Reference > PPI_ToonShader 선택
- (opt) PostProcessVoume > Infinite Extent (Unbound) 활성화

> [!info] Post Process Material & Volume
> Post Process Material 은 PostProcessVolume 영역 이내에서만 렌더가 됨. PostProcessVolume 의 영역을 infinite 로 설정해서 화면에 보이는 모든것에 PP 재질이 적용되게 할 수 있으며, 반대로 infinite 이 아닌 바운더리 박스 안에 카메라가 들어가서 보이는 것에만 적용되게 할 수도 있음.
> 모든 영역(infinite)에 적용하되 특정 객체에만 PP 재질이 적용되게 하는 방법은 CustomDepth 를 사용해야 되는데, 이 것은 나중에 좀 더 설명될 것임.

- 결과 확인
	- ![[Pasted image 20230612150432.png|500]] (전)
	- ![[Pasted image 20230612150454.png|500]] (후)

### 색상 차감을 통한 라이팅 값 추출
- PP_ToonShader 노드 > Edit > SceneTexture 노드 생성 > Scene Texture Id : BaseColor (as stored in GBuffer)
- SceneTexture: BaseColor 노드 Color 아웃풋 --> PP_ToonShader 노드 Emissive Color 인풋 > 결과 확인
	- ![[Pasted image 20230612151549.png|500]]

> [!info] GBuffer
> GBuffer 는 라이팅이 적용되기 전의 Base Color, Specular Color, Roughness 등의 텍스쳐 정보와 Normal, Depth 와 같은 객체 속성 값을 저장하는 버퍼임. Post Processing 단계에서 GBuffer 안에 있는 값을 호출해서 사용할 수 있음.

- Desaturation 노드 생성 > 첫번째 인풋을 SceneTexture: BaseColor 노드 Color 아웃풋에 연결 > PP_ToonShader 노드에 연결해서 결과 확인
	- ![[Pasted image 20230612152954.png|500]]
- Divide 노드 생성 > Desaturation 1 아웃풋 --> A 인풋, Desaturation 2 아웃풋 --> B 인풋
- 결과 확인
	- ![[Pasted image 20230612153836.png|500]]

### 노드 에디터 - 라이팅 추출 부분
![[Pasted image 20230612160901.png]]

## 라이팅 전환점 정의
어두운/밝은 영역이 명확하게 구분될 수 있도록 해줌; 두 영역을 나누는 전환점을 정의하고, 전환점에서 변환되는 부분을 부드럽게 해줌.

예를 들어, 밝기가 0~1 값으로 표현된다면, 0.4 이하는 어두운 색 (고정), 0.6 이상은 밝은 색 (고정), 0.4 ~ 0.6 사이는 부드럽게 이어질 수 있도록 Step 연산을 해줌.

### Black & White 변환 / 전환점 생성
- Saturate 노드 생성 > 인풋 --> Divide 노드 아웃풋
	- 0 미만 값은 0, 1 초과 값은 1, 0~1 사이 값은 그대로 전달됨
-  ComponentMask (R) 노드 생성 > 인풋 --> Divide 노드 아웃풋
	- 회색 RGB 에서 R 채널만 가져옴
- Smooth Step 노드 생성 > Value 인풋 --> Mask (R) 노드 아웃풋
- SmoothStep 노드에 Min 값을 0.4, Max 값을 0.6 으로 설정하고 결과 확인
	- ![[Pasted image 20230612163204.png|500]]

#### Min/Max 값 조절 설정
- ScalarParameter 노드 생성 > 이름 "Light Shadow Threshold" > Default Value 값 0.5
	- 사용자가 지정할 수 있는 전환점 변수
- ScalarParameter 노드 생성 > 이름 "Light Shadow Transition Size" > Default Value 값 0.2
	- 사용자가 지정할 수 있는 전환점 변환 범위 변수 (이 범위 내에 Step 연산이 이루어짐)
- Multiply 노드 생성 > A 인풋 <-- Light Shadow Transition Size 노드, B 인풋 <-- 0.5 값 노드
- Subtract 노드 생성 > A 인풋 <-- Light Shadow Treshold 노드, B 인풋 <-- Multiply 노드
- Add 노드 생성 > ^ 위에 작업 반복
- SmoothStep 노드 > Min 인풋 <-- Subtract 노드, Max 인풋 <-- Add 노드
- SmoothStep 노드 아웃풋 --> PP_ToonShader 노드 EmissionColor > 결과 확인
	- 화면에 아무런 변경이 없음
- PPI_ToonShader 에서 두 개의 파라미터가 새로 생긴 것을 확인
	- ![[Pasted image 20230612164627.png]]

### 노드 에디터 - 라이팅 전환 부분
![[Pasted image 20230612164948.png]]

## 영역별 색상 지정 / Tint
밝은 영역에 고정 색, 어두운 영역에 고정 색을 적용해줌.

- LinearInterpolation(Lerp) 노드 생성 > Alpha 인풋 <-- SmoothStep 노드 아웃풋
- VectorParameter 노드 생성 (Shadow Tint) > 어두운 영역 색상 지정 > Color 아웃풋 --> Lerp 노드 A 인풋
- VectorParameter 노드 생성 (Light Tint) --> 밝은 영역 색상 지정 > Color 아웃풋 --> Lerp 노드 B 인풋
- Lerp 노드 아웃풋 --> PP_ToonShader 노드 Emissive Color 인풋 > 결과 확인
	- ![[Pasted image 20230612165639.png|500]]
- 좀 더 재밌는 색상을 지정해서 재밌는 효과를 줄 수 있음
	- ![[Pasted image 20230612165500.png|500]]

### 노드 에디터 - Tint 색상 부분
![[Pasted image 20230612170132.png]]

## 프로젝트 설정 - 지글 현상 제거
일반적인 프로젝트 설정은 Toon Shading 을 위한 것이 아니기 때문에, Toon Shading 을 하다 보면 화면에 깨지거나 지글거리는 현상이 생길 수 있음.

- Edit > Project Settings > Engine :: Rendering > Global Illumination :: Dynamic Global Illumination Method : None > Reflections :: Reflection Method : None

> [!important] 주의사항
> GI, Reflection 등 프로젝트 설정을 변경하는 작업은 해당 장면 외에 다른 장면에도 영향을 주기 때문에 조심해서 사용할 것. 별도로 따로 Actor 에 적용하는 방법은 나중에 설명된다고 함.

## 색상 복구
색상을 복구하여 라이팅에 다시 합쳐줌.

### 색상 호출 및 블렌딩
- SceneTexture (GBuffer BaseColor) 노드 생성 > ComponentMask (RGB) 생성 및 연결
	- 변형된 라이팅 값이 현재 Lerp 노드 아웃풋으로 출력되며, 해당 값이 RGB 임; 이 값과 색상 값 (RGBA) 를 합쳐주려면 Mask 노드로 RGB 만 분리해야 함.
- Multiply 노드 생성 > A 인풋 --> Lerp 노드 아웃풋, B 인풋 --> Mask 노드 아웃풋
- Multiply 노드 아웃풋 --> PP_ToneShader 노드 > 결과 확인
	- ![[Pasted image 20230612172104.png|500]]

### 라이팅 색상 복구
> [!info] 라이팅 색상?
> 일반적으로 라이팅은 하얀색~검은색으로 표현되는 밝기라고 생각되는데, Unreal Engine 에서 밝기는 재질 자체의 색상에 빛의 색상이 블렌딩 된 것으로 이해하면 됨.
> 이전에 라이팅을 Greyscale 로 변환했기 때문에, 라이팅의 색상 정보가 제거되었음. 재질 색상을 블렌딩 하여도 라이팅 색상은 복구되지 않음으로, 색상이 있는 라이트(Point Light, Sky Light 등)가 제대로 반영되지 않음.

- SceneTexture (PostProcessInput0) 노드 생성
- Multiply 노드 생성 > B 인풋 승격 ("Base Render Blend Amount") > Default Value 0.5 설정
- 파라미터 노드 아웃풋 --> Multiply 노드 B 인풋
- SceneTexture (PostProcessInput0) 노드 Color 아웃풋 --> Multiply 노드 A 인풋
- Add 노드 생성 > A 인풋 --> SceneTexture (PostProcessInput0) 노드 Color 아웃풋, B 인풋 -->  SceneTexture (GBuffer BaseColor) 노드 Color 아웃풋
- Add 노드 아웃풋 --> Mask (RGB) 노드 인풋
- Multiply 노드 생성 > B 인풋 --> Mask (RGB) 노드 아웃풋, A 인풋 --> Lerp 노드 아웃풋
- Multiply 노드 아웃풋 --> PP_ToonShader 노드 연결 > 결과 확인
	- ![[Pasted image 20230612173816.png|500]] (원본)
	- ![[Pasted image 20230612173845.png|500]] (Toon Shading 적용)

### 노드 에디터 - 색상 복구 부분
![[Pasted image 20230612180305.png]]

## 거리 기준 대상 선별
하늘 텍스쳐는 Toon Shading 에서 제외하며, 이를 구현하기 위해 임의의 먼 거리를 기준으로 Toon Shading 영역 / 일반 영역 구분을 해줌.

- Linear Interpolation (Lerp) 노드 생성 > A 인풋 --> Multiply 노드 아웃풋
	- Lerp 노드 Alpha 값이 0 이면 Toon Shading 이 적용됨
- SceneTexture: PostProcessInput0 노드 생성
	- Component Mask (RGB) 노드 생성 > ST: PPI0 노드 Color 아웃풋 --> Mask 노드 인풋 > Mask 노드 아웃풋 --> Lerp 노드 B 인풋
		- Lerp 노드 Alpha 값이 1 이면 Toon Shading 이 적용되지 않은 일반 장면이 구현됨
- Step 노드 생성 > Y 인풋 승격 > 이름 "Effect Max Distance" > Default Value 값 500,000
- Scene Depth 노드 생성 > 아웃풋 --> Step 노드 X 인풋
	- Scene Depth 는 장면에 그려지는 픽셀(?)의 거리 정보를 호출해줌
- Step 노드 아웃풋 --> Lerp 노드 Alpha 인풋
	- Scene Depth 값이 500,000 을 넘으면 Step 노드는 1 을 리턴함
- Lerp 노드 아웃풋 -->  PP_ToonShader 노드 인풋 > 결과 확인
	- ![[Pasted image 20230612182520.png|500]]
	- 하늘이 원래 라이팅/색을 유지하는 것을 확인

### 노드 에디터 - 거리 기준 대상 선별 부분
![[Pasted image 20230612182707.png]]

## Custom Depth 속성 기준 대상 선별
PostProcessingVolume 영역 안에 있는 객체 중 일부에만 Toon Shading 을 적용할 수 있도록 할 수 있으며, 이는 Custom Depth 라는 속성을 사용해서 구현함.

- Toon Shading 을 적용할 모델 > 디테일 :: Advanced :: Render CustomDepth Pass 옵션 활성화
	- ![[Pasted image 20230608193229.png|300]]
- SceneTexture: PostProcessInput0 노드 생성
- Component Mask (RGB) 노드 생성 > 인풋 --> ST: PPI0 노드 Color 아웃풋
- Linear Interpolation (Lerp) 노드 생성 > A 인풋 --> Mask (RGB) 노드 아웃풋
- SceneTexture: CustomDepth 노드 생성
	- 장면의 픽셀(?)이 CustomDepth 에 해당되는 경우 거리를 반환하는데, 해당되지 않은 경우 아주 큰 거리를 반환함;
- Component Mask (R) 노드 생성 > 인풋 --> ST: CD 노드 Color 아웃풋
- Step 노드 생성 > Y 인풋 값 500,000 지정
	- Custom Depth 에 해당되지 않는 경우 리턴되는 아주 큰 값이 500,000 보다 크면 Step 노드는 1 을 리턴함.
- Step 노드 X 인풋 --> Mask (R) 노드 아웃풋
	- Custom Depth 에 해당되며 거리가 500,000 이내에 있는 경우 Step 노드는 0 을 리턴함.
- One Minus (1-x) 노드 생성 > 인풋 --> Step 노드 아웃풋
	- Lerp 노드의 A 인풋은 Custom Depth 에 해당되지 않는 경우, B 인풋은 해당되는 경우로 지정할 것임. 따라서, Custom Depth 가 적용되는 부분은 Step 노드에서 0 을 리턴할 것이며, 1-x 연산으로 0 을 1 로 변환하는 것임.
- 1-x 노드 아웃풋 --> Lerp 노드 Alpha 인풋
- 거리 기준 대상 선별 (하늘 제외) 그룹에 Lerp 노드 아웃풋 --> Lerp 노드 B 인풋
- Lerp 노드 아웃풋 --> PP_ToonShader 노드 인풋 > 결과 확인 (오른쪽 Custom Depth 적용)
	- ![[Pasted image 20230612191521.png|500]]

### 노드 에디터 - Custom Depth 부분
![[Pasted image 20230612212504.png]]

참고로 Step + One Minus 조합 대신 if 노드를 사용할 수 있음. 개인적으로 if 노드가 의도를 잘 보이는 듯함.
![[Pasted image 20230612203803.png|600]]

## Custom Depth 겹치는 문제 해결
Custom Depth가 적용된 객체가 적용되지 않은 객체 뒤에 있는 경우 겹쳐서 보이는 문제가 있음.

![[Pasted image 20230612203948.png|500]] (예시)

이러한 문제는 Scene Depth 값과 Custom Depth 값을 비교해서 해결할 수 있음.

- Scene Depth 노드 생성
- Component Mask (R) 노드 생성
- if 노드 생성
	- ST: CustomDepth 노드에 연결된 Mask (R) 노드 아웃풋 --> if 노드 A 인풋
	- Scene Depth 노드에 연결된 Mask (R) 노드 아웃풋 --> if 노드 B 인풋
	- if 노드 A > B 인풋 --> 0
	- if 노드 A == B 인풋 & A < B 인풋 --> 1
- Multiply 노드 생성
	- Custom Depth 쪽 if 노드 (또는 1-x 노드) 아웃풋 --> Multiply 노드 A 인풋
	- Scene Depth 쪽 if 노드 아웃풋 --> Multiply 노드 B 인풋
- Multiply 노드 아웃풋 --> 제일 마지막 Lerp 노드 Alpha 인풋
- 결과 확인
	- ![[Pasted image 20230612210726.png|500]]

### 노드 에디터 - 겹치기 문제 해결 부분
![[Pasted image 20230612210847.png]]

## Custom Depth 스위치 생성
Custom Depth 처리하는 부분을 On/Off 하는 스위치를 추가해줌 - Toon Shading 전체 적용 vs. Custom Depth 객체에만 적용.

- 거리 기준 대상 선별 부분과 Custom Depth 기준 대상 선별 부분의 순서를 우선 바꿔줘야 함
	- ![[Pasted image 20230612212902.png|500]] (전)
	- ![[Pasted image 20230612213044.png|500]] (후)
- Custom Depth 처리 부분, 하늘 제외 처리 부분 사이에 StaticSwitchParamter 노드 생성 > 이름 "Custom Depth Buffer"
- SSP 노드 True 인풋 --> Custom Depth 처리 부분 Lerp 노드 아웃풋
- Custom Depth 처리 부분 Lerp 노드 B 인풋으로 들어오는 값 (Multiply 노드 아웃풋) 에 Reroute 추가 > SSP 노드 False 인풋 --> Reroute
- SSP 노드 아웃풋 --> 하늘 제외 처리 부분 Lerp 노드 A 인풋
- SSP 노드 기본 값 True/False 스위치 해보면서 결과 확인
	- ![[Pasted image 20230612214149.png|500]] (True)
	- ![[Pasted image 20230612214202.png | 500]] (False)

### 노드 에디터 - Custom Depth 스위치 부분
![[Pasted image 20230612214326.png]]