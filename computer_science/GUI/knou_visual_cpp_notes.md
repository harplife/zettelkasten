---
aliases: [Visual C++ Notes, 비주얼 C++ 노트]
tags: [computer_science, computer_vision, computer_graphics, GUI, KNOU, study]
status: ongoing
created: 2022-10-20
edited: 2022-10-20
---

# Visual Studio 설치 및 설정
교과서에는 2019 버전 설치를 말하는데.. 일단 2022 버전으로 설치해서 진행할 것.

주의 : "C++를 사용한 데스크톱 개발"을 선택한 후 설치 세부 정보 아래 추가 옵션들 모두 선택해줘야 함.

## 도움말 뷰어 설치
오프라인 Visual C++ 도움말 설치. 기본적으로 온라인에서 매번 도움말을 호출해오지만, 도움말 뷰어에서 VC++ 도움말을 설치하면 오프라인 도움말을 불러옴으로 훨씬 빠름.

일단 이 [링크](https://learn.microsoft.com/ko-kr/visualstudio/help-viewer/installation?view=vs-2022)를 통해서 도움말 뷰어를 설치하고, 상단 메뉴 `Help` 아래 `Add and Remove Help Content` 클릭하면 밑과 같은 창이 뜸.

![[비주얼_스튜디오_도움말_뷰어_창_20221020.png]]

교과서에는 Visual C++ 도움말을 설치하라고 하는데, 검색에 뜨지 않음. 그냥 C++ 관련된 모든 도움말을 업데이트 해보고 진행함.

## 파일 확장자
C++ 프로젝트를 진행하며 발생되는 파일들의 유형은 밑과 같다.

![[cpp_file_formats.png]]


`.sdf` 포맷의 파일들은 용량이 크고 "필요가 없으니" 프로젝트를 생성할 때 생성되지 않게 설정할 수 있음.

상단 메뉴 `Tools` -> `Options` -> `Text Editor` -> `C/C++` -> `Advanced` -> `Browsing Database Fallback`에 있는 설정들을 밑에 그림과 같이 설정.

![[visual_studio_cpp_turnoff_sdf_file_generation.png]]

## 백신 검사 예외 설정
C++로 개발하다 보면 백신 프로그램에서 바이러스로 오인하는 경우가 발생할 수 있으니 백신 프로그램에서 프로젝트 폴더 경로를 검사 예외로 지정하는게 좋다.

# 제1장 WinApi
- 윈도우 프로그램은 Windows 운영체제의 지원을 받으며 실행되는 응용 프로그램이므로 과거 콘솔 프로그램과 달리 Windows 운영체제의 특징을 그대로 반영하고 있다.
- **Windows 운영체제에서 실행되는 윈도우 프로그램들은 편리한 사용자 인터페이스를 지원받고 장치 독립적이며 멀티태스킹이 가능하다.**
- Visual C++을 이용하여 윈도우 프로그램을 개발하는 경우, 개발자는 Windows 운영체제에서 제공하는 WinAPI 함수와 방대한 클래스 라이브러리인 MFC을 자유롭게 사용할 수 있어 적은 노력과 시간으로도 과거에는 생각할 수 없었던 대규모 프로그램들을 개발할 수 있다.
- 윈도우 프로그램을 공부하려면, 먼저 WinAPI 함수를 사용하는 API 프로그래밍을 살펴본 다음 MFC에서 제공하는 방대한 클래스를 사용하는 MFC 프로그래밍을 공부해야 한다.
- 이 장에서는 먼저, WinAPI를 사용하여 윈도우를 생성하는 윈도우 프로그램에 대해 설명한다. Windows 운영체제의 지원을 받는 윈도우 프로그램의 특징을 살펴보고 WinAPI로 구성된 윈도우 프로젝트를 작성해 본다. 윈도우를 등록/생성하고 보여 주는 데 필요한 각각의 WinAPI 함수와 이를 위해 필요한 메시지 처리방식, 윈도우 프로시저 함수 등을 중심으로 설명한다.

## 학습목표
1. 윈도우 프로그램의 특징을 이해한다.
2. 메시지 중심의 처리과정을 이해한다.
3. 간단한 윈도우를 생성하는 윈도우 프로젝트를 작성할 수 있다.
4. WinMain 함수의 역할과 코드를 이해할 수 있다.
5. 윈도우 프로시저 함수의 역할을 이해할 수 있다.
6. 차일드 윈도우와 버튼 컨트롤을 생성하는 데 필요한 함수와 추가 코드를 작성할 수 있다.

## 주요용어
- Windows 운영체제
- 멀티태스킹
- 메시지 구동방식
- MFC
- GDI
- API
- WinMain
- 윈도우 프로시저
- CALLBACK 함수
- 윈도우 클래스
- 윈도우 클래스 등록
- 윈도우 생성
- 메시지 루프
- TextOut 함수
- 버튼
- 컨트롤

## 윈도우 프로그램
- MS Windows는 Microsoft사에서 만든 개인용 컴퓨터의 운영체제 이름으로 간단히 Windows라고 부른다.
- 1990년대 초까지만 해도 개인용 컴퓨터의 운영체제는 MS사에서 제작한 DOS였다.
- 1990년대 이후 DOS는 여러 가지 버전의 Windows로 바뀌었다.
- 윈도우 프로그램이란 Windows에서 실행할 수 있는 응용 프로그램이다.
- 우리가 자주 사용하는 윈도우 프로그램은 실행 결과가 항상 사각형 윈도우(Window) 형태인데, 자세히 보면 윈도우 안에 타이틀바, 툴바, 메뉴바, 버튼 등 여러 개의 윈도우가 들어 있다.

### 윈도우 프로그램 특징
Windows에서 실행하는 윈도우 프로그램은 다음과 같은 특징을 갖는다.

#### 장치 독립적
- 윈도우 프로그램을 작성할 떄는 설치된 하드웨어의 사양을 고려하지 않고 자유롭게 작성할 수 있다.
- 과거 DOS에서 프로그램은 화면에 점 하나를 찍는 단순 작업을 위해 그래픽카드 종류, 화면 해상도 지원 범위, 컬러 지원 범위 등을 검사해 본 후 여기에 맞게 소스 코드를 작성해야만 했다.
- 윈도우 프로그램의 경우 하드웨어 장치가 어떤 모델이든 상관없다. Windows에 요청하면 운영체제가 하드웨어에 적당한 드라이버를 찾아서 스스로 설치하므로 윈도우 프로그램은 하드웨어에 종속되지 않는다. 즉, 언제나 동일한 소스 코드를 작성한다.

#### 멀티태스킹
- Windows는 멀티태스킹(Multitasking)을 지원하므로 여러 윈도우 프로그램이 동시에 실행된다.
- 화면에 여러 개의 윈도우가 동시에 있어서 사용자 입장에서는 여러 개의 태스크가 동시에 실행되는 것처럼 보인다.
- 각각의 윈도우 프로그램은 다른 윈도우 프로그램에 의해 자신의 작업 영역에 영향을 받을 수 있으므로, 윈도우 프로그램은 항상 자신의 작업 영역을 복수할 수 있도록 작성되어야 한다.

#### 메시지 구동방식
- 윈도우 프로그램은 메시지 구동방식(Message-Driven)으로 동작한다.
- 메시지 구동방식은 Windows의 가장 중요한 특징으로, 모든 윈도우 프로그램은 이러한 메시지 구동방식에 적절히 대처할 수 있도록 작성되어야 한다.

#### GUI
- Windows는 사용자 인터페이스인 GUI (Graphic User Interface)로 동작된다.
- 사용자의 컴퓨터 사용환경이 모두 그래픽 모드에서 이루어지므로 윈도우 프로그램도 이에 맞는 GUI를 제공해야 한다.
- 윈도우 프로그램은 GUI를 제공하기 위한 리소스 (예: 비트맵 이미지, 아이콘, 커서, 메뉴, 대화상자 등)가 필요하다.

### 기초 용어
윈도우 프로그램을 작성할 때 기본적으로 알아야 하는 기초 용어

#### 운영체제
- 운영체제(OS : Operating System)은 컴퓨터의 하드웨어를 직접적으로 제어하고 관리하는 시스템 소프트웨어이다.
- 운영체제는 실행되는 응용 프로그램이 메모리와 CPU, 입출력장치 등의 자원을 사용할 수 있도록 만들어 주고, 그들을 추상화하여 파일 시스템 등의 서비스를 제공한다.
- 운영체제는 여러 개의 응용 프로그램이 실행되는 동안 모든 프로세스를 스케줄링하여 마치 그들이 동시에 수행되는 듯한 효과를 낸다.

#### 커널
- 커널(Kernel)은 운영체제의 핵심 부분으로 운영체제의 다른 부분 및 응용 프로그램 수행에 필요한 여러 가지 서비스를 제공한다.

#### 소스 코드
- 소스 코드(Source Code)는 컴퓨터 프로그램을 사람이 읽고 사용할 수 있는 프로그래밍 언어로 기술한 글을 말한다.

#### 컴퓨터 프로그램
- 컴퓨터 프로그램(Computer Program)은 컴퓨터에 의해 실행되는 지시사항의 모음인 컴퓨터 소프트웨어의 한 예이다.
- 프로그램은 대부분 실행 중에 사용자의 입력에 반응하도록 구현된 명령어의 집합으로 구성되어 있다.

#### MS DOS
- MS DOS(Microsoft Disk Operating System)은 MS사가 개발한 IBM PC용 운영체제이다.
- 1981년에 처음 제공되어 널리 사용되었으나, 1995년 이후에 Windows로 대체되면서 개발이 중단되었다.

#### MS Windows
- MS Windows는 MS사가 개발한 컴퓨터 운영체제이다.
- MS DOS에서 멀티태스킹과 GUI 환경 등을 제공하기 위해 개발된 운영체제로 현재 PC로 가장 많이 사용되고 있다.

#### 멀티태스킹
- 다수의 작업/프로세스/태스크가 중앙 처리장치(CPU)와 같은 공용자원을 나누어 사용하는 것을 말한다.
- 멀티태스킹은 스케줄링(Scheduling)이라는 방식을 사용하여 컴퓨터 사용자에게 병렬 연산이 이루어지는 것과 같은 환경을 제공한다..

#### Windows와 Window
- Windows는 운영체제를 뜻한다.
- Window는 화면에 나타나는 창을 뜻한다.

#### GDI (Graphic Device Interface)
- Windows의 하위 시스템 중 하나의 DLL 모듈로, 모든 출력장치를 제어하는 역할을 한다.
- 윈도우 프로그램에서 요청하는 모든 출력은 GDI를 통해 실제 출력장치인 화면이나 프린터에 출력된다.
- 윈도우 프로그램에서 GDI 함수를 사용하여 프린터, 화면 등에 출력하면 GDI는 설치된 해당 드라이버를 연결하여 출력한다.
- GDI로 인해 프로그래머는 장치에 일일이 신경 쓸 필요가 없으므로, 이를 장치 독립적(Device Indepence)라고 표현한다.

#### DC (Device Context)
- 출력에 필요한 모든 정보를 갖고 있는 데이터 구조체로, GDI가 생성하고 관리한다.
- 출력에 필요한 정보란 문자열의 모양을 지정하는 폰트, 선의 색상과 굵기, 채움 무늬와 색상, 그리기 모드 등을 뜻한다.
- 윈도우 프로그램에서 무언가를 출력하려면 반드시 DC가 필요하다.

![[visual_cpp_device_dependence_diagram.png]]

### API
- API (Application Programming Interface)는 운영체제가 응용 프로그램을 위해 제공하는 함수의 집합이다.
- 운영체제는 하드웨어와 응용 프로그램 사이에 위치하며 응용 프로그램을 대신하여 하드웨어를 관리하고 메모리를 관리하는 시스템 소프트웨어를 말한다.
- 특정 운영체제에서 실행되는 응용 프로그램은 운영체제의 종속적일 수밖에 없으며, 운영체제가 규정한 대로 하드웨어를 액세스해야 한다.
- Windows와 같은 멀티태스킹 운영체제의 경우, 응용 프로그램 간 상호작용을 할 때 운영체제의 규정을 따라야 한다.
  ![[visual_cpp_hardware_api_program_relationship.png]]
- **운영체제는 가장 기본적인 동작을 할 수 있는 함수의 집합을 응용 프로그램에 제공하여, 이를 WinAPI라고 한다.**
- API는 운영체제의 중요한 한 부분이며 운영체제 그 자체라고도 할 수 있다.

### SW - OS - HW 관계
운영체제와 응용 프로그램, MFC, API, GDI의 관계

![[visual_cpp_os_sw_hw_relationship.png]]

- 커널은 메모리 관리와 프로그램 실행을 담당한다.
- 사용자(User)는 사용자 인터페이스와 윈도우를 관리한다.
- GDI는 모든 출력장치를 제어한다.

### WinAPI에서 사용하는 자료형
밑에 표에 윈도우 프로그래밍에서 사용되는 기본 자료형이 명시되어 있다. `windows.h`라는 헤더 파일에서 `typedef`로 선언되어 있으며, 거의 모든 프로그램에서 표준 자료형처럼 사용되고 있다.

#todo 교과서에 있는 자료는 좀 그러니, 인터넷에서 정보를 찾아서 마저 표를 작성할 것.

| DataType     | Description               |
| ------------ | ------------------------- |
| BOOL/BOOLEAN | TRUE or FALSE             |
| BYTE         | Byte(8 bit)               |
| CALLBACK     | Defines CALLBACK function |
| COLORREF     | RGB color value(32 bit)   |
| DWORD        | 32 bit unsigned integer   |
| HANDLE       | Defines handle            |
| HBITMAP      | Bitmap Handle             |
| HBRUSH       | Brush Handle              |
| HCURSOR      | Cursor Handle             |
| HDC          | DC Handle                 |
| HFONT        | Font Handle               |
| HICON        | Icon Handle               |
| HMENU        | Menu Handle               |
| HWND         | Window Handle             |
| LONGLONG     | 64 bit signed integer     |
| LPARAM       | 32 bit message parameter  |
| LPCSTR       |                           |
| LPCTSTR      |                           |
| LPCWSTR      |                           |
| LPSTR        |                           |
| LPTSTR       |                           |
| LPVOID       | void pointer              |
| PCSTR        | Previous char pointer     |
| PCTSTR       | Previous char pointer     |
| TBYTE        | 2 Byte                    |
| TCHAR        | UNICODE char              |
| UINT         | Unsigned int              |
| WCHAR        | UNICODE char              |
| WORD         | 16 bit unsigned integer   |
| WPARAM       | 32 bit message parameter  |
| RECT         | Rectangle object          |
| POINTS       | Point object              |
| LRESULT      |                           |

### 핸들
- 핸들(Handle)이란 어떤 대상에 붙여진 번호로, 문법적으로 32 비트의 정수 값이다.
- DOS 프로그램에서는 거의 유일하게 파일 핸들만이 사용되었다.
- 윈도우 프로그램에서는 여러 종류의 핸들이 사용된다.
- 모든 윈도우에는 윈도우 핸들(`hWnd`)이 붙여지며, 논리적 펜과 브러시에도 핸들을 붙여 관리한다.
- 메모리를 할당할 때도 할당된 메모리 번지를 취급하기보다, 메모리 핸들을 사용한다.
- 핸들을 자주 사용하는 이유는 대상을 구분하기 위해서이며, 핸들값으로 정수를 사용함으로 문자열을 사용하는 것보다 훨씬 속도가 빠르다.

#### 핸들의 특징
1. 핸들은 정수 값이며 대부분의 경우 32 비트로 구현된다. 핸들을 사용하는 목적은 오로지 구분을 위한 것이다.
2. 핸들은 운영체제가 발급해 주며, 사용자는 발급된 핸들을 사용하기만 하면 된다. 예를 들어, 윈도우를 만들면 운영체제는 만들어진 윈도우에 핸들을 붙여준다. 사용자는 이 핸들을 잘 보관해 두었다가, 해당 윈도우를 다시 참조할 때 핸들을 사용하면 된다. 사용자가 직접 핸들을 만들지는 않는다.
3. 같은 종류의 핸들끼리는 중복된 값을 갖지 않는다. 다른 종류의 핸들끼리는 중복된 값을 가질 수도 있다.
4. 핸들의 실제 값이 무엇인지 몰라도 상관없다. 핸들은 단순한 이름표의 역할을 할 뿐으로, 핸들형 변수를 만들어 핸들을 대입받아 쓰고 난 후에는 버려도 된다.

#### h 접두어
- 윈도우에서 핸들은 예외 없이 접두어 `h`로 시작되며, 핸들값을 저장하기 위해 별도의 자료형까지 정의해 두고 있다.
- `HWND`, `HPEN`, `HBRUSH`, `HDC` 등이 핸들을 담기 위한 자료형이며, 모두 `UNSIGNED INTEGER` 이다.

### WinAPI 프로그램 흐름
- 모든 WinAPI 프로그램은 가장 먼저 `windows.h`라는 헤더 파일을 포함(Include)한다.
- `windows.h` 헤더 파일은 내부적으로 WinAPI에서 사용하는 상수, 매크로, 구조체와 함수원형 등에 대한 선언(Declaration)을 담고 있는 여러 가지 부문별 헤더를 포함한다.
- `windows.h` 헤더 파일은 `WinMain` 함수와 윈도우 프로시저 함수로 구성되어 있다.

#### WinMain 함수
```C++
int APIENTRY WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, 
                     LPSTR lpszCmdParam, int nCmdShow)
```

- `WinMain` 함수는 윈도우 메인 함수라고 하며 콘솔 응용 프로그램에서 등장하는 `main()` 함수에 해당한다.
- `main()` 함수는 프로그램의 진입점(Entry Point)이라고 하는데, 프로그램이 실행될 때 처음 시작하는 부분이라는 의미이며, 이 함수를 갖고 있어야만 독립적으로 실행 가능한 프로그램이 된다.
- `WinMain` 함수의 반환 타입은 `int`형이다.

##### WinMain 호출 방식
- `APIENTRY` 매크로는 함수호출규약(Function Calling Convention)으로, `_stdcall`형 호출규약을 사용한다는 뜻이다.
- `_stdcall`은 `WinAPI` 함수들의 호출방식이며, 밑에와 같은 방식들을 매크로로 기술한 것이다.
    - 매개변수의 전달 순서는 왼쪽에서 오른쪽으로,
    - 값에 의한 전달을 사용하고,
    - 함수호출을 위해 사용한 스택은 호출된 함수 자신이 리턴되면서 비우고,
    - 호출된 함수가 스택의 유지보수를 담당한다.

##### WinMain 주요 기능
- `WinMain` 함수는 먼저 메인 윈도우를 만들고, 그 다음에는 메시지를 처리하기 위하여 메시지 루프를 운영하는데 다음과 같은 다섯 가지 주요 기능으로 되어 있다.
    1. 윈도우 클래스 정의 : `WNDCLASS` 윈도우 클래스 구조체를 사용하여 윈도우를 생성하기 위한 기본 속성을 정의한다.
    2. 윈도우 클래스 등록 : `RegisterClass()` 함수로 윈도우 클래스를 등록한다.
    3. 윈도우 객체 생성 : `CreateWindow()` 함수로 윈도우 객체를 생성한다.
    4. 화면에 윈도우 보이기 : `ShowWindow()` 함수로 미리 생성된 윈도우 객체를 화면에 보이게 한다.
    5. 메시지 루프 : 메시지 큐에서 메시지를 가져와서 처리하는 반복문
- 윈도우 프로그램은 이벤트 중심의 프로그램이며 모든 이벤트는 밑에와 같이 메시지로 표현된다.
  ![[visual_cpp_event_to_message.png]]

##### 메시지 처리 과정
- 메인 윈도우 생성에 성공하면 그 다음부터는 계속 메시지 큐에서 메시지를 가져와서 처리하는 일을 반복하는데 다음과 같은 While 반복문으로 처리한다.
  ```C++
  while(GetMessage(&Message,0,0,0)) // 메시지를 가져온다.
  {
    TranslateMessage(&Message); // 키보드 메시지인지 검사
    DispatchMessage(&Message); // 메시지 전달
    ..
  }
  ```
- `GetMessage` 함수는 시스템 메세지 큐에서 메시지를 가져오는 역할을 하며, 무한 루프를 돌게 된다.
- `WM_QUIT` 메시지가 오면 종료한다.
- 윈도우 우측 상단의 종료 버튼을 누르면 `WM_DESTORY` 메시지가 발생되고, 이것을 처리하는 함수가 `WM_QUIT` 메시지를 발생시킨다.
- ![[visual_cpp_message_processing_flow.png]]
- `TranslateMessage` 함수는 키보드 메세지를 문자 입력 메시지로 변환해준다.
- `DispatchMessage` 함수는 메시지를 해당 윈도우의 윈도우 프로시저 함수로 전달하는 역할을 한다.
- 모든 메시지는 운영체제가 관리하는 시스템 메시지 큐에 보관된다.
- 운영체제는 메시지가 발생한 응용 프로그램 큐에 메시지로 전달하고, 응용 프로그램은 자신의 윈도우 프로시저에서 그 메시지를 처리한다.

#### 윈도우 프로시저
- `WndProc` 함수는 API 프로그램에서 메시지를 처리하는 또 하나의 중요한 함수다.
  ```C++
  LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);
  ```
- `WndProc`은 윈도우 프로시저라고 불리며, 프로그램이 실행되는 동안 발생하는 모든 메시지를 처리하는 역할을 한다.
- 함수명 바로 앞에 `CALLBACK`이라는 매크로를 사용하여 `CALLBACK` 함수로 정의한다. `CALLBACK` 함수는 사용자가 정의하지만 호출은 운영체제가 한다.
  ![[visual_cpp_wndproc_and_callback.png]]
- 일반적으로 API 함수는 운영체제가 제공하며, 프로그램에서는 이 함수를 호출해서 사용한다.
    - 예를 들어, 운영체제의 `TextOut` 함수는 프로그램이 호출하면, 이를 수행하여 문자열을 출력한다. 
- 반면에, `CALLBACK` 함수는 응용 프로그램이 제공하지만, 프로그램이 아닌 운영체제가 필요할 때 호출한다.

## 프로젝트
- Win32 API 프로그래밍을 직접 해본다.
    - 메인 윈도우를 생성하고 메인 윈도우에 문자열을 출력하는 프로젝트를 작성한다.
    - 메인 윈도우에 차일드 윈도우를 추가하고 차일드 윈도우에 문자열을 출력한다.

### 프로젝트 생성
- 비주얼 스튜디오를 열고 `Create a new project`를 클릭한다.
- 프로젝트 생성 창에서 `Windows Desktop Wizard`를 클릭하고 `Next`를 누른다.
- 프로젝트 이름, 위치 등을 입력하고 `Create`을 누른다. 새로 뜨는 창에 Application Type에 `Desktop Application(.exe)`를 선택하고, 추가 옵션에 `Empty Project`를 선택한 후 `OK`를 누른다.
  ![[visual_studio_new_project.png]]
  ![[visual_studio_new_project_desktop_app.png]]

### 소스 파일 추가
- 프로그램을 작성하기 위해 프로젝트에 새로 소스 파일을 추가해야 한다.
- `Solution Explorer` 창 안에 `Source Files`를 우클릭하고 `Add` -> `New Item`을 클릭한다.
  ![[visual_studio_new_file.png]]
- 파일 추가 창에서 `C++ File (.cpp)`을 선택하고 이름을 `helloAPI.cpp`로 입력한 다음 `Add`를 클릭하면 새로운 C++ 파일이 생성되고 창에 열린다.
  ![[visual_studio_new_file_cpp.png]]
- 아직 코드는 작성하지 않는다. 소스 코드는 1.3절에 있다.

### UNICODE 문자집합 설정
- 비주얼 스튜디오에 문자집합(Character Set)의 기본설정(Default)은 UNICODE이다.
- 기존에 생성하였던 프로젝트의 문자집합 설정을 확인하기 위해 `Solution Explorer` 창 -> 프로젝트 우클릭 -> `Properties` 선택 -> `Advanced` 클릭 -> `Advanced Properties` 아래 `Character Set`의 값을 확인해보면 된다. `Use Unicode Character Set`라고 설정되어 있는 경우, UNICODE를 사용하고 있다는 것이다.
  ![[visual_studio_project_character_set.png]]
- 프로젝트 설정은 UNICODE로 되어있지만, 실제로 UNICODE를 사용하는 방법은 간단하지 않다.
- C++을 만들 때 기본적인 명령어 대부분은 ASCII 코드를 기반으로 되어있으며, 이를 수정해서 UNICODE도 사용할 수 있도록 변경해야 한다. 특히 문자열이 들어가는 곳이라면 코드를 대부분 변경해 주어야 한다.
- 윈도우 프로그래밍에서는  `char`가 직접적으로 쓰이지 않는다. `char`는 `TCHAR`로 사용하는데, `TCHAR`의 정의를 보면 다음과 같다.
  ```C++
  #ifdef UNICODE
    typedef wchar_t TCHAR;
  #else
    typedef char TCHAR;
  #endif
  ```
  만약 UNICODE를 사용한다면 `wchar_t`형의 `TCHAR`를 사용하고, UNICODE가 아니면 그냥 `char`를 사용한다는 뜻이다.

#### 문자열 자료형
- `char`와 관련된 자료형은 밑과 같다.
    - `TCHAR` : `char`
    - `LPSTR` :`char*`
    - `LPCSTR` : `const char*`
    - `LPWSTR` : `wchar_t*`
    - `LPCWSTR` : `const wchar_t*`
    - `LPCTSTR` : `const wchar_t*` or `const char*`

#### 문자열 자료형 접두사
- `W` : Wide char (16 bit)
- `T` : UNICODE or ASCII
- `C` : constant
- `LP` : Long Pointer
- `STR` : string

#### UNICODE 호환 문자열 함수
- 문자열 함수는 밑과 같이 변경하여 UNICODE와 호환되게 할 수 있다.
    - `strlen` -> `lstrlen`
    - `strcpy` -> `lstrcpy`
    - `strcat` -> `lstrcat`
    - `strcmp` -> `lstrcmp`
    - `sprintf` -> `wsprintf`

#### UNICODE 문자열 입력 매크로
- 비주얼 C++에서 UNICODE를 입력하려면 다음과 같은 매크로를 사용한다.
    - `TEXT("text here")`
    - `_T("text here")`
    - `L"text here"`

## 메인 윈도우
메인 윈도우를 생성하는 소스 코드는 다음과 같다.

```C++
#include <windows.h>

LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);
HINSTANCE g_hInst;
LPCTSTR lpszClass = L"HelloAPI";

int APIENTRY WinMain(HINSTANCE hInstance,
	HINSTANCE hPrevInstance,
	LPSTR lpszCmdParam,
	int nCmdShow)
{
	HWND hWnd;
	MSG Message;
	WNDCLASS WndClass;
	g_hInst = hInstance;

	WndClass.cbClsExtra = 0;
	WndClass.cbWndExtra = 0;
	WndClass.hbrBackground = (HBRUSH)GetStockObject(WHITE_BRUSH);
	WndClass.hCursor = LoadCursor(NULL, IDC_WAIT);
	WndClass.hIcon = LoadIcon(NULL, IDI_APPLICATION);
	WndClass.hInstance = hInstance;
	WndClass.lpfnWndProc = (WNDPROC)WndProc;
	WndClass.lpszClassName = lpszClass;
	WndClass.lpszMenuName = NULL;
	WndClass.style = CS_HREDRAW | CS_VREDRAW;
	RegisterClass(&WndClass);

	hWnd = CreateWindow(lpszClass,			//윈도우클래스 이름
		L"윈도우 프로그래밍",			    //윈도우타이틀
		WS_OVERLAPPEDWINDOW | WS_VISIBLE,   //윈도우스타일
		200, 200,							//윈도우가 보일때 X Y좌표
		600, 600,							//윈도우의 폭과 높이				
		(HWND)NULL,							//부모윈도우 핸들
		(HMENU)NULL,						//윈도우가 가지는 메뉴핸들
		hInstance,							//인스턴스핸들
		NULL);								//여분의 데이터

	ShowWindow(hWnd, nCmdShow);

	while (GetMessage(&Message, 0, 0, 0)) {
		TranslateMessage(&Message);
		DispatchMessage(&Message);
	}
	return Message.wParam;
}

LRESULT CALLBACK WndProc(HWND hWnd, UINT iMessage,
	WPARAM wParam, LPARAM lParam)
{
	LPCTSTR text = L"메인윈도우 생성";
	switch (iMessage) {
    	case WM_PAINT:
    	{
    		PAINTSTRUCT ps;
    		HDC hdc = BeginPaint(hWnd, &ps);
    		TextOut(hdc, 100, 100, text, lstrlen(text));
    		EndPaint(hWnd, &ps);
    		return 0;
    	}
    	case WM_DESTROY:
    		PostQuitMessage(0);
    		return 0;
	}
	return(DefWindowProc(hWnd, iMessage, wParam, lParam));
}
```

### 헤더 파일
```C++
#include <windows.h>
```

- 윈도우 프로그램의 첫 줄은 대부분 이렇게 시작된다. `windows.h` 헤더 파일은 기본적인 자료 타입, API 함수 원형과 상수 등을 정의하며, 그 외 필요한 헤더 파일을 포함하고 있다.

### WinMain 함수
```C++
int APIENTRY WinMain(HINSTANCE hInstance,
	HINSTANCE hPrevInstance,
	LPSTR lpszCmdParam,
	int nCmdShow)
```

- 윈도우 프로그램의 시작점(Entry Point)은 `main`이 아닌 `WinMain`이다.
- `APIENTRY` 지정자는 `_stdcall`형 호출규약을 사용한다는 뜻이다.
- `WinMain` 함수의 4개 매개변수의 의미는 밑에와 같다.
    - `hinstance` : 프로그램의 객체 핸들이다.
    - `hPrevInstance` : 바로 앞에 실행된 현재 프로그램의 객체 핸들이다. 없을 경우에는 `NULL`이 되며, WIN32 에서는 항상 `NULL`이다. 호환성을 위해서 존재하는 매개변수이다.
    - `lpCmdLine` : 명령행으로 입력된 프로그램 매개변수이다. DOS의 `argv` 매개변수에 해당한다.
    - `nCmdShow` : 프로그램이 실행될 형태며 최소화, 보통 모양 등이 전달된다.
- `hInstance` 외 매개변수는 잘 사용하지 않는다. 객체(Instance)는 클래스가 메모리에 실제로 구현된 실체를 의미한다. 윈도우 프로그램은 여러 개의 프로그램이 동시에 실행되는 멀티태스킹일 뿐만 아니라, 하나의 프로그램이 여러 번 실행될 수 있다. 실행되고 있는 각각의 프로그램을 프로그램 객체 또는 인스턴스라고 한다. `hInstance`는 프로그램 자체를 나타내는 핸들로 API 함수에서 수시로 사용된다.
    - 위 소스코드에서는 `WinMain`의 매개변수로 전달된  `hInstance` 값을 전역변수 `g_hInst`에 저장해 두었다. 이는 `hInstance` 값을 `WinMain` 바깥에서도 사용할 수 있도록 하기 위함이다. 
- 윈도우 클래스 이름을 저장하기 위해 문자열 형태(`LPCTSTR`) 전역변수 `lpszClass`에 값을 저장해 두었다.

### WndProc 함수
```C++
LRESULT CALLBACK WndProc(HWND hWnd, UINT iMessage, WPARAM wParam, LPARAM lParam)
```

- `WinMain`은 프로그램을 시작시키고 메인 윈도우를 만들지만 그 이외에 문자열 출력이나 차일드 윈도우 생성 등 실질적인 처리는 대부분 윈도우 프로시저 함수인 `WndProc`에서 이루어진다.
- `WinMain` 함수의 소스코드 내용은 대체로 일정하지만 `WndProc`은 프로그램에 따라 달라진다. 그래서 소스코드를 분석할 때 주의 깊게 봐야 할 부분은 `WndProc` 함수이다.

### WNDCLASS 구조체
- 윈도우 클래스(`WNDCLASS`)에서 의미하는 '클래스'는 C++의 클래스와는 다른 개념으로, 윈도우 클래스는 윈도우의 특성을 정의한 구조체이다.
- `WinMain` 함수에서 하는 가장 중요한 일은 윈도우를 만드는 일이다 - 윈도우가 존재해야 사용자로부터 입력을 받을 수 있고 출력을 보여 줄 수 있기 때문이다.
- 윈도우를 만들려면 `WNDCLASS`를 먼저 등록한 후, `CreateWindow` 함수를 호출해야 한다.
- 모든 윈도우는 `WNDCLASS`를 기반으로 만들어지며, `WNDCLASS`는 만들어질 윈도우의 여러 가지 특성을 정의한다.
- `WNDCLASS`는 `windows.h`에 다음과 같이 정의되어 있는 구조체이다.
  ```C++
  typedef struct tagWNDCLASS
  {
      UINT         style;
      WNDPROC      lpfnWndProc;
      int          cbClsExtra;
      int          cbWndExtra;
      HINSTANCE    hInstance;
      HICON        hIcon;
      HCURSOR      hCursor;
      HBRUSH       hbrBackground;
      LPCSTR       lpszMenuName;
      LPCSTR       lpszClassName;
  } WNDCLASS;
  ```

#### style
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.style = CS_HREDRAW | CS_VREDRAW;
    ..
}
```

- `WNDCLASS`의 `style`은 윈도우의 스타일을 정의한다. 즉, 윈도우가 어떤 형태를 가질 것 인가를 지정하는 멤버이다.
- 가장 많이 사용하는 값이 `CS_HREDRAW`와 `CS_VREDRAW`이다. 이 두 값은 `OR` 연산자(`|`)로 연결하여 사용한다. 이 값들의 의미는 윈도우의 수직(또는 수평) 크기가 변할 경우 윈도우를 다시 그린다는 뜻이다.
- 위 두 값 외에도 많은 값이 올 수 있다.

#### lpfnWndProc
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.lpfnWndProc = (WNDPROC)WndProc;
    ..
}
```

