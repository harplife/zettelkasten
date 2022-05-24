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

## 명제 논리
[명제 논리(Propositional Logic)](https://en.wikipedia.org/wiki/Propositional_calculus)는 진실이 담긴 명제/문장들 간의 관계를 기계적으로 판단하는 체계이다.

문장 논리(Sentential Logic)라고 불리기도 한다.

### 명제와 진리값
[명제(Proposition)](https://en.wikipedia.org/wiki/Proposition) : 참과 거짓을 구별할 수 있는 문장이나 수학적 식.

명제 예시:
1. "5 더하기 3은 8이다"는 참이다.
2. "하루는 25시간이다"는 거짓이다.
3. "차는 빠르다"는 명제가 아니다.

[진리값(Truth Value)](https://en.wikipedia.org/wiki/Truth_value) : 명제의 참(True)과 거짓(False). Logical Value라고도 한다.

거짓은 **모순(Contradiction)**이라고도 불리운다.

참의 기호는 `⊤`로 표기된다. 거짓의 기호는 `⊥`로 표기된다.

latex:
- $\top$
- $\bot$

### 논리연산
**논리연산(Logical Operation)** : 명제들의 관계를 참과 거짓으로 나타내는 연산.

**논리연산자(Logical Operator)** : 명제들의 관계를 나타내는 기호. 논리연산에 사용된다.

### 합성명제와 진리표
**합성명제(Compound Proposition)** : 하나 이상의 명제와 논리연산자들이 결합되어 만들어진 명제.

[진리표(Truth Table)](https://en.wikipedia.org/wiki/Truth_table) : 각 명제가 갖는 진리값과 논리연산으로 구해지는 진리값을 정리한 표.

### 부정
[부정(Negation)](https://en.wikipedia.org/wiki/Negation) : 주어진 하나의 명제의 진리값을 반대로 하는 논리연산. **Complement** 라고도 불린다. 논리연산자로 `~`,  `¬`, 또는 `!`로 명제 왼쪽에 붙어서 표현된다 (예: `¬𝑃`).

부정 연산을 "not (아니다)"이라 읽는다.

부정 예시:
1. `𝑃` = "지구는 둥글다"는 참이다. `~𝑃` = "지구는 둥글지 않다"는 거짓이다.
2. `𝑃` = "지구는 납작하다"는 거짓이다. `~𝑃` = "지구는 납작하지 않다"는 참이다.

### 논리합
[논리합(Disjunction)](https://en.wikipedia.org/wiki/Logical_disjunction) :두 개의 명제 중 하나 이상의 참이 있을 경우 참이되고, 모두 거짓일 경우 거짓이 되는 논리연산. 논리연산자로 두 명제 사이에 `∨`, `+`, 또는 `∥`로 표현된다 (예: `𝑃 ∨ 𝑄`).

![[disjunction_venn_diagram.svg]]

논리합 연산을 "or (또는)"로 읽되, 오해하면 안 된다. 우리가 일반적으로 생각하는 "또는"은 둘 중 하나만 가능한 경우지만, 논리합은 둘 다 가능하기 때문에 차라리 **"this, that, or both (이것, 저것, 또는 둘다)"** 라고 생각하는게 좋다.

명확하기 위해 **이타적(Inclusive) 논리합**이라고 부르는 경우도 있다.

> | 𝑃 | 𝑄 | 𝑃 ∨ 𝑄 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   T   |
| F | T |   T   |
| F | F |   F   |
> 논리합 `𝑃 ∨ 𝑄` 진리표

논리합 예시:
1. "1분에 60초" 또는 "1시간에 60분" = 참
2. "하루에 24시간" 또는 "일주일에 8일" = 참
3. "8 + 1 = 3" 또는 "3 + 4 = 1" = 거짓

#### 배타적 논리합
[배타적 논리합(Exclusive Disjunction)](https://en.wikipedia.org/wiki/Exclusive_or) : 두 개의 명제 중 하나만 참인 경우 참이 되는 논리연산. 논리연산자로 두 명제 사이에 `⊕`, `⊻`, `≢`, 또는 `↮`로 표현된다 (예: `𝑃 ⊕ 𝑄`).

배타적 논리합을 "xor" 또는 "either .. or .."로 읽는다. 한국어로 표현하면 ".. 또는 .."이 되지 않을까 싶다.

우리가 일반적으로 생각하는 "or (또는)", 즉, 둘 중 꼭 하나만 존재할 수 있는 상황이 배타적 논리합과 동일하다.

진리값이 서로 달라야 하는 배타적 논리합의 반대로 진리값이 서로 같아야 하는 [[#쌍조건명제]]가 있다는 것을 참고해야 한다.

> | 𝑃 | 𝑄 | 𝑃 ∧ 𝑄 |
|:-:|:-:|:-----:|
| T | T |   F   |
| T | F |   T   |
| F | T |   T   |
| F | F |   F   |
> 배타적 논리합 `𝑃 ⊕ 𝑄` 진리표

배타적 논리합 예시:
1. either "1시간은 60분이다" or "1분은 60초이다" = 두 명제가 모두 참이기 때문에 거짓이다.
2. either "지구는 둥글다" or "지구는 납작하다" = 한 명제만 참이기 때문에 참이다.

#### 부정 논리합
[부정 논리합(Negation of Disjunction)](https://en.wikipedia.org/wiki/Logical_NOR) : 논리합의 반대되는 논리연산으로, 하나의 명제라도 참이 있는 경우 연산 결과가 거짓이 된다. 논리연산자로 두 명제 사이에 `↓` 또는 `⊽`로 표현된다 (예: `𝑃 ↓ 𝑄`).

참고 : Joint Denial 로 불리기도 한다.

부정 논리합 연산을 "(neither) nor"로 읽는다. 한국어로 표현하기는 어렵다!!

> | 𝑃 | 𝑄 | 𝑃 ↓ 𝑄 |
|:-:|:-:|:-----:|
| T | T |   F   |
| T | F |   F   |
| F | T |   F   |
| F | F |   T   |
> 부정 논리합 `𝑃 ↓ 𝑄` 진리표

### 논리곱
[논리곱(Conjunction)](https://en.wikipedia.org/wiki/Logical_conjunction) : 두 개의 명제 중 두 명제가 참일 경우 참이되고, 하나라도 거짓일 경우 거짓이 되는 논리연산. 논리연산자로 두 명제 사이에 `∧`, `·`, 또는 `&`로 표현된다 (예: `𝑃 ∧ 𝑄`). 

논리곱 연산을 "and (그리고)"로 읽는다. 명제 둘 다 진실되어야만이 연산 결과가 참이 된다. 차라리 "둘 다 가지고 있다"라고 이해하는게 더 편할 듯 싶다.

> | 𝑃 | 𝑄 | 𝑃 ∧ 𝑄 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   F   |
| F | T |   F   |
| F | F |   F   |
> 논리곱 `𝑃 ∧ 𝑄` 진리표

논리곱 예시:
1. "1분에 60초" 그리고 "1시간에 60분" = 참
2. "하루에 24시간" 그리고 "일주일에 8일" = 거짓

#### 부정 논리곱
[부정 논리곱(Negation of Conjunction)](https://en.wikipedia.org/wiki/Sheffer_stroke) : 논리곱의 반대되는 논리연산으로, 두 명제가 참이 되는 경우 연산 결과가 거짓이 된다. 논리연산자로 두 명제 사이에 `↑`, `⊼`, 또는 `|`로 표현된다 (예: `𝑃 ↑ 𝑄`).

참고 : Alternative Denial 로 불리기도 한다.

부정 논리곱 연산을 "nand"로 읽는다. 한국어로 표현하기는 어렵다!!

> | 𝑃 | 𝑄 | 𝑃 ↑ 𝑄 |
|:-:|:-:|:-----:|
| T | T |   F   |
| T | F |   T   |
| F | T |   T   |
| F | F |   T   |
> 부정 논리곱 `𝑃 ↑ 𝑄` 진리표

### 조건명제
**조건명제(Conditional Proposition)** : 명제 `𝑃`와 `𝑄`가 있을 때, 명제 `𝑃`가 조건의 역할을 수행하고 명제 `𝑄`가 결론의 역할을 수행하는 경우, `𝑃`와 `𝑄`의 합정명제를 조건명제라 한다. 명제에 숨어있는 뜻이 암시된다는 의미에서  **함의/함축(Implication)** 라고 불리기도 한다. 논리연산자로 두 명제 사이에 `→`, `⇒`, 또는 `⊃`로 표현된다 (예: `𝑃 → 𝑄`).

결로은 [논리적 귀결(Logical Consequence)](https://en.wikipedia.org/wiki/Logical_consequence)

조건이 참인 경우, 결론도 마찬가지로 참이여만 논리연산의 결과가 참이 된다. 조건이 거짓인 경우, 결론의 진리값이 무엇이든 상관이 없다. 조건과 결론의 순서를 바꿀 수 없다.

> | 𝑃 | 𝑄 | 𝑃 → 𝑄 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   F   |
| F | T |   T   |
| F | F |   T   |
> 조건명제 `𝑃 → 𝑄` 진리표

조건명제를 "If .. Then ..(.. 이면 .. 이다)"로 읽는다. 하지만 이런 자연어(Natural Language)로 조건명제를 이해하기에는 조건명제가 너무 반직관적이다. 예를 들어, "불 앞에 있어서 몸이 따뜻하다"라는 명제를 봤을떄, 실제로 불 앞에 있어서 몸이 따뜻하면 참이고, 몸이 따뜻하지 않으면 거짓이 된다. 그런데 불 앞에 있는게 아닌데도, 몸이 따뜻하던 말건 참이 된다 - 이걸 어떻게 받아들어야 할까? [Reddit 글](https://www.reddit.com/r/logic/comments/ni04fz/what_does_it_mean_for_a_material_conditional_to/)에 의하면 나만 이렇게 헷갈린게 아닌 듯 싶다.

여러 자료에서는 조건명제를 인과관계(Causality)로 받아드리면 안 된다고 한다. 조건이 있으면 결론에 영향을 주지만, 조건이 없다면 결론은 상관없이 존재할 수도 있다고 생각하면 된다. 조건명제 `𝑃 → 𝑄` 대신  `~𝑃 ∨ 𝑄`로 생각하는게 더 이롭다 (이를 [[#논리적 동치]]라고 한다).

우리가 일반적으로 생각하는 인과관계는 [[#쌍조건명제]]와 더 가깝다.

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

쌍조건명제에선 두 명제의 진리가 같은 경우에만 참이 나온다. [[#배타적 논리합]]의 반대로 볼 수 있다.

> | 𝑃 | 𝑄 | 𝑃 ↔ 𝑄 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   F   |
| F | T |   F   |
| F | F |   T   |
> 쌍조건명제 `𝑃 ↔ 𝑄` 진리표

쌍조건명제를 "if and only if (짧게 iff)"라고 읽는다 (예: `𝑃 iff 𝑄`). 한국어론 "..인 경우에만"이라고 이해하면 될 것 같다.

쌍조건명제 예시:
1. "사람이 살아 있다 ↔ 사람이 호흡을 한다"는 참이다 (참과 참).
2. "4+5=20 ↔ 6x2=8"은 참이다 (거짓과 거짓).
3. "놀이공원에 아침 9시부터 10시 사이에 도착한 경우에만 놀이공원에 입장할 수 있다"는 참이다.

### 논리적 동치
**논리적 동치(Logical Equivalence)** : 두 명제의 진리값이 항상 동일하다는 뜻. **동치관계** 라고 부르기도 한다. 쌍조건명제하고 연산은 동일하지만, 조건-결론 관점이 아닌 논리적 동등성 관점에서 명제들을 봤을 떄 논리적 동치 표현을 사용한다. 논리연산자로 두 명제 사이에 `≡`로 표현된다.

논리적 동치를 ".. means the same as .."라고 읽는다. 한국어론 "..는 ..과 동일하다"라고 이해하면 된다.

### 조건명제의 변형
**조건명제의 3가지 변형**:
1. **역(Converse)** : 조건명제에서 명제의 위치를 바꾼 경우 (예: `𝑃 → 𝑄`의 역은 `𝑄 → 𝑃`이다).
2. **이(Inverse)** : 조건명제에서 두 명제의 진리값이 반대가 되는 경우 (예:  `𝑃 → 𝑄`의 이는 `~𝑃 → ~𝑄`이다).
3. **대우(Contrapositive)** : 조건명제에서 converse와 inverse 둘 다 적용되는 경우 (예: `𝑃 → 𝑄`의 대우는 `~𝑄 → ~𝑃`이다).

> | 𝑃 | 𝑄 | ~𝑃 | ~𝑄 | 𝑃 → 𝑄 | 𝑄 → 𝑃 | ~𝑃 → ~𝑄 | ~𝑄 → ~𝑃 |
|:-:|:-:|:--:|:--:|:-----:|:--------:|:-------:|:--------------:|
| T | T |  F |  F |   T   |     T    |    T    |        T       |
| T | F |  F |  T |   F   |     T    |    T    |        F       |
| F | T |  T |  F |   T   |     F    |    F    |        T       |
| F | F |  T |  T |   T   |     T    |    T    |        T       |
> 조건명제 `𝑃 → 𝑄`의 inverse, converse, contrapositive 진리표

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

논리곱의 교환성
`𝑃∧𝑄 ≡ 𝑃∧𝑄`

논리합의 교환성
`𝑃∨𝑄 ≡ 𝑄∨𝑃`

조건명제의 교환성 (aka **Law of Permutation**)
`𝑃→(𝑄→𝑅) ≡ (𝑄→𝑃)→𝑅`

쌍조건명제의 교환성 ()
`𝑃↔𝑄 ≡ 𝑄↔𝑃`

![[propositional_logic_commutative_property.png]]

#### 결합법칙
https://en.wikipedia.org/wiki/Associative_property

- `(𝑃∨𝑄)∨𝑅 ≡ 𝑃∨(𝑄∨𝑅)`
- `(𝑃∧𝑄)∧𝑅 ≡ 𝑃∧(𝑄∧𝑅)`

![[propositional_logic_associative_property.png]]

#### 분배법칙
https://en.wikipedia.org/wiki/Distributive_property#Propositional_logic

- `𝑃∨(𝑄∧𝑅) ≡ (𝑃∨𝑄)∧(𝑃∨𝑅)`
- `𝑃∧(𝑄∨𝑅) ≡ (𝑃∧𝑄)∨(𝑃∧𝑅)`

![[propositional_logic_distributive_property.svg]]

#### 항등법칙
-  `𝑃∨F ≡ 𝑃` (x 곱하기 1은 x다)
-  `𝑃∧T ≡ 𝑃` (x 더하기 0은 x다)



### 벤 다이아그램
논리와 집합 이론은 죽이 잘 맞는다. [[#Chapter 2]]에 정리한 내용들을 벤 다이아그램을 사용해서 정리해본다.

https://betterinformatics.com/resources/inf1-cl/venn

#todo logic_venn_diagram 폴더 내에 있는 캡처들 파워포인트로 수정해서 여기에 올림.

#### Hasse Diagram
논리의 Hasse DIagram. 뭔가.. 보면은 이해될 것 같기도 하고..?

https://en.wikipedia.org/wiki/Logical_connective

![[Logical_connectives_Hasse_diagram.svg]]

### 명제 논리 참고 자료
[Tutorial Point - 이산수학](https://www.tutorialspoint.com/discrete_mathematics/discrete_mathematics_propositional_logic.htm)

[논리연산자 목록 1](http://discrete.openmathbooks.org/dmoi3/appendix-1.html)

[논리연산자 목록 2](https://en.wikipedia.org/wiki/List_of_logic_symbols)

[수학 알파벳 목록](https://en.wikipedia.org/wiki/Mathematical_Alphanumeric_Symbols)

[나무위키 - 명제 논리](https://namu.wiki/w/%EB%AA%85%EC%A0%9C%20%EB%85%BC%EB%A6%AC)

[명제 논리 Latex](https://www.geeksforgeeks.org/logic-notations-in-latex/?ref=lbp)

## 술어 논리
[술어 논리(Predicate Logic)](https://en.wikipedia.org/wiki/First-order_logic)

1차 논리(First-Order Logic) 또는 Quantificational Logic 이라고도 불린다.