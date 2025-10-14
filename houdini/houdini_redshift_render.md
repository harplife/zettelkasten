<mark style="background: #ADCCFFA6;">저자 : 김우빈</mark>
<mark style="background: #FFF3A3A6;">작성 일자 : 2023-04-18</mark>
<mark style="background: #FF5582A6;">버전 : v02_20230421</mark>

---
# Houdini 에서 Redshift 로 렌더하기
Houdini와 Redshift 연동 방법에서 간단한 장면 렌더 방법까지 정리합니다.

![[20230421_scatter_balls_redshift_render.png|500]]

> [!info] Houdini Apprentice 도 가능!

> [!warning] 해당 가이드는 Maxon Redshift 3.5.14 번과 Houdini 19.5.534 버전으로만 테스트 했음!

> [!important] 특정 버전 후디니 설치하는 방법
> 후디니 설치 파일 다운로드 할 때 두 가지 옵션이 있음으로, Launcher를 다운로드 해야 Launcher 안에서 이전 버전 후디니를 선택해서 설치 할 수 있습니다!

## 목차
- [[#Step 1 : Redshift의 Houdini 플러그인 확인]]
- [[#Step 2 : Houdini에 Redshift 패키지 추가]]
- [[#Step 3 : 간단한 장면 구성]]
- [[#Step 4 : Redshift 라이트 생성]]
- [[#Step 5 : 카메라 생성]]
- [[#Step 6 : Redshift Material 생성]]
- [[#Step 7 : Redshift 로 렌더하기]]
- [[#(Opt.) Step 8 : 렌더 설정]]
- [[#참고 자료]]
- [[#끝~]]

## Step 1 : Redshift의 Houdini 플러그인 확인
1. Redshift 플러그인 폴더 경로 `C:\ProgramData\redshift\Plugins`로 이동 후 `Houdini` 폴더와 `Solaris` 폴더가 있는지 확인
2. 각 플러그인 폴더 안에 `19.5.534` 이름의 폴더가 있는지 확인
3. 폴더 내부가 밑에 스샷과 같으면 `OK!`

![[Pasted image 20230418120539.png]]

## Step 2 : Houdini에 Redshift 패키지 추가
1. 후디니 설정 폴더 경로 `C:\Users\AIA\Documents\houdini19.5` 로 이동
2. `packages` 폴더로 이동 (없는 경우 새로 생성)
3. 새로운 텍스트 파일 생성해서 밑에 내용 입력하고 파일명 `redshift.json` 으로 저장
```json
{
	"env" : [
		{"REDSHIFT_ROOT":"C:/ProgramData/redshift"},
		{"HOUDINI_PATH" : "${REDSHIFT_ROOT}/Plugins/Houdini/19.5.534"},
		{"PXR_PLUGINPATH_NAME": "${REDSHIFT_ROOT}/Plugins/Solaris/19.5.534"},
		{"PATH" : "${REDSHIFT_ROOT}/bin"}
	]
}
```
4. 후디니 프로그램 열고 (열려 있었으면 닫기) 상단 메뉴에 Redshift 가 생겼으면 `OK!`
	- ![[Pasted image 20230418121309.png]]
5. Redshift 책장(Shelf)도 추가해주면 편함
	- ![[Pasted image 20230418122325.png|500]]

## Step 3 : 간단한 장면 구성
1. 동그라미 하나 만들어주던가.. (`geo1`)

## Step 4 : Redshift 라이트 생성
Dome 라이트 설치하고 이 안에 HDRI 이미지 넣어줍니다~

1. 네트워크 뷰 패널 > `/obj` 탭 > `RSLightDome` 노드 생성 및 선택 (`rslightdome1`) > 속성 패널 > `Light` 탭 > `General` :: `Texture` 속성에서 HDRI 이미지 파일 선택
	- ![[Pasted image 20230421125552.png]]
	- ![[Pasted image 20230421125633.png]]
2. 밑에 같이 나오면 `OK!`

![[Pasted image 20230421125946.png]]

## Step 5 : 카메라 생성
1. 네트워크 뷰 패널 > `/obj` 탭 > `Camera` 노드 생성 및 선택 (`cam1`) > 속성 패널 > `Redshift Camera` 탭이 있는지 확인
	- (없는 경우) Redshift 책장에서 `CamParams` 클릭
	- ![[Pasted image 20230421130253.png]]
	- ![[Pasted image 20230421130305.png]]
2. 카메라를 조절하기 위해서는 뷰포트 화면 오른쪽 상단에 `No cam` 으로 되어있는 아이콘을 클릭해서 `cam1` 선택, `Lock Camera`(자물쇠) 아이콘 선택한 후 화면을 움직이면 됨
	- ![[Pasted image 20230421130605.png]]
	- 이렇게 카메라 노드를 고정한 후 카메라를 Native Viewport Camera 로 변경하면, 카메라에 영향을 주지 않고 작업 가능
	- 나중에 렌더할 때 `cam1` 카메라 노드를 선택해서 렌더할것임
3. 밑에 같이 보이면 `OK!`

![[Pasted image 20230421130915.png]]

## Step 6 : Redshift Material 생성
1. 네트워크 뷰 패널 > 핀 아이콘 (`Not following selection`) 활성화 > 탭 생성 (Ctrl + T) > 드랍다운 메뉴에서 `mat` 선택
	- ![[Pasted image 20230421131659.png|50]]
	- ![[Pasted image 20230421131633.png]]
2. `RS Standard Material` 노드 생성 및 선택 (`StandardMaterial1`) > 속성 패널 > `Base Properties` 탭 > `Base` :: `Color` 속성에 색상 조절 (색 아이콘 눌러서 설정, 또는 값 입력 `1.0 // 0.5 // 0.0`)
	- ![[Pasted image 20230421131410.png]]
	- ![[Pasted image 20230421143641.png]]
3. 네트워크 뷰 패널 > `/obj` 탭 > `geo1` 노드 선택 > 파라미터 패널 > `Render` 탭 > `Material` 속성에서 선택 아이콘 (`Open floating operator chooser`) 클릭 > 선택창에서 `StandardMaterial1` 노드 선택
	- ![[Pasted image 20230421131953.png|50]]
	- ![[Pasted image 20230421131935.png]]
	- ![[Pasted image 20230418123744.png]]
4. 밑에 같이 보이면 `OK!`

![[Pasted image 20230421143746.png]]

> [!important]
> 도형 노드가 `Cd` 속성 값을 조절하는 `Attribute Randomize` 노드와 연결되어 있는 경우, 뷰포트에서 `Material` 노드의 색이 아닌 `Attribute Randomize` 노드가 지정한 색이 보임. 반면에, 렌더뷰에서는 `Material` 노드의 색이 보임. `Material` 노드가 `Attribute Randomize` 노드가 지정한 색을 상속 받는 것은 나중에 설명할 것임!

## Step 7 : Redshift 로 렌더하기
1. Redshift 책장에서 `RenderView` 클릭
	- ![[Pasted image 20230421144821.png]]
	- `Redshift Render View` 창이 따로 뜨고, 바로 `IPR` 모드로 렌더됨 (개인적으로 `IPR` 모드는 끄고 `Render` 버튼 눌러서 직접 렌더하는 것을 선호함)
2. 렌더가 밑에 같이 나오면 `OK!`

![[Pasted image 20230421145102.png]]

## (Opt.) Step 8 : 렌더 설정
1. 렌더한 후 네트워크 뷰 패널을 보면 `/out` 탭이 자동으로 생성된 것을 확인할 수 있으며, 안에 `Redshift_ROP1`, `Redshift_IPR1` 노드가 보임
	- ![[Pasted image 20230421145549.png]]
2. 렌더 설정의 일부는 `Redshift_ROP1` 노드의 파라미터에 있음
	- ![[Pasted image 20230421150413.png]]
	- `Main` 탭 > `Render Camera` 속성에서 카메라 선택 가능
		- ![[Pasted image 20230421150445.png]]
	- `Redshift` 탭에서 렌더 화질 설정 가능
		- ![[Pasted image 20230421150626.png]]
3. 렌더 설정의 일부는 카메라 노드 파라미터에 있음
	- ![[Pasted image 20230421152355.png]]
4. Redshift ROP 노드 파라미터에 Render to Disk 또는 Render to MPlay로 이미지/영상 렌더 저장이 가능함
	- ![[Pasted image 20230421152523.png]]

## 참고 자료
- [Redshift Initialization in Houdini | Mark Fancher | Youtube](https://youtu.be/9TJi-sE2g-w)

## 끝~
언제든지 문의 주세요!