- `lpfnWndProc`은 윈도우의 메시지 핸들러 함수를 지정한다.
- 메시지가 발생할 때마다 `lpfnWndProc`으로 지정한 함수가 호출되며, 이 함수가 모든 메시지를 처리한다.
- 메시지 핸들러 함수의 이름은 임의로 정할 수 있지만, 거의 `WndProc`으로 정해져 있는 편이다.

#### cbClsExtra/cbWndExtra
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.cbClsExtra = 0;
    WndClass.cbWndExtra = 0;
    ..
}
```

- 일종의 예약 영역이다.
- Windows가 내부적으로 사용하며 매우 특수한 목적에 사용되는 여분의 공간이다.
- 예약영역을 사용하지 않을 경우는 `0`으로 지정한다.

#### hInstance
```C++
int APIENTRY WinMain(HINSTANCE hInstance, ..)
{
    ..
    WNDCLASS WndClass;
    WndClass.hInstance = hInstance;
    ..
}
```

- `hInstance`는 이 `WNDCLASS`를 사용하는 프로그램의 번호이며, 이 값은 `WinMain`의 매개변수로 전달된 `hInstance` 값을 그대로 대입해 주면 된다.

#### hIcon
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.hIcon = LoadIcon(NULL, IDI_APPLICATION);
    ..
}
```

