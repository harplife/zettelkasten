---
aliases: [Data Structure Lesson 2 (KNOU)]
tags: [computer_science, data_structure, data, lesson, school]
status: ongoing
edited: 2021-11-09
---

# Data Structure Lesson 2 (KNOU)
2021 Fall Semester Data Structure by professor Jung (정광식).
Textbook is _Data Structure_ written by the professor himself.
Learning method is Online Videos + 1 session of Online Class.

## Learning Goals:
1. To be able to explain Array's Abstract Data Type.
2. To be able to explain the order and place of Elements inside an Array.
3. To be able to explain the memory allocation for Two-Dimensional Array.
4. To be able to explain the structure and advantages of a Sparse Matrix.

## Array
- Array is a set of elements that are in <index, value> pairs.
- 원소의 메모리 공간(메인 메모리, DDR)의 물리적인 위치를 '순서'적으로 결정하는 특징
- 배열의 순서는 메모리 공간에서 저장되는 '원소값의 물리적 순서'
- 인덱스로 표현되는 '순서'를 갖는 메모리 영역 (원소값을 위한 저장소)
- 원소들이 모두 같은 자료형과 같은 크기의 기억 공간을 가짐
- 배열의 인덱스 값을 이용해서 배열의 원소값에 접근하기 떄문에 직접 접근이 가능함
- 인덱스 값은 추상하된 값: 컴퓨터의 내부구조나 메모리 주소와 무관하게 개발자에게 개념적으로 정의됨
- 메모리 주소값은 실제 메모리의 물리적인 위치값(주소값)

## Array's Abstract Data Type
- 추상자료형 : 객체 및 관련된 연산의 정의
- 자료형 : 메모리 저장 할당을 위한 선언