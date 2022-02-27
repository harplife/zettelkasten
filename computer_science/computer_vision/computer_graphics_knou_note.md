
# Notes from textbook

# 챕터 1

## 1.3 컴퓨터 그래픽스 시스템 구성
컴퓨터 그래픽스 시스템은 3가지로 구성되어 있다.
1. 입력장치
2. 그래픽스 워크스테이션 (PC)
3. 출력장치

그래픽스 워크스테이션은 4가지로 구성되로 있다.
1. 중앙처리장치 (CPU)
2. 메모리
3. 그래픽스 처리장치 (GPU) / 비디오 카드
4. 입출력 인터페이스

![[knou_cg_pic1-14.jpg]]

### GPU
GPU는 그래픽스를 가속하기 위하여 최적화된 전용 프로세서로 주로 비디오 카드에 탑재되지만 일부 시스템에서는 CPU 내에 구현되기도 한다.

GPU는 3D 그래픽스 렌더링에 필수적인 실수연산을 실행하기 위하여 특별하게 설계된다.

GPU를 구별하는 속성:
1. 클럭 주파수 (200~850MHz)
2. 파이프라인 (꼭짓점과 선으로 특성화되는 3D 영상을 화소로 구성되는 2D 영상으로 변환)
3. etc.

### 비디오 BIOS
비디오 BIOS 또는 펌웨어(Firmware)는 비디오 카드의 동작을 조절한다.

컴퓨터와 소프트웨어가 비디오 카드와 상호 동작할 수 있도록 하는 명령어를 지원하는 기본 프로그램을 포함하고 있다.

### 비디오 메모리
비디오 메모리는 화면에 출력할 그래픽 데이터를 저장하는 용도로 사용한다.

프레임 버퍼, 깊이 버퍼 등이 비디오 메모리에 포함된다.

또한 GPU가 동작하는데 필요한 프로그램 및 데이터 역시 비디오 메모리에 저장된다.

### RAMDAC
RAMDAC(Random Access Memory Digital-to-Analog Converter)은 아날로그 디스플레이 장치(i.e. CRT, etc)를 위하여 디지털 신호를 아날로그 신호로 변환한다.

사용되는 비트 수와 RAMDAC 데이터 전송률에 따라 변환기는 다른 Refresh Rate을 지원할 수 있다.
- CRT 디스플레이 경우 Flicker를 최소화하기 위하여 75hz 이상에서 최상으로 동작
- LCD 디스플레이는 Flicker 문제가 없음

디지털 디스플레이 장치가 대중화됨으로 RAMDAC이 GPU에 통합되는 추세이기 때문에 RAMDAC은 점차 사라져 가고 있다.

