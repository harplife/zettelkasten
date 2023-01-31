---
aliases: [Computer Graphics, 컴퓨터 그래픽스]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study]
status: ongoing
created: 2022-03-02
edited: 2022-05-30
---

# 컴퓨터 그래픽스
방통대 교과서에 있는 내용을 토대로 하되, 여러 부분을 수정/제거/추가한 노트. 개인적으로 느낀 바로, 방통대 교과서는 정리가 잘 안 되어 있을 뿐만이 아니라 틀린 정보가 많다.

## 용어 정의
[컴퓨터 그래픽스(Computer Graphics)](https://en.wikipedia.org/wiki/Computer_graphics)는 이미지를 컴퓨터로 구현하는 기술을 뜻한다.

"이미지"라는 용어가 다양하게 사용되다 보니 컴퓨터 그래픽스에서 좀 헷갈린다. 영어도 이와 관련되어 혼용되는 단어가 많다. 따라서, 여기선 내 방식대로 용어 정의 한다!
- 장면(Scene) : 시각적 요소(물체, 빛, 그림자 등)를 담는 시공간 범위/단위. 시각적 요소로 상황을 묘사한 개념적인 문구에 가깝다 (예: "파란색 삼각형이 있다").
- 영상(Picture) : 아날로그 또는 디지털 매체를 통해 장면을 재현한 것.
- 그림(Drawing) : 아날로그/디지털 매체가 영상을 그리는 행위/결과물.
- 이미지(Image) :  영상을 담는 디지털 매개체. 주로 이미지 파일을 뜻한다.
- 이미지 데이터(Image Data) : 이미지의 픽셀값 (또는 픽셀값을 저장한 비트)
- 영상 처리(Picture Processing) : 영상을 이미지로 변환하는 작업
- 이미지 처리(Image Processing) : 디스플레이 시스템으로 이미지를 변환/전송/저장하는 작업
- 렌더링(Rendering) : 그래픽스 소프트웨어로부터 내려진 이미지를 그리라는 명령과 이미지 데이터를 그래픽스 장치(CPU/GPU)에서 처리하여 화면에 표출하는 작업

위 용어들을 사용해서 종합적인 디지털 그래픽스 처리 프로세스를 간단히 정의하면,
1. 스캐너(카메라 등)을 통해 한 장면의 영상을 이미지로 저장한다.
2.  이미지를 그릴수 있는 디스플레이 시스템으로 이미지 데이터를 전송하고 저장한다.
3.  디스플레이 시스템에서 이미지를 변환한다 (예: 스크린에 맞는 사이즈로 축소/확대).
4.  디스플레이 시스템에서 이미지를 그린다.

일반적으로 장면, 영상, 그림, 이미지의 차이는 애매하고 서로 많이 혼용된다.

[그래픽스 (Graphics)](https://en.wikipedia.org/wiki/Graphics)는 컴퓨터 그래픽스 시스템에서 디지털 이미지를 처리하는 방식을 뜻한다. 컴퓨터 과학 기준으로 [자료 구조 (Data Structure)](https://en.wikipedia.org/wiki/Data_structure)라 볼 수 있다.

참고 2 : 컴퓨터 그래픽스 시스템에서 처리된 이미지를 "그래픽스"라고도 한다. 그래픽스는.. 동명사라고 해야할까? 방식과 방식으로 처리된 것, 이 둘 다 뜻하는 것을 뭐라부를까?

## 컴퓨터 그래픽스 토픽
1. 하드웨어
2. 소프트웨어
3. 기본 요소
4. 기본 요소의 속성
5. 기하변환
6. 2차원 뷰잉
7. 3차원 뷰잉
8. 선과 면의 표현
9. 가시면 결정
10. 조명 및 표면 렌더링

## 컴퓨터 그래픽스 하드웨어
[[computer_graphics_hardware|컴퓨터 그래픽스 하드웨어]]

## 컴퓨터 그래픽스 소프트웨어
[[computer_graphics_software|컴퓨터 그래픽스 소프트웨어]]

## 컴퓨터 그래픽스 기본 요소
- 점 그리기
- 선분 그리기
- 원 그리기
- 다각형 그리기

## 컴퓨터 그래픽스 기본 요소의 속성
- 색 모델
- 속성 파라미터
- 영역 채우기 알고리즘
- 안티 에일리어싱

## 기하변환
- 기본 2차원 변환
- 행렬표현과 동차좌표
- 기본 3차원 변환
- 복합기하변환
- 기타 기하변환
- 좌표계 사이의 변환
- OpenGL의 기하변환

## 2차원 뷰잉
- 2차원 뷰잉 파이프라인
- 클리핑과 뷰포트 변환
- 선분 클리핑
- 다각형 클리핑

## 3차원 뷰잉
- 3차원 뷰잉 개요
- 3차원 뷰잉 좌표 파라미터
- 평행투영
- 원근투영
- 3차원 클리핑 알고리즘
- OpenGL의 3차원 뷰잉

## 선과 면의 표현
- 객체의 모델링
- 2차 곡면
- 스플라인 곡선 및 곡면

## 가시면 결정
- 가시면 결정 방법의 개념
- 깊이 버퍼 알고리즘
- 주사선 알고리즘
- 깊이정렬 기법
- OpenGL의 가시면 결정 함수

## 조명 및 표면 렌더링
- 표면 렌더링 개요
- 조명 모델
- 다각형 음영법


# 참고자료
- [Pixar 논문 모음](https://graphics.pixar.com/library/)
- [OpenGL 교육 자료](https://learnopengl.com/)
- [C++ 교육 자료](https://www.learncpp.com/)
- [Microsoft - Direct X 교육 자료](https://docs.microsoft.com/en-us/windows/uwp/gaming/directx-programming)