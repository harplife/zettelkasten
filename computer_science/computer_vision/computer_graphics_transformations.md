---
aliases: [선형변환, 변환행렬, Graphics Transformation, Linear Transformation, Transformation Matrix]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming]
status: ongoing
created: 2022-06-16
edited: 2022-06-16
---

# 선형변환
[선형변환(Linear Transformation)](https://en.wikipedia.org/wiki/Linear_map)은 입력-출력 관계($V \rightarrow W$)의 벡터 공간 성질이 보존되는 행렬(Matrix)에 대한 함수이다 - 아마도?

간단하게 설명하면.. 선형변환은 행렬에 대한 연산이되 벡터 공간 안의 덧셈, 곱셈의 성질이 변경되지 않으며, 입력 될 때의 공간의 원점과 출력 될 떄의 공간의 원점이 동일하다는 것이다.

위키에서 수학적으로 정의한 내용 참고.

Let $V$ and $W$ be vector spaces over the same field $K$. A function $f : V \rightarrow W$ is said to be a *linear map* if for any two vectors $u,v \in V$ and any scalar $c \in K$ the following two conditions are satisfied:
1. Additivity / Operation of Addition
$f(u+v)=f(u)+f(v)$
2. Homogeneity of degree 1 / Operation of Scalar Multiplication
$f(cu)=cf(u)$

참고 : 선형사상(Linear Map) 또는 일차변환 으로 불리기도 한다.


## 어파인 변환


### 어파인 변환 차트
![[2d_affine_transformation.svg]]