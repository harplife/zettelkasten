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
언어학(Linguistic)에 있어 명사(名辭)는 문장의 문법에서 개념적으로 그 구성단위가 되는 낱말을 가르킨다. 명사의 종류는 주사(主辭)와 빈사(賓辭) 그리고 계사(繫辭)로 구분된다.

[주사/주어(Subject)](https://en.wikipedia.org/wiki/Subject_(grammar))는 발언의 주제가 되는 것(Thing)이다.

[빈사/술어(Predicate)](https://en.wikipedia.org/wiki/Predicate_(grammar))는 주어의 동작, 상태, 성질에 대해 서술하는 설명(Description)이 된다.

[계사(Copula)](https://en.wikipedia.org/wiki/Copula_(linguistics))는 주사와 빈사를 연결하여 긍정 또는 부정의 뜻을 나타내는 말이다.

"나는 사람이다"라는 문장에서 "나"는 주어이며, "사람"은 빈사이고, "~이다"는 계사이다.

> 어떤 존재에 관한 사태판단에 있어 그 주대상(主對象)을 지시하는 판단요소를 주개념이라 하고, 주개념을 규정하는 판단요소를 빈개념(賓槪念)이라 하는데, 이때 주개념을 주사(主辭)라 하고, 빈개념을 객어(客語)·술어·빈사라 한다. 단, 빈사는 일반적으로 술어 가운데서 계사(繫辭)를 제외한 것을 일컫는다. - [네이버 블로그](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=martsong&logNo=100156041029)

[술어 논리(Predicate Logic)](https://en.wikipedia.org/wiki/First-order_logic)는 주사와 빈사로 구성된 명제로서 명제 간의 관계를 논리적으로 판단하는 체계이다.

주사를 하나의 **상수(Constant)\*** 로서 여기며, 빈사는 이 상수가 들어갈 수 있는 하나의 **함수(Function)\*\*** 로 여겨진다 - 이를 `빈사(주사)`와 같이 표현한다.

술어논리에서 "소크라테스는 사람이다"를 `사람(소크라테스)`와 같이 표현한다.

\* a, b, c 등 소문자 알파벳 기호가 특정 개체를 가리키는 경우, 이를 **상수(Constant)** 라 부른다. `a=홍길동`에서 `a`는 `홍길동`을 가르키는 상수이다. 특정 개체를 가르키지 않는 소문자 알파벳 기호(x, y, z 등)는 **변항/변수(Variable)** 라 부른다.

\*\* 빈사는 대문자 알파벳 (F, G, H 등)으로 표현된다.

명제에 변수가 사용되는 경우 (예: `사람(x)`), 이러한 명제를 열린 문장(Open Sentence)라고 한다. 열린 문장은 진리값을 가질 수 없다. 명제에 상수가 사용되는 경우 (예: `a=홍길동, 사람(a)`), 이러한 명제를 닫힌 문장(Closed Sentence)라고 한다.

술어 논리는 **양화 논리(Quantificational Logic)** 로 불리기도 하는데, 그 이유는 주사와 빈사로서 판단되는 진리가 적용될 수 있는 특정 영역(Domain) 내 범위를 존재(Existential) 또는 보편(Universal) 양화사(Quantifier)로서 정의한다는 의미에 비롯된다.

열린 문장이 의미를 지닐 수 있게 하기 위해서는 변수가 양화사를 통해 속박(Bound)되어야 한다. 양화사에 속박되지 않은 변술르 자유 변수(Free Variable)이라고 한다. 자유 변수만으로 이루어진 표현을 식(Formula)이라 부른다.

[[propositional_logic|명제 논리]]는 진리가 담긴 명제 간의 관계를 논리적으로 판단하는 체계이다  - 완전한 명제(Complete Proposition)에 참 또는 거짓을 기입하여 특정 연결사(Connectives)로 구성된 명제 간의 관계가 성립되는지를 확인하는 논리 체계이며, 명제와 관계의 진리 그 이상을 추구하지 않기 때문에 Zeroth Order ㄴ

"나는 존재한다"는 완전한 명제로서 제일 단순한() 논리로, 



명제논리는 명제와 명제의 관계로서 진리를 찾는 체계라면, 술어 논리는 

논리는 일반적으로 [[#명제 논리]]와 술어 논리로 구분한다.

명제논리는 주어와 술어를 구분하지 않고, 문장 전체를 하나의 명제로 간주하여 진리를 판별하는 법칙을 다룬다. 반대로, [술어 논리(Predicate Logic)](https://en.wikipedia.org/wiki/First-order_logic)는 주어와 술어를 구분하여 진리를 판별하는 법칙을 다룬다.

술어 논리는 술어를 중심으로 그에 딸린 주어를 나열하는 형태로 문장을 표현한다 - 그러므로, 명제를 주어와 술어로 구분한 다음 "술어(주어)"와 같은 형태로 나타낸다. 이때 주어는 변수(Variable)의 역할을 수행한다.

예시: "소크라테스는 사람이다"라는 명제는 술어 논리로 `사람(소크라테스)`와 같이 표현한다.

술어 논리를 **1차 논리(First-Order Logic)** 또는  이라고도 불린다.

명제 "모든 사람은 죽는다"와 명제 "소크라테스는 사람이다"가 있으면, 우리는 "소크라테스는 죽는다"라는 추론을 할 수 있다. 하지만 이는 명제 논리로서 나올 수 있는 추론이 아니며, 술어 논리를 사용해야 가능한 추론이다.

