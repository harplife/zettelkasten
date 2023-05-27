# 출석대체시험
## 2019
> [!quiz]
> 알고리즘 생성 단계 중에서 시간 복잡도 및 공간 복잡도를 계산하는 단계는?
> 1. 정확성 분석
> 2. 알고리즘 기술
> 3. 효율성 분석
> 4. 알고리즘 설계
>
> > [!warning]- answer
> > 답 : (3)
> > 풀이 : 알고리즘의 효율성은 필요한 수행 시간과 공간(메모리)에 따라 계산된다.


> [!quiz]
> 선형 자료구조 중에서 데이터에 대한 임의 접근을 제공하는 것은?
> 1. 큐
> 2. 배열
> 3. 연결 리스트
> 4. 그래프
>
> > [!warning]- answer
> > 답 : (2)
> > 풀이 : 배열은 인덱스-원소값 쌍의 집합으로, 하나의 인덱스가 주어지면 이와 연관된 원소값이 결정되는 대응 관계를 갖는다. 따라서, 배열은 인덱스를 이용해서 빠른 임의 접근이 가능하다.

> [!quiz]
> 다음 트리에 대한 설명 중 <ins>틀린</ins> 것은?
> ![[Pasted image 20230527092519.png]]
> 1. 트리의 차수는 3이다.
> 2. 노드의 차수가 0인 노드의 개수는 7이다.
> 3. 노드 D의 후손 노드의 개수는 노드 L의 조상 노드의 개수보다 많다.
> 4. 트리의 레벨은 4이다.
>
> > [!warning]- answer
> > 답 : (4)
> > 풀이 : 노드의 레벨은 있지만 트리의 레벨이란 없다. 트리의 높이/깊이는 4 이다.

> [!quiz]
> 전 이진 트리(full binary tree)에서 루트 노드를 포함한 비단말 노드가 3개인 경우 단말 노드의 개수는?
> 1. 2
> 2. 3
> 3. 4
> 4. 6
>
> > [!warning]- answer
> > 답 : (3)
> > 풀이 : 전 이진 트리의 비단말 노드의 개수는 언제나 단말 노드의 개수보다 1개 적다 ($n_{0}-1$). 반대로, 단말 노드는 비단말 노드보다 1개 많다. 교과서 16 페이지 참고.

> [!quiz]
> 알고리즘의 시간 복잡도에 대한 설명으로 <ins>틀린</ins> 것은?
> 1. 입력 데이터의 상태에 따라 달라진다.
> 2. 입력 크기에 대한 함수로 표현한다.
> 3. 알고리즘에서 기본 명령의 수행 횟수의 합으로 나타낸다.
> 4. 일반적으로 평균 수행 시간을 평가 척도로 사용한다.
>
> > [!warning]- answer
> > 답 : (4)
> > 풀이 : 수행 시간은 기본 명령의 수행 횟수의 합으로 나타내되, 일반적으로 다양한 상태의 데이터로 알고리즘의 수행 시간을 계산하여 그 중 최악의 수행 시간이 평가 척도로 사용된다.

> [!quiz]
> 점근 성능의 표기법 중에서 최악의 수행 시간만 나타낼 때 적합한 것은?
> 1. $O$ ("big-oh")
> 2. $\Omega$ ("big-omega")
> 3. $\Theta$ ("big-theta")
> 4. $\Phi$ ("big-phi")
>
> > [!warning]- answer
> > 답 : (1)
> > 풀이 : #todo 교과서에서 제대로 설명되지 않음. 일반적으로 사용되는게 O 표기법이니 이것이 답!

> [!quiz]
> 분할정복 방법의 분할 과정에서 입력 크기 n인 문제가 일정하기 않은 크기의 두 개의 작은 문제로 분할되는 알고리즘은?
> 1. 합병 정렬
> 2. 이진 탐색
> 3. 퀵 정렬
> 4. 동전 거스름돈 문제
>
> > [!warning]- answer
> > 답 : (3)
> > 풀이 : 퀵 정렬은 피벗(pivot)을 기준으로 주어진 배열을 두 개의 부분배열로 분할한다. 피벗은 랜덤하게 선택되기 때문에 부분배열의 크기가 일정하지 않다.

> [!quiz]
> 다음과 같이 주어진 데이터에 대해 적절한 처리를 거친 후 이진 탐색을 적용하였을 때 접근 시간이 가장 빠른 데이터는?
> $60\ 25\ 40\ 35\ 50\ 55\ 20\ 45\ 30$
> 1. 20
> 2. 30
> 3. 40
> 4. 50
>
> > [!warning]- answer
> > 답 : (3)
> > 풀이 : 이진 탐색은 원하는 값과 중앙값을 비교하여 중앙값 리턴 또는 왼쪽/오른쪽 부분배열을 대상으로 탐색을 순환하는 알고리즘이다. 주어진 데이터 그대로 보면 중앙값인 $50$ 에 대한 접근 시간이 가장 빠르지만, 데이터를 정렬하면 중앙값은 $40$ 이 된다.

