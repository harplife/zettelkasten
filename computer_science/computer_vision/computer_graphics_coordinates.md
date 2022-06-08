---
aliases: [그래픽스 좌표계, Graphics Coordinates]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming]
status: ongoing
created: 2022-06-08
edited: 2022-06-08
---

# 그래픽스 좌표계
컴퓨터 그래픽스에선 6가지 좌표계(Coordinate System)를 다룬다.
1. Local Space (Object Space)
2. World Space
3. View Space (Eye Space, Camera Space)
4. Projection Space
5. Clip Space
6. Screen Space

주의 : 위 좌표계들은 개념적인(Conceptual) 요소로서, OpenGL에서 각 좌표계를 정의한 것은 아니다. GPU는 우리가 주는 정보를 그대로 구현할 뿐이다.

## Local Space
지역 공간(Local Space), 또는 객체 공간(Object Space)는 3D 좌표계에서 원점(Origin)에 상대적인(Relative) 좌표로서 3D 모델 정점의 위치를 표현한 것이다 - 각 3D 모델에 하나의 공간이 부여된다는 뜻이다.

여기서 정점의 위치가 서로 상대적임을 명심해야 한다. 정점 A에서 정점 B를 -0.5와 0.5로 표현하든, -5와 5로 표현하든 의미는 똑같다는 것이다.

참고 : 정점과 정점의 거리는 화면의 픽셀값과 동일하지 않다!

## World Space
세계 공간(World Space)는 3D 좌표계에서 원점(Origin)에 상대적인(Relative) 좌표로서 3D 모델의 위치를 표현한 것이다 - 하나의 장면(Scene)에 대한 공간으로 볼 수 있고, 여러 모델이 세계 공간에 있을 수 있다.

지구 위에 여러 국가가 있듯이, 세계 공간 위에 여러 지역 공간이 있다고 비유할 수 있다.

주의할 점은, OpenGL에서 