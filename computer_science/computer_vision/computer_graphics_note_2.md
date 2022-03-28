---
aliases: [Computer Graphics Note 2]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study]
status: ongoing
created: 2022-03-27
edited: 2022-03-27
---

# Computer Graphics Note 2
방통대 교과서에 있는 내용을 토대로 하되, 여러 부분을 수정/제거/추가한 노트.

개인적으로 느낀 바로, 방통대 교과서는 정리가 잘 안 되어 있을 뿐만이 아니라 틀린 정보가 많다.

# 컴퓨터 그래픽스 소프트웨어
그래픽스 워크스테이션에서 디지털 이미지를 다루는 방법, 즉, 그래픽스 소프트웨어에 대하여 알아본다.

## 컴퓨터 그래픽스 표현
[그래픽스 (Graphics)](https://en.wikipedia.org/wiki/Graphics)는 컴퓨터 그래픽스 시스템에서 다루는 디지털 이미지를 뜻한다. 컴퓨터 과학 기준으로 [자료 구조 (Data Structure)](https://en.wikipedia.org/wiki/Data_structure)라 볼 수 있다.

여기서 다룰 내용은 [[#래스터 스캔]] 기반 시스템에서 그래픽스를 표현하는 방식이다.

그래픽스 표현 방식은 래스터와 벡터로 2가지로 나뉜다.

### 래스터 그래픽스
[래스터 그래픽스 (Raster Graphics)](https://en.wikipedia.org/wiki/Raster_graphics)는 사각형 그리드 안에 [[computer_graphics_note_1#픽셀]]로 표현되는 방식 또는 이미지를 뜻한다.

비트맵 이미지 (Bitmap Image)라고도 불리기도 한다 - [비트맵 (Bitmap)](https://en.wikipedia.org/wiki/Bitmap)은 디지털 이미지를 저장하는 메모리 저장 방식이다. 각 픽셀을 비트로

편의상 래스터 이미지로 불리기도 한다.

우리가 흔히 사용하는 `.jpg`, `.png`, `.gif` 이미지 파일 포맷이 래스터 그래픽스를 기반으로 한다.



### 벡터 그래픽스