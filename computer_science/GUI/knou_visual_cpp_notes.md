---
aliases: [Visual C++ Notes, 비주얼 C++ 노트]
tags: [computer_science, computer_vision, computer_graphics, GUI, KNOU, study]
status: ongoing
created: 2022-10-20
edited: 2022-10-20
---

# Visual C++ 노트

## Visual Studio 설치 및 설정
교과서에는 2019 버전 설치를 말하는데.. 일단 2022 버전으로 설치해서 진행할 것.

### 도움말 뷰어 설치
오프라인 Visual C++ 도움말 설치. 기본적으로 온라인에서 매번 도움말을 호출해오지만, 도움말 뷰어에서 VC++ 도움말을 설치하면 오프라인 도움말을 불러옴으로 훨씬 빠름.

일단 이 [링크](https://learn.microsoft.com/ko-kr/visualstudio/help-viewer/installation?view=vs-2022)를 통해서 도움말 뷰어를 설치하고, 상단 메뉴 `Help` 아래 `Add and Remove Help Content` 클릭하면 밑에와 같은 창이 뜸.

![[비주얼_스튜디오_도움말_뷰어_창_20221020.png]]

교과서에는 Visual C++ 도움말을 설치하라고 하는데, 검색에 뜨지 않음. 그냥 C++ 관련된 모든 도움말을 업데이트 해보고 진행함.

### 파일 확장자
C++ 프로젝트를 진행하며 발생되는 파일들의 유형은 밑에와 같다.

![[cpp_file_formats.png]]


`.sdf` 포맷의 파일들은 용량이 크고 "필요가 없으니" 프로젝트를 생성할 때 생성되지 않게 설정할 수 있음.

상단 메뉴 `Tools` -> `Options` -> `Text Editor` -> `C/C++` -> `Advanced` -> `Browsing Database Fallback`에 있는 설정들을 밑에 그림과 같이 설정.

![[visual_studio_cpp_turnoff_sdf_file_generation.png]]

### 백신 검사 예외 설정
C++로 개발하다 보면 백신 프로그램에서 바이러스로 오인하는 경우가 발생할 수 있으니 백신 프로그램에서 프로젝트 폴더 경로를 검사 예외로 지정하는게 좋다.

## 제1장
- 윈도우 프로그램은 Windows 운영체제의 지원을 받으며 실행되는 응용 프로그램이므로 과거 콘솔 프로그램과 달리 Windows 운영체제의 특징을 그대로 반영하고 있다.
- **Windows 운영체제에서 실행되는 윈도우 프로그램들은 편리한 사용자 인터페이스를 지원받고 장치 독립적이며 멀티태스킹이 가능하다.**
- Visual C++을 이용하여 윈도우 프로그램을 개발하는 경우, 개발자는 