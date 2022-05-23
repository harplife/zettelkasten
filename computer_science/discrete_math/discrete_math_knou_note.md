---
aliases: [이산수학 방통대 노트, Discrete Math KNOU Note]
tags: [knou, computer_graphics, discrete_math, study]
status: ongoing
created: 2022-05-21
edited: 2022-05-21
---

# 이산수학 방통대 노트

## Chapter 1
Intro SKIP

## Chapter 2
### 명제와 진리
**명제(Proposition)** : 참과 거짓을 구별할 수 있는 문장이나 수학적 식.

명제 예시:
1. "5 더하기 3은 8이다"는 참이다.
2. "하루는 25시간이다"는 거짓이다.
3. "차는 빠르다"는 명제가 아니다.

**진리값(Truth Value)** : 명제의 참(True)과 거짓(False).

### 논리연산
**논리연산(Logical Operation)** : 명제들의 관계를 참과 거짓으로 나타내는 연산.

**논리연산자(Logical Operator)** : 명제들의 관계를 나타내는 기호. 논리연산에 사용된다.

### 합성명제
**합성명제(Compound Proposition)** : 하나 이상의 명제와 논리연산자들이 결합되어 만들어진 명제.

**진리표(Truth Table)** : 각 명제가 갖는 진리값과 논리연산으로 구해지는 진리값을 정리한 표.

### 논리합
**논리합(Disjunction)** :두 개의 명제 중 하나 이상의 참이 있을 경우 참이되고, 모두 거짓일 경우 거짓이 되는 논리연산. 논리연산자로 두 명제 사이에 `∨`, `+`, 또는 `∥`로 표현된다 (예: `𝑝 ∨ 𝑞`).

> | 𝑝 | 𝑞 | 𝑝 ∨ 𝑞 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   T   |
| F | T |   T   |
| F | F |   F   |
> 논리합 `𝑝 ∨ 𝑞` 진리표

논리합 연산을 "or (또는)"로 읽는다.

논리합 예시:
1. "1분에 60초" 또는 "1시간에 60분" = 참
2. "하루에 24시간" 또는 "일주일에 8일" = 참
3. "8 + 1 = 3" 또는 "3 + 4 = 1" = 거짓

### 논리곱
**논리곱(Conjunction)** : 두 개의 명제 중 두 명제가 참일 경우 참이되고, 하나라도 거짓일 경우 거짓이 되는 논리연산. 논리연산자로 두 명제 사이에 `∧`, `·`, 또는 `&`로 표현된다 (예: `𝑝 ∧ 𝑞`). 

> | 𝑝 | 𝑞 | 𝑝 ∧ 𝑞 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   F   |
| F | T |   F   |
| F | F |   F   |
> 논리곱 `𝑝 ∧ 𝑞` 진리표

논리곱 연산을 "and (그리고)"로 읽는다.

논리곱 예시:
1. "1분에 60초" 그리고 "1시간에 60분" = 참
2. "하루에 24시간" 그리고 "일주일에 8일" = 거짓

### 부정
**부정(Negation)** : 주어진 하나의 명제의 진리값을 반대로 하는 논리연산. 논리연산자로 `~`,  `¬`, 또는 `!`로 명제 왼쪽에 붙어서 표현된다 (예: `~𝑝`).

부정 연산을 "not (아니다)"이라 읽는다.

부정 예시:
1. `𝑝` = "지구는 둥글다"는 참이다. `~𝑝` = "지구는 둥글지 않다"는 거짓이다.
2. `𝑝` = "지구는 납작하다"는 거짓이다. `~𝑝` = "지구는 납작하지 않다"는 참이다.

### 베타적 논리합
**베타적 논리합(Exclusive Disjunction)** : 두 개의 명제 중 하나만 참인 경우 참이 되는 논리연산. 논리연산자로 두 명제 사이에 `⊕`, `⊻`, 또는 `≢`로 표현된다 (예: `𝑝 ⊕ 𝑞`).

> | 𝑝 | 𝑞 | 𝑝 ∧ 𝑞 |
|:-:|:-:|:-----:|
| T | T |   F   |
| T | F |   T   |
| F | T |   T   |
| F | F |   F   |
> 베타적 논리합 `𝑝 ⊕ 𝑞` 진리표

베타적 논리합을 "xor" 또는 "either .. or .."로 읽는다. 안타깝게도 한국어로 표현하기는 어렵다.

베타적 논리합 예시:
1. either "1시간은 60분이다" or "1분은 60초이다" = 두 명제가 모두 참이기 때문에 거짓이다.
2. either "지구는 둥글다" or "지구는 납작하다" = 한 명제만 참이기 때문에 참이다.

### 조건명제
**조건명제(Conditional Proposition)** : 명제 `𝑝`와 `𝑞`가 있을 때, 명제 `𝑝`가 조건의 역할을 수행하고 명제 `𝑞`가 결론의 역할을 수행하는 경우, `𝑝`와 `𝑞`의 합정명제를 조건명제라 한다. **함의(Implication)** 라고 불리기도 한다. 논리연산자로 두 명제 사이에 `→`, `⇒`, 또는 `⊃`로 표현된다 (예: `𝑝 → 𝑞`).