- 윈도우가 최소화되었을 경우 출력될 아이콘을 `LoadIocn` 함수를 사용하여 지정한다.
- 사용자가 직접 아이콘을 만들어 사용할 수도 있지만, Windows가 기본적으로 제공하는 아이콘을 사용할 수 있다.

#### hCursor
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.hCursor = LoadCursor(NULL, IDC_WAIT);
    ..
}
```

- 윈도우가 사용할 마우스 커서를 `LoadCursor` 함수를 사용하여 지정한다.
- 사용자가 직접 커서를 만들어 사용할 수도 있지만, Windows가 기본적으로 제공하는 커서를 사용할 수 있다.

#### hbrBackground
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.hbrBackground = (HBRUSH)GetStockObject(WHITE_BRUSH);
    ..
}
```

- 윈도우의 배경색을 지정한다 - 정확히는, 윈도우의 배경색을 채색할 브러시를 지정하는 멤버이다.
- `GetStockObject`라는 함수를 사용하여 윈도우에서 기본적으로 제공하는 브러시를 지정할 수 있다.
- 지정할 수 있는 브러시는 여러 가지 종류가 있지만, 가장 일반적인 흰색 배경(`WHITE_BRUSH`)이 많이 사용된다.

#### lpszMenuName
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.lpszMenuName = NULL;
    ..
}
```

- 프로그램이 사용할 메뉴를 지정한다.
- 메뉴는 프로그램 코드에서 만드는 것이 아니라, 리소스 에디터에 의해 별도로 만들어진 후 링크 시에 같이 합쳐진다.
- 메뉴를 사용하지 않을 경우, 이 멤버에 `NULL` 값을 대입해 주면 된다.

#### lpszClassName
```C++
LPCTSTR lpszClass = L"HelloAPI";

