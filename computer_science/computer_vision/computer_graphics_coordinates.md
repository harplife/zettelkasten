---
aliases: [그래픽스 좌표계, Graphics Coordinates]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming]
status: ongoing
created: 2022-06-08
edited: 2022-06-08
---

# 뷰잉 및 사영
컴퓨터 그래픽스에 있어 3D 모델을 "본다"는 것은 추상적으로만 존재하는 3D 모델을 현실 세계 2D 화면의 픽셀로서 사람이 인식할 수 있는 그림으로 재현한다는 의미로 해석된다 - 그리고 이 행위를 뷰잉(Viewing)이라고 한다.

뷰잉(Viewing)을 실제로 구현하는 것을 [사영(Projection)](https://en.wikipedia.org/wiki/3D_projection)이라고 한다.

참고 : 정확히는 그래픽 사영(Graphical Projection) 또는 3차원 사영(3D Projection)이라 부른다.

뷰잉은 말 그대로 보는 행위, 사영은 보이는 것을 그림으로 그리는 행위로 생각하면 될 것 같다.

> ![[graphical_projection.svg]]
> 사영을 수학적 다이어그램으로 표현한 그림



사영에 종류 중 [원근법(Perspective)](https://en.wikipedia.org/wiki/Perspective_(graphical))이 속한다.

![[camera_focal_length_distance_animation.gif]]




컴퓨터 그래픽스에 있어 3D 모델을 "본다"는 것을 구현하기 위해 3D 모델을 표현할 여러 공간과, 공간과 공간으로서 전달되며 적용되는 변환들을 알아볼 필요가 있다.

컴퓨터 그래픽스에선 6가지 좌표계(Coordinate System)를 다룬다.
1. Local Space (Object Space)
2. World Space
3. Camera Space (Eye Space,  View Space)
4. Projection Space
5. Clip Space
6. Screen Space

주의 : Clip Space와 Screen Space를 제외한 위 좌표계들은 추상적인(Abstract) 요소로서, OpenGL에서 각 좌표계를 정의한 것은 아니다. GPU는 우리가 주는 정보를 그대로 구현할 뿐이다.

## Local Space
지역 공간(Local Space)는 3D 좌표계에서 원점(Origin)에 상대적인(Relative) 좌표로서 3D 모델 정점의 위치를 표현한 것이다 - 각 3D 모델에 하나의 공간이 부여된다는 뜻이다.

객체만의 공간이란 의미로 객체 공간(Object Space)라고도 부른다.

여기서 정점의 위치가 서로 상대적임을 명심해야 한다. 정점 A에서 정점 B를 (-0.5, 0)와 (0.5, 0)로 표현하든, (-5, 0)와 (5, 0)로 표현하든 의미는 똑같다는 것이다 (정점과 정점의 위치가 원점 기준으로 비율이 변경되지 않는 이상).

참고 : 정점과 정점의 거리는 화면의 픽셀값과 동일하지 않다!

3D 모델의 지역 좌표는 정점 셰이더에 입력되는 값이라 볼 수 있다.

참고 : 특별한 이유가 있지 않는 이상, 지역 원점은 3D 모델의 가운데(에 근접한 위치)에 있다.

## World Space
세계 공간(World Space)는 3D 좌표계에서 원점(Origin)에 상대적인(Relative) 좌표로서 3D 모델의 위치와 크기를 표현한 것이다 - 하나의 장면(Scene)에 대한 공간으로 볼 수 있고, 여러 모델이 세계 공간에 있을 수 있다.

지구 위에 여러 국가가 있듯이, 세계 공간 위에 여러 지역 공간이 있다고 비유할 수 있다.

세계 공간은 OpenGL이 구현하는게 아니라 소스 프로그램이 직접 구현하는 것이다. 정점 셰이더에서 정점 좌표를 받아 그대로 전달하거나, 또는 변환(이동, 크기, 회전)을 구현한 경우, 세계 공간을 구현했다고 생각하면 된다.

참고 : 처음에 OpenGL을 시작할 때 삼각형 하나 그리는 것으로 시작한다. 정점 좌표에 아무런 변환이 없는 경우, 지역 공간과 세계 공간이 동일하다고 볼 수 있다.

## Camera Space
카메라 공간(Camera Space)은 

참고 : Eye Space 또는 View Space라고도 불린다.




# 시각단서
#todo 시지각에 대한 자료 따로 정리

뷰잉에 있어 사람의 [시지각(Visual Perception)](https://en.wikipedia.org/wiki/Visual_perception)을 최대한 모방하기 위해서는 모형, 크기, 위치, 그리고 색상으로 현실적인 [시각단서(Visual Cue)](https://en.wikipedia.org/wiki/Sensory_cue#Visual_cues)를 구현해야 한다.

시각단서 :
1. [깊이(Depth)](https://en.wikipedia.org/wiki/Depth_perception)
2. [움직임(Motion)](https://en.wikipedia.org/wiki/Motion_perception)
3. [생물학적 움직임(Biological Motion)](https://en.wikipedia.org/wiki/Biological_motion)
4. [대비(Contrast)](https://en.wikipedia.org/wiki/Contrast_(vision))

참고 : [단안단서(Monocular Vision)](https://en.wikipedia.org/wiki/Monocular_vision)