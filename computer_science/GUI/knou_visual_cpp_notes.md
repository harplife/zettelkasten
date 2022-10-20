---
aliases: [Visual C++ Notes, 비주얼 C++ 노트]
tags: [computer_science, computer_vision, computer_graphics, GUI, KNOU, study]
status: ongoing
created: 2022-10-20
edited: 2022-10-20
---

# Visual C++ 노트

## 준비

### Visual Studio 설치 및 설정
교과서에는 2019 버전 설치를 말하는데.. 일단 2022 버전으로 설치해서 진행할 것.

#### 도움말 뷰어 설치
오프라인 Visual C++ 도움말 설치. 기본적으로 온라인에서 매번 도움말을 호출해오지만, 도움말 뷰어에서 VC++ 도움말을 설치하면 오프라인 도움말을 불러옴으로 훨씬 빠름.

일단 이 [링크](https://learn.microsoft.com/ko-kr/visualstudio/help-viewer/installation?view=vs-2022)를 통해서 도움말 뷰어를 설치하고, 상단 메뉴 `Help` 아래 `Add and Remove Help Content` 클릭하면 밑에와 같은 창이 뜸.

![[비주얼_스튜디오_도움말_뷰어_창_20221020.png]]

교과서에는 Visual C++ 도움말을 설치하라고 하는데, 검색에 뜨지 않음. 그냥 C++ 관련된 모든 도움말을 업데이트 해보고 진행함.

#### 파일 확장자
C++ 프로젝트를 진행하며 발생되는 파일들의 유형은 밑에와 같다.

![[cpp_file_formats.png]]


`.sdf` 포맷의 파일들은 용량이 크고 "필요가 없으니" 프로젝트를 생성할 때 생성되지 않게 설정할 수 있음.

상단 메뉴 `Tools` -> `Options` -> `Text Editor` -> `C/C++` -> `Advanced` -> `Browsing Database Fallback`에 있는 설정들을 밑에 그림과 같이 설정.

![[visual_studio_cpp_turnoff_sdf_file_generation.png]]

#### 백신 검사 예외 설정