int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    WndClass.lpszClassName = lpszClass;
    ..
}
```

- 윈도우 클래스의 이름을 정의한다.
- 여기서 지정한 이름은 `CreateWindow` 함수에 전달되며, `CreateWIndow` 함수는 윈도우 클래스에서 정의한 특성값을 참조하여 윈도우를 만든다.
- 윈도우 클래스의 이름은 보통 실행 파일의 이름과 일치시켜 작성한다.

### RegisterClass 함수
```C++
int APIENTRY WinMain(..)
{
    ..
    WNDCLASS WndClass;
    // 윈도우 클래스의 멤버들 모두 등록 후
    RegisterClass(&WndClass);
    ..
}
```

- 정의된 `WndClass`를 등록하기 위해 `RegisterClass`에 매개변수로 `WndClass` 구조체의 번지를 넘겨주면 된다.
  ```C++
  ATOM RegisterClass(CONST WNDCLASS *lpWndClass);
  ```

### CreateWindow 함수
- 윈도우 클래스를 등록한 후 등록된 윈도우 클래스를 기준으로 `CreateWindow` 함수를 사용하여 윈도우를 생성하면 된다.
  ```C++
  HWND CreateWindow(
      lpszClassName,	//윈도우클래스 이름
      lpszWindowName,	//윈도우타이틀
      dwStyle,			//윈도우스타일
      x, y,				//윈도우가 보일때 X Y좌표
      nWidth, nHeight,	//윈도우의 폭과 높이
      hWndParent,		//부모윈도우 핸들
      hMenu,			//윈도우가 가지는 메뉴핸들
      hInstance,		//인스턴스핸들
      lpParam			//여분의 데이터
  )
  ```
  - `CreateWindow` 함수는 윈도우에 관한 모든 정보를 메모리에 만든 후, 윈도우 핸들을 리턴값으로 넘겨준다. 넘겨지는 윈도우 핸들은 `hWnd`라는 지역변수에 저장되었다가 윈도우를 참조하는 모든 함수의 매개변수로 사용된다.
  - `CreateWindow` 함수로 만든 윈도우는 어디까지나 메모리상에만 있을 뿐이며, 아직까지 화면에 출력되지 않는다.
  - 예시 소스코드에는 밑과 같이 작성되어있다.
  ```C++
  LPCTSTR lpszClass = L"HelloAPI";
  
  int APIENTRY WinMain(..)
  {
      ..
      hWnd = CreateWindow(
        lpszClass,							//윈도우클래스 이름
      	L"윈도우 프로그래밍",			    //윈도우타이틀
      	WS_OVERLAPPEDWINDOW | WS_VISIBLE,   //윈도우스타일
      	200, 200,							//윈도우가 보일때 X Y좌표
      	600, 600,							//윈도우의 폭과 높이				
      	(HWND)NULL,							//부모윈도우 핸들
      	(HMENU)NULL,						//윈도우가 가지는 메뉴핸들
      	hInstance,							//인스턴스핸들
      	NULL);								//여분의 데이터
      ..
  }
  ```

#### lpszClassName
- 생성하고자 하는 윈도우의 클래스를 지정하는 문자열이다.
- 앞에서 정의한 `WndClass.lpszClassName` 멤버의 값과 동일하게 입력하면 된다.
- 예시 소스코드에는 `lpszClass` 문자열 전역변수에 미리 윈도우클래스 이름을 저장해놨으니, 이 변수를 그대로 넘겨준다.

#### lpszWindowName
- 윈도우의 타이틀바에 나타날 문자열이다.

#### dwStyle
- 만들고자 하는 윈도우의 형태를 지정하는 매개변수이다.
- 일종의 비트 필드 값이며, 거의 수십 개를 헤아리는 매크로 상수가 정의되어 있다.
    - 이 상수들을 OR 연산자로 연결하여 윈도우의 다양한 형태를 지정할 수 있다.
- 윈도우가 경계선을 가질 것인가, 타이틀바를 가질 것인가, 스크롤바의 유무 등을 세세하게 지정할 수 있다.
- 가능한 스타일 값에 관한 자세한 내용은 `MSDN`을 참조하되, `WS_OVERLAPPEDWINDOW`를 사용하면 가장 무난한 윈도우 설정 상태가 된다.
    - 시스템 메뉴, 최대/최소 버튼, 타이틀바, 경계선을 가진 윈도우를 만들어 준다.

#### x, y, nWidth, nHeight
- 이름이 의미하듯이, 윈도우의 크기와 위치를 지정하는 매개변수들이다.
- 픽셀 단위를 사용한다.
- (x, y) 좌표는 메인 윈도우의 경우에 전체 화면을 기준으로 하며, 차일드 윈도우는 부모 윈도우의 왼쪽 상단을 기준으로 한다.
- 정수값을 바로 지정해도 되며, 또는 `CW_USEDEFAULT`를 사용하여 Windows가 알아서 적당한 크기와 위치를 설정하게 할 수 있다.

#### hWndParent
- 부모 윈도우가 있을 경우 부모 윈도우의 핸들을 지정해 준다.
- MDI 프로그램이나 팝업 윈도우끼리 수직적인 상하관계를 가짐으로서 부자(Parent-Child) 관계가 성립되는데, 이 관계를 지정해주는 매개변수가 `hWndParent`이다.
- 부모 윈도우가 없을 경우에 `NULL`로 지정하면 된다.

#### hMenu
- 윈도우에서 사용할 메뉴의 핸들을 지정한다.
- `WndClass`에도 메뉴를 지정하는 멤버가 있는데, `WndClass`의 메뉴는 그 윈도우 클래스를 기반으로 하는 모든 윈도우에서 사용되는 반면, `hMenu`로 지정한 메뉴는 `CreateWindow` 함수로 만들어지는 윈도우에서만 사용된다.
- `WndClass`에서 지정한 메뉴를 그대로 사용하려면, `hMenu`의 값을 `NULL`로 지정하면 된다.
- `WndClass`에서 지정한 메뉴 대신 다른 메뉴를 사용하려면, `hMenu`에 원하는 메뉴 핸들을 주면 된다.
- 메뉴 없는 프로그램을 만들려면 `WndClass`와 `CreateWindow`에 메뉴를 지정하지 않으면 된다.

#### hInstance
- 윈도우를 만드는 주체, 즉, 프로그램의 핸들을 지정한다.
- `WinMain`의 매개변수로 전달된 `hInstsance`를 대입해 주면 된다.

#### lpParam
- `CREATESTRUCT`라는 구조체의 번지이다.
- #todo 특수한 목적에 사용된다. 보통은 `NULL` 값을 사용한다.

### ShowWindow 함수
- `CreateWindow` 함수로서 준비된 윈도우를 실제로 화면에 출력하려면 `ShowWindow` 함수를 사용해야 한다.
  ```C++
  BOOL ShowWindow(hWnd, nCmdShow);
  ```
- `hWnd` 매개변수는 화면으로 출력하고자 하는 윈도우의 핸들이며, `CreateWindow` 함수가 리턴한 핸들을 그대로 넘겨 받으면 된다.
- `nCmdShow` 매개변수는 윈도우를 화면에 출력하는 방법을 지정하며, 다음과 같은 매크로 상수를 받는다.
    - `SW_HIDE` : 윈도우를 숨긴다.
    - `SW_MINIMIZE` : 윈도우를 최소화 시킨다.
    - `SW_MAXIMIZE` : 윈도우를 최대화 시킨다.
    - `SW_SHOW` : 윈도우를 활성화시켜 보여 준다.
    - `SW_SHOWNORMAL` : 윈도우를 원래 크기와 위치로 보여 준다.
- `nCmdShow` 매개변수에는 `WinMain` 함수의 매개변수로 전달된 `nCmdShow` 값을 그대로 넘겨주기만 하면 된다.
- 예시 소스코드에는 밑과 같이 `ShowWindow` 함수를 호출한다.
  ```C++
  int APIENTRY WinMain(nCmdShow, ..)
  {
      ..
      HWND hWnd;
      hWnd = CreateWindow(..);
      ShowWindow(hWnd, nCmdShow);
      ..
  }
  ```
- `ShowWindow` 함수까지 실행하면 화면에 윈도우가 출력된다. 이후부터는 메시지 루프가 시작되며, 프로그램이 사용자와 Windows 그리고 다른 프로그램과 정보를 교환하며 실행된다.
  ![[visual_cpp_window_process.png]]

### 메시지 루프
- Windows를 **메시지 구동 시스템(Message Driven System)** 이라고 하는데, 이 점이 DOS와 가장 뚜렷한 대비를 이루는 특징이다. DOS에서는 프로그래머에 의해 미리 입력된 일련의 명령을 순서대로 실행하는 순차적 실행방법을 사용하는 반면, Windows에서는 프로그램의 실행순서가 명확하게 정해져 있지 않으며 상황에 따라 달라진다는 것이다. 여기서 말하는 "상황"이란, 바로 어떤 메시지가 주어졌는가를 뜻한다.
- **메시지(Message)** : 사용자나 시스템 내부적인 동작에 의해 발생한 일체의 변화에 대한 정보를 뜻한다.
    - 예를 들어, 사용자가 마우스의 버튼을 눌렀다거나, 키보드를 눌렀다거나, 윈도우가 최소화 되었다거나 하는 변화에 대한 정보가 메시지이다.
    - 메시지가 발생하면 프로그램에서는 메시지가 어떤 정보를 담고 있는가를 분석하여, 어떤 루틴을 호출할 것인가를 결정한다. 즉, 순서를 따르지 않고 주어진 메시지에 대한 반응을 정의하는 방식으로 프로그램이 실행된다.
- 윈도우 프로그램에서 메시지를 처리하는 부분을 **메시지 루프(Message Loop)** 라고 하며, 보통 `WinMain` 함수의 끝에 다음과 같은 형식으로 존재한다.
  ```C++
  int APIENTRY WinMain(..)
  {
      ..
      MSG Message;
      
      while (GetMessage(&Message, 0, 0, 0)) {
          TranslateMessage(&Message);
          DispatchMessage(&Message);
      }
      
      return Message.wParam;
  }
  ```
- 메시지 루프에서 하는 일은 메시지를 꺼내고, 필요한 경우 형태를 조금 바꾼 후 응용 프로그램으로 메시지를 전달하는 것 뿐이다. 이 과정은 `WM_QUIT` 메시지가 전달될 때까지 (프로그램이 종료될 때까지) 반복된다.
- 다르게 정리하면, 메시지 루프가 하는 일이란 메시지 큐에서 메시지를 꺼내서, 꺼낸 메시지를 메시지 핸들러 함수로 보내는 것이다.
- 메시지 루프는 3개의 함수호출로 이루어져 있으며, 전체 루프는 `while`문으로 싸여 있다.

#### GetMessage
- `GetMessage` 함수는 시스템이 유지하는 메시지 큐에서 메시지를 읽어 들인다.
  ```C++
  BOOL GetMessage(LPMSG lpMsg, HWND hWnd, UINT wMsgFilterMin, UINT wMsgFilterMax);
  ```
- 읽어 들인 메시지는 첫 번째 매개변수가 지정하는 `MSG` 구조체에 저장된다.
- 이 함수는 읽어들인 메시지가 프로그램을 종료하라는 `WM_QUIT`일 경우 `False`를 리턴한다. 그 외에 메시지에 대해서는 `True`를 리턴한다.
- 프로그램이 종료되어 `WM_QUIT` 메시지가 읽혀질 때까지 전체 `while` 루프는 계속 실행된다.
- #todo 나머지 3개의 매개변수는 읽어 들일 메시지의 범위를 지정하는데, 잘 사용되지 않으므로 일단 무시한다??

#### TranslateMessage
- `TranslateMessage` 함수는 키보드 입력 메시지를 가공하여 프로그램에서 쉽게 쓸 수 있도록 해준다.
  ```C++
  BOOL TranslateMessage(CONST MSG *lpMsg);
  ```
- `Windows`는 키보드의 어떤 키가 눌러졌다거나 떨어졌을 때 키보드 메시지를 발생시키는데, 이 함수는 눌림(`WM_KEYDOWN`)과 떨어짐(`WM_KEYUP`)이 연속적으로 발생할 때 문자가 입력되었다는 메시지(`WM_CHAR`)를 만드는 역할을 한다.
- 예를 들어, `A`를 누른 후 `A`를 떼면, `A` 문자가 입력되었다는 메시지를 만들어낸다.

#### DispatchMessage
- `DispatchMessage` 함수는 시스템 메시지 큐에서 꺼낸 메시지를 프로그램의 메시지 핸들러 함수(`WndProc`)에 전달하는 역할을 가진다.
- 이 함수에 의해 메시지가 프로그램으로 전달되며, 프로그램에서는 전달된 메시지를 점검하여 다음 동작을 결정하게 된다.

#### MSG 구조체
- 실제 메시지 처리는 메시지 핸들러 함수인 `WndProc`에서 수행한다.
- 메시지는 시스템 변화에 대한 정보며, `MSG`라는 구조체에 보관된다. `MSG` 구조체는 다음과 같이 정의되어 있다.
  ```C++
  typedef struct tagMSG
  {
      HWNDh		Wnd;		// 메시지를 받을 윈도우 핸들
      UINT		message;	// 메시지 종류
      WPARAM	wParam;		// 32bit 값으로, 이벤트 메시지와 윈도우 ID 정보를 갖는다.
      LPARAM	lParam;		// 32 bit 윈도우 핸들
      DWORD		time;		// 메시지 발생 시간
      POINT		pt;			// 메시지 발생 시 마우스 위치
  } MSG;
  ```

#### 메시지 루프의 흐름
- `messsage` 멤버를 읽음으로써 메시지 종류를 파악하며, `message` 값에 따라 프로그램의 반응이 달라진다.
- `GetMessage` 함수는 읽은 메시지를 `MSG` 구조체에 대입해 주며, 이 구조체는 `DistpatchMessage` 함수에 의해 응용 프로그램의 메시지 핸들러 함수인 `WndProc`으로 전달된다.
- 메시지 루프가 종료되면 프로그램은 마지막으로 `Message.wParam`을 리턴하고 종료한다. 이 값은 `WM_QUIT` 메시지로부터 전달된 코드이다.

##### 메시지와 그 의미
- 메시지는 실제로 하나의 정수값으로 표현된다.
- 메시지의 종류는 다양하며 `windows.h` 헤더파일에 메시지별로 매크로 상수를 정의되어있다.
- 메시지는 `WM_` 접두어로 시작된다.
- `WM_QUIT` : 프로그램을 끝낼 때 발생하는 메시지
- `WM_LBUTTONDOW` : 마우스 좌클릭 시 발생
- `WM_CHAR` : 키보드 문자 입력 시 발생
- `WM_PAINT` : 화면을 다시 그려야 할 필요가 있을 때 발생
- `WM_DESTROY` : 윈도우가 메모리에서 파괴될 때 발생
- `WM_CREATE` : 윈도우가 처음 만들어질 때 발생

### 윈도우 프로시저
- 윈도우 프로시저(`WndProc`)는 메시지가 발생할 때 프로그램의 반응을 처리하는 일을 하는 메시지 핸들러 함수이다.
- `WndProc`는 `WinMain`에서 호출하는 것이 아니라 Windows에 의해 호출된다.
- `WinMain` 내의 메시지 루프는 메시지를 메시지 핸들러 함수로 보내 주기만 할 뿐이고, `WndProc`는 메시지가 입력되면 Windows에 의해 호출되어 메시지를 처리한다.
- `WndProc`은 운영체제에 의해 호출되기 때문에 CALLBACK 함수라고도 한다.
- `WndProc`의 매개변수는 모두 4개로, `MSG` 구조체의 멤버 4개와 동일하다.
    - `hWnd`는 메시지를 받을 위도우의 핸들이다.
    - `iMessage`는 어떤 종류의 메시지인가 (어떤 변화가 발생했는가)에 관한 정보를 가진다.
    - `iMessage`의 값이 `WM_MOVE`이면 윈도우의 위치가 변경되었음을 알리는 것이고, `WM_DESTORY면` 윈도우가 파괴(종료)되었음을 알리는 것이다.
    - `wParam`과 `lParam`은 메시지의 부가적인 정보를 가진다.
        - 예를 들어, 마우스 버튼이 눌러졌다는 `WM_LBUTTONDOWN` 메시지가 입력되었다면 메시지가 발생한 당시에 마우스 버튼의 클릭된 위치, 키보드 상황 등의 정보를 가진다.
        - `WM_CHAR` 메시지 발생시 어떤 키가 입력되었는가에 대한 정보를 가진다.

#### 윈도우 프로시저 구조
- `WndProc`의 구조는 다음과 같은 형태를 가진다. 메시지의 종류에 따라 다중 분기하여 메시지별로 처리를 진행한다.
  ```C++
  LRESULT CALLBACK WndProc(HWND hWnd, UINT iMessage, WPARAM wParam, LPARAM lParam) {
  	switch (iMessage) {
  	case Msg1:
  		// 처리 1
  		return 0;
  	case Msg2:
  		// 처리 2
  		return 0;
  	..
  	case WM_DESTORY:
  		PostQuitMessage(0);
  		return 0;
  	}
  	return(DefWindowProc(hWnd, iMessage, wParam, lParam));
  }
  ```
- `Msg1` 메시지가 전달되면 '처리 1'을 한 후 리턴하고, `Msg2` 메시지가 전달되면 '처리 2'를 한 후 리턴한다.
- `case`문은 프로그램이 처리할 메시지의 수만큼 반복된다.
- 제일 끝에 있는 `DefWindowProc` 함수는 `WndProc`에서 처리하지 않은 나머지 메시지에 관한 처리를 해준다.
	- 예를 들어, 시스템 메뉴를 더블클릭하여 프로그램을 종료할 시 별도로 지정하지 않아도 `DefWindowProc` 함수에서 알아서 해준다.
	- 윈도우의 이동이나 크기 변경 같은 기본적인 처리는 직접 해줄 필요 없이 `DefWindowProc`으로 넘기면 된다.
- `WM_DESTORY` 메시지는 사용자가 시스템 메뉴를 더블클릭하거나 `[ALT + F4]`를 눌러 프로그램을 끝내려고 할 때 발생하는 메시지이다.
	- `WndProc`에서 `WM_DESTORY` 메시지가 발생하면 `PostQuitMessage` 함수를 호출하여 `WM_QUIT` 메시지를 시스템 큐에 보낸다.
	- `WM_QUIT` 메시지가 입력되면 메시지 루프의 `GetMessage` 함수 리턴값이 `False`가 되어 프로그램이 종료된다.
- `WM_DESTROY` 외의 메시지는 모두 `DefWindowProc` 함수로 전달되는데 이 함수에서 디폴트 처리를 수행해준다.
- `WndProc`에서 메시지를 처리할 경우 반드시 `0`을 리턴 해줘야 한다. 또한, `DefWindowProc` 함수가 메시지를 처리할 경우 이 함수가 리턴한 값을 `WndProc` 함수가 다시 리턴해줘야 한다.

#### 윈도우 프로시저 순서도
![[visual_cpp_window_procedure_flow.png]]

### 문자열 출력하기
- 윈도우 프로그램에서 무언가를 출력하려면 반드시 DC (Device Context)가 필요하다.
- Device Context는 출력에 필요한 모든 정보를 갖고 있는 데이터 구조체이다.
	- 출력에 필요한 정보란 문자열의 모양을 지정하는 폰트, 선의 색상과 굵기, 채움 무늬와 색상, 그리기 모드 등을 뜻한다.
- 화면에 여러 개의 윈도우가 겹쳐지는 경우 그리고자 하는 윈도우의 클라이언트 영역의 좌표 정보가 필요하고, 다른 윈도우에 가려지는 부분은 그리지 않아야 하는데, 이러한 처리를 선 그리기 함수로 직접 하는 것은 아주 복잡하기 때문에 Device Context를 통해 간단히 해결한다.
	- 따라서, 윈도우 프로그램에서는 윈도우나 화면 또는 프린터에 출력하려면 각각 윈도우 DC, 화면 DC, 프린터 DC가 필요하다.
- 윈도우 클라이언트 영역에 문자열을 출력하려면 `TextOut` Win32 API 함수를 사용하면 된다.
  ```C++
  BOOL TextOut(hdc, nXStart, nYStart, lpszString, cbString)
  ```
	- 첫 번째 인자는 Device Context의 핸들인 `hdc`이다. `TextOut` 함수를 포함해서 화면에 무언가를 출력하는 모든 함수의 첫 번째 인수는 항상 `hdc`이다.
	- `nXStart`, `hYStart`는 문자열이 출력될 좌표이다.
	- `lpszString`은 출력할 문자열을 담고 있는 문자열 포인터이다.
	- `cbString`은 출력할 문자열의 길이 이다. `TextOut` 함수는  `NULL` 종료 문자열을 사용하지 않음으로, 문자열의 길이를 인수로 반드시 밝혀 주어야 한다.

#### 문자열 출력 소스코드 예시
```C++
LRESULT CALLBACK WndProc(HWND hWnd, UINT iMessage, WPARAM wParam, LPARAM lParam) {
	..
	switch (iMessage) {
		..
    	case WM_PAINT:
    	{
    		PAINTSTRUCT ps;
    		HDC hdc = BeginPaint(hWnd, &ps);
    		TextOut(hdc, 100, 100, text, lstrlen(text));
    		EndPaint(hWnd, &ps);
    		return 0;
    	}
    	..
	}
	..
}
```

- `WM_PAINT` 메시지는 윈도우에 무언가를 그리려고 할 때 발생되는 메시지이다.
- 여기서 `PAINTSTRUCT`는 윈도우 클라이언트 영역에 무언가를 그리려고 할 때 필요한 정보를 담고 있는 구조체이다.
	- 예: 핸들, 배경을 지울 것인지 여부, 클라이언트 영역 좌표 등
- `BeginPaint()` 함수는 그리는데 필요한 정보를 `PAINTSTRCUT` 구조체에 넣어서 윈도우에 그릴 준비를 한 후, 리턴값으로 DC (Device Context) 핸들을 가져온다.
- `TextOut()` 함수가 문자열을 출력한 후 `EndPaint()` 함수는 DC 핸들을 해제한다.
- 출력방법을 정리하면 다음과 같다.
	1. 운영체제에 DC를 요청한다.
	2. 운영체제가 제공한 DC를 매개변수로 하는 API 함수를 호출하여 출력한다.
	3. DC 사용이 끝났음을 운영체제에 알린다.

### 메인 윈도우 생성 결과
![[visual_cpp_chapter1_main_window.png]]

## 차일드 윈도우
- 차일드 윈도우에는 두 가지 종류가 있다.
	1. 버튼이나 콤보 박스와 같은 컨트롤 형태의 차일드 윈도우
	2. 일반 윈도우 형태의 차일드 윈도우 (메인 윈도우 안에 또 다른 윈도우)
- 밑에 코드는 메인 윈도우 안에 차일드 윈도우가 나타나도록 하는 소스코드 이다.

```C++
#include <windows.h>

