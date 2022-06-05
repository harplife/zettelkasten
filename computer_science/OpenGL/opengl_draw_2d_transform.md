---
aliases: [OpenGL 2D 기하변환, OpenGL 2D Transform]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study, display, settings, example]
status: ongoing
created: 2022-06-06
edited: 2022-06-06
---

# OpenGL 2D 기하변환
[방통대 교재 코드 참고](https://professor.knou.ac.kr/bbs/brlee/2983/289896/artclView.do?layout=unknown)

`04_GeoTransform` 폴더 아래 코드들에 대해 정리한다.
1. `GeoTransform.cpp`
2. `gTransform.cpp`
3. `gTransform.h`

이 코드는 5가지 작업을 한다?
1. 기하변환행렬 준비

## 기하변환행렬 준비
도형을 하나의 행렬(Matrix)로 볼 때, 도형의 행동(이동, 크기 조절, 회전 등)을 변환행렬(Transformation Matrix)과의 연산으로 표현할 수 있다.

편의를 위해서, 도형의 행렬을 정점좌표행렬(Vertex Coordinates Matrix)라고 칭하고, 도형의 행동을 기하변환행렬(Geometric Transformation Matrix)이라 칭한다.

OpenGL에서는 따로 도형 변환에 대한 기능을 제공하지 않는다. GLM (OpenGL Mathematics)라는 라이브러리를 사용하면 이 문제를 쉽게 해결하는데, 일단 여기선 도형 변환이 내부적으로 어떻게 적용되는지 보기 위해 각 도형 행동에 대한 변환행렬을 구현한다.

`gTransform.h`와 `gTransform.cpp`는 변환행렬의 구조체와 각 행동에 대한 변환행렬을 정의한다.

### 변환행렬 구조체
`vec3f`는 3개의 소수값을 받는 배열로 3차원 좌표를 표현하기 위한 구조체이다. 배열에 배열을 사용해서 3x3 행렬을 구현할 수 있다.

```cpp
struct Vec3f {	// 3차원 좌표를 표현하기 위한 구조체
    float x, y, z;
    Vec3f() {}
    Vec3f(float _x, float _y, float _z) : 
        x(_x), y(_y), z(_z) {}
};
```

`TransMat4f`는 소수값 4x4 행렬(Matrix)로 3x3 행렬에 대한 변환 함수들을 제공하는 구조체이다.

참고 : 변환행렬이 3x3이 아닌 4x4인 이유는 교재 5.2 "행렬표현과 동차좌표" (페이지 155)에 설명되어 있다 (설명이 개같아서 이해가 되는 것은 아니다 ㅋ).

```cpp
// gTransform.h
class TransMat4f {
    float   mat[4][4];
public:
    TransMat4f() {}
    TransMat4f  operator * (const TransMat4f& m) const;
    const TransMat4f&   operator *= (const TransMat4f& m);
    void    identity();
    void    translate(const Vec3f& d);
    void    scale(const Vec3f& s);
    void    rotateX(float theta);
    void    rotateY(float theta);
    void    rotateZ(float theta);
    const   float*  getPMat() const { return &mat[0][0]; }
};
```

`TransMat4f` 변환행렬이 제공하는 변환 함수들은 밑에와 같다.
1. 항등함수(Identity)
2. 이동(Translate)
3. 크기 조절(Scale)
4. 회전(Rotate)

#### 항등함수
항등함수(Identity Function) 또는 단위행렬(Identity Matrix)는 

| 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 0 | 0 | 1 |


#### 이동
Translate

#### 크기 조절
Scale

#### 회전
rotateX
rotateY
rotateZ