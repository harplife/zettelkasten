---
aliases: [Computer Graphics Note]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study]
status: ongoing
created: 2022-03-02
edited: 2022-03-12
---

# Computer Graphics Note
방통대 교과서에 있는 내용을 토대로 하되, 여러 부분을 수정/제거/추가한 노트.

개인적으로 느낀 바로, 방통대 교과서는 정리가 잘 안 되어 있을 뿐만이 아니라 틀린 정보가 많다.

# 컴퓨터 그래픽스 하드웨어
컴퓨터 그래픽스 시스템을 구성하는 하드웨어 요소들과 동작 원리를 알아본다.
1. [[#컴퓨터 그래픽스 시스템 구성]]
2. [[#그래픽스 출력 방식]]
3. [[#디스플레이 종류]]
4. [[#디스플레이 규격]]

## 컴퓨터 그래픽스 시스템 구성
컴퓨터 그래픽스 시스템은 3가지로 구성되어 있다.
1. 입력장치
2. 그래픽스 워크스테이션 (PC)
3. 출력장치

![[computer.PNG | 300]]

### 입력장치
컴퓨터 그래픽스 시스템에서 [입력장치 (Input Device)](https://en.wikipedia.org/wiki/Input_device)는 키보드, 마우스, 컨트롤러 등 PC에 연결되어 신호를 전송하는 장치를 뜻한다.

### 그래픽스 워크스테이션
그래픽스 워크스테이션이라 쓰고, 컴퓨터(PC)라고 읽는다.

일반적으로 "워크스테이션"은 전문 작업을 수행하는데 적합한 고성능 컴퓨터를 뜻한다. 그래픽스 워크스테이션은 말 그대로 컴퓨터 그래픽 업무 전용 고성능 컴퓨터를 뜻한다.

그래픽스 워크스테이션은 4가지로 구성되로 있다.
1. 중앙처리장치 (CPU)
2. 메모리 (RAM)
3. [[#그래픽 카드]]
4. [[#출력 인터페이스]]

![[knou_cg_pic1-14.jpg]]

#### 그래픽 카드
[그래픽 카드 (Graphics Card)](https://en.wikipedia.org/wiki/Graphics_card)는 그래픽 작업을 전문적으로 빠르게 처리하고 이미지 데이터를 출력장치에 전송하는 역할을 하는 [확장 카드](https://en.wikipedia.org/wiki/Expansion_card)이다.

참고: 그래픽 작업 외 다목적 컴퓨팅에도 사용되기도 한다 (예: 인공지능, 비트코인 채굴) -  [GPU 상 다목적 컴퓨팅 (GPGPU)](https://en.wikipedia.org/wiki/General-purpose_computing_on_graphics_processing_units). [OpenCL](https://sweetcode.io/know-when-you-need-opencl/), Cuda 등의 병렬처리 프레임워크를 참고해보면 좋다.

그래픽 카드가 "확장 카드"인 이유는 그래픽 카드가 컴퓨터의 필수 요소가 아니기 때문이다. 정확히는, 그래픽 카드가 없어도 CPU에 아주 기본적인 영상처리 기능이 있기 때문에 모니터에 연결해서 이미지를 볼 수 있다.

#todo 규격/성능 관련 부분 추가. [참고1](https://www.binarytides.com/graphics-card-specs-explained/), [참고2](https://m.blog.naver.com/neolims/50096275324)

그래픽 카드의 구성 요소는 다음과 같다.
1. GPU
2. 방열판
3. 비디오 BIOS
4. 비디오 메모리
5. RAMDAC
6. 출력 인터페이스

##### GPU
[GPU (Graphics Processing Unit)](https://en.wikipedia.org/wiki/Graphics_processing_unit)는 그래픽 작업을 가속하기 위해 최적화된 전용 프로세서/전자회로 이다. 

GPU는 3D 그래픽스 렌더링에 필수적인 실수 연산을 실행하기 위하여 특별하게 설계된다. 특히나 다수의 코어를 활용하여 병렬처리를 하기 때문에 고속의 실수연산이 가능하다.

참고: CPU는 수많은 [명령어 집합 (Instruction Set)](https://en.wikipedia.org/wiki/Instruction_set_architecture)을 갖추고 있고 복잡한 연산이 가능하다. 반면에, GPU는 적은 수의 명령어 집합을 갖추고 있고 간단한 실수 연산만 가능하다.

GPU는 주로 그래픽 카드에 탑재되지만 일부 시스템에서는 CPU 내에 구현되기도 한다.
- 그래픽 카드에 탑재되면 Discrete GPU (dGPU), 전용 그래픽이라 불리운다.
- CPU에 탑재되면 Integrated GPU (iGPU), 내장 그래픽이라 불리운다.

참고: 전용 그래픽은 Dedicated GPU라고 불리기도 한다.

일반적으로 사무용 컴퓨터/노트북에는 내장 그래픽을 사용한다. 게임용/전문가용 컴퓨터는 전용 그래픽을 사용한다.

전용 그래픽을 "외장" 그래픽이라 부르지 않는 이유는 이미 외장 그래픽 (External GPU)이라는 개념이 있기 때문이다. 전용 그래픽, 내장 그래픽은 컴퓨터 구조 내부에 있지만, 외장 그래픽은 말 그대로 컴퓨터 구조 바깥에 있어 케이블로 연결해서 사용한다. 다른 유형의 GPU보다 성능이 좋지 않고 좀 번거롭기 때문에 인기는 별로 없다.

참고: 일반적으로 그래픽 카드와 GPU는 혼용되어 불리운다. 하지만 GPU와 그래픽 카드는 엄연히 다른 것이며 명확히 구분할 필요가 있다.

##### 비디오 BIOS
[비디오 BIOS](https://en.wikipedia.org/wiki/Video_BIOS)는 그래픽 카드의 초기 설정과 간단한 동작을 제어하기 위해 최소한의 기능을 포함한 프로그램으로 컴퓨터 시작 시 (그래픽 카드 시작 시) 실행된다.

컴퓨터와 소프트웨어가 그래픽 카드와 상호 동작할 수 있도록 하는 명령어를 지원한다.

##### 비디오 메모리
비디오 메모리는 화면에 출력할 그래픽 데이터를 저장하는 용도로 사용한다.

비디오 메모리에 저장할 수 있는 여러 프로그램 및 데이터:
- [깊이 버퍼 (Z-Buffer)](https://en.wikipedia.org/wiki/Z-buffering)
- [텍스처 매핑 (Texture Mapping)](https://en.wikipedia.org/wiki/Texture_mapping)
- [버텍스 버퍼 (Vertex Buffer)](https://en.wikipedia.org/wiki/Vertex_buffer_object)
- [셰이더 프로그램 (Shader)](https://en.wikipedia.org/wiki/Shader)

#todo 비디오 메모리가 어떻게 활용되는지, 아직 정확한 지식이 없다. 결국엔 여러군데 둘러봐야 할 것 같다. [Hardware Overlay](https://en.wikipedia.org/wiki/Hardware_overlay)가 참고해볼만한 것 같다.

##### RAMDAC
[RAMDAC (Random Access Memory Digital-to-Analog Converter)](https://en.wikipedia.org/wiki/RAMDAC)은 아날로그 디스플레이 장치(i.e. CRT, etc)를 위하여 디지털 신호를 아날로그 신호로 변환한다.

사용되는 비트 수와 RAMDAC 데이터 전송률에 따라 변환기는 다른 Refresh Rate을 지원할 수 있다.
- CRT 디스플레이 경우 Flicker를 최소화하기 위하여 75hz 이상에서 최상으로 동작
- LCD 디스플레이는 Flicker 문제가 없음

디지털 디스플레이 장치가 대중화되며 아날로그 디스플레이 장치가 사라져 가고 있으며, 마찬가지로 RAMDAC도 같이 사라져 가고 있다.

#### 출력 인터페이스
[출력 인터페이스](https://en.wikipedia.org/wiki/Audio_and_video_interfaces_and_connectors)는 그래픽 카드와 디스플레이 간을 연결하는 시스템/규격을 뜻 한다.

가장 보편적인 연결 시스템은 다음과 같다.
1. Video Graphics Array (VGA) : CRT 디스플레이를 위하여 1980대 후반 채택된 아날로그 기반 표준. 전기적 잡음, 영상왜곡, 표본화 오차 등의 문제를 갖고 있다.
2. Digital Visual Interface (DVI) : LCD, 플라즈마 스크린 등의 Flat Display를 위한 디지털 기반 표준. 영상왜곡, 전기적 잡음 등을 피할 수 있다.
3. Video In Video Out (VIVO) : TV, DVD 재생기, 비디오 녹화기 등을 위한 S-비디오, 복합 비디오, 컴포넌트 비디오를 위한 표준. 빨강, 파랑, 노상, 초록 등 여러 가지 색상으로 되어있던 케이블 이다.
4. High-Definition Multimedia Interface (HDMI) : 2003년에 발표된 디지털 오디오/비디오 표준. HDCP 복사장지 기능을 제공한다.
5. [Display Port](https://en.wikipedia.org/wiki/DisplayPort) : 2007년에 발표된 오디오/비디오 표준. 특허권 사용료 없음.

그 외에 USB-C, Thunderbolt 등이 있다. 심지어는 [무선 디스플레이 (Miracast)](https://en.wikipedia.org/wiki/Miracast)]도 있다.

### 출력 장치
컴퓨터 그래픽스에 있어서 [출력 장치 (Output Device)](https://en.wikipedia.org/wiki/Output_device)는 출력 인터페이스를 통해 컴퓨터로부터 받는 이미지 데이터를 인간이 볼 수 있는 이미지로 재현하는 장치를 뜻한다.

기본적인 예시로 모니터, 프로젝터, 그리고 프린터가 있다.

컴퓨터 그래픽스 관련 노트에서는 출력 장치 또는 기술 관련해서는 모니터 위주로 설명할 것이다. 그리고 편의상 출력 장치를 "디스플레이" 또는 "모니터"라고 부른다.

## 그래픽스 출력 방식
화면에 그림을 그리는 방식을 디스플레이 (Display) 또는 스캔 (Scan/Scanning)이라 부른다.

장치도 디스플레이, 기술도 디스플레이라고 하니 많이 헷갈린다. 심지어 인터넷에 나와있는 자료들도 단어들을 혼용한다. 따라서,이 문제를 해결하기 위해 용어 정의를 한다:
1. 디스플레이 : 그림을 그리는 장치
2. 스캔 : 그림을 읽거나, 전송하거나, 또는 그리는 방식
3. 그래픽스 : 그림/이미지 (데이터)
4. 컴퓨터 그래픽스 : 컴퓨터로 그림을 그리는 기술 분야

스캔 (Scan)은 한글로 "주사"라고도 하지만, 되도록이면 그냥 스캔이라고 칭하겠다.

일반적으로 "스캔"은 보통 촬영 (카메라, 스캐너 등 장치를 사용하여 현실의 객체를 기록/저장하는 행위)과 같은 개념으로 이해된다. 하지만 컴퓨터 그래픽스에 있어서 "스캔"은 이미지를 읽고, 신호로 변환하고, 전송하고, 그리고 그리는 것, 이 전체를 뜻한다.

물론, 읽는 방식, 변환 방식, 전송 방식, 그리는 방식 각각에 사용되는 다양한 기술들도 있다. 스캔은 단순히, 이 모든 것의 틀이 되는 가장 큰 개념이라고 볼 수 있다.

읽기/변환/전송/그리기, 이렇게 표현하기 번거롭기 떄문에, 편의를 위해 일단 스캔은 그림을 그리는 방식 또는 그래픽스 출력 방식이라고 표현한다.

스캔은 두 가지 종류가 있다.
1. 벡터 스캔
2. 래스터 스캔

### 벡터 스캔
[벡터 스캔 (Vector Scan)](https://en.wikipedia.org/wiki/Vector_monitor)는 점 또는 라인으로 명령 집합(지정된 경로)에 따라 빛을 내어 그림을 그리는 방식이다. Random Scan이라고도 불리운다.

![[vector_scan_01.PNG]]

참고: [벡터 그래픽스 (Vector Graphics)](https://en.wikipedia.org/wiki/Vector_graphics)는 기본 도형으로 명령 집합에 따라 이미지를 그리는 방식으로, 벡터 스캔의 개념과 유사하되 디자인 (일러스트레이션) 분야에 사용되는 기술이기 때문에 헷갈리면 안 된다.

벡터 스캔은 그림(이미지 데이터)을 그래픽스 명령들로 표현하며, 이를 [Display List](https://en.wikipedia.org/wiki/Display_list) 또는 Display Program이라고 한다. 여기서 명령이란 좌표계에 위치(점)을 지정하거나 라인을 그리는 지시를 뜻한다.

![[knou_cg_pic1-15.jpg]]

벡터 스캔은 래스터 스캔과 달리 Aliasing 문제가 발생하지 않는 장점이 있어 설계도면을 그리는데 많이 사용되었다. 1970년 이후에는 래스터 스캔이 대중적으로 사용됨으로 벡터 스캔은 [오실로스코프 (Oscilloscope)](https://en.wikipedia.org/wiki/Oscilloscope)와 같은 특정 과학/의료/방위 기구들을 제외하고 더 이상 사용되지 않는다.

![[oscilloscope_animation_01.webp]]

주의 : 벡터 스캔은 벡터 디스플레이 또는 벡터 모니터라고도 불리운다.

### 래스터 스캔
[래스터 스캔 (Raster Scan)](https://en.wikipedia.org/wiki/Raster_scan)은 수많은 점으로 이루어진 그리드 형식의 사각형 화면에 왼쪽 상단부터 오른쪽 하단까지 지그재그 형식에 순서대로 각 점에 빛을 내는 방식이다.

필요한 부분만 그리는 벡터 스캔과 달리, 래스터 스캔은 전체 화면을 그린다.

우리가 일반적으로 사용하는 모니터는 래스터 스캔을 사용한다.

![[raster_scan_01.PNG]]

참고: [래스터 그래픽스 (Raster Graphics)](https://en.wikipedia.org/wiki/Raster_graphics)는 래스터 스캔에 그려지는 그림을 뜻한다. 벡터 그래픽스와 같이 디자인 (일러스트레이션) 분야에 사용된다.

참고 : 어떤 자료에는 래스터 스캔은 CRT에만 사용된다고 하고, 다른데는 LCD에서도 사용한다고 상반된 내용이 있다.

#### 픽셀
그리드 상의 각 점은 [픽셀 (Pixel)](https://en.wikipedia.org/wiki/Pixel) 또는 화소라 부른다. 각 픽셀의 밝기를 조절하여 그림을 그릴 수 있다. 픽셀로 색을 표현하기도 하며, 이 부분은 [[#컬러 모니터]]에 설명한다.

![[pixel_closeup.webp]]

래스터 스캔은 그림(이미지 데이터)을 픽셀 값 목록으로 표현한다. 여기서 픽셀 값이란 빛의 강도를 뜻하며, 0~255 사이의 값이 사용된다.

![[lincoln_pixel_values.png]]

참고: 픽셀 값들은 화면에 그려지기 전에 [프레임 버퍼 (Frame Buffer)](https://en.wikipedia.org/wiki/Framebuffer)에 저장된다. 자세한 내용은 나중에 다루겠다.

#### 스캔 라인
좌우로 그려진 한 행의 픽셀들을 [스캔 라인 (Scan Line)](https://en.wikipedia.org/wiki/Scan_line) 또는 주사선이라고 한다.

![[slowmo_raster_scan_half.gif]]
![[scanline_slowmo_mario.webp]]

#### 이미지 vs. 프레임
스캔 라인이 최상단에서 최하단까지 한번 지나가면 하나의 "이미지"가 보여진다. 하지만 여기서 편의상 이미지라 하는 것이고, 보다 명확한 용어가 없는 듯 하다. 워낙 이미지란 단어가 너무 다양하게 사용되서 헷갈린데, 어쩔수가 없다.

[프레임 (Frame)](https://en.wikipedia.org/wiki/Film_frame)은 영상에 찍혀진 여러 정적 이미지 중 하나의 이미지를 뜻한다.

화면의 그려지는 이미지와 콘텐츠의 프레임을 잘 구분해야 한다. 서로 비슷한 개념이며 상관 관계도 꽤 깊은 편이다. 관련된 자세한 내용은 [[#재생률]]에서 다룬다.

참고: 이미지 크기, 즉, 디스플레이 화면의 크기를 [[#해상도]]라고 한다.

#### 순차 주사 vs. 비월 주사
래스터 스캔은 순차 주사와 비월 주사로 구분된다.

![[interlaced_progressive_comparison.png]]

[순차 주사 (Progressive Scan)](https://en.wikipedia.org/wiki/Progressive_scan)는 화면의 최상단부터 최하단까지 프레임 전체를 스캔하는 방식을 뜻하며, Non-interlaced Scan 이라고도 불린다.

Reminder : 여기서 스캔 (Scan)은 이미지를 촬영, 전송, 또는 그리는 것을 뜻한다. 촬영되는 규격에 맞추어 전송이 되어야 하고, 전송 규격에 따라 그리는 것도 또한 맞춰저야 하기 때문이다.

[비월 주사 (Interlaced Scan)](https://en.wikipedia.org/wiki/Interlaced_video)는 홀수 번째 주사선과 짝수 번째 주사선을 번갈아 프레임의 일부만 스캔하는 방식을 뜻한다. 첫 번째 프레임에 홀수 번째 주사선만 그려 스캔했다면, 다음 프레임은 짝수 번째 주사선만 그려 전송하고, 다음은 홀수, 다음은 짝수, 이런 식으로 번갈아 가며 스캔한다.

반쪽짜리 프레임을 [필드 (Field)](https://en.wikipedia.org/wiki/Field_(video))라고 한다.

![[interlaced_scan.gif | 300]]

비월 주사의 장점은:
- 프레임의 일부만 보내기 때문에 데이터 용량이 작다. 순차 주사 영상에 비해 데이터 전송량이 절반이라 보면 된다.
- 대역폭 (Bandwidth)를 크게 높일 필요없이 [프레임 레이트 (Frame Rate)](https://en.wikipedia.org/wiki/Frame_rate)를 높일 수 있다. 1초에 순차 조사 프레임 30개 보내기 충분한 네트워크에서 비월 주사 프레임을 60개를 보낼 수 있다는 뜻이다. 프레임 레이트가 높으면 움직임이 더 부드러워 보인다.
- 대역폭 (Bandwidth)를 크게 높일 필요없이 [[#해상도]]를 높일 수 있다. 보다 큰 화면에서 영상을 즐길 수 있다.

비월 주사의 단점은:
- 순차 주사보다 선명도가 떨어진다.
- [영상 압축 (Video Compression)](https://en.wikipedia.org/wiki/Video_coding_format)으로 인해 퀄리티가 많이 떨어질 수 있다.
- Combing이라는 비월 주사 특유의 모션 에러 현상 (Motion Artifact)이 발생할 수 있다.

참고 : [주사(Scan) 관련 추가 자료](https://lurkertech.com/lg/fields)

##### HDTV
[High-Definition Television (HDTV)](https://en.wikipedia.org/wiki/High-definition_television)은 "고화질" 영상을 시청할 수 있는 TV 방송과 수신기(TV 모니터)를 뜻한다.

2000년도에 지정된 기준으로, "고화질"은 밑에 3가지 [[#해상도]] + 주사 방식 조합을 뜻한다:
1. 720p : 해상도 1280x720  + 순차 주사
2. 1080i : 해상도 1920x1080  + 비월 주사
3. 1080p : 해상도 1920x1080 + 순차 주사

2022년 기준 현재, 고화질을 넘어선 "초고화질" 기술, [Ultra-High-Definition TV (UHDTV)](https://en.wikipedia.org/wiki/Ultra-high-definition_television)도 있다. 아직 대중화되지는 않았다.

#### 컬러 모니터
컬러 디스플레이에서 픽셀은 RGB (빨강, 초록, 파랑) 색상을 갖는 [부화소 (Subpixel)](https://en.wikipedia.org/wiki/Pixel#Subpixels) 3개로 구성된다.

![[pixel_subpixel.PNG]]

색상을 구현하기 위해 각 부화소는 독립적으로 제어되며, 모니터의 용도에 따라 여러 가지 형태의 [화소 배열 (Pixel Geometry)](https://en.wikipedia.org/wiki/Pixel_geometry)로 배치된다. 특정 디스플레이의 화소 배열 형태를 알고 있다면, [부화소 렌더링 (Subpixel Rendering)](https://en.wikipedia.org/wiki/Subpixel_rendering)을 소프트웨어로 구현하여 모니터의 외견상 해상도를 향상시킬 수 있다.

![[pixel_geometry.PNG | 300]]

##### 가산혼합과 감산혼합
참고 : [빛 (Light)](https://en.wikipedia.org/wiki/Light)은 아주 복잡하다. 빛은 반사되고, 흡수되고, 통과되고, 왜곡되고 별별 특성을 다 갖고 있다. [색 (Color)](https://en.wikipedia.org/wiki/Color)은 빛에서 나오기 때문에, 색도 마찬가지로 복잡하다. 여기서 다루는 내용은 "내가 이해할 수 있는" 수준으로 간단하게 정리한 것이기 때문에, 좀 더 정확한 정보는 따로 리서치 해봐야 한다.

![[light_dispersion_prism.PNG]]

[가산혼합 (Additive Color)](https://en.wikipedia.org/wiki/Additive_color)은 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

가산 (Additive)의 의미는 빛이 없는 공간 (검은색)에 빛을 "더하여" 하얀색으로 만든다는 뜻이다. 다른 말로는, 검은색에 각 색을 "더하여" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 더하면 하얀색이 나온다.

가산혼합에 사용되는 색을 [원색 (Primary Color)](https://en.wikipedia.org/wiki/Primary_color)이라고 부르며, 서로 독립적인 색을 뜻한다 - 서로 독립적인 색은, 둘을 혼합해도 남은 셋째의 색을 만들 수 없다.

가산혼합에 일반적으로 사용되는 원색은 RGB: Red, Green, Blue이다. 이 색들을 사용하는 가산혼합을 [RGB 색 모델](https://en.wikipedia.org/wiki/RGB_color_model)이라 부른다.

모든 모니터/프로젝터는 RGB 색 모델을 사용한다.

이론적으로 RGB가 아닌 다른 가산혼합 원색도 있다. 하지만 사람은 RGB 색에 가장 민감하게 반응하기 때문에 RGB가 사용된다.

![[rgb_summation.webp]]

[감산혼합 (Subtractive Color)](https://en.wikipedia.org/wiki/Subtractive_color)은 가산혼합과 마찬가지로 3개 색을 혼합하여 모든 색을 구현하는 방식이다.

감산 (Subtractive)의 의미는 빛이 반사하는 공간 (하얀색)에 빛을 "빼서" 검은색으로 만든다는 뜻이다. 다른 말로는, 하얀색에 각 색을 "빼서" 여러 색을 구현한다는 뜻이다. 최종적으로 모든 색을 최대 비율로 빼면 검은색이 나온다.

감산혼합에 일반적으로 사용되는 원색은 CMY: Cyan, Magenta, Yellow이다. 이 색들을 사용하는 감산혼합을 [CMY 색 모델](https://en.wikipedia.org/wiki/CMY_color_model)이라 부른다.

모든 인쇄기는 CMY (정확히는 CMYK) 색 모델을 사용한다.

마찬가지로 CMY가 아닌 다른 감산혼합 원색도 있지만, CMY가 "얕은 색"을 구현하기 제일 쉬운 조합이기 때문에 사용된다 (얕은 색에서 찐한 색으로 가는 것은 가능하지만, 그 반대는 불가능하다).

![[color_mixes.png]]

참고: 모니터에 출력되는 색은 인쇄기로 출력된 색과 다르게 보일 수 있다. 서로 색 모델이 다를 뿐더러, 잉크 (Ink)의 한계가 있다. 인쇄기 출력물과 매칭되는 색을 봐야한다면, 포토샵 같은 디자인 전용 프로그램에서 보정을 해줘야 한다.

![[cmyk_conversion.PNG]]

## 디스플레이 종류
그래픽 시스템에서 기본 출력장치이자 가장 일반적인 디스플레이 장치는 모니터다.

### 평판 디스플레이
[평판 디스플레이 (Flat-Panel Display)](https://en.wikipedia.org/wiki/Flat-panel_display)는 부피가 얇고, 화면이 평평한 비디오 장치를 뜻한다. 한떄는 화면이 둥그런 CRT와 비교되어 이 단어에 큰 의미가 있었지만, 요즘에는 [곡면 디스플레이 (Curved Screen)](https://en.wikipedia.org/wiki/Curved_screen)를 제외한 모든 디스플레이가 평판 디스플레이기 때문에 그리 큰 의미가 없다.

### 방사성 vs. 비방사성
[평판 디스플레이는 두 가지 부류로 나뉜다](https://siim.org/page/displays_chapter2).
1. 방사성 (Emissive)
2. 비방사성 (Nonemissive)

방사성 디스플레이는 각 픽셀에서 다양한 강도와 색상의 빛을 발한다. 기본적으로 명암 대비율이 높은 편이며, 완벽한 검정 (True Black)을 구현한다. 더불어, 대부분의 방사성 디스플레이는 [램버시안 법칙](https://en.wikipedia.org/wiki/Lambert%27s_cosine_law)에 따라 각도와 관계없이 같은 밝기를 갖기 때문에 [[#시야각]]이 넓다.

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

음극선 (또는 전자빔, e-beam)은 [[#그래픽스 출력 방식]]에 따라 편향 시스템으로 제어되어 스크린 위에 그림을 출력한다.

![[Cathode_ray_Tube.png | 300]]

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

일반 LCD 모니터는 내부 광원으로 [형광등](https://en.wikipedia.org/wiki/Fluorescent_lamp)을 사용한다.

LCD 디스플레이의 일반적인 문제로 [불량화소 (Defective Pixel)](https://en.wikipedia.org/wiki/Defective_pixel)가 있다. 불량화소 유형 중 고착화소 (Stuck Pixel)은 화소가 항상 켜져 있는 현상이고, 죽은 화소 (Dead Pixel)은 화소가 항상 꺼저 있는 현상이다.

### LED 디스플레이

### 플라즈마 디스플레이

### OLED 디스플레이

## 디스플레이 규격
모니터의 규격을 규정하는 요소는 다음과 같다.
1. [[#화면 사이즈]]
2. [[#해상도]]
3. [[#픽셀 밀도]]
4. [[#응답 시간]]
5. [[#재생률]]
6. [[#색 재현율]]
7. [[#밝기]]
8. [[#명암 대비율]]
9. [[#시야각]]
10. [[#패널 종류]]
11. 입출력 및 연결성
12. 음향

### 화면 사이즈
모니터 화면의 물리적 크기로 대각선 길이를 뜻하며, 주로 inch로 표현된다.

모니터 패키징/광고에 표시된 화면 사이즈는 정확한 사이즈는 아니다. 실제 사이즈와 아주 아주 미세한 차이가 있다. 실제 사이즈는 "액티스 디스플레이 사이즈"라고 불리우며, 제품사양에 명시되어 있다.

모니터 화면에 따라 권장/적정 시청 거리가 있다 - 화면이 클 수록 시청 거리가 더 멀어야 한다.

### 해상도
해상도 (Resolution)는 디스플레이 화면의 총 픽셀 수 (스캔 라인 픽셀 수 x 스캔 라인 수)를 뜻 한다. 수평과 수직의 크기 (픽셀 수)로 1920 x 1080 과 같은 포맷으로 표현된다.

해상도가 높을수록 더욱 정교한 그림을 그릴 수 있다. 하지만, 그리려는 그림의 해상도가 모니터의 해상도보다 높은 경우, 이미지의 일부가 식별할 수 없게 되며 왜곡 현상이 일어난다. 이러한 현상을 [Aliasing](https://en.wikipedia.org/wiki/Aliasing)이라고 부른다 (정확히는 Spatial Aliasing이라고 부른다).

![[aliasing_example_01.PNG]]

Aliasing 현상 중 그림의 윤곽선이 거칠어지고 계단 형식으로 변하는 것을 [Jaggies](https://en.wikipedia.org/wiki/Jaggies)라고 부른다.

![[aliasing_example_02.PNG | 300]]

그리드 (Grid) 형식으로 촘촘이 수많은 작은 디테일이 있는 이미지에서는 [무아레 패턴 (Moiré Pattern)](https://en.wikipedia.org/wiki/Moir%C3%A9_pattern)의 Aliasing이 발생되기도 한다.

![[aliasing_example_03.PNG | 300]]

Aliasing 문제를 해결하기 위해 [Anti-Aliasing](https://en.wikipedia.org/wiki/Spatial_anti-aliasing)이 사용된다. Anti-aliasing의 기본 원리는 디테일이 작고 촘촘한 부분을 제거하거나 흐리게하는 것이다. Anti-aliasing에 사용되는 예시로 Low Pass Filter, Down Sampling, Gaussian Blur, Sinc Filter 등이 있다.

![[anti_aliasing_example_01.PNG]]

참고
1. 비디오 메모리 사용량은 화면 해상도에 따라 고정된다.
2. 아날로그인 CRT 모니터를 제외한 모든 모니터에는 최적의 해상도가 있다.
3. 화면 사이즈가 크다고 해상도가 높은 것이 아니다. 화면 사이즈에 비해 해상도가 낮을수록 선명도가 떨어진다.

### 픽셀 밀도
참고 : 픽셀은 논리적 픽셀 (Logical Pixel), 렌더 픽셀 (Rendered Pixel), 물리적 픽셀 (Physical Pixel)로 구분된다. 논리적 픽셀과 렌더 픽셀은 소프트웨어에서 다루는 가상의 픽셀을 뜻한다 ( #todo 자세한 내용은 나중에). 물리적 픽셀은 모니터 화면 (하드웨어)에 포함된 실제의 픽셀을 뜻한다. 여기서 다룰 내용은 물리적 픽셀을 위주로 설명된다.

픽셀의 크기는 고정되어 있지 않다. 화면 사이즈와 해상도를 비례하여 픽셀의 크기와 픽셀 간의 거리가 정해진다.

픽셀 간의 거리를 [도트 피치 (Dot Pitch)](https://en.wikipedia.org/wiki/Dot_pitch)라고 부른다.

[픽셀 밀도 (Pixel Density)](https://en.wikipedia.org/wiki/Pixel_density)는 모니터 화면의 일정한 단위 면적에 포함된 픽셀의 비율을 뜻하며, Pixel Per Inch (1인치 당 픽셀 수) 또는 Pixels Per Centimetre (1cm 당 픽셀 수)로 표현된다.

픽셀 크기와 도트 피치는 픽셀 밀도에 직접적인 영향을 준다. 픽셀 밀도가 높을 수록 더욱 상세한/선명한 이미지를 재현할 수 있지만, 특정 범위를 넘어서면 낭비이다. 일반 모니터는 화면 사이즈와 시청 거리를 고려하여 간접 픽셀이 인식되지 않을 수준의 픽셀 밀도를 갖춘다.

### 응답 시간
응답 시간, 또는 반응 시간 (Response Time)은 픽셀의 색상/밝기를 변화시키는 속도를 뜻한다.

일반적으로 BTB (Black to Black) 테스트가 사용되며, Black (inactive) → White (active) → Black (active) 으로 변경하는데 걸리는 시간을 ms 단위로 측정한다.

참고1 : 10 ms 정도는 사무용 또는 30 FPS 콘텐츠를 즐기는데 문제는 없지만, 60 FPS 이상의 경쟁 게임 (Competitive Gaming)에는 5ms 이하가 권장된다.

때로는 GTG (Gray to Gray) 테스트가 사용되기도 한다. 극과 극으로 변화하는 BTB 테스트와는 달리, 검은색과 하얀색 사이의 회색 범위 내에 여러번 변화하여 변화할때 마다 걸리는 시간의 평균을 측정한다.

참고2 : 검증된 것은 아니지만, GTG 테스트가 BTB 더 정확하다고 여겨지는 이유가 - 픽셀을 껐다 켰다 할때 변화 범위가 큼으로 높은 전압 (High Voltage)이 사용되어 변화 속도가 빠른 반면에, 픽셀을 켠 상태로 조금씩 변화하는 것은 낮은 전압 (Low Voltage)이 사용되어 변화 속도가 느리고, 컬러 TV의 특성상 픽셀은 하얀색/검은색으로 전환하는 것보다는 회색의 범위에 왔다갔다 하는 횟수가 많기 때문에 GTG 테스트가 실제 사용 환경에 더 유사하다는 것이다.

응답 시간이 느린 경우, Ghosting 또는 Smearing 현상이 일어난다고 한다.
- __Ghosting__ : 이전 프레임의 잔상이 보이는 현상. [Screen Burn-in](https://en.wikipedia.org/wiki/Screen_burn-in) 하고 혼동하면 안 된다.
- __Smearing__ : 빠르게 움직이는 물체가 늘어나서 흐리게 보이는 현상.

![[response_time_comparison.PNG]]

참고 : Ghosting, Smearing 문제는 응답 시간 뿐만이 아니라 주사 방식, 주사율, 패널 종류 등 여러 요인으로부터 발생된다.

### 재생률
[재생률 (Refresh Rate)](https://en.wikipedia.org/wiki/Refresh_rate)은 모니터가 화면에 1초 동안 이미지를 그리는 횟수를 뜻하며 Hz (Hertz) 단위로 센다.

주사율 (Scan Rate)이라고도 불리운다.

[프레임 레이트 (Frame Rate)](https://en.wikipedia.org/wiki/Frame_rate)도 마찬가지로 1초 동안 이미지를 그리는 횟수를 뜻하지만, 여기서 "그린다"는 것은 소프트웨어 / GPU가 이미지를 [렌더링 (Rendering)](https://en.wikipedia.org/wiki/Rendering_(computer_graphics))하는 것을 뜻한다.

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

### 색 재현율
[색 재현율 (Color Gamut)](https://en.wikipedia.org/wiki/Gamut)은 모니터가 색을 얼마만큼 표현할 수 이는지 나타내는 수치이다.

여기서 [색 (Color](https://en.wikipedia.org/wiki/Color)이란 아주 복잡한 개념이다.
알아둬야 할 것은,
1. [색 공간 (Color Space)](https://en.wikipedia.org/wiki/Color_space)는 색을 이해하기 위해 최대한 수학적으로 색을 정리한 좌표계를 뜻한다.
2. [CIE 1931](https://en.wikipedia.org/wiki/CIE_1931_color_space) 색 공간은 인간의 색 인식률과 [휘도 (Luminance)](https://en.wikipedia.org/wiki/Luminance)를 기준으로 표현한 좌표계 입니다. 이 색 공간은 다른 색 공간들의 기반이 되었다.
3. [NTSC](https://en.wikipedia.org/wiki/NTSC)는 National Television System Committee의 약자로, 방송용 전파에 대한 미국 표준화 담당기구의 이름이자, NTSC가 제정한 아날로그 방송 기술 표준을 의미한다. 이 표준에는 방송에 사용될 색 공간을 정의하고, 디스플레이 기술은 이 색 공간을 기준으로 색 재현율을 계산한다.
4. NTSC 외에도 다른 색 공간들도 정의되었으며, [각 색 공간들에 따라 용도가 여러 있다](https://en.wikipedia.org/wiki/List_of_color_spaces_and_their_uses).

참고 : 여러 포럼, Q&A 등을 찾아보면 일반적으로 NTSC 70% 정도이면 충분하다고 한다. 하지만 NTSC는 오래된, 퇴화한 기준으로 여겨지는 듯 하고, sRGB, Adobe RGB, DCI-P3 등이 좀 더 유용하게 사용되는 것으로 확인된다.

디자인, 포토그래피 등의 관련 업무를 하는 사람에게는 색 재현율이 중요하다. 모니터에 출력되는 색과 프린터에 출력되는 색이 다를 수도 있으며, 실제 눈으로 보는 색과 카메라에 찍히는 색이 다를 수도 있다. 그래픽 입출력 장치 간의 색 재현율 차이를 색 공간 기준으로 잘 매칭되는지 확인해야 한다.

### 밝기
[밝기 (Luminance)](https://en.wikipedia.org/wiki/Luminance)는 화면에 모든 픽셀을 켰을 경우 (하얀색 이미지를 그릴 경우) 측정된 빛의 강도를 뜻한다. 단위는 [cd/m² (Candela per square metre)](https://en.wikipedia.org/wiki/Candela_per_square_metre) 이되, _nit_ 으로 불리기도 한다 (1 nt = 1 cd/m²).

밝기의 영어는 Brightness와 Luminance가 있다. Luminance는 특정 기구를 사용하여 측정된 빛의 강도로서 객관적 (Objective) 측정 값을 뜻하는 방면, Brightness는 인간이 느끼는 빛의 강도로서 주관적 (Subjective) 측정 값을 뜻한다. 하지만 많은 사람들은 이 차이를 이해하지 못하기 때문에, 대부분 Brightness라고 부르는 경향이 있다.

모니터 제품사양에는 밝기를 3가지로 분류한다.
1. 최소
2. 보통 (Typical) : 중간값 정도로 생각하면 될 듯
3. 최대

밝기를 측정하는 테스트에 대한 표준이 없어서 이 제품사양은 곧이곧대로 믿기에는 힘들다.

참고1 : 포럼 글들 읽어보면, 대략 250 nit 정도가 괜찮은 수준이라고 한다.
참고2 : 갤럭시 S20 노트 울트라가 최대 밝기 1,342 nits 를 낸다고 한다. 직접 사용해보니, 해가 쨍쨍한 날 오후 2시 바깥에서 화면이 잘 보이긴 한다.
참고3: 프로젝터는 [Lumens](https://en.wikipedia.org/wiki/Lumen_(unit)) 단위로 밝기를 측정한다.

### 명암 대비율
[명암 대비율 (Contrast Ratio)](https://en.wikipedia.org/wiki/Contrast_ratio), 간단히 명암비라 부르며, 픽셀이 낼수 있는 빛의 강도 최대값과 최소값을 비교하는 값으로 n : n 포맷으로 표현한다 (e.g. 2,000 : 1)

밝기와 마찬가지로 명암비 테스트 방식에 대한 표준이 없다.

명암비가 낮으면 화면에 그림이 흙탕물처럼 흐리게 보인다고 한다. 반면에, 명암비가 높으면 더 많은 색상을 재현할 수 있어 이미지가 선명해 보인다고 한다.

참고 : `500:1`은 봐줄만한 수준이고, `1,000 : 1 (Typical)` 이 2022년도 최신 모니터 보통 수준이라고 보면 될 듯 하다.

### 시야각
[시야각 (Viewing Angle)](https://en.wikipedia.org/wiki/Viewing_angle)은 화면 정면에서 회도, 색도, 감마 등이 특정 기준을 만족하는 상하좌우 방향의 범위를 의미한다.

![[viewing_angle.jpg]]

여기서 "특정 기준"이란 이미지가 왜곡되는 현상의 허용 수준이며, 다른 말로 "보기 좋은 수준"이다.

![[tn_ips_comparison_01.jpg]]

시야각은 수직, 수평 각도(°)로 표현된다. 최대 시야각은 178°/178° 이다.

시야각은 [[#패널 종류]]에 큰 영향을 받는다.

### 패널 종류
#todo VA, IPS, 등등

참고: "IPS와 VA의 차이"라는 주제의 그림이다. 코멘트를 읽어보니 동의하는 사람도 몇 있지만, 오히려 주사율이 너무 높아서 생기는 문제라고 주장하는 사람들도 있다.
> ![[ips_va_panel_comparison.webp]]
> -- 이미지 출처 : [Reddit](https://www.reddit.com/r/Monitors/comments/ls81ey/ips_versus_va_monitor_in_one_gif_black_smearing/)


## 모니터 종류별 사양 비교 차트
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
- [Dell사에서 알려주는 "모니터 선택하는 방법"](https://www.dell.com/learn/us/en/22/consumer/choose-a-monitor-all)
- [티비를 슬로우 모션으로 보기](https://youtu.be/3BJU2drrtCM)

## 모니터 제품사양 예시
삼성 모니터 LS27R350 - LED(LCD) Standard(일반) 27인치 2019년 Full HD 모니터
![[samsung_monitor_S27R350_specs.jpg | 삼성 모니터 제품사양]]

# 컴퓨터 그래픽스 소프트웨어
그래픽스 워크스테이션에서 디지털 이미지를 다루는 방법, 즉, 그래픽스 소프트웨어에 대하여 알아본다.

## 컴퓨터 그래픽스 표현
[그래픽스 (Graphics)](https://en.wikipedia.org/wiki/Graphics)는 컴퓨터 그래픽스 시스템에서 다루는 디지털 이미지를 뜻한다. 컴퓨터 과학 기준으로 [자료 구조 (Data Structure)](https://en.wikipedia.org/wiki/Data_structure)라 볼 수 있다.

여기서 다룰 내용은 [[#래스터 스캔]] 기반 시스템에서 그래픽스를 표현하는 방식이다.

그래픽스 표현 방식은 래스터와 벡터로 2가지로 나뉜다.

### 래스터 그래픽스
[래스터 그래픽스 (Raster Graphics)](https://en.wikipedia.org/wiki/Raster_graphics)는 사각형 그리드 형식의 틀에 [[#픽셀]]로 표현하는 방식 또는 이미지를 뜻한다.

비트맵 이미지 (Bitmap Image)라고도 불리기도 한다 - [비트맵 (Bitmap)](https://en.wikipedia.org/wiki/Bitmap)은 디지털 이미지를 저장하는 메모리 저장 방식이다. 각 픽셀을 비트로

편의상 래스터 이미지로 불리기도 한다.

우리가 흔히 사용하는 `.jpg`, `.png`, `.gif` 이미지 파일 포맷이 래스터 그래픽스를 기반으로 한다.



### 벡터 그래픽스