LRESULT CALLBACK WndProc(HWND,UINT,WPARAM,LPARAM);
LRESULT CALLBACK ChildWndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam);

HINSTANCE g_hInst;
LPCTSTR lpszClass = L"HelloAPI";
LPCTSTR ChildClassName  = L"ChildWin";

int APIENTRY WinMain(HINSTANCE hInstance,
					 HINSTANCE hPrevInstance,
					 LPSTR lpszCmdParam,
					 int nCmdShow)
{
	HWND hWnd;
	MSG Message;
	WNDCLASS WndClass;
	g_hInst=hInstance;
	
	WndClass.cbClsExtra=0;
	WndClass.cbWndExtra=0;
	WndClass.hbrBackground=(HBRUSH)GetStockObject(WHITE_BRUSH); 
	WndClass.hCursor=LoadCursor(NULL,IDC_ARROW);    
	WndClass.hIcon=LoadIcon(NULL,IDI_APPLICATION);
	WndClass.hInstance=hInstance;
	WndClass.lpfnWndProc=(WNDPROC)WndProc;
	WndClass.lpszClassName=lpszClass;
	WndClass.lpszMenuName=NULL;
	WndClass.style=CS_HREDRAW | CS_VREDRAW;
	RegisterClass(&WndClass);     //메인윈도우 클래스 등록

	WndClass.lpfnWndProc =ChildWndProc;      //차일드 윈도우 프로시저
	WndClass.lpszClassName =ChildClassName; //차일드 윈도우 클래스이름
	RegisterClass(&WndClass); 

	hWnd=CreateWindow(
					lpszClass,							//윈도우클래스 이름
					L"윈도우 프로그래밍",			    //윈도우타이틀
					WS_OVERLAPPEDWINDOW | WS_VISIBLE,   //윈도우스타일
					200, 200,							//윈도우가 보일때 X Y좌표
					600, 600,							//윈도우의 폭과 높이				
					(HWND)NULL,							//부모윈도우 핸들
					(HMENU)NULL,						//윈도우가 가지는 메뉴핸들
					hInstance,							//인스턴스핸들
					NULL);								//여분의 데이터

 	   ShowWindow(hWnd,nCmdShow);
	
	while(GetMessage(&Message,0,0,0)) {
		TranslateMessage(&Message);
		DispatchMessage(&Message);
	}
	return Message.wParam;
}

