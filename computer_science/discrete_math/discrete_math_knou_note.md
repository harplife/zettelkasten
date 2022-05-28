---
aliases: [이산수학 방통대 노트, Discrete Math KNOU Note]
tags: [knou, computer_science, discrete_math, study]
status: ongoing
created: 2022-05-21
edited: 2022-05-28
---

# 이산수학 방통대 노트

# Chapter 1
Intro SKIP

# 명제 논리
[[propositional_logic]]

# 술어 논리
언어학(Linguistic)에 있어 문장은 주어와 술어로 이루어진다.
- [주어(Subject)](https://en.wikipedia.org/wiki/Subject_(grammar))는 발언의 주제가 되는 것(Thing)이다.
- [술어(Predicate)](https://en.wikipedia.org/wiki/Predicate_(grammar))는 주어의 동작, 상태, 성질에 대해 서술하는 설명(Description)이 된다.

"나는 피자를 좋아한다"에서 "나"와 "피자"는 주어고, "좋아한다"는 술어이다.



논리는 일반적으로 [[#명제 논리]]와 술어 논리로 구분한다.

명제논리는 주어와 술어를 구분하지 않고, 문장 전체를 하나의 명제로 간주하여 진리를 판별하는 법칙을 다룬다. 반대로, [술어 논리(Predicate Logic)](https://en.wikipedia.org/wiki/First-order_logic)는 주어와 술어를 구분하여 진리를 판별하는 법칙을 다룬다.

술어논리는 술어를 중심으로 그에 딸린 주어를 나열하는 형태로 문장을 표현한다 - 그러므로, 명제를 주어와 술어로 구분한 다음 "술어(주어)"와 같은 형태로 나타낸다. 이때 주어는 변수(Variable)의 역할을 수행한다.

예시: "소크라테스는 사람이다"라는 명제는 술어논리로 `사람(소크라테스)`와 같이 표현한다.

술어 논리를 **1차 논리(First-Order Logic)** 또는 **Quantificational Logic** 이라고도 불린다.

명제 "모든 사람은 죽는다"와 명제 "소크라테스는 사람이다"가 있으면, 우리는 "소크라테스는 죽는다"라는 추론을 할 수 있다. 하지만 이는 명제 논리로서 나올 수 있는 추론이 아니며, 술어 논리를 사용해야 가능한 추론이다.