조건이 참인 경우, 결론도 마찬가지로 참이여만 논리연산의 결과가 참이 된다. 조건이 거짓인 경우, 결론의 진리값이 무엇이든 상관이 없다. 조건과 결론의 순서를 바꿀 수 없다.

> | 𝑝 | 𝑞 | 𝑝 → 𝑞 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   F   |
| F | T |   T   |
| F | F |   T   |
> 조건명제 `𝑝 → 𝑞` 진리표

조건명제를 "If .. Then ..(.. 이면 .. 이다)"로 읽는다. 하지만 이런 자연어(Natural Language)로 조건명제를 이해하기에는 조건명제가 너무 반직관적이다. 예를 들어, "불 앞에 있어서 몸이 따뜻하다"라는 명제를 봤을떄, 실제로 불 앞에 있어서 몸이 따뜻하면 참이고, 몸이 따뜻하지 않으면 거짓이 된다. 그런데 불 앞에 있는게 아닌데도, 몸이 따뜻하던 말건 참이 된다 - 이걸 어떻게 받아들어야 할까? [Reddit 글](https://www.reddit.com/r/logic/comments/ni04fz/what_does_it_mean_for_a_material_conditional_to/)에 의하면 나만 이렇게 헷갈린게 아닌 듯 싶다.. 몇 시간 삽질을 해봤지만, 이건 그냥 받아들이고 넘어가야 할 듯 하다.

조건명제 예시:
1. "이탈리아의 수도가 뉴욕이라면, 대한민국의 수도는 서울이다" = 참
2. "지구가 평면이면, 지구인은 모두 화성에 산다" = 참
3. "1+3=4이면, 2x3=5이다" = 거짓
4. "삼각형 내각의 합이 180도라면, 포도는 과일이다" = 참

#### 필요성과 충분성
https://en.wikipedia.org/wiki/Necessity_and_sufficiency

**필요조건(Necessary Condition)** : 필요성(Necessity)은 결론을 내기 위해선 조건이 꼭 있어야 한다는 것을 뜻한다. 조건 없이는 결론이 존재할 수 없다 (If not P, then not Q). 하지만 조건이 있다고 꼭 결론이 있다는 것은 아니다.

예를 들어, "X가 숫자다"라는 조건이 있다면, "X는 3보다 크다"라는 결론이 나올 수 있다. 이 조건이 없다면, 결론은 나올 수가 없다. 하지만 조건이 참이라고 결론이 꼭 참인 것은 아니다.

**충분조건(Sufficient Condition)** : 충분성(Sufficiency)은 조건이 참이면 결론이 참임을 보장한다는 것을 뜻한다. 하지만 조건이 거짓이라고 결론도 거짓이라 하는 것은 아니다.

예를 들어, 조건이 "x = 2"라면, "x² = 4"가 결론이 되기에 충분하다고 볼 수 있다. 하지만 조건이 거짓이여도 결론은 참이 될 수 있다 (조건이 "x = -2"인 경우).

#### 쌍조건명제
**쌍조건명제(Biconditional Proposition)** : 조건과 결론이 양방향으로 이루어지는 조건명제를 뜻한다. 조건명제 "if P, then Q"가 있다면, 반대로 "if Q, then P"도 성립된다는 것이다. 조건-결론 관계에 있어 **동치(Equivalence)** 라고 불리기도 한다. 필요성과 충분성 둘 다 성립하다는 의미에 있어 쌍조건명제의 조건을 **필요충분조건** 이라 부른다. 논리연산자로 두 명제 사이에 `↔` 또는 `⇔`로 표현된다.

> | 𝑝 | 𝑞 | 𝑝 ↔ 𝑞 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   F   |
| F | T |   F   |
| F | F |   T   |
> 쌍조건명제 `𝑝 ↔ 𝑞` 진리표

쌍조건명제를 "if and only if"라고 읽는다. 한국어론 "..인 경우에만"이라고 이해하면 될 것 같다.

쌍조건명제 예시:
1. "사람이 살아 있다 ↔ 사람이 호흡을 한다"는 참이다 (참과 참).
2. "4+5=20 ↔ 6x2=8"은 참이다 (거짓과 거짓).
3. "놀이공원에 아침 9시부터 10시 사이에 도착한 경우에만 놀이공원에 입장할 수 있다"는 참이다.

### 논리적 동치
**논리적 동치(Logical Equivalence)** : 두 명제의 진리값이 항상 동일하다는 뜻. **동치관계** 라고 부르기도 한다. 쌍조건명제하고 연산은 동일하지만, 조건-결론 관점이 아닌 논리적 동등성 관점에서 명제들을 봤을 떄 논리적 동치 표현을 사용한다. 논리연산자로 두 명제 사이에 `≡`로 표현된다.

논리적 동치를 ".. means the same as .."라고 읽는다. 한국어론 "..는 ..과 동일하다"라고 이해하면 된다.

### 조건명제의 변형
**조건명제의 3가지 변형**:
1. **역(Converse)** : 조건명제에서 명제의 위치를 바꾼 경우 (예: `𝑝 → 𝑞`의 역은 `𝑞 → 𝑝`이다).
2. **이(Inverse)** : 조건명제에서 두 명제의 진리값이 반대가 되는 경우 (예:  `𝑝 → 𝑞`의 이는 `~𝑝 → ~𝑞`이다).
3. **대우(Contrapositive)** : 조건명제에서 converse와 inverse 둘 다 적용되는 경우 (예: `𝑝 → 𝑞`의 대우는 `~𝑞 → ~𝑝`이다).

> | 𝑝 | 𝑞 | ~𝑝 | ~𝑞 | 𝑝 → 𝑞 | 𝑞 → 𝑝 | ~𝑝 → ~𝑞 | ~𝑞 → ~𝑝 |
|:-:|:-:|:--:|:--:|:-----:|:--------:|:-------:|:--------------:|
| T | T |  F |  F |   T   |     T    |    T    |        T       |
| T | F |  F |  T |   F   |     T    |    T    |        F       |
| F | T |  T |  F |   T   |     F    |    F    |        T       |
| F | F |  T |  T |   T   |     T    |    T    |        T       |
> 조건명제 `𝑝 → 𝑞`의 inverse, converse, contrapositive 진리표

위 진리표를 보면, 다음과 같은 사실을 알 수 있다.
1. 명제와 대우는 동치관계이다.
2. 역과 이는 동치관계이다.

조건명제 "영희가 서울에 있다면, 그녀는 한국에 있는 것이다"를 봤을떄, 대우인 "영희가 한국에 없다면, 그녀는 서울에 없는 것이다"가 성립된다.

### 논리적 동치법칙
https://en.wikipedia.org/wiki/Logical_equivalence

동치관계를 증명하거나 복잡한 합성명제를 간단히 표시할 때 사용되는 여러 법칙이 있다.
1. 교환법칙(Commutative Law)
2. 결합법칙(Associative Law)
3. 분배법칙(Distributive Law)
4. 항등법칙(Identity Law)
5. 지배법칙(Domination Law)
6. 부정법칙(Negation Law)
7. 이중 부정법칙(Double Negation Law)
8. 멱등법칙(Idempotent Law)
9. 드 모르간 법칙(De Morgan's Law)
10. 흡수법칙(Absorption Law)
11. 함축법칙(Implication Law)
12. 대우법칙(Contrapositive Law)

#todo 위 법칙들에 대해 정리. 교과서 P.37 표 2-8 참고.

#### 교환법칙
https://en.wikipedia.org/wiki/Commutative_property#Propositional_logic

- `𝑝∨𝑞 ≡ 𝑞∨𝑝`
- `𝑝∧𝑞 ≡ 𝑞∧𝑝`
- `𝑝↔𝑞 ≡ 𝑞↔𝑝`

![[propositional_logic_commutative_property.png]]

#### 결합법칙
https://en.wikipedia.org/wiki/Associative_property

- `(𝑝∨𝑞)∨𝑟 ≡ 𝑝∨(𝑞∨𝑟)`
- `(𝑝∧𝑞)∧𝑟 ≡ 𝑝∧(𝑞∧𝑟)`

![[propositional_logic_associative_property.png]]

#### 분배법칙
https://en.wikipedia.org/wiki/Distributive_property#Propositional_logic

- `𝑝∨(𝑞∧𝑟) ≡ (𝑝∨𝑞)∧(𝑝∨𝑟)`
- `𝑝∧(𝑞∨𝑟) ≡ (𝑝∧𝑞)∨(𝑝∧𝑟)`

![[propositional_logic_distributive_property.svg]]

#### 항등법칙
-  `𝑝∨F ≡ 𝑝` (x 곱하기 1은 x다)
-  `𝑝∧T ≡ 𝑝` (x 더하기 0은 x다)



## 벤 다이아그램
논리와 집합 이론은 죽이 잘 맞는다. [[#Chapter 2]]에 정리한 내용들을 벤 다이아그램을 사용해서 정리해본다.

https://betterinformatics.com/resources/inf1-cl/venn

#todo logic_venn_diagram 폴더 내에 있는 캡처들 파워포인트로 수정해서 여기에 올림.

### Hasse Diagram
논리의 Hasse DIagram. 뭔가.. 보면은 이해될 것 같기도 하고..?

![[Logical_connectives_Hasse_diagram.svg]]

# Resources
[Tutorial Point - 이산수학](https://www.tutorialspoint.com/discrete_mathematics/discrete_mathematics_propositional_logic.htm)

[논리연산자 목록 1](http://discrete.openmathbooks.org/dmoi3/appendix-1.html)

[논리연산자 목록 2](https://en.wikipedia.org/wiki/List_of_logic_symbols)

[수학 알파벳 목록](https://en.wikipedia.org/wiki/Mathematical_Alphanumeric_Symbols)