LRESULT CALLBACK WndProc(HWND hWnd, UINT iMessage,
						 WPARAM wParam, LPARAM lParam)
{
	LPCTSTR text = L"메인윈도우 생성";
	switch(iMessage) {
		case WM_PAINT:
			{
				PAINTSTRUCT ps;
				HDC hdc = BeginPaint(hWnd, &ps);
				TextOut(hdc,100, 100, text, lstrlen(text));
				EndPaint(hWnd,&ps);
				return 0;
			}
		case WM_CREATE:
		{
			HWND hChildWnd = CreateWindow( 
				ChildClassName,     				// 차일드 윈도우 클래스 이름 
				L"차일드 윈도우",            		// 윈도우 타이틀 
				WS_OVERLAPPEDWINDOW | WS_CHILD,		// 윈도우 스타일 
				150, 150,							// 윈도우 보일 때 x,y 좌표 
				260, 200,							// 윈도우 width, height
				hWnd,								// 부모 윈도우
				(HMENU) 1000,						// 차일드 윈도우ID 
				g_hInst,							// 인스턴스 핸들 
				(LPVOID) NULL);						// 여분의 데이터

			if (!hChildWnd) 	return -1;

			ShowWindow(hChildWnd, SW_SHOW); 
			return 0;
		}
		case WM_DESTROY:
			PostQuitMessage(0);
			return 0;
		}
	return(DefWindowProc(hWnd,iMessage,wParam,lParam));
}
LRESULT CALLBACK ChildWndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
{
	LPCTSTR text = L"차일드 윈도우생성";
	switch(message)
	{
		case WM_PAINT:
		{
			PAINTSTRUCT ps;
			HDC hdc = BeginPaint(hWnd,&ps);
			TextOut(hdc,10, 10, text, lstrlen(text));
			EndPaint(hWnd,&ps);
			return 0;
		}
	}
	return DefWindowProc(hWnd, message, wParam, lParam);
}
```

- 메인 윈도우는 부모 윈도우가 없는 최상위 윈도우지만, 차일드 윈도우(Child Window)는 부모 윈도우(Parent Window)에 포함되어 있으므로 부모 윈도우에서 만들어야 한다 - 그 말은, 부모 윈도우 프로시저 안에서 차일드 윈도우를 생성하는 함수들을 실행한다는 것이다.

### 차일드 윈도우 프로시저 작성
- 차일드 윈도우 프로시저를 `ChildWndProc()`라는 함수로서 정의한다. 차일드 윈도우 프로시저는 `WM_PAINT` 메시지로 문자열을 화면에 표출하는 기능을 구현하며, 그 외 모든 메시지는 `DefWindowProc()` 함수로서 Default값으로 처리한다.

### 차일드 윈도우 클래스 등록
- 윈도우 클래스라는 용어에서 가리키는 클래스는 프로그래밍에서 말하는 클래스와는 다른 개념이다 - 윈도우 클래스는 윈도우의 특성을 정의한 구조체이다.
- 윈도우 클래스는 부류 내지는 종류, 등급이라고 할 수 있다.
- 메인 윈도우와 마찬가지로 `WinMain()` 함수에서 윈도우 클래스를 정의하면서 윈도우에 대한 속성들을 입력하고 `RegisterClass()` 함수로 정의된 윈도우 클래스를 등록한다.

### 차일드 윈도우 생성
- 차일드 윈도우는 메인 윈도우와 마찬가지로 `CreateWindow()` 함수를 사용해서 윈도우에 대한 정보가 담긴 윈도우 객체를 생성하고, `ShowWindow()` 함수로 화면에 차일드 윈도우를 그린다.
  ![[visual_cpp_chapter1_child_window_spec.png]]
- 차일드 윈도우의 생성은 메인 윈도우 프로시저 `WndProc()` 함수 안에서 구현되며, `hChildWnd` 변수 안에 차일드 윈도우의 핸들이 담긴다.
- 차일드 윈도우는 캡션을 가지고 있고, 크기 조절도 가능하다. 메인 윈도우의 차일드로 존재한다는 것을 제외하고 메인 윈도우와 모두 같다.
- 차일드 윈도우는 부모 윈도우 바깥으로 나갈 수 없다.

### 차일드 윈도우 생성 결과
![[visual_cpp_chapter1_child_window.png]]

## 버튼 사용하기
```C++
#include <windows.h>

#define ID_OK_BTN	2000

HINSTANCE g_hInst;
LPCTSTR lpszClass = L"HelloAPI";
LPCTSTR ChildClassName = L"ChildWin";

LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);
LRESULT CALLBACK ChildWndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam);