### 출력
비디오 카드와 컴퓨터 디스플레이 간의 가장 보편적인 연결 시스템은 다음과 같다.
1. Video Graphics Array (VGA) : CRT 디스플레이를 위하여 1980대 후반 채택된 아날로그 기반 표준. 전기적 잡음, 영상왜곡, 표본화 오차 등의 문제를 갖고 있다.
2. Digital Visual Interface (DVI) : LCD, 플라즈마 스크린 등의 Flat Display를 위한 디지털 기반 표준. 영상왜곡, 전기적 잡음 등을 피할 수 있다.
3. Video In Video Out (VIVO) : TV, DVD 재생기, 비디오 녹화기 등을 위한 S-비디오, 복합 비디오, 컴포넌트 비디오를 위한 표준. 빨강, 파랑, 노상, 초록 등 여러 가지 색상으로 되어있던 케이블 이다.
4. High-Definition Multimedia Interface (HDMI) : 2003년에 발표된 디지털 오디오/비디오 표준. HDCP 복사장지 기능을 제공한다.
5. [Display Port](https://en.wikipedia.org/wiki/DisplayPort) : 2007년에 발표된 오디오/비디오 표준. 특허권 사용료 없음.

## 1.4.1 Vector Display and Raster Display
디스플레이에서 그림을 그리는 방식은 Raster와 Vector로 구분된다.

### Vector Display
"전자빔으로 도형을 주사하여 원하는 그림을 그리는 방식"이라고 보통 설명되어 있다.
지정된 경로에 따라 라인을 그리는 방식으로 그냥 생각하면 될 듯 하다.
- [Vector Display (wiki)](https://en.wikipedia.org/wiki/Vector_monitor)
- [Vector Graphics (wiki)](https://en.wikipedia.org/wiki/Vector_graphics)

벡터 디스플레이 방식에서는 그림을 그래픽스 명령들로 표현하며, 이를 Display List 또는 Display Program이라고 한다.

![[knou_cg_pic1-15.jpg]]

Display List는 비디오 메모리에 저장되며, 이를 그래픽스 프로세서가 초당 30회 이상 반복하여 디스플레이한다.

비디오 메모리 사용량은 화면에 얼마나 많은 물체가 포함되는가에 따라 달라진다.

벡터 방식은 래스터 방식과 달리 Aliasing 문제가 발생하지 않는 장점이 있어 설계도면을 그리는데 많이 사용되었다.

1970년 이후에는 래스터 디스플레이가 대중적으로 사용됨으로 벡터 디스플레이는 더 이상 사용되지 않는다.

### Raster Display
래스터 디스플레이 방식은 위에서 아래로 한 행씩, 왼쪽에서 오른쪽으로 스크린을 가로질러 그리는 방식이다.

디스플레이하고자 하는 그림은 빨강, 초록, 파랑(RGB)의 색 정보를 표현하는 비디오 신호로 전달된다.

우리가 사용하는 대부분의 모니터는 래스터 방식을 사용한다고 보면 된다.

화면에 그림을 그리는 수평선을 주사선(Scan Line)이라고 한다.

주사선에 그려지는 점들을 픽셀(Pixel)이라고 한다.

해상도(Resolution)는 디스플레이 화면의 총 픽셀 수 (주사선 당 픽셀 수 x 주사선 수)를 뜻 한다.

해상도가 낮으면 그림을 정교하게 그릴 수 없다 - 매끄러운 선을 그리지 못하고 거친 선을 그리게 하는 현상을 Aliasing이라고 하며, 이를 완하하기 위해 Anti-aliasing을 사용한다.

래스터 방식에서는 그림을 한 화면을 구성하는 픽셀들의 값으로 표현한다. 이러한 픽셀 값들을 프레임 버퍼([Frame Buffer](https://en.wikipedia.org/wiki/Framebuffer))에 저장한다.

비디오 메모리 사용량은 화면 해상도에 따라 고정된다.

## 1.4.2 디스플레이 장치
그래픽 시스템에서 기본 출력장치이자 가장 일반적인 디스플레이 장치는 모니터다.

평판 디스플레이 (Flat Panel Display)는 CRT에 비해 부피나 무게, 소비전력을 줄인 평평한 화면의 비디오 장치를 뜻한다 (요즘에는 굳이? 이 단어를 사용할 필요가 있을까 싶다).

평판 디스플레이는 두 가지 부류로 나뉜다.
1. 방사성 (Emissive)
2. 비방사성 (Non-Emissive, Non-Emitter)

방사성 디스플레이는 전기 에너리를 빛으로 변환하는 장치이다. 예:
1. 플라즈마 패널 (Plasma Panel)
2. 박막 전자발광 디스플레이 (Thin-film Electroluminescent Display)
3. 발광 다이오드 (LED)

비방사성 디스플레이는 태양광이나 다른 광원으로 광학적 효과를 사용하여 그래픽 패턴으로 변환한다. 가장 중요한 예시로 액정 디스플레이(LCD)가 있다.

### CRT 디스플레이
![[crt_monitor.jpg | 300]]

CRT (Cathode Ray Tube)는 오랫동안 널리 사용되어 오던 디스플레이 장치이다. 하지만 현재 가볍고 큰 평판 디스플레이인 LCD, 플라즈마, OLED 등으로 빠르게 대체되고 있다.

최초의 CRT는 1897년에 독일 물리학자 Ferdinand Braun이 발명했다. Western Electric의 Harry Weinhart와 John Johnson이 온음극 CRT를 개발함으로 1922년에 CRT가 상용화 되었따.

음극선관 (Cathode Ray Tube: CRT)은 전자총과 형광 스크린을 갖는 진공관이며, 형광 스크린으로부터 방출되는 빛의 형태로 영상을 형성하는데, 음극선(Cathode Ray)은 전계나 자계의 의해 편향되어 스크린상에서 원하는 위치로 밝은 점을 이동시킨다.

> "Old cathode ray tube (CRT) televisions have an [electron gun](http://electronics.howstuffworks.com/question694.htm) which fires electrons at the back of the screen. And the screen is coated with _phosphors_ which emit light whenever struck by an electron." - Reddit

음극선 (또는 전자빔, e-beam)은 디스플레이 방식에 따라 편향 시스템에 의해 제어되어 스크린 위에 그림을 출력한다.
- 벡터 방식 : 디스플레이 리스트에 나열된 명령에 따라 전자빔을 제어하여 물체 단위로 디스플레이 한다.
- 레스터 방식 : 주사선 단위로 전자빔을 제어한다.

1초에 전자총이 전체 그림을 다시 그리는 횟수를 재생률 (Refresh Rate)이라고 하며, 이를 세는 단위로 Hertz를 사용한다.

TV와 초기 모니터는 홀수 번쨰와 짝수 번쨰 주사선을 번갈아 주사하는 [비월주사 (Interlaced Scanning)](https://en.wikipedia.org/wiki/Interlaced_video)를 사용했다. 비월주사는 Frame Rate을 증가시키며 (실제로 증가하지 않되 증가된 것과 같이 인식된다) 대역폭(bandwidth)를 그대로 유지한다는 장점이 있다. 더불어, 움직이는 모션을 부드럽게 하며 Flicker를 줄여주는 효과가 있다. 하지만 Progressive Scan (모든 픽셀을 그리는 방식)과 비교하여 디테일이 부드럽지 못 하고 움직임 아티팩트 (Motion Artifact)가 생긴다는 단점이 있다.

모니터는 빛을 발하는 수만 개의 작음 점으로 이루어져 있다. 각각 R(빨강), G(초록), B(파랑) 색상을 갖는 점 3개가 모여 하나의 화소(Pixel)를 구성한다. 화소 간의 거리를 도트 피치(Dot Pitch)라고 부르며, 이 거리가 가까울수록 스크린이 더욱 선명해진다. 대부분의 모니터는 0.28mm 또는 그 이하의 도트 피치를 갖는다.

#### CRT의 장점
1. 20,000 : 1 이상의 높은 명함 대비율. 이는 LCD나 플라즈마에 비하여 매우 높은 편이다.
2. 빠른 응답속도
3. 넓은 범위의 색 재현성, 실제에 가까운 검정색의 재생
4. 해상도와 무관하게 자연스러운 디스플레이 가능
5. 0에 가까운 왜곡 (색, 포화도, 명암 대비, 명도)
6. 우수한 시야각
7. 입력 지연이 없다
8. 오랜 기간동안 사용되어 증명된 신뢰성이 있다

#### CRT의 단점
1. 부피가 크고 무겁다.
2. 비평면 CRT에서 발생하는 기하학적 왜곡
3. 최고 명도와 컬러 렌더링에 이르기까지 예열시간이 필요하다.
4. 전력 소모가 많다.
5. 습기에 취약하다.
6. 낮은 재생률의 경우 화면 깜빡임이 나타난다.
7. 치명적인 내부 전압

### LCD 디스플레이
