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

참의 기호는 `⊤`로 표기된다. 거짓의 기호는 `⊥`로 표기된다.

latex:
- $\top$
- $\bot$

### 논리연산
**논리 연산(Logical Operation)** : 명제들의 관계를 참과 거짓으로 나타내는 연산.

**논리 연산자(Logical Operator)** : 명제들의 관계를 나타내는 기호. 논리연산에 사용된다. **연결사(Connective)** 라고 부르기도 한다.

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

참고 : 영어 Disjunction은 "2개 이상의 무언가가 흩어지는 지점(point)"을 의미함으로서, 한국어로 직역하면 이접점(離接點)이라 할 수 있다. 논리 관점에서 봤을때, 흩어진 모든 것을 뜻하는게 아닐까 싶다.

#### 배타적 논리합
[배타적 논리합(Exclusive Disjunction)](https://en.wikipedia.org/wiki/Exclusive_or) : 두 개의 명제 중 하나만 참인 경우 참이 되는 논리연산. 논리연산자로 두 명제 사이에 `⊕`, `⊻`, `≢`, 또는 `↮`로 표현된다 (예: `𝑃 ⊕ 𝑄`).

![[exclusive_disjunction_venn_diagram.svg]]

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

![[negation_disjunction_venn_diagram.svg]]

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

![[conjunction_venn_diagram.svg]]

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

참고 : 영어 Conjunction은 "2개 이상의 무언가가 연결되는 지점(point)"을 의미함으로서, 한국어로 직역하면 합접점(合接點)이라 할 수 있다. 논리 관점에서 봤을때, 명제들의 공통점이 되지 않을까 싶다.

#### 부정 논리곱
[부정 논리곱(Negation of Conjunction)](https://en.wikipedia.org/wiki/Sheffer_stroke) : 논리곱의 반대되는 논리연산으로, 두 명제가 참이 되는 경우 연산 결과가 거짓이 된다. 논리연산자로 두 명제 사이에 `↑`, `⊼`, 또는 `|`로 표현된다 (예: `𝑃 ↑ 𝑄`).

![[negation_conjunction_venn_diagram.svg]]

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
[조건명제(Conditional Proposition)](https://en.wikipedia.org/wiki/Material_conditional) : 명제 `𝑃`와 `𝑄`가 있을 때, 명제 `𝑃`가 명제 `𝑄`에 영향을 주는 관계를 조건명제라 한다. 논리연산자로 두 명제 사이에 `→`, `⇒`, 또는 `⊃`로 표현된다 (예: `𝑃 → 𝑄`).

![[implication_venn_diagram.svg]]

조건명제의 `𝑃`는 [전건(Antecedent)](https://en.wikipedia.org/wiki/Antecedent_(logic)) 이라 불리운다.

조건명제의 `𝑄`는 [후건(Consequent)](https://en.wikipedia.org/wiki/Consequent) 이라 불리운다.

조건명제의 특징은 전건이 참이면 후건이 참이된다는 것을 **보장(Guarantee)** 한다는 것이다. 조건명제의 진리는 "이 보장이 지켜졌는가?"의 답으로 볼 수 있다. 따라서,
1. 전건이 참이고 후건이 참이면 보장이 지켰기 때문에 조건명제는 참이된다.
2. 전건이 참이고 후건이 거짓이면 보장이 지키지 않았기 때문에 조건명제는 거짓이 된다.
3. 전건이 거짓인 경우에 대해서 보장을 하지 않았고, 보장은 지켜지지 않았기 *않았기* (NOT NOT) 때문에 조건명제는 참이된다.

참고 : 이 [SO 답변](https://math.stackexchange.com/a/229845) 덕분에 조건명제를 잘 정리할 수 있었다!

> | 𝑃 | 𝑄 | 𝑃 → 𝑄 |
|:-:|:-:|:-----:|
| T | T |   T   |
| T | F |   F   |
| F | T |   T   |
| F | F |   T   |
> 조건명제 `𝑃 → 𝑄` 진리표

조건명제를 "If .. Then ..(.. 이면 .. 이다)"로 읽는다. 이렇게 읽으면 마치 두 명제가 인과관계(Causality)를 가진 것 처럼 느껴진다. 하지만 조건명제는 인과관계를 말하는 것이 아니며, 결과를 뜻하는 것도 아니다 - 두 명제의 관계로서 도출될 수 있는 사실 (숨어있는 사실)이 조건명제며, 이를 [함의(Implication)](https://www.britannica.com/topic/implication) 라고도 한다.

참고 : 우리가 일반적으로 생각하는 인과관계는 [[#쌍조건명제]]와 더 가깝다.

조건명제 예시:
1. "이탈리아의 수도가 뉴욕이라면, 대한민국의 수도는 서울이다" = 참
2. "지구가 평면이면, 지구인은 모두 화성에 산다" = 참
3. "1+3=4이면, 2x3=5이다" = 거짓
4. "삼각형 내각의 합이 180도라면, 포도는 과일이다" = 참

조건명제를 때로는 `~𝑃 ∨ 𝑄` 표현할 때가 있다. 이를 [[#논리적 동치]]라고 한다.

#### 조건명제의 역설
https://en.wikipedia.org/wiki/Paradoxes_of_material_implication

#### 필요성과 충분성
https://en.wikipedia.org/wiki/Necessity_and_sufficiency

**필요조건(Necessary Condition)** : 필요성(Necessity)은 결론을 내기 위해선 조건이 꼭 있어야 한다는 것을 뜻한다. 조건 없이는 결론이 존재할 수 없다 (If not P, then not Q). 하지만 조건이 있다고 꼭 결론이 있다는 것은 아니다.

예를 들어, "X가 숫자다"라는 조건이 있다면, "X는 3보다 크다"라는 결론이 나올 수 있다. 이 조건이 없다면, 결론은 나올 수가 없다. 하지만 조건이 참이라고 결론이 꼭 참인 것은 아니다.

**충분조건(Sufficient Condition)** : 충분성(Sufficiency)은 조건이 참이면 결론이 참임을 보장한다는 것을 뜻한다. 하지만 조건이 거짓이라고 결론도 거짓이라 하는 것은 아니다.

예를 들어, 조건이 "x = 2"라면, "x² = 4"가 결론이 되기에 충분하다고 볼 수 있다. 하지만 조건이 거짓이여도 결론은 참이 될 수 있다 (조건이 "x = -2"인 경우).

#### 쌍조건명제
[쌍조건명제(Biconditional Proposition)](https://en.wikipedia.org/wiki/Logical_biconditional) : 조건과 결론이 양방향으로 이루어지는 조건명제를 뜻한다. 조건명제 "if P, then Q"가 있다면, 반대로 "if Q, then P"도 성립된다는 것이다. 조건-결론 관계에 있어 **동치(Equivalence)** 라고 불리기도 한다. 필요성과 충분성 둘 다 성립하다는 의미에 있어 쌍조건명제의 조건을 **필요충분조건** 이라 부른다. 논리연산자로 두 명제 사이에 `↔` 또는 `⇔`로 표현된다.

![[biconditional_venn_diagram.svg]]

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
[논리적 동치(Logical Equivalence)](https://en.wikipedia.org/wiki/Logical_equivalence) : 두 명제의 진리값이 항상 동일하다는 뜻. **동치관계** 라고 부르기도 한다.

[[#쌍조건명제]]하고 연산은 동일하지만, 조건-결론 관점이 아닌 논리적 동등성 관점에서 명제들을 봤을 떄 논리적 동치 표현을 사용한다. 논리연산자로 두 명제 사이에 `≡`로 표현된다.

논리적 동치를 ".. means the same as .."라고 읽는다. 한국어론 "..는 ..와 동일하다"라고 이해하면 된다.

논리적 동치 예시:
1. "비가 내린다"는 "비가 내린다"와 동일하다 (`𝑃 ≡ 𝑃`).
2. "비가 내리고 날씨가 춥다"는 "날씨가 춥고 비가 내린다"와 동일하다 (`𝑃∧𝑄 ≡ 𝑄∧𝑃`).

### 조건명제의 변형
**조건명제의 3가지 변형**:
1. [역(Converse)](https://en.wikipedia.org/wiki/Converse_(logic)) : 조건명제에서 명제의 위치를 바꾼 경우 (예: `𝑃 → 𝑄`의 역은 `𝑄 → 𝑃`이다).
2. [이(Inverse)](https://en.wikipedia.org/wiki/Inverse_(logic)) : 조건명제에서 두 명제의 진리값이 반대가 되는 경우 (예:  `𝑃 → 𝑄`의 이는 `~𝑃 → ~𝑄`이다).
3. [대우(Contrapositive)](https://en.wikipedia.org/wiki/Contraposition) : 조건명제에서 converse와 inverse 둘 다 적용되는 경우 (예: `𝑃 → 𝑄`의 대우는 `~𝑄 → ~𝑃`이다).

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

### 논리적 동치 법칙
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
[교환법칙(Commutative Law)](https://en.wikipedia.org/wiki/Commutative_property#Propositional_logic)은 특정 논리연산자를 기준으로 명제들의 위치를 교환할 수 있음을 뜻한다.

논리합의 교환성
- `𝑃∨𝑄 ≡ 𝑄∨𝑃`

[논리곱의 교환성 (Commutativity of Conjunction)](https://en.wikipedia.org/wiki/Commutativity_of_conjunction)
- `𝑃∧𝑄 ≡ 𝑄∧𝑃`

동치의 교환성 ( #todo complete commutative law of equivalence)
- `𝑃↔𝑄 ≡ 𝑄↔𝑃`

주의 : 위키에 3번째 교환법칙 예시는 좀 이상하니 일단 무시한다.

#### 결합법칙
[결합법칙(Associative Law)](https://en.wikipedia.org/wiki/Associative_property#Propositional_logic)은 특정 논리연산자를 기준으로 연산의 순서를 변경할 수 있음을 뜻한다.

논리합의 결합성
- `(𝑃∨𝑄)∨𝑅 ≡ 𝑃∨(𝑄∨𝑅)`

논리곱의 결합성
- `𝑃∧(𝑄∧𝑅) ≡ (𝑃∧𝑄)∧𝑅`

쌍조건명제의 결합성
- `(𝑃↔𝑄)↔𝑅 ≡ 𝑃↔(𝑄↔𝑅)`

#### 분배법칙
[분배 법칙(Distributive Law)](https://en.wikipedia.org/wiki/Distributive_property#Propositional_logic)은 특정 논리연산자를 기준으로 연산을 분배할 수 있음을 뜻한다.

##### 논리합의 분배성
일반 수학과는 달리 명제논리에는 논리합을 기준으로 분배가 가능하다.

논리곱(∧)에 대한 논리합(∨)의 분배성
(Distribution of Disjunction over Conjunction)
- `𝑃∨(𝑄∧𝑅) ≡ (𝑃∨𝑄)∧(𝑃∨𝑅)`

논리합(∨)에 대한 논리합(∨)의 분배성
(Distribution of Disjunction over Disjunction)
- `𝑃∨(𝑄∨𝑅) ≡ (𝑃∨𝑄)∨(𝑃∨𝑅)`

동치(↔)에 대한 논리합(∨)의 분배성
(Distribution of Disjunction over Equivalence)
- `𝑃∨(𝑄↔𝑅) ≡ (𝑃∨𝑄)↔(𝑃∨𝑅)`

##### 논리곱의 분배성
논리합(∨)에 대한 논리곱(∧)의 분배성
(Distribution of Conjunction over Disjunction)
- `𝑃∧(𝑄∨𝑅) ≡ (𝑃∧𝑄)∨(𝑃∧𝑅)`

논리곱(∧)에 대한 논리곱(∧)의 분배성
(Distribution of Conjunction over Conjunction)
- `𝑃∧(𝑄∧𝑅) ≡ (𝑃∧𝑄)∧(𝑃∧𝑅)`

##### 함의의 분배성
함의(→)에 대한 함의(→)의 분배성
(Distribution of Implication)
- `𝑃→(𝑄→𝑅) ≡ (𝑃→𝑄)→(𝑃→𝑅)`

동치(↔)에 대한 함의(→)의 분배성
- `𝑃→(𝑄↔𝑅) ≡ (𝑃→𝑄)↔(𝑃→𝑅)`

논리곱(∧)에 대한 함의(→)의 분배성
- `𝑃→(𝑄∧𝑅) ≡ (𝑃→𝑄)∧(𝑃→𝑅)`

#### 항등법칙
-  `𝑃∨F ≡ 𝑃` (x 더하기 0은 x다)
-  `𝑃∧T ≡ 𝑃` (x 곱하기 1은 x다)

### 항진명제
항진명제(Tautology) : 항상 참인 명제.

`𝑃∨~(𝑃∧𝑄)`은 항상 참이 됨으로 항진명제이다.

항진을 직관적으로 이해하려면 제일 쉬운 예시로 `𝑃∨𝑃`가 있다. "비가 내리거나, 비가 안 내린다" 또는 "비가 안 내리거나, 비가 내린다"는 참이다.

또 다른 쉬운 예시로 `𝑃→𝑃`가 있다. "비가 내리면, 비가 내린다" 또는 "비가 안 내리면, 비가 안 내린다"는 참이다.

### 모순명제
모순명제(Contradiction) : 항상 거짓인 명제.

`(𝑃∧𝑄)∨~(𝑃∨𝑄)`은 항상 거짓이 됨으로 모순명제이다.

모순을 직관적으로 이해하려면 제일 쉬운 예시로 `𝑃∧~𝑃`가 있다. "비가 내리고, 비가 안 내린다", 또는 "비가 안 내리고, 비가 내린다"는 거짓이다.

`𝑃→~𝑃`, 즉, "비가 내리면, 비가 안 내린다"가 모순일거라 생각할 수 있는데, 전건이 거짓일 경우 무조건 참이되는 조건명제의 특성으로 모순명제가 아니다.

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

[형식적 오류(Formal Fallacy)](https://en.wikipedia.org/wiki/Formal_fallacy) - just for fun

[Deduction vs. Induction vs. Abduction](https://www.merriam-webster.com/words-at-play/deduction-vs-induction-vs-abduction) - just for fun too.

[Truth Table Generator - Stanford](https://web.stanford.edu/class/cs103/tools/truth-table-tool/)

## 술어 논리
**술어(Predicate)** 는 문장을 구성하는 기본요소로서 **주어(Subject)** 의 동작, 상태, 성질에 대해 서술하는 말이다.

"A는 B이다" 또는 "A는 B가 아니다"에서 A를 "주어"라고 하고 B를 "술어"라고 한다.

논리는 일반적으로 [[#명제 논리]]와 술어 논리로 구분한다.

명제논리는 주어와 술어를 구분하지 않고, 문장 전체를 하나의 명제로 간주하여 진리를 판별하는 법칙을 다룬다. 반대로, [술어 논리(Predicate Logic)](https://en.wikipedia.org/wiki/First-order_logic)는 주어와 술어를 구분하여 진리를 판별하는 법칙을 다룬다.

술어논리는 술어를 중심으로 그에 딸린 주어를 나열하는 형태로 문장을 표현한다 - 그러므로, 명제를 주어와 술어로 구분한 다음 "술어(주어)"와 같은 형태로 나타낸다. 이때 주어는 변수(Variable)의 역할을 수행한다.

예시: "소크라테스는 사람이다"라는 명제는 술어논리로 `사람(소크라테스)`와 같이 표현한다.

술어 논리를 **1차 논리(First-Order Logic)** 또는 **Quantificational Logic** 이라고도 불린다.

명제 "모든 사람은 죽는다"와 명제 "소크라테스는 사람이다"가 있으면, 우리는 "소크라테스는 죽는다"라는 추론을 할 수 있다. 하지만 이는 명제 논리로서 나올 수 있는 추론이 아니며, 술어 논리를 사용해야 가능한 추론이다.