int APIENTRY WinMain(HINSTANCE hInstance,
	HINSTANCE hPrevInstance,
	LPSTR lpszCmdParam,
	int nCmdShow)
{
	HWND hWnd;
	MSG Message;
	WNDCLASS WndClass;
	g_hInst = hInstance;

	WndClass.cbClsExtra = 0;
	WndClass.cbWndExtra = 0;
	WndClass.hbrBackground = (HBRUSH)GetStockObject(WHITE_BRUSH);
	WndClass.hCursor = LoadCursor(NULL, IDC_ARROW);
	WndClass.hIcon = LoadIcon(NULL, IDI_APPLICATION);
	WndClass.hInstance = hInstance;
	WndClass.lpfnWndProc = (WNDPROC)WndProc;
	WndClass.lpszClassName = lpszClass;
	WndClass.lpszMenuName = NULL;
	WndClass.style = CS_HREDRAW | CS_VREDRAW;
	RegisterClass(&WndClass);					// 메인 윈도우 클래스 등록

	WndClass.lpfnWndProc = ChildWndProc;
	WndClass.lpszClassName = ChildClassName;
	RegisterClass(&WndClass);					// 차일드 윈도우 클래스 등록

	hWnd = CreateWindow(						// 메인 윈도우 객체 생성
		lpszClass,								// 윈도우클래스 이름
		L"윈도우 프로그래밍",						// 윈도우타이틀
		WS_OVERLAPPEDWINDOW | WS_VISIBLE,		// 윈도우스타일
		200, 200,								// 윈도우가 보일때 X Y좌표
		600, 600,								// 윈도우의 폭과 높이				
		(HWND)NULL,								// 부모윈도우 핸들
		(HMENU)NULL,							// 윈도우가 가지는 메뉴핸들
		hInstance,								// 인스턴스 핸들
		NULL);									// 여분의 데이터

	ShowWindow(hWnd, nCmdShow);					// 메인 윈도우 그리기

	while (GetMessage(&Message, 0, 0, 0)) {
		TranslateMessage(&Message);
		DispatchMessage(&Message);
	}
	return Message.wParam;
}

LRESULT CALLBACK WndProc(HWND hWnd, UINT iMessage,
	WPARAM wParam, LPARAM lParam)
{
	LPCTSTR text = L"메인윈도우 생성";
	switch (iMessage) {
	case WM_PAINT:
	{
		PAINTSTRUCT ps;
		HDC hdc = BeginPaint(hWnd, &ps);
		TextOut(hdc, 100, 100, text, lstrlen(text));
		EndPaint(hWnd, &ps);
		return 0;
	}
	case WM_CREATE:
	{
		HWND hChildWnd = CreateWindow(			// 차일드 윈도우 생성
			ChildClassName,						// 윈도우 클래스 이름 
			L"차일드 윈도우",						// 윈도우 타이틀 
			WS_OVERLAPPEDWINDOW | WS_CHILD,		// 윈도우 스타일 
			150, 150,							// 윈도우 x,y 좌표 
			260, 200,							// 윈도우 width,height
			hWnd,								// 부모 윈도우 핸들
			(HMENU)1000,						// 차일드 윈도우ID 
			g_hInst,							// 인스턴스 핸들 
			(LPVOID)NULL);						// 여분의 데이터			

		ShowWindow(hChildWnd, SW_SHOW);

		hChildWnd = CreateWindow(				// 차일드 윈도우 생성
			L"button",							// 윈도우 클래스 이름 
			L"지역대학",							// 윈도우 타이틀 
			WS_CHILD | WS_VISIBLE,				// 윈도우 스타일 
			20, 400,							// 윈도우 x,y 좌표 
			100, 30,							// 윈도우 폭, 높이
			hWnd,								// 부모 윈도우 핸들
			(HMENU)ID_OK_BTN,					// 컨트롤 ID
			g_hInst,							// 인스턴스 핸들 
			(LPVOID)NULL);						// 여분의 데이터

		if (!hChildWnd) 	return -1;
		return 0;
	}
	case WM_COMMAND:
	{
		if (LOWORD(wParam) == ID_OK_BTN)
		{
			MessageBox(hWnd, L"[지역대학] 버튼이 클릭되었다", L"지역대학", MB_OK);
		}

		return 0;
	}
	case WM_DESTROY:
		PostQuitMessage(0);
		return 0;
	}
	return(DefWindowProc(hWnd, iMessage, wParam, lParam));
}
LRESULT CALLBACK ChildWndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
{
	LPCTSTR text = L"차일드 윈도우생성";
	switch (message)
	{
	case WM_PAINT:
	{
		PAINTSTRUCT ps;
		HDC hdc = BeginPaint(hWnd, &ps);
		TextOut(hdc, 10, 10, text, lstrlen(text));
		EndPaint(hWnd, &ps);
		return 0;
	}

	}

	return DefWindowProc(hWnd, message, wParam, lParam);
}
```

### 버튼 컨트롤
- 윈도우는 화면에 그려지는 창 뿐만이 아니라 윈도우에 일정한 영역을 차지하며 자신의 고유 메시지를 처리하는 컨트롤(Control)도 포함한다.
- 컨트롤은 독립적으로 사용될 수 없고, 반드시 차일드 윈도우로만 존재한다.
- 컨트롤은 운영체제에서 제공해주기 때문에 별도로 윈도우 클래스를 만들 필요가 없다.
- Windows에서 제공하는 컨트롤은 다음과 같다.
	- button (버튼, 체크, 라디오)
	- static (텍스트)
	- scrollbar (스크롤바)
	- edit (에디터)
	- listbox (리스트 박스)
	- combobox (콤보 박스)
- 컨트롤은 `CreateWindow()` 함수의 첫 번째 매개변수로 운영체제에서 제공해준 컨트롤의 윈도우 클래스 이름만 지정함으로서 간단히 만들 수 있다.
- `CreateWindow()` 함수는 `WM_CREATE` 메시지가 발생했을 때 호출되며, 이 함수가 호출됨으로 컨트롤이 생성된다.

#### 버튼 컨트롤 매개변수
```C++
hChildWnd = CreateWindow(				// 버튼 컨트롤 차일드 윈도우 생성
	L"button",							// 윈도우 클래스 이름 
	L"지역대학",							// 윈도우 타이틀 
	WS_CHILD | WS_VISIBLE,				// 윈도우 스타일 
	20, 400,							// 윈도우 x,y 좌표 
	100, 30,							// 윈도우 폭, 높이
	hWnd,								// 부모 윈도우 핸들
	(HMENU)ID_OK_BTN,					// 컨트롤 ID
	g_hInst,							// 인스턴스 핸들 
	(LPVOID)NULL);						// 여분의 데이터
