---
aliases: [Computer Graphics Note]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study]
status: ongoing
edited: 2022-03-02
---

# Computer Graphics Note
방통대 교과서에 있는 내용을 토대로 하되, 여러 부분을 수정/제거/추가한 노트.
개인적으로 방통대 교과서는 정리가 잘 안 되어 있을 뿐만이 아니라 틀린 정보가 의외로 많다.

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

#### 픽셀
주사선에 그려지는 점들을 [화소 (픽셀, Pixel)](https://en.wikipedia.org/wiki/Pixel)이라고 한다. 각 픽셀의 밝기와 색상을 조절하여 그림을 구성한다.

컬러 디스플레이에서 각 화소는 각각 R(빨강), G(초록), B(파랑) 색상을 갖는 부화소 (Subpixel) 3개로 구성된다.

색상을 구현하기 위해 각 부화소는 독립적으로 제어되며, 모니터의 용도에 따라 여러 가지 형태의 [화소 배열 (Pixel Geometry)](https://en.wikipedia.org/wiki/Pixel_geometry)로 배치된다. 특정 디스플레이의 화소 배열 형태를 알고 있다면, [부화소 렌더링 (Subpixel Rendering)]을 소프트웨어로 구현하여 모니터의 외견상 해상도를 향상시킬 수 있다.

![[pixel_geometry.PNG | 300]]

화소 간의 거리를 [도트 피치 (Dot Pitch)](https://en.wikipedia.org/wiki/Dot_pitch)라고 부르며, 이 거리가 가까울수록 스크린이 더욱 선명해진다. 대부분의 모니터는 0.28mm 또는 그 이하의 도트 피치를 갖는다.

피치값이 작으면 보다 선명한 영상을 표현할 수 있다 (해상도가 높아진다). 하지만 무조건 작다고 좋은 것은 아니다 - 시청 거리가 먼 경우 피치값이 낮아봤자 더 선명하게 보이는 것이 아니기 떄문에 돈만 낭비하는 꼴이된다.

참고: 픽셀 값들은 화면에 그려지기 전에 [프레임 버퍼 (Frame Buffer)](https://en.wikipedia.org/wiki/Framebuffer)에 저장된다. 비디오 카드의 RAM이라고 생각하면 된다.

#### 해상도
해상도 (Resolution)는 디스플레이 화면의 총 픽셀 수 (주사선 당 픽셀 수 x 주사선 수)를 뜻 한다. 수평과 수직의 크기 (픽셀 수)로 1920 x 1080 과 같은 포맷으로 표현된다.

해상도가 높을수록 더욱 정교한 그림을 그릴 수 있다. 하지만, 그리려는 그림의 해상도가 모니터의 해상도보다 높은 경우, 이미지의 일부가 식별할 수 없게 되며 왜곡 현상이 일어난다. 이러한 현상을 [Aliasing](https://en.wikipedia.org/wiki/Aliasing)이라고 부른다 (정확히는 Spatial Aliasing이라고 부른다).

![[aliasing_example_01.PNG]]

Aliasing 현상 중 그림의 윤곽선이 거칠어지고 계단 형식으로 변하는 것을 [Jaggies](https://en.wikipedia.org/wiki/Jaggies)라고 부른다.

![[aliasing_example_02.PNG | 300]]

그리드 (Grid) 형식으로 촘촘이 수많은 작은 디테일이 있는 이미지에서는 [무아레 패턴 (Moiré Pattern)](https://en.wikipedia.org/wiki/Moir%C3%A9_pattern)의 Aliasing이 발생되기도 한다.

![[aliasing_example_03.PNG | 300]]

Aliasing 문제를 해결하기 위해 [Anti-Aliasing](https://en.wikipedia.org/wiki/Spatial_anti-aliasing)이 사용된다. Anti-aliasing의 기본 원리는 디테일이 작고 촘촘한 부분을 제거하거나 흐리게하는 것이다. Anti-aliasing에 사용되는 예시로 Low Pass Filter, Down Sampling, Gaussian Blur, Sinc Filter 등이 있다.

![[anti_aliasing_example_01.PNG]]

참고: 비디오 메모리 사용량은 화면 해상도에 따라 고정된다.

참고: 아날로그인 CRT 모니터를 제외한 모든 모니터에는 최적의 해상도가 있다.

#### 재생률 / 주사율
[재생률 (Refresh Rate)](https://en.wikipedia.org/wiki/Refresh_rate)은 모니터가 화면에 1초 동안 이미지를 그리는 횟수를 뜻하며 Hz (Hertz) 단위로 센다.

주사율 (Scan Rate)이라고도 불리운다.

[Frame Rate](https://en.wikipedia.org/wiki/Frame_rate)도 마찬가지로 1초 동안 이미지를 그리는 횟수를 뜻하지만, 여기서 "그린다"는 것은 소프트웨어 / GPU가 이미지를 [렌더링 (Rendering)](https://en.wikipedia.org/wiki/Rendering_(computer_graphics))하는 것을 뜻한다.

Refresh Rate과 Frame Rate를 혼동하면 안 된다.

Refresh Rate과 Frame Rate은 1:1로 완벽하게 싱크 (Sync)되는게 좋다. 예를 들어, 소프트웨어에서 60 FPS로 이미지를 전송하는 경우, 모니터에서 60 Hz로 이미지를 그려주면 좋다. 1:1로 완벽하게 싱크되지 않는 경우, [티어링 현상 (Screen Tearing)](https://en.wikipedia.org/wiki/Screen_tearing)이 발생할 수 있다.

![[screen_tear_face.PNG | 300]]

Refresh Rate과 Frame Rate을 언제나 완벽하게 싱크하는 것은 어렵기 때문에, 모니터에서 Refresh Rate을 자동으로 조절하여 Frame Rate과 동일하게 하는 [적응형 수직동기화 (Adaptive Sync)](https://en.wikipedia.org/wiki/Variable_refresh_rate) 기술이 사용된다.

Adaptive Sync는 가변 주사율 (Variable Refresh Rate) 또는 동적 주사율 (Dynamic Refresh Rate)으로 불리기도 한다. 그리고 여기서 명시하는 Adaptive Sync는 Refresh Rate과 Frame Rate을 동기화하는 개념을 뜻하며, [VESA (Video Electronics Standards Association, 비디오 전자공학 표준위원회)](https://en.wikipedia.org/wiki/Video_Electronics_Standards_Association)에서 발표한 _Adaptive Sync_ 기술과 혼동되지 않아야 한다.

NVIDIA의 [G-SYNC](https://en.wikipedia.org/wiki/Nvidia_G-Sync)와 AMD의 [FreeSync](https://en.wikipedia.org/wiki/FreeSync)가 Adaptive Sync가 상용화된 대표적인 예시이다.

Adaptive Sync를 사용하기 위해서는 모니터와 GPU가 호환되어야 한다 - Adaptive Sync를 사용할수 있는 GPU와 Adaptive Sync가 장착된 모니터가 있어야 한다. 원래는 NVIDIA GPU는 G-Sync만 지원했지만, [요즘에는 FreeSync까지 지원한다고 한다](https://www.pcgamesn.com/nvidia/what-is-freesync).

참고: G-Sync, FreeSync는 HDMI 또는 DisplayPort만 지원한다고 하는데, 이에 대하여 정보를 더 찾아봐야 한다.

모니터에 제품사양을 확인해보면 FreeSync 또는 G-Sync를 사용 유뮤가 표시되어 있다. 예로서, 삼성 LED 모니터 (LS27R350FHKXKR) 같은 경우 28인치에 FreeSync를 지원한다.

[VSync (Vertical Sync)](https://en.wikipedia.org/wiki/Screen_tearing#Vertical_synchronization)는 Frame Rate을 Refresh Rate에 맞추는 기술이다 - 모니터의 새로운 재생 주기가 시작하기 전에 그래픽 카드가 렌더링하는 장면이 모니터로 업데이트되지 않도록 장면 업데이트를 지연시키는 원리로 작동한다.

VSync는 Frame Rate이 Refresh Rate보다 높을 때 사용하는게 제일 효과가 좋다. Frame Rate이 더 낮은 경우, 움직임이 늘어졌다 짧아졌다 하는 현상 (Judder), 움직임이 끊기는 현상 (Stutter), 또는 입력에 대한 반응이 늦는 현상 (Input Lag)이 발생한다.

Judder는 각 프레임마다 재생 횟수가 균일하지 못 하면 발생한다. 이미지 참고.

![[judder_example_01.png]]

Adaptive VSync는 VSync가 Frame Rate이 Refresh Rate보다 높은 경우에만 켜지도록 하는 기술이다.

VSync 옵션은 GPU 설정 또는 게임/DVD플레이어 설정에 있다.

참고1: https://blog.tommyzip.co.kr/report/g-sync-vesa-adaptive-sync-freesync/
참고2: https://www.viewsonic.com/library/tech/explained/what-is-adaptive-sync

#### 응답 시간
응답 시간, 또는 반응 시간 (Response Time)은 픽셀의 색상이나 밝기를 변화시키는 속도를 뜻한다.

일반적으로 BTB (Black to Black) 테스트가 사용되며, Black (inactive) → White (active) → Black (active) 으로 변경하는데 걸리는 시간을 ms 단위로 측정한다.

10 ms 정도는 사무용 또는 30 FPS 콘텐츠를 즐기는데 문제는 없지만, 60 FPS 이상의 경쟁 게임 (Competitive Gaming)에는 5ms 이하가 권장된다.

때로는 GTG (Gray to Gray) 테스트가 사용되기도 한다. 극과 극으로 변화하는 BTB 테스트와는 달리, 검은색과 하얀색 사이의 회색 범위 내에 여러번 변화하여 변화할때 마다 걸리는 시간의 평균을 측정한다.

참고: 검증된 것은 아니지만, GTG 테스트가 BTB 더 정확하다고 여겨지는 이유가 - 픽셀을 껐다 켰다 할때 변화 범위가 큼으로 높은 전압 (High Voltage)이 사용되어 변화 속도가 빠른 반면에, 픽셀을 켠 상태로 조금씩 변화하는 것은 낮은 전압 (Low Voltage)이 사용되어 변화 속도가 느리고, 컬러 TV의 특성상 픽셀은 하얀색/검은색으로 전환하는 것보다는 회색의 범위에 왔다갔다 하는 횟수가 많기 때문에 GTG 테스트가 현실 사용 환경에 더 유사하다는 것이다.

#### 색 재현율
[색 재현율 (Color Gamut)](https://en.wikipedia.org/wiki/Gamut)은 모니터가 색을 얼마만큼 표현할 수 이는지 나타내는 수치이다.

여기서 [색 (Color](https://en.wikipedia.org/wiki/Color)이란 아주 복잡한 개념이다. 알아야 할 것은,
1. [색 공간 (Color Space)](https://en.wikipedia.org/wiki/Color_space)는 색을 이해하기 위해 최대한 수학적으로 색을 정리한 좌표계를 뜻한다.
2. [CIE 1931](https://en.wikipedia.org/wiki/CIE_1931_color_space) 색 공간은 인간의 색 인식률과 [휘도 (Luminance)](https://en.wikipedia.org/wiki/Luminance)를 기준으로 표현한 좌표계 입니다. 이 색 공간은 다른 색 공간들의 기반이 되었다.
3. [NTSC](https://en.wikipedia.org/wiki/NTSC)는 National Television System Committee의 약자로, 방송용 전파에 대한 미국 표준화 담당기구의 이름이자, NTSC가 제정한 아날로그 방송 기술 표준을 의미한다. 이 표준에는 방송에 사용될 색 공간을 정의하고, 디스플레이 기술은 이 색 공간을 기준으로 색 재현율을 계산한다.
4. NTSC 외에도 다른 색 공간들도 정의되었으며, [각 색 공간들에 따라 용도가 여러 있다](https://en.wikipedia.org/wiki/List_of_color_spaces_and_their_uses).

일반적으로 NTSC 70% 정도이면 충분하다고 한다.

## 1.4.2 디스플레이 장치
그래픽 시스템에서 기본 출력장치이자 가장 일반적인 디스플레이 장치는 모니터다.

### 평판 디스플레이

[평판 디스플레이 (Flat Panel Display)](https://en.wikipedia.org/wiki/Flat-panel_display)는 CRT에 비해 부피나 무게, 소비전력을 줄인 평평한 화면의 비디오 장치를 뜻한다 (요즘에는 굳이? 이 단어를 사용할 필요가 있을까 싶다).

#### 방사성 vs. 비방사성

[평판 디스플레이는 두 가지 부류로 나뉜다](https://siim.org/page/displays_chapter2).
1. 방사성 (Emissive)
2. 비방사성 (Nonemissive)

방사성 디스플레이는 각 픽셀에서 다양한 강도와 색상의 빛을 발한다. 기본적으로 명암 대비율이 높은 편이며, 완벽한 검정 (True Black)을 구현한다. 더불어, 대부분의 방사성 디스플레이는 [램버시안 법칙](https://en.wikipedia.org/wiki/Lambert%27s_cosine_law)에 따라 각도와 관계없이 같은 밝기를 갖기 때문에 시야각 (Viewing Angle)이 넓다.

PDP, LED, OLED, FED 등이 모두 방사성 디스플레이다.
^ CRT도 방사성 디스플레이인지?

비방사성 디스플레이는 광원(Light Source)에 흡수(Absorption), 반사(Reflection), 굴절(Refraction) 등의 광학적 효과를 사용하여 픽셀에 빛을 발한다.
^ 위 문구가 좀 헷갈릴 수 있는데, 이를 비유로 이해한다면 방사성 디스플레이는 각 픽셀에 전구가 있어 전구를 껐다 켰다 해서 픽셀로 그림을 그리는 반면, 비방사성 디스플레이는 각 픽셀에 광학적 효과를 내는 필터가 있어 픽셀에 비추는 빛을 통과시키거나 막아서 픽셀로 그림을 그린다. __한 마디로, 방사성 디스플레이는 픽셀 자체가 광원이고 비상사성 디스플레이는 다른 광원으로부터 픽셀을 비춘다.__

비방사성 디스플레이에 가장 중요하고 유일한 예시로 LCD 디스플레이가 있다.

계산기나 전자시계에 사용되는 LCD 디스플레이는 주변광/환경광 (Ambient Light)을 반사하여 그림을 그린다. 그래서 어두운 곳에서는 잘 안 보인다.

TV, 컴퓨터 모니터에 사용되는 LCD 디스플레이는 화면 뒤에 백라이트 (Backlight)가 있다. 색상에 상관없이 백라이트는 항시 켜져있으며, 검은색을 구현할 때도 마찬가지 이다. 따라서, LCD 디스플레이는 명암 대비율이 낮은 편이다. 일반적으로 백라이트로 [형광등 (Fluorescent Light)](https://en.wikipedia.org/wiki/Fluorescent_lamp)를 사용한다.

참고로, LED 디스플레이는 LCD 디스플레이에 속하며, 백라이트로 형광등 대신 LED를 사용한다. <-- 내가 헷갈리는 것은, 그러면 LED 디스플레이도 비방사성 디스플레이 속하지 않는가 이다.

### CRT 디스플레이
![[crt_monitor.jpg | 300]]

[음극선관 (Cathode Ray Tube: CRT)](https://en.wikipedia.org/wiki/Cathode-ray_tube)는 오랫동안 널리 사용되어 오던 디스플레이 장치이다. 하지만 현재 가볍고 큰 평판 디스플레이인 LCD, 플라즈마, OLED 등으로 빠르게 대체되고 있다.

최초의 CRT는 1897년에 독일 물리학자 Ferdinand Braun이 발명했다. Western Electric의 Harry Weinhart와 John Johnson이 온음극 CRT를 개발함으로 1922년에 CRT가 상용화 되었따.

CRT는 [전자총 (Electron Gun)](https://en.wikipedia.org/wiki/Electron_gun)과 [형광 스크린 (phosphor screen)](https://en.wikipedia.org/wiki/Phosphor)을 갖는 [진공관](https://en.wikipedia.org/wiki/Vacuum_tube)이며, 형광 스크린으로부터 방출되는 빛의 형태로 영상을 형성하는데, [음극선(Cathode Ray)](https://en.wikipedia.org/wiki/Cathode_ray)은 [전계나 자계](https://home.kepco.co.kr/kepco/KO/D/htmlView/KODBHP00302.do?menuCd=FN05040203)의 의해 편향되어 스크린상에서 원하는 위치로 밝은 점을 이동시킨다.

> "Old cathode ray tube (CRT) televisions have an [electron gun](http://electronics.howstuffworks.com/question694.htm) which fires electrons at the back of the screen. And the screen is coated with _phosphors_ which emit light whenever struck by an electron." - Reddit

음극선 (또는 전자빔, e-beam)은 디스플레이 방식에 따라 편향 시스템에 의해 제어되어 스크린 위에 그림을 출력한다.
- 벡터 방식 : 디스플레이 리스트에 나열된 명령에 따라 전자빔을 제어하여 물체 단위로 디스플레이 한다.
- 레스터 방식 : 주사선 단위로 전자빔을 제어한다.

1초에 전자총이 전체 그림을 다시 그리는 횟수를 재생률 (Refresh Rate)이라고 하며, 이를 세는 단위로 Hertz를 사용한다.

![[Cathode_ray_Tube.png | 300]]

TV와 초기 모니터는 홀수 번쨰와 짝수 번쨰 주사선을 번갈아 주사하는 [비월주사 (Interlaced Scanning)](https://en.wikipedia.org/wiki/Interlaced_video)를 사용했다. 비월주사는 Frame Rate을 증가시키며 (실제로 증가하지 않되 증가된 것과 같이 인식된다) 대역폭(bandwidth)를 그대로 유지한다는 장점이 있다. 더불어, 움직이는 모션을 부드럽게 하며 Flicker를 줄여주는 효과가 있다. 하지만 Progressive Scan (모든 픽셀을 그리는 방식)과 비교하여 디테일이 부드럽지 못 하고 움직임 아티팩트 (Motion Artifact)가 생긴다는 단점이 있다.

![[CRT_image_creation_animation.gif | 300]]

[주사(Scan) 관련 추가 자료](https://lurkertech.com/lg/fields)

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
1. 부피가 크고 무겁다
2. 비평면 CRT에서 발생하는 기하학적 왜곡
3. 최고 명도와 컬러 렌더링에 이르기까지 예열시간이 필요하다
4. 전력 소모가 많다
5. 습기에 취약하다
6. 낮은 재생률의 경우 화면 깜빡임이 나타난다
7. 치명적인 내부 전압

### LCD 디스플레이
LCD 디스플레이는 주변광 또는 내부 광원으로부터 나오는 빛을 막거나 통과시키도록 정렬될 수 있는 액정물질 (Liquid Crystal)을 조절하여 그림을 그린다.

LCD 디스플레이의 일반적인 문제로 [불량화소 (Defective Pixel)](https://en.wikipedia.org/wiki/Defective_pixel)가 있다. 불량화소 유형 중 고착화소 (Stuck Pixel)은 화소가 항상 켜져 있는 현상이고, 죽은 화소 (Dead Pixel)은 화소가 항상 꺼저 있는 현상이다.

### 모니터 규격
LCD 모니터의 규격을 규정하는 요소는 다음과 같다.
1. 해상도 (Resolution)
2. 도트 피치 (Dot Pitch)
3. 반응시간 (Response Time)
4. 재생률 (Refresh Rate)
5. 지원 색상 (색 심도 Color Depth & 색 재현율 Color Gamut)
6. 시야각 (Viewing Angle)
7. 명암 대비 (Contrast Ratio)
8. 종횡비 (Aspect Ratio)

#### 모니터 비교 차트
|      Monitor Type     |         **LCD**        |         **LED**        |           **OLED**           |         **Plasma**        |        **CRT**       |
|:---------------------:|:----------------------:|:----------------------:|:----------------------------:|:-------------------------:|:--------------------:|
|       Full Form       | Liquid Crystal Display |  Light Emitting Diode  | Organic Light Emitting Diode | PDP, Plasma Display Panel |   Cathode Ray Tube   |
| Color and Black Level |          Good          |        Excellent       |           Excellent          |         Excellent         |         Good         |
|        Contrast       |    1,000:1 ~ 4,000:1   |        100,000:1       |          1,000,000:1         |          20,000:1         |       15,000:1       |
|       Brightness      |          Fair          |          Good          |           Excellent          |            Fair           |         Good         |
|    Weight and Size    |    compact and light   | compact and very light |        large and heavy       |   large and little heavy  | bulky and very heavy |
|     Response Time     |        8 - 10 ms       |        8 - 10 ms       |            0.1 ms            |           0.1 ms          |         1 ms         |
|   Energy Consumption  |           Low          |        Very Low        |           Moderate           |          Moderate         |         High         |
|      Manufacture      |       Continuing       |       Continuing       |          Continuing          |        Discontinued       |     Discontinued     |

source : [Digital World 839 - Computer Basics - 5 Different Types of Monitors](https://digitalworld839.com/different-types-of-monitor-computer/)

## 참고 자료
- [Programmer's Guide to Video Systems - Lurker's Guide](https://lurkertech.com/lg/video-systems/)
- [The Lurker's Guide](https://lurkertech.com/lg/)