> [!quiz]
> 분할정복 방법을 적용한 알고리즘 중에서 결합 단계를 거쳐야만 하는 것은?
> 1. 퀵 정렬
> 2. 합병 정렬
> 3. 이진 탐색
> 4. 분할함수를 이용한 선택 문제
>
> > [!warning]- answer
> > 답 : (2)
> > 풀이 : 합병 정렬(merge sort)은 입력 데이터를 2개의 부분배열로 분리하며 각 부분배열을 또 다시 분리함을 반복하고, 더 이상 분리될 수 없을 때 다시 결합하면서 값들을 비교하는 방식으로 하는 알고리즘이다.

> [!quiz]
> 차원이 각각 $3 \times 2$, $2 \times 4$, $4 \times 1$ 인 세 개의 행렬 $M_{1}$, $M_{2}$, $M_{3}$ 을 연쇄적으로 곱하는 데 필요한 최소의 기본 곱셈 횟수는?
> 1. 14
> 2. 20
> 3. 24
> 4. 36
>
> > [!warning]- answer
> > 답 : (1)
> > 풀이 : 교과서.. 참고해봤자?

> [!quiz]
> 다음 중 동적 프로그래밍을 적용한 알고리즘은?
> 1. 데이크스트라 알고리즘
> 2. 프림 알고리즘
> 3. 플로이드 알고리즘
> 4. 크루스칼 알고리즘
>
> > [!warning]- answer
> > 답 : (2)
> > 풀이 : 합병 정렬(merge sort)은 입력 데이터를 2개의 부분배열로 분리하며 각 부분배열을 또 다시 분리함을 반복하고, 더 이상 분리될 수 없을 때 다시 결합하면서 값들을 비교하는 방식으로 하는 알고리즘이다.

3(2)112

## 2009
> [!quiz]
> 그래프에서 정점 $v1$ 에서 $vn$ 까지의 (    )라는 것은 간선으로 연결된 정점들의 순차열 $v1, v2, ⋯, vn$ 이다. 빈 칸에 들어갈 알맞은 용어는 무엇인가?
> 1. 차수
> 2. 길이
> 3. 경로
> 4. 깊이
>
> > [!warning]- answer
> > 답 : (3) 경로
> > 풀이 : 경로 정의


> [!quiz]
> 다음과 같은 이진 트리를 무엇이라고 하는가?
> ![[Pasted image 20230527084343.png|200]]
> 1. 전 이진 트리
> 2. 포화 이진 트리
> 3. 완전 이진 트리
> 4. 경사 이진 트리
>
> > [!warning]- answer
> > 답 : (1) 전 이진 트리
> > 풀이 : 전 이진 트리 (Full Binary Tree)는 모든 노드의 차수가 $0$ 또는 $2$ 인 이진 트리이다.

> [!quiz]
> 배낭 문제에 가장 효과적으로 적용될 수 있는 알고리즘 설계기법은?
> 1. 분할 정복 방법
> 2. 상각 분석 방법
> 3. 동적 프로그래밍 기법
> 4. 욕심쟁이 방법
>
> > [!warning]- answer
> > 답 : (4) 욕심쟁이 방법
> > 풀이 :
> > - 배낭 문제는 배낭의 용량을 초과하지 않는 범위 내에서 배낭에 들어 있는 물체의 이익의 합이 최대가 되도록 물체를 넣는 방법을 찾는 문제이다.
> > - 배낭 문제의 최적 해(Optimal Solution) 는 단위 무게당 이익이 가장 큰 물체부터 최대한 배낭에 담는 것이다.
> > - 욕심쟁이 방법은 해를 구하는 일련의 선택 단계마다 전후 단계의 선택과는 무관하게 해당 단계에서 가장 최선이라고 여겨지는 국부적인(Local) 최적해를 선택함으로써 전체적인(Global) 최적해를 구하는 방법이다.
> > - 물체를 쪼개서 넣을 수 있다는 가정하에 욕심쟁이 방법이 배낭 문제에 가장 효과적이다.
> >
> > 참고 : 4장

다음 그래프가 의미하는 점근적 표기법에 해당하는 것은 어느 것인가?
![[Pasted image 20230527084940.png|200]]
1. f(n)=O(g(n))
2. f(n)=Ω(g(n))
3. f(n)=o(g(n))
4. f(n)=Θ(g(n))

답 : 