```

1. `button` : 첫 번째 매개변수는 윈도우 클래스 이름으로, 운영체제에서 버튼 컨트롤에 대해 미리 정해준 값이다.
2. `지역대학` : 윈도우 타이틀바에 표시될 캡션이다. 컨트롤 종류에 따라 캡션의 위치가 달라진다. 일반 버튼 컨트롤 같은 경우 버튼 위에 캡션이 나타나며, 체크  또는 라디오 버튼 컨트롤은 버튼 왼쪽에 캡션이 나타난다. 리스트 박스나 스크롤바처럼 캡션이 필요 없는 컨트롤은 NULL 값을 지정하면 된다.
3. `WS_CHILD | WS_VISIBLE` : 윈도우 스타일을 지정하는 값으로, 컨트롤의 경우 예외 없이 `WS_CHILD` 스타일이 사용된다. `WS_VISIBLE` 스타일은 `ShowWindow()` 함수 호출이 필요 없는 컨트롤인 경우 사용된다. #todo 컨트롤은 무조건 ShowWindow가 필요없는가 모르겠음.
4. `20, 400` : 윈도우가 그려질 x, y 좌표 위치이다.
5. `100, 30` : 윈도우 사이즈(Width, Height)이다.
6. `hWnd` : 버튼 컨트롤은 차일드 윈도우이기 때문에 무조건 부모 윈도우 핸들을 넘겨줘야 한다. 여기서 만든 버튼 컨트롤은 `hWnd` 메인 윈도우 작업 영역을 기준으로 한 좌표에서 생성되며, 무슨 일이 생기면 `hWnd`에 메시지를 보내고, 또한 `hWnd`가 소멸될 때 같이 소멸된다.
7. `(HMENU)ID_OK_BTN` : 윈도우에서 사용할 메뉴 핸들이며, 버튼 컨트롤의 경우 메뉴가 없으므로 이 매개변수를 컨트롤의 ID를 지정하는 용도로 사용한다.
8. `g_hInst` : 이 윈도우를 만드는 객체의 핸들로서, `WinMain()` 함수의 첫 번째 매개변수로 전달받은 `hInstance` 값을 넘겨주면 된다.
9. `(LPVOID)NULL` : 여분의 데이터이며, 이번에 해당되는 값이 없어 NULL 값을 입력한다.

### 버튼으로부터 메시지 받기
- 컨트롤에 대한 행동이 이루어졌을 경우 (버튼 클릭, 에디터 문자열 입력 등), 컨트롤은 부모 윈도우로 이벤트 메시지/통지 메시지(Notification Message)를 보낸다.
- 버튼 클릭 시 `WM_COMMAND` 통지 메시지가 부모 윈도우에 발송되며 `wParam`과 `lParam` 정보가 함께 전달된다.
	- `wParam`의 상위 2바이트는 부모 윈도우에 알려주는 이벤트 메시지로서, 버튼 클릭 시 `BN_CLICK`이 전달된다.
	- `wParam`의 하위 2바이트는 윈도우나 컨트롤의 ID로서, 버튼 컨트롤 ID가 전달된다.
	- `lParam`은 버튼 컨트롤의 윈도우 핸들이다.
- `wParam`은 4바이트(32비트) 값으로, 상위 2바이트(16비트)와 하위 2바이트(16비트)에 각각 다른 정보를 포함하고 있다.
	- 상위/하위 바이트 정보를 가져오려면 `HIWORD(wParam)` 또는 `LOWORD(wParam)` 함수를 사용하면 된다.
- 컨트롤의 ID는 `CreateWindow()` 함수의 아홉 번째 매개변수에 지정한 정수값으로, 어떤 컨트롤이 메시지를 보냈는지를 알려준다. 부모 윈도우는 `LOWORD(wParam)` 리턴값을 조사하여 어떤 컨트롤이 보냈는지 알 수 있고 이에 대한 적절한 처리가 가능하다.
- 이벤트 메시지는 차일드 컨트롤이 왜 메시지를 보냈는가를 나타내는 값이다.
	- 버튼의 경우 이벤트 메시지는 사용자가 자신을 클릭했다는 의미의 `BN_CLICKED`가 있지만, 두 번 클릭했다는 `BN_DOUBLECLICKED`도 있으며 그 외 여러 가지가 있다. #todo 이벤트 메시지 처리는 교재 제4장부터 소개된다.
- `MessageBox()` 함수를 사용함으로서 버튼 클릭 시 화면에 메시지 박스가 그려지게 할 수 있다.
  ```C++
  int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption, UINT uType)
  ```
	- `hWnd` : 메시지 박스를 소유하는 윈도우의 핸들
	- `lpText` : 메시지 박스의 텍스트에 보여질 문자열
	- `lpCaption` : 메시지 박스의 캡션에 보여질 문자열
	- `uType` : 메시지 박스에 보여 줄 버튼의 종류
		- `MB_OK` : 확인 버튼만 있는 메시지 박스
		- `MB_OKCANCEL` : 확인, 취소 버튼만 있는 메시지 박스
		- `MB_YESNO` : YES, NO 버튼만 있는 메시지 박스

### 버튼 컨트롤 생성 결과
![[visual_cpp_chapter1_button_control_01.png]]
![[visual_cpp_chapter1_button_control_02.png]]

## 정리요약
1. **윈도우 프로그램이란** Windows에서 실행할 수 있는 프로그램으로, 모든 윈도우는 윈도우 클래스로부터 만들어진다. 윈도우 클래스는 생성될 윈도우의 여러가지 특징을 모아 놓은 구조체이다. `CreateWindow()` 함수의 첫 번째 매개변수가 바로 윈도우 클래스 이름이다. 전달된 윈도우 클래스가 지정한 특성대로 윈도우를 만든다.
2. **메시지는** 시스템이나 응용 프로그램에 의해 생성된다. 키보드나 마우스 등으로 사용자가 입력하면 시스템은 입력에 대해 메시지를 발생시키며 또한 시스템의 상황 변화를 통지하기 위해서도 메시지를 발생시킨다. 응용 프로그램도 윈도우 간의 통신을 위해 메시지를 보내며 특정 함수호출에 의해 간접적으로 메시지가 발생하기도 한다. 이처럼 Windows는 끊임없는 메시지의 생성과 처리를 무수히 반복하면서 실행된다.
3. **운영체제는** 하나의 시스템 메시지 큐를 관리하며, 또한 스레드(Thread)별로 하나씩 메시지 큐(Message Queue)를 생성한다. 시스템 메시지 큐는 시스템 전체에 유일한 메시지 큐며, 모든 큐 메시지는 먼저 이곳에 저장된다. 시스템은 큐의 메시지를 하나씩 꺼내 어떤 스레드로 보낼 메시지인지 판단하여 스레드 메시지 큐로 메시지를 보내고 시스템 메시지 큐에서 메시지를 지운다. 그러면 메시지 루프에 의해 이 메시지는 해당 윈도우의 윈도우 프로시저로 보내져 처리되고, 스레드 메시지 큐에서는 메시지가 삭제된다.
4. **Windows는** 세 가지 동적 연결 라이브러리(DLL)로 구성되어 있다 - 메모리를 관리하고 프로그램을 실행시키는 Kernel, 유저 인터페이스와 윈도우를 관리하는 User, 그리고 화면 처리와 그래픽을 담당하는 GDI(Graphic Device Interface)이다. Windows API 함수는 대부분 이 세 가지 DLL에 의해 제공되고 있다.
5. **윈도우 프로시저 또는 CALLBACK 함수는** 응용 프로그램이 제공하며, 운영체제가 필요할 때 호출하는 함수로 '운영체제에 의해 호출되는 프로그램 내부의 함수'라고 할 수 있다.
6. 핸들(Handle)이란 어떤 대상을 구분하기 위해 붙여진 번호로 Windows에서 핸들은 예외 없이 접두어 `h`로 시작되며, 핸들값을 저장하기 위해 별도의 자료형까지 정의해 두고 있다. `HWND`, `HPEN`, `HBRUSH`, `HDC` 등이 핸들을 담는 자료형이며 모두 부호 없는 정수형(Unsigned Integer)이다.

## 연습문제
1. 예제 프로그램에서 '지역대학' 버튼 옆에 '학과' 버튼을 생성하고, '학과' 버튼 클릭 시 '컴퓨터과학과' 내용이 나오는 메시지가 팝업되는 기능을 추가하시오.
2. 예제 프로그램에서 차일드 윈도우 옆에 또 다른 차일드 윈도우를 생성하고 차일드 윈도우 안에 '두 번째 차일드 윈도우'라는 내용이 출력되도록 수정하시오.
3. 예제 프로그램에서 차일드 윈도우 안에 '지역대학'과 '학과' 버튼을 생성하고, 버튼 클릭 시 각각 메시지 박스 안에 '지역대학'과 '컴퓨터과학과' 내용이 출력되도록 프로그램을 수정하시오.
4. 윈도우 메시지와 메시지 큐, 그리고 CALLBACK 함수의 역할에 대해 설명하시오.
5. `WM_LBUTTONDOWN`, `WM_CHAR`, `WM_KEYDOWN` 메시지를 활용하여 윈도우 화면에 문자열을 출력해 보시오.
6. `WM_COMMAND` 메시지에 대해 설명하시오.
7. 윈도우 색상, 커서, 아이콘 등의 스타일을 변경해 보시오. 밑에 참고.
	- `GetStockObject()` 함수에 대한 [정보](https://learn.microsoft.com/en-us/windows/win32/api/wingdi/nf-wingdi-getstockobject)
	- `LoadCursor()` 함수에 대한 [정보](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-loadcursora)
	- `LoadIcon()` 함수에 대한 [정보](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-loadicona)
	- `CreateSolidBrush()` 함수에 대한 [정보](https://learn.microsoft.com/en-us/windows/win32/api/wingdi/nf-wingdi-createsolidbrush)

# 제2장 MFC 프로그래밍
- WinAPI 외에 윈도우 프로그래밍을 할 수 있는 다른 방법으로는 MFC(Microsoft Foundation Class) 클래스 라이브러리(Class Library)를 사용하는 방법이 있다.
- MFC는 WinAPI보다 훨씬 더 효율적이고 생산성 있게 프로그램을 개발할 수 있는 방법이다.
- MFC에 클래스라는 용어에서 알 수 있듯이 MFC는 OOP(Object Oriented Programming)을 기반으로 한다. 클래스는 캡슐화, 정보은닉, 상속 등의 특징을 갖는다.
- MFC는 윈도우 프로그래밍을 보다 쉽게 하기 위하여 WinAPI 함수들을 클래스들로 포장하여 구성한 클래스 라이브러리이다.
- MFC에는 윈도우, DC, 펜, 브러시, 파일, 심지어 프로그램 그 자체까지도 객체로 정의되어 있다.
	- 변수를 선언하는 것만으로도 객체를 쉽게 만들 수 있다. 예를 들어, 윈도우 하나를 만들기 위해 `CWnd ChildWnd;` 처럼 변수 선언만 하면 된다.
	- 객체 안에 포함된 멤버 함수로 이 객체의 모든 속성을 조정할 수 있고 동작을 표현할 수 있다.

## 학습목표
1. MFC와 WinAPI의 관계를 정확히 설명할 수 있다.
2. MFC 클래스 계층도를 이해한다.
3. MFC 응용 프로그램 마법사를 이용해서 SDI 윈도우를 생성할 수 있다.
4. SDI 프로그램에 여러 가지 컨트롤들을 추가할 수 있다.

## 주요용어
- MFC
- 클래스 라이브러리
- MFC 클래스 계층도
- SDI
- MDI
- 컨트롤

## SDI 프로젝트
- SDI, Single Document Interface : 메모장, 워드패드처럼 하나의 View 윈도우를 가진 프로그램이다.
- MDI, Multiple Document Interface : 여러 개의 View 윈도우를 가진 프로그램으로, 거의 대부분 프로그램이 MDI이다.
- Dialog 기본 프로그램 : 계산기 프로그램처럼 메인 윈도우가 다이얼로그 박스인 SDI 프로그램이다.

### MFC 프로젝트 생성
- Visual Studio -> New Project -> MFC App 으로 프로젝트 생성을 하면 MFC 응용 프로그램 마법사 창이 뜬다.

### MFC 응용 프로그램 마법사
- 프로젝트 만들기를 진행하면 MFC 애플리케이션 설정창이 뜬다. 다음과 같이 옵션을 선택하고 진행한다.
	1. 애플리케이션 종류 설정에 "애플리케이션 종류(Application type)"는 "단일 문서(Single Document)"로 선택한다.
		- 단일 문서, 즉, SDI 프로그램을 개발할 것임을 가리키는 것이다.
	2. 애플리케이션 종류 설정에 "프로젝트 스타일(Project style)"은 "MFC standard"로 선택한다.
	3. 애플리케이션 종류 설정에 "비주얼 스타일 및 색(Visual style and colors)"은 "Windows Native/Default"로 선택한다.
	4. 애플리케이션 종류 설정에 "복합 문서 지원(Compound document support)"은 "없음(none)"으로 선택한다.
		- SDI 프로그램은 복합 문서를 사용하지 않기 때문이다.
	5. 애플리케이션 종류 설정 나머지는 모두 Default 그대로 선택한다.
	6. 문서 템플릿 속성 설정은 모두 Default 그대로 선택한다.
	7. 사용자 인터페이스 기능 설정은 모두 Default 그대로 선택한다.
	8. 고급 기능 설정은 모두 Default 그대로 선택한다.
	9. 생성된 클래스 설정은 모두 Default 그대로 선택한다.
- 위 설정을 선택하고 마침(Finish)를 누르면 프로젝트가 생성된다. 이 프로젝트는 바로 빌드가 가능하고, 아주 간단한 윈도우가 그려진다.
  ![[visual_cpp_chapter2_mfc_sdi_base.png]]

## SDI 기본 코드 이해하기
- 프로젝트 내에 있는 파일 또는 클래스들을 관리하기 위해 Visual Studio는 "솔루션 탐색기(Solution Explorer)"와 "클래스 뷰(Class View)"를 제공한다.
  ![[visual_cpp_chapter2_mfc_sdi_solution_explorer.png]]
  ![[visual_cpp_chapter2_mfc_sdi_class_view.png]]

### SDI 프로그램의 구조
- MFC 응용 프로그램 마법사로 생성한 SDI 프로그램은 기본적으로 여러 개의 윈도우으로 구성된다. 메인 윈도우가 있고 그 안에 툴바, 상태바, 그리고 View 윈도우가 있다.
- 하나의 View 윈도우를 가지고 있으므로 SDI(Single Document Interface) 프로그램이라고 한다.
- MFC는 우니도우의 모든 기능을 클래스로 구현해서 제공하고 있다.
	- `CMainFrame`은 메인 윈도우를 나타내는 클래스다.
	- `CSDIView`는 View 윈도우를 나타내는 클래스다.
	- `CSDIDoc`은 데이터를 처리하고 저장하는 것을 담당하는 클래스다.
	- `CSDIApp`은 전체 프로그램을 관리하는 클래스다.

#### MFC가 생성한 소스 파일
| Source File                | Description                                              |
| -------------------------- | -------------------------------------------------------- |
| SDI.vcxproj                | VC++ 프로젝트 정보를 포함하고 있는 프로젝트 파일         |
| SDI.sln                    | 비주얼 스튜디오의 프로젝트 환경정보 파일로서 가장 메인임 |
| SDI.h, SDI.cpp             | CSDIApp 클래스를 정의하고 구현한 프로그램의 메인 파일    |
| MainFrame.h, MainFrame.cpp | CMainFrame 클래스 파일                                   |
| SDIView.h, SDIView.cpp     | CSDIView 클래스 파일                                     |
| SDIDoc.h, SDIDoc.cpp       | CSDIDoc 클래스 파일                                      |
| StdAfx.h, StdAfx.cpp       | MFC를 사용하기 위한 기본 헤더 파일을 포함하는 파일       |
| Resource.h                 | 리소스 ID 정의를 포함하고 있는 파일                      |
| SDI.rc                     | 프로그램에서 사용하는 리소스가 정의된 파일               |
| resSDI.ico                 | 아이콘 파일                                              |
| resSDI.rc2                 | Visual C++에 의해 편집되지 않는 리소스를 포함함          |
| resToolbar.bmp             | 툴바 이미지를 생성하는데 사용되는 그림 파일              |

### 응용 프로그램 프레임워크
- MFC는 응용 프로그램을 작성하기 위해 필요한 프레임워크를 제공한다.
- MFC가 제공하는 SDI 프로그램의 응용 프로그램 프레임워크는 다음과 같다.
	- `CSDIApp` : `CWinApp`에서 상속받은 응용 프로그램 클래스
	- `CMainFrame` : `CFrameWnd`에서 상속받은 프레임 윈도우 클래스
	- `CSDIView` : `CView`에서 상속받은 View 클래스
	- `CSDIDoc` : `CDoument`에서 상속받은 Document 클래
- SDI 프로임워크 내의 클래스들의 관계를 그림으로 표현하면 다음과 같다.
  ![[visual_cpp_chapter2_mfc_sdi_framework.png]]
- 