<mark style="background: #ADCCFFA6;">저자 : 김우빈</mark>
<mark style="background: #FFF3A3A6;">작성 일자 : 2023-04-25</mark>

# Houdini Project 4 : Vivi Ornitier
![[PFF_Vivi.webp]]
![[xi4rshsf.bmp|100]]
[Vivi Ornitier (Final Fantasy)](https://finalfantasy.fandom.com/wiki/Vivi_Ornitier) 캐릭터 모델을 가져와서 수정 후 텍스쳐를 입히고 Karma 렌더러로 영상을 출력해봅니다~

![[vivi_render_v01_1001.png|500]]

## Step 1 : 캐릭터 다운로드
Sketchfab 사이트에 들어가서 Vivi Ornitier 를 검색하면 유저 ChrisLee 가 제작한 모델을 볼 수 있습니다 ([링크](https://sketchfab.com/3d-models/vivi-ornitier-5edb4f4c8a4b47d2a735807f0f4646cc)). `Download 3D Model` 을 눌러서 `fbx` 포맷으로 다운로드하면 됩니다.

![[Pasted image 20230424110419.png|300]]

## Step 2 : 캐릭터 모델 불러오기
1. 네트워크 뷰 패널 > `/obj` > `Geometry` 노드 생성 > 노드 이름 수정 `Vivi_geo` > 들어가기
2. `File` 노드 생성 (`file1`) > `Geometry File` 속성에서 다운로드했던 모델 선택 (`vivi_complete.fbx`)
3. 모델이 너무 크니 사이즈 줄여줌 : `Transform` 노드 생성 (`transform1`) > `Uniform Scale` 속성 `0.01` 로 지정
4. 모델의 위치를 바닥 위에 딱 놓이게 해줌 : `Match Size` 노드 생성 (`matchsize1`) > `Matching` :: `Justify Y` 에 `Center` 로 되어있는 값을 `Min` 으로 수정
	- ![[Pasted image 20230424112948.png|400]]
5. 네트워크 뷰 패널
	- ![[Pasted image 20230424113132.png|200]]
6. 밑에 같이 모델이 잘 보이면 `OK!`

![[Pasted image 20230424114354.png|300]]

> [!info]
> 후디니의 기본 거리 단위는 1 meter 임

## Step 3 : 모델 일부 제거해주기
모델에서 캐릭터 + 바닥(Base)를 제외해서 모두 제거해줍니다 - 이는 Delete 노드 또는 Blast 노드를 활용해서 구현합니다.

1. 자잘한 스파크들 제거 : `Delete` 노드 생성 (`delete1`) > `Entity` 속성 `Primitives` > `Group` 속성에서 커서 아이콘 클릭 > 뷰포트에서 하이트라이트 박스로 제거할 것들을 한꺼번에 선택 > `Shft` 를 누른 상태로 추가 선택 > `Enter`
	- ![[Pasted image 20230424115249.png|300]]
	- ![[Pasted image 20230424115222.png|300]]
	- ![[Pasted image 20230424115506.png|300]]
	- ![[Pasted image 20230424115641.png|300]]
2. 남은 잔재(포인트)들 제거 : `Delete` 노드 생성 (`delete2`) > `Entity` 속성 `Points` > 위 방식과 동일하게 포인트들 제거
	- ![[Pasted image 20230424115942.png|300]]
	- ![[Pasted image 20230424120044.png|300]]
3. 스피어도 제거 (나중에 새로 만들거임) : `Group` 노드 생성 (`group1`) > `Group Name` 속성에 `orb_grp` 입력 > `Base Group` 속성에서 스피어 도형 `Primitives` 모두 선택 및 적용 > `Blast` 노드 생성 (`blast1`) > `Group` 속성에 `orb_grp` 선택
	- ![[Pasted image 20230424120907.png]]
	- ![[Pasted image 20230424120934.png|200]]
	- ![[Pasted image 20230424121259.png|200]]
	- ![[Pasted image 20230424121227.png|200]]
4. 밑에 같이 나오면 `OK!`

![[Pasted image 20230424121352.png|500]]

## Step 4 : 스피어 생성
이전에 지웠던 스피어를 대체할 새로운 스피어를 하나 만들어줍니다~

1. `Vivi_geo` 노드 안에서 `Sphere` 생성 (`sphere1`) > `Primitive Type` 속성 `Polygon` > `Frequency` 속성 `10`
2. `Merge` 노드 생성 (`merge1`) > `blast1` 아웃풋과 `sphere1` 아웃풋을 `merge1` 인풋에 연결 > `merge1` 노드를 디스플레이 해보면 캐릭터 모델과 새로 생성한 스피어가 보여짐 (캐릭터에 가려서 안 보일수도..)
	- ![[Pasted image 20230424122513.png|300]]
3. 스피어 위치 변경 : `sphere1` 에 연결해서 `Transform` 노드 생성 (`transform2`) > `Translate` 속성 적절히 조정
	- ![[Pasted image 20230424122713.png]]
	- ![[Pasted image 20230424124441.png|300]]
4. 밑에 같이 나오면 `OK!`

![[Pasted image 20230424122633.png]]


## Step 5 : 스피어에 애니메이션 주기
간단히 커졌다 작아졌다 하게 키프레임 심어줌

1. 애니메이션 설정창 열기 (`Global Animation Options` | `Shft + Alt + G`) > FPS `24`, Start `1001`, End `1300` 지정
	- #todo 왠지는 모르지만 실무에서 시작 프레임을 `1` 대신에 `1001` 으로 설정하는 것이 권장됨
2. 타임라인에서 시작 프레임 (`1001`) 클릭 > `sphere1` 선택 > 파라미터 패널 > `Uniform Scale` 속성 입력 칸에 `Alt + LMB` > 입력 칸이 초록색으로 변하고 `1001` 프레임에 초록색 박스가 생긴 것이 보임
	- ![[Pasted image 20230424125236.png]]
	- ![[Pasted image 20230424125245.png]]
3. 타임라인에서 아무 프레임 (예: 1032) 클릭 > sphere1 의 Uniform Scale 올리기 (예: 3.02) > 키프레임 생성 > 다른 프레임에서 다시 줄여주기 > 적당한 구간에 반복
4. 타임라인에서 플레이 버튼 누르면 스피어가 커지고 작아지고 애니메이션이 실행됨

![[Pasted image 20230424125855.png]]
![[Pasted image 20230424125927.png|200]]
![[Pasted image 20230424125943.png|200]]

> [!info]
> 기본(Default) 프로젝트 설정에서 애니메이션 실행 시 아주 빠르게 움직일 수 있음. 타임라인에 `Real Time Toggle` 버튼을 눌러주면 정상 속도로 실행됨.
> ![[Pasted image 20230424130201.png]]

## Step 6 : 스피어에 노이즈 주기
1. `transform2` 노드에 이어 `Mountain` 노드 생성 (`mountain1`) > 노이즈 설정
	- ![[Pasted image 20230424155302.png|300]]
	- `Noise Value` :: `Amplitude` 속성 `0.2`
	- `Noise Pattern` :: `Noise Type` 속성 `Worley Cellular F1`
	- `Animation` :: `Animate Noise` 속성 활성화, `Pulse Duration` 속성 `0.5`
	- `Fractal` :: `Roughness` 속성 `0.604`
2. 노이즈의 크기를 스피어의 크기에 맞추어 스케일링 되게 하기
	- `sphere1` 노드 `Uniform Scale` 우클릭 > `Copy Parameter` > `mountain1` 노드 `Noise Pattern` :: `Element Size` 입력 칸에 우클릭 > `Paste Relative References` > 입력 칸에 `ch("../sphere1/scale")` 와 같이 입력됨 > 끝에 `*0.6` 입력해서 스케일 비율 조정
3. 타임라인에서 플레이하면 스피어가 커지고 작아지며 동시에 겉면이 울렁거리는 애니메이션이 실행됨

![[Pasted image 20230424154940.png|200]]
![[Pasted image 20230424155039.png|200]]
![[Pasted image 20230424155056.png|200]]

## Step 7 : 배경 만들어주기
1. 네트워크 뷰 > `/obj` > `Geometry` 노드 생성 > 이름 변경 `Backdrop` > 들어가기
2. `Grid` 노드 생성 (`grid1`) > 적당히 위치 및 사이즈 조절 (스샷 참고)
	- 폴리곤 개수 올려주기 : `Columns` 속성 `RMB` (우클릭) > `Copy Parameter` > `Rows` 속성 `RMB` > `Paste Relative References` > `Columns` 속성 값 올리기 (`Rows` 속성 값도 같이 올라감)
	- ![[Pasted image 20230424160615.png]]
	- ![[Pasted image 20230424160242.png]]
3. `grid1` 노드에 이어 `Edit` 노드 생성 (`edit1`) > `Group` 속성 커서 아이콘 클릭 > Z축 기준 맨 뒤 `Edge` 에 있는 `Point` 전체 선택 및 적용
	- ![[Pasted image 20230424170655.png]]
	- ![[Pasted image 20230424171252.png]]
	- ![[Pasted image 20230424170731.png]]
4. `edit1` 노드 `Translate` 속성 Y축 값 올리기 (직접 값 입력하거나 MMB 으로 우측 방향 드래그); 대략 `31` 맞춤
	- ![[Pasted image 20230424173301.png|300]]
5. `edit1` 노드 `Soft Settings` : `Soft Radius` 속성 값 올리기; 대략 `45.9` 로 맞춤
	- ![[Pasted image 20230424173626.png|300]]
6. 밑에 같이 나오면 `OK!`

![[Pasted image 20230424174820.png]]
(Backdrop을 보기 쉽게 이미 재질을 입힌 상태로 스샷 찍은 것으로 다르게 보일 수 있음)

## Step 8 : 재질(Material) 설정

### Backdrop 재질 설정
1. 네트워크 뷰 > `/mat` > `Principled Shader` 노드 생성 & 이름 변경 (`backdrop_mat`) > `Base Color` 속성 검은색에 가깝게 조정
	- ![[Pasted image 20230424175858.png|150]]
2. 네트워크 뷰 > `/obj/Backdrop` > `edit1` 노드에 이어서 `Material` 노드 생성 (`material1`) > 파라미터 패널 > `Material` 속성에 선택 아이콘 클릭 > `backdrop_mat` 선택
	- ![[Pasted image 20230424180008.png]]
	- ![[Pasted image 20230424175943.png|150]]
	- ![[Pasted image 20230424180030.png]]

### 캐릭터 재질 설정
1. 네트워크 뷰 > `/mat` > `Principled Shader` 생성 & 이름 변경 (`Vivi_pants`) > `Base Color`, `Roughness`, `Metallic`, `Normal` 속성 `Use Texture` 옵션 활성화 > 텍스쳐 이미지 선택 (밑에와 같이 진행)
	- `Textures` 탭 > `Base Color` :: `Texture` 속성에 텍스쳐 이미지 선택 (캐릭터 모델 폴더 > `textures` 폴더 > `vivi_complete_Legs_BaseColor.png`)
	- Textures 탭 > Roughness :: Texture 속성에 텍스쳐 이미지 선택 (`vivi_complete_Legs_Roughness.png`)
	- `Textures` 탭 > `Metallic` :: `Texture` 속성에 텍스쳐 이미지 선택 (`vivi_complete_Legs_Metallic.png`)
	- `Bumps & Normals` 탭 > `Enable` 옵션 활성화 > `Texture Path` 속성에 노멀 이미지 선택 (`vivi_complete_Legs_Roughness.png`)
	- ![[Pasted image 20230424181004.png]]
2. `Principled Shader` 노드 5개 추가 > `Vivi_coats` (자켓), `Vivi_hat` (모자), `Vivi_hands` (손과 지팡이), `Vivi_body` (얼굴), `Vivi_base` (캐릭터 받침대) > 각 재질, 속성에 맞는 텍스쳐 이미지 선택
	- ![[Pasted image 20230424181419.png]]
3. 네트워크 뷰 > `/obj/Vivi_geo` > `merge1` 노드에 이어 `Material` 노드 생성 (`material1`) > 파라미터 패널
	- ![[Pasted image 20230424211918.png|300]]
	- `Number of Materials` 속성에 `6` 입력 > 1~6 탭이 생성되며, 각 탭에 연결된 박스가 보여짐
		- ![[Pasted image 20230424210056.png]]
	- 1번 박스 내 `Group` 속성 커서 아이콘 클릭 > 뷰포트 우측 상단 코너에 창이 생성되며 모델이 하이라이트 됨 > 기어 아이콘 클릭 > 팝업 메뉴에서 `Attributes` :: `shop_materialpath` 클릭
		- ![[Pasted image 20230424210446.png|500]]
	- 모델이 미리 지정된 부위(그룹)로 나뉘어 하이라이트 되며, 각 부위의 이름이 목록에 명시됨
		- ![[Pasted image 20230424211215.png|500]]
	- 목록에 한 부위(`Legs.001`)를 선택하고 `Enter` > `Group` 속성 입력 칸에 `@shop_materialpath=Legs.001` 로 채워짐 > `Material` 속성에 선택 아이콘 클릭 > 팝업 창에서 매칭되는 재질 선택 (`Vivi_pants`)
		- ![[Pasted image 20230424211528.png|200]]
		- ![[Pasted image 20230424211614.png]]
	- 위와 동일하게 2~6번 탭에서 각 부위별로 매칭되는 재질 선택해줌
4. `Vivi_body` 와 `Vivi_base` 노드에 `Textures` :: `Emission` 속성 텍스쳐 이미지를 넣은 후 `Surface` :: `Emission` 속성도 마찬가지로 조정해줘야 함; Vivi 캐릭터의 몸체는 어둡지만 반대로 눈이 옅게 빛나며, 돌바닥은 뜨겁게 달아오른듯 사이사이 빛남.
5. `Roughness` 등은 마음에 드는 정도로 조절~ (`0.5` 가 좋은듯)
6. `sphere1` 에도 맘대로 재질 입힐 것!
7. 밑에 같이 나오면 `OK!`

![[Pasted image 20230425191757.png|500]]

## Step 9 : 스테이징
> [!important] 스테이징(Staging) 정의
> "스테이징"이란 라이트, 카메라, 렌더 등 하나의 장면을 구성하는 요소들을 정리하는 것을 뜻하며, 후디니에서는 이러한 스테이징 작업을 하는 전용 레벨과 노드를 제공함; 이를 Solaris (솔라리스)라고 이름까지 붙혔음. 굳이 솔라리스를 사용할 필요는 없지만, 후디니에서 USD (Universal Scene Description) 기반 렌더러인 Karma 를 제공하며, Karma 를 사용하기 위해서 솔라리스로 작업해야 함. 한 마디로, Solaris -> USD -> Karma !

> [!info]
> 개인적으로 Redshift 로 그냥 렌더하는 것을 선호하지만, USD 는 Disney (Pixar) & NVIDIA 에서 열심히 투자하고 있어서 일단 한번 알아보는 것은 좋음!

> [!info]
> 조명, 카메라 셋팅 관련해서 상세하게 정리하진 않았음; 관련하여 따로 가이드 작성 예정

### 조명 및 카메라
1. 네트워크 뷰 > `/stage` > `Scene Import (All)` 노드 생성 (`sceneimportall1`)
2. `sceneimportall1` 노드에 이어 `Dome Light` 노드 생성 (`domelight1`) > `domelight1` 노드 `Base Properties` :: `Texture` 속성에 HDRI 이미지 선택
3. `Light` 노드 생성 > 이름 변경 (`keylight`) > `keylight` 노드 `Type` 속성 `Disk` 로 변경 > 적절하게 조명 밝기 & 각도 조절해주기 (나중에 최종적으로 믹스할 것임)
	- #참고 `Disk Type` 의 `Light` 는 `Area Light` 로 이해하면 됨
4. `Light` 노드 생성 > 이름 변경 (`rimlight`) > `rimlight` 노드 `Type` 속성 `Distant` 로 변경 > 적절하게 조명 밝기 & 각도 조절해주기 (나중에 최종적으로 믹스할 것임)
	- #참고 `Distant Type` 의 `Light` 는 `Infinite Light` 로 이해하면 됨
5. 대강 이런 구도가 나오면 됨~
	- ![[Pasted image 20230425192506.png|500]]
	- ![[Pasted image 20230425192603.png|300]]
6. `Light Linker` 노드 생성 (`lightlinker1`) > 파라미터 패널 > Lights List 목록에 `domelight1`, `keylight`, `rimlight` 가 모두 있는지 확인
	- ![[Pasted image 20230425192659.png|500]]
7. `Light Mixer` 노드 생성 (`lightmixer1`) > 파라미터 패널 > Sliders 탭 클릭
	- ![[Pasted image 20230425192834.png|500]]
	- `Mute` / `Solo` 로 조명 구성을 좀 더 상세하게 조절할 수 있음
		- `domelight1`, `rimlight` 노드 `mute` (`keylight` 노드 `solo`)
			- ![[Pasted image 20230425193017.png]]
			- ![[Pasted image 20230425193044.png|300]]
		- `rimlight` 노드 `solo`
			- ![[Pasted image 20230425193205.png]]
			- ![[Pasted image 20230425193218.png|300]]
8. `Camera` 노드 생성 (`camera1`) > 대강 마음에 드는 구조 잡기
	- ![[Pasted image 20230425193610.png|500]]
	- ![[Pasted image 20230425193659.png|500]]
9. 여기까지 문제 없으면 `OK!`

### 렌더링
1. `camera1` 노드에 이어 `Karma Render Settings` 노드 생성 (`karmarendersettings`) > `Output Picture` 속성에서 선택 아이콘 클릭 > 렌더 이미지 저장 경로 선택 (예: `$HIP/render/vivi_render_v01/`) > 렌더 이미지 파일명 패턴 선택 (예: `vivi_render_v01_$F4.exr`) > `Resolution` 은 알아서 > `Rendering Engine` 속성은 `CPU Engine` 또는 `XPU Engine (Beta)` 둘 다 사용 가능 (XPU = CPU + GPU)
	- #참고 `$F4` 는 4자리 수를 뜻하며, 각 파일명에 1001, 1002, .. 로 1단위로 올라가며 추가됨
2. 이어서 `USD Render ROP` 노드 생성 (`usdrender_rop1`) > `Valid Frame Range` 속성 `Render Current Frame`, `Render Delegate` 속성 `Karma` > 그 외 렌더 설정은 맘대로
3. `usdrender_rop1` 노드에서 `Render to MPlay` 버튼을 누르면 바로 렌더가 시작하면서 `MPlay` 창에서 렌더되는 상황을 볼 수 있음 (`Render to Disk` 는 조용히 알아서 렌더됨)
4. 밑에 같이 나오면 `OK!`

![[Pasted image 20230425201246.png|500]]
![[vivi_render_v01_1001.png]]

## 참고 자료
- [Houdini For The New Artist | CG Forge | Youtube Playlist](https://youtube.com/playlist?list=PL2SMrYpOIl0McqZHMV7dONrmIpJTY2WpH)

## 끝
언제든지 문의!