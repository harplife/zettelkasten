# 통계학개론

- [R for Data Science](https://r4ds.had.co.nz/) 책이 무료로 웹사이트로 제공되니 꼭 참고할 것.
- [CRAN Contributed Documentation](https://cran.r-project.org/other-docs.html) 에 무료 R 및 통계 교육 자료가 넘쳐있음.
- [Probability Theory (Wiki)](https://en.wikipedia.org/wiki/Probability_theory) 에 여러가지 흩어보는 것도 좋을 듯.

## Chapter 1
- **통계학**은 불확실한 현상을 이해하기 위해 데이터를 수집하고, 그 데이터가 가지고 있는 패턴을 요약, 분석하여 이로부터 불확실한 현상에 대한 결론을 찾는 학문이다.
- **통계학의 역할**에는 데이터의 수집, 데이터의 요약, 추론이 있다.
- **통계방법**은 기술통계와 추측통계로 나뉜다.
- **기술통계 (Descriptive Statistics)** : 데이터를 수치나 표, 그래프 등으로 요약하여 데이터의 특징을 드러내는 통계 방법.
- **추측통계 (Inferential Statistics)** : 데이터를 이용하여 그 데이터가 대표하는 불확실한 전체에 관해 추측하고 그 추측의 신뢰성을 계량화하는 통계방법.
- **단위 (Unit)** : 관측되는 개별 대상. 관측 단위 (Observational Unit), 개인 (Individual), 케이스 (Case) 등의 다양한 이름으로 불린다.
- **변수 (Variable)** : 각 단위에 대해 관측되는 특성 (Characteristic, Feature). 필드 (Field) 등의 이름으로도 불린다.
- **관찰값/관측치 (Observation)** : 각 단위로부터 관측한 특성의 값.
- **데이터 (Data)** : 하나 이상의 변수에 대한 관찰값의 모음.
- **모집단 (Population)** : 관심 대상이 되는 모든 개체의 모임.
- **유한모집단 (Finite Sample)** : 개체 수가 유한개인 모집단.
- **무한모집단 (Infinite Sample)** : 개체 수가 무한개인 모집단.
- **표본 (Sample)** : 모집단을 알기 위해 실제로 관측한 모집단의 일부.
- **단순랜덤표집 (Simple Random Sampling)** : 유한모집단에서 n개의 개체로 이루어진 가능한 모든 부분집합이 표본으로 선택될 확률이 같도록 설계된 표본 표집 방법.
- **모수 (Parameter)** : 모집단의 특성을 나타내는 대푯값.
- **통계량 (Statistic)** : 표본의 특성을 나타내는 대푯값.
- 모수의 값을 정확히 추정하기 위해 표본을 표집하는 방법이나, 모수에 근접한 통계량을 구하는 방법, 통계량을 이용한 모수 추정의 신뢰도를 계량화하는 방법 등이 모두 **통계학의 문제**라고 할 수 있다.

### R 언어 사용법
- **R**은 통계 분석과 그래프 작성에 쓰이는 무료 소프트웨어이자 프로그래밍 언어이다. **R Development Core Team**에 의하여 지속적으로 유지, 개선되고 있다.
- R은 [CRAN (Comprehensive R Archive Network)](https://cran.r-project.org/) 에서 다운로드 할 수 있다.
- R 설치 도중 '구성 요소 설치' 단계에서 'Message translations' 요소의 체크박스를 해제하는 것이 추천된다 - 이로서 R의 출력 언어가 한글 대신 영어가 된다.
- R 전용 편집기는 RStudio 이다. 하지만 현재 [Posit](https://posit.co/) 으로 이름이 변경되었다. 변경된 이유는 R 뿐만 아니라 Python도 사용될 수 있고, 앞으로 데이터 과학과 관련된 모든 언어와 호환될 것을 목표로 하기 때문이라고 한다.
- RStudio에서 `File -> New File -> R Script` 를 클릭해서 새로운 R 파일을 생성한다. 여기에 코드를 작성하고 실행하면 그 결과가 밑에 콘솔에 출력 된다. 코드 실행은 Ctrl + Enter 로 지정된 영역만 실행할 수 있고, 또는 Ctrl + Shift + Enter 로 소스 전체를 실행할 수 있다.
- 소스에 `setwd("C:\Users\ben\Projects\r_projects")` 명령어를 넣고 실행하면, 지정된 경로로 작업 디렉토리가 지정된다. 작업 디렉토리를 지정함으로서 코드에서 파일을 import/export 할 때 지정된 폴더 내에 있는 파일을 상대 경로로서 손쉽게 불러낼 수 있다.
- RStudio 설정에서 **기본 작업 디렉토리**를 설정하는 방법도 있다. `Tools -> Global Options -> Options -> General -> Default working directory (when not in a project)`를 지정해주면 된다.
- R 자체에 여러 함수가 내장되어 있지만, 기본으로 포함되지 않은 함수를 모아 놓은 **패키지**를 따로 설치할 수 있다. R 패키지는 라이브러리(Library)로 불리기도 한다. CRAN 사이트에서 어떤 패키지들이 있는지 확인할 수 있다.
- **R 패키지 설치**는 RStudio에서 손쉽게 할 수 있다. RStudio 화면에 오른쪽 아래 창을 보면 `Packages`라는 탭이 보인다. 여기서 `Install` 버튼을 누르면 따로 패키지를 찾고 설치하는 창이 뜬다. 한번 설치된 패키지는 RStudio를 닫아도 유지된다.
- R 콘솔 창에서 패키지를 설치하는 방법도 있다. `install.packages("패키지명")`를 입력하면 된다.
- 패키지를 주기억장치에 로드하려면 `library(패키지명)` 함수를 사용하면 된다. RStudio를 닫으면 로딩된 모든 패키지들은 사라진다.
- R로 그래프를 그릴 때 유용한 패키지로 `ggplot2` 이 있다. 소스에서 `library(ggplot2)`를 입력하고 실행하면 이 패키지가 로딩된다.

### 개인 노트
- A singular person or a group of people is a **unit** of people. A **characteristic** or a feature of people can include weight, height, gender, or anything that be observed. An **observation** is the value(s) of a characteristic. A collection of observation(s) is referred to as **data**.
- Example A : There is a group of people. Each person from that group is considered a unit. Weight is the characteristic of people that we are interested in. An observation is made by measuring the weight of each person. This collection of measured values of weight is the data.


## Chapter 2
- **질적/범주형 변수 (Qualitative Variable)** : 유한개의 범주 중 하나의 값을 취하는 변수.
- **명목형 변수 (Nominal Variable)** : 범주들에 의미 있는 순서를 정할 수 없는 질적 변수.
- **순서형 변수 (Ordinal Variable)** : 범주 간의 의미 있는 순서를 정할 수 있는 질적 변수.
- **양적 변수 (Quantitative Variable)** : 양적인 수치로 측정되는 변수.
- **연속형 변수 (Continuous Variable)** : 어떤 실수 구간 안의 모든 값을 가질 수 있는 양적 변수.
- **이산형 변수 (Discrete Variable)** : 취할 수 있는 값을 셀 수 있는 양적 변수.
- 기술통계에서 경향성 (Tendency)과 변산도 (Variability)가 핵심이다.
- **경향성 (Tendency)** : 데이터에서 중심이 되는 값들을 뜻한다. 대표값 (Representative Value) 또는 중심경향 (Central Tendency)으로 불리기도 한다. 경향성은 평균 (Mean), 중앙값 (Median), 그리고 최빈값 (Mode)으로 표현된다.
- **변동/변산도 (Variability)** : 데이터에 각 값들의 차이를 표현하는 값을 뜻한다. 영어로 Variation, Spread, Scatter (산포), 또는 Dispersion으로 불리기도 한다. 변산도는 최소/최대값, 범위 (Range), 사분위수(Quantile), 분산 (Variance), 편차 (Deviation), 분포 (Distribution), 비대칭도/왜도 (Skewness), 그리고 첨도 (Kurtosis)로 표현된다.
- **도수분포표 (Frequency Table)** : 데이터에서 각 값의 출현빈도나 비슷한 값끼리 묶은 구간별로 관측된 데이터의 개수를 정리한 표.
- **특이점 (Outlier)** : 대부분의 데이터로부터 멀리 떨어져 있는 관찰값. 딱히 고정된 값 또는 수식이 있는 것은 아니다.
- **종 모양 분포 (Bell-Shaped Distribution)** : 데이터 분포(각 값/구간의 출현 빈도수/확률)를 그래프로 표현하였을 때, 전체 그래프 모형이 종 모양과 유사한 경우를 뜻한다. 이 때 그래프는 좌우 대칭 (Symmetry)이며, 가운데에 봉우리 (Peak)가 하나 있다. 대표값(평균, 중앙값, 최빈값)이 모두 가운데에 있는 값과 근접하다는 것이 특징이다. 확률을 표현하는 경우 정규 분포 (Normal Distribution) 또는 가우시안 분포 (Gaussian Distribution)로 불리기도 한다.
- **쌍봉우리형 분포 (Bimodal Distribution)** : 데이터 분포를 그래프로 표현하였을 때, 전체 그래프 모형이 종 모양 분포와 유사하되, 가운데에 봉우리가 두 개 있는 경우를 뜻한다. 종 모양 분포와 마찬가지로 좌우 대칭이다. 데이터가 이러한 분포를 가진 경우, 평균/중앙값/최빈도가 데이터를 대표하기 적절하지 못 할 수 있다.
- **치우친/기운 분포 (Skewed Distribution)** : 데이터 분포를 그래프로 표현하였을 때, 전체 그래프 모형이 좌우 대칭을 이루지 않고 한쪽으로 데이터가 크고 반대쪽이 작은 경우를 뜻한다. 데이터가 대부분 모여 있는 부분, 즉, 분포의 무게중심이 치우친 방향을 두고 왼쪽 또는 오른쪽으로 치우친 분포로 불린다. 하지만 영어로는 분포의 무게중심이 치우친 방향의 반대, 즉, 꼬리 (Tail)의 방향으로서 Left-Skewed 또는 Right-Skewed Distribution으로 부른다.
- **균등분포 (Uniform Distribution)** : 데이터가 집중되지 않고 모두 비슷한 수준으로 고르게 퍼져 있는 분포를 뜻한다.
- **평균 (Mean)** : 양적 변수의 분포의 균형을 이루는 무게중심의 위치에 해당하는 값.
    - 평균은 모집단 평균 (Population Mean)과 표본 평균 (Sample Mean)으로 나누어 진다.
    - 평균은 관찰값들의 합을 관찰값 개수로서 나누는 것으로 계산할 수 있다.
    - 모집단 평균은 x-bar($\bar{x}$)로 표현되고, 표본 평균은 뮤(Mu, $\mu$)로 표현된다.
    - 평균은 특이점의 영향을 많이 받는 단점이 있다.
- **모집단 평균 수식** : 모집단의 크기(관찰값의 개수)가 $n$인 데이터의 관찰값을 $x_1, x_2, \ldots, x_n$ 이라고 할 때, 모집단의 평균은 $\bar{x} = \frac{\sum_{i=1}^{n}x_i}{n}$ 이다.
- **표본 평균 수식** : 표본의 크기(관찰값의 개수)가 $n$인 데이터의 관찰값을 $x_1, x_2, \ldots, x_n$ 이라고 할 때, 표본의 평균은 $\mu = \frac{\sum_{i=1}^{n}x_i}{n}$ 이다.
- **편차 (Deviation)** : 관찰값에서 평균을 뺀 값. 관찰값과 평균 사이의 거리 (Distance)로 이해하면 된다.
- **분산 (Variance)** : 편차 제곱의 평균. 편차의 경향을 파악하기 위해 편차의 평균을 구할 수 있는데, 일반적인 방법으로 평균을 구하는 경우, 편차의 값이 양수 또는 음수이기 때문에 값은 언제나 0이 된다. 따라서, 편차의 제곱을 구함으로서 양수/음수 문제를 해결한다. 하지만 완변한 "편차 평균"이라 보기는 힘들다.
    - 모집단의 분산(aka, 모분산)은 관찰값 개수를 그대로 사용하여 편차 제곱의 평균을 구하지만, 표본의 분산은 관찰값 개수에서 1을 빼서 구한다. 표본분산을 구할때 1을 빼는 이유 중 하나는 이렇게 구한 표분분산의 값이 모분산의 값에 더 가깝다는 것이다 (이는 수학적으로 증명된 사실).
    - 모분산은 시그마 제곱(Sigma Squared, $\sigma^2$)로 표현되며, 표본 표준편차는 $s^2$로 표현된다.
    - 분산의 단위는 데이터 측정단위의 제곱 형태로 표시된다. 예를 들어, 킬로그램($kg$) 단위로 측정한 몸무게 데이터의 분산은 $kg^2$으로 표시된다.
- **표본분산 수식** : 관찰값의 개수(표본 크기)가 $n$인 데이터의 관찰값을 $x_1, x_2, \ldots, x_n$ 이라고 할 때, 표본 분산은 $s^2 = \frac{\sum_{i=1}^{n}(x_i - \bar{x})^2}{n-1}$ 이다. 참고로 $\bar{x}$는 평균을 뜻한다.
- **표준편차 (Standard Deviation)** : 데이터의 변산도(Variability/Spread), 즉, 데이터가 얼만큼 "퍼져있는지"를 측정하는데 일반적으로 사용되는 값이다. 진정한 편차의 평균이라 볼 수 있으며, 분산에 제곱근(Square Root)을 계산하면 구할 수 있다.
    - 참고 1 : 어떠한 값의 제곱에 제곱근을 구하면 이 값의 절대값 (Absolute Value)이 구해진다 -> $|x| = \sqrt{x^2}$.
    - 참고 2 : 편차 절대값(편차 제곱 + 제곱근)의 합을 관찰값 크기로 나눈 것을 [Mean Absolute Deviation](https://byjus.com/maths/mean-absolute-deviation/)이라 부른다. MAD 대신 표준편차를 사용하는 이유는 잘 모르겠는데, 이 [stackexchange 답변](https://stats.stackexchange.com/a/88829)이 어느 정도 도움이 되는 듯 하다.
    - 모집단 표준편차(aka, 모표준편차)는 시그마(Sigma, $\sigma$)로 표현되며, 표본 표준편차는 $s$로 표현된다.
- **표본 표준편차 수식** : 관찰값의 개수(표본 크기)가 $n$인 데이터의 관찰값을 $x_1, x_2, \ldots, x_n$ 이라고 할 때, 표본 표준편차는 $s = \sqrt{s^2} = \sqrt{\frac{\sum_{i=1}^{n}(x_i - \bar{x})^2}{n-1}}$ 이다. 참고로 $\bar{x}$는 평균을 뜻한다.
- 분산, 표준편차가 크면 데이터가 평균을 중심으로 광범위하게 분포되어 있다는 뜻이다. 반대로, 작으면 데이터가 평균을 중심으로 조밀하게 모여있다는 뜻이다. 분산과 표준편차가 0인 경우는 데이터가 모두 같은 값을 가진 경우다.
- 평균은 특이점의 영향을 많이 받는 통계량으로, 평균을 이용하여 계산한 분산과 표준편차도 특이점의 영향을 많이 받는다.
- **변이계수 (Coefficient of Variation)** : 표준편차의 크기를 평균에 대한 비율로 나타낸 값으로, 변수 2개의 이상의 변동을 비교하는 경우 일반적으로 사용된다.
- **변이계수 수식** : 모집단 변이계수는 $CV = \frac{\sigma}{\mu}$이며, 표본 변이계수는 $CV = \frac{s}{\bar{x}}$ 이다.
- 중앙값 (Median) : 데이터를 크기 순서대로 정렬 했을 때 정확히 중앙에 위치하는 값.
    - 관찰값의 개수가 짝수인 경우, 일반적으로 중앙에 위치한 2개 관찰값의 평균을 사용한다. 참고로 프로그램으로 이를 계산하는 경우, 사용될 수 있는 패키지 또는 함수들의 계산식이 다를 수도 있으니 주의해야 한다.
- **사분위수 (Quantiles)** : 데이터를 크기 순서대로 정렬 했을 때 이 데이터를 4등분하는 3개의 값. 관찰값 개수의 짝수/홀수 여부에 따라 값이 다를 수 있다.
    - 1사분위수(First Quantile, $Q1$) : 전체 데이터 중 값이 낮은 $1/4$와 나머지를 가르는 값. 첫번째 관찰값과 중앙값 사이의 중앙값으로 생각하면 될 듯.
    - 2사분위수(Second Quantile, $Q2$) : 중앙값.
    - 3사분위수(Third Quantile, $Q3$) : 전체 데이터 중 값이 낮은 $3/4$와 나머지를 가르는 값. 마지막 관찰값과 중앙값 사이의 중앙값으로 생각하면 될 듯.
- **사분위수 범위 (InterQuartile Range, IQR)** : 3사반위수에서 1사분위수를 뺀 값으로, 데이터의 산포를 설명하기 위해 사용된다. 특이점을 분류하는데 사용될 수도 있다. 가장 작은 데이터와 가장 큰 데이터에 영향을 받지 않음으로, 특이점의 영향을 잘 받지 않는다 (Robust).
- **백분위수 (Percentile)** : 교과서 정의는 "전체 데이터의 p%가 이 값보다 작거나 같은 값"이다. 데이터를 크기 순서대로 정렬 했을 때 이 데이터를 100등분하는 99개의 값으로 이해하는게 좋을 듯 하다. 관찰값 개수의 짝수/홀수 여부에 따라 값이 다를 수 있다.
    - 1, 2, 3사분위수는 각각 25백분위수, 50백분위수, 75백분위수에 해당한다.
- **다섯 수치요약 (Five-Number Summary)** : 최소값, 1사분위수, 2사분위수, 3사분위수, 최대값
- **상자그림 (Boxplot)** : 다섯 수치요약을 나타낸 그래프

### R 언어 사용법
- `<-`와 `=`는 대입 연산자로서, 이 기호의 오른쪽에 있는 값을 왼쪽의 객체에 저장한다 (예: `a <- 1`).
- `c(elements)` : 벡터 생성 함수. 예: `height <- c(165, 151, 162)`
- `int : int` : 왼쪽값부터 오른쪽값까지 1씩 증가하는 벡터 생성. 예: `cten <- 1:10`. 참고로 왼쪽,오른쪽값 포함됨.
- `seq(start, stop, interval)` : 초기값에서 종료값까지 일정 간격으로 증가하는 벡터 생성 함수. 예: `eventen <- seq(0,10,2)`. 참고로 초기값, 종료값은 포함됨(inclusive).
- `rep(element, n_reps)` : 지정된 값을 n번 반복하는 벡터를 생성하는 함수. 예: `fivetens <- rep(10,5)`.
- 벡터 결합 : `c(v1,v2,..)` 함수를 사용하여 여러 벡터를 하나의 벡터로 결합할 수 있음.
- 벡터 연산 : 길이가 동일한 벡터끼리 사칙연산(덧셈,뺄셈,나눗셈,곱셈)이 가능함. 예: `a+b, a-b, a/b, a*b`. 참고로 논리연산도 가능함.
- `as.factor(vector)` : 범주형 벡터 변환 함수. 예: `cat <- as.factor(1:4)`. 참고로 범주형 벡터는 사칙연산이 불가능함.
- `as.character(vector)` : 문자열 벡터 변환 함수. 예: `numchrs <- as.character(1:10)`. 참고로 문자열 벡터는 사칙연산이 불가능함.
- `cbind(v1,v2,..)` : 여러 벡터를 각각의 열(column)로 합친 행렬을 생성함.
  ```r
  > a <- rep(10,5)
  > b <- rep(20,5)
  > cbind(a,b)
        a  b
  [1,] 10 20
  [2,] 10 20
  [3,] 10 20
  [4,] 10 20
  [5,] 10 20
  ```
- `rbind(v1,v2,..)` : 여러 벡터를 각각의 행(row)으로 합친 행렬을 생성함.
  ```r
  > a <- rep(10,5)
  > b <- rep(20,5)
  > rbind(a,b)
    [,1] [,2] [,3] [,4] [,5]
  a   10   10   10   10   10
  b   20   20   20   20   20
  ```
- `matrix(data,nrow,ncol)` : 입력된 벡터를 지정된 행/열 개수로 맞추어 행렬을 생성하는 함수. 행 개수만 지정해도 열 개수가 자동으로 계산되며 (반대도 마찬가지), 지정된 행/열 개수가 벡터 길이와 일치하지 않으면 경고문이 뜬다. 행렬을 채우는 순서는 열을 기준으로 한다는 것 주의.
  ```r
  > c <- matrix(1:6,2,3)
  > c
       [,1] [,2] [,3]
  [1,]    1    3    5
  [2,]    2    4    6
  ```
- 행렬곱 (Matrix Multiplication) : `%*%`은 행렬곱셈 연산자이다.
  ```r
  > a <- matrix(1:4,2,2)
  > b <- matrix(2:5,2,2)
  > a %*% b
       [,1] [,2]
  [1,]   11   19
  [2,]   16   28
  ```
- `solve(matrix)` : 입력된 행렬의 역행렬(Inverse Matrix)를 구하는 함수이다.
- `data.frame(v1,v2,..)` : 데이터프레임을 생성하는 함수.
  ```R
  > name <- c('kim','lee','park','choi')
  > age <- c(20, 32, 17, 51)
  > sex <- as.factor(c('M','F','F','F'))
  > df <- data.frame(name, age, sex)
  > df
    name age sex
  1  kim  20   M
  2  lee  32   F
  3 park  17   F
  4 choi  51   F
  > df$name
  [1] "kim"  "lee"  "park" "choi"
  > df[1,1]
  [1] "kim"
  ```
- `fivenum(vector)` : 다섯수치요약 함수

### ggplot 막대그래프 (1)
- `ggplot2`는 [ The Grammar of Graphics](https://www.amazon.com/Grammar-Graphics-Statistics-Computing/dp/0387245448/ref=as_li_ss_tl) 라는 책을 기준으로 만들어진 데이터 시각화 패키지이다. R 자체에도 간단히 그래프를 그리는 함수들이 있지만, `ggplot2` 패키지를 사용하면 좀 더 상세하게, 멋지게 그릴 수 있다. 더 자세한 정보는 [패키지 공식 사이트](https://ggplot2.tidyverse.org/) 또는 [[ggplot2_cheatsheet.pdf]] 에서 찾아볼 수 있다.
- `ggplot2` 패키지를 이용하여 그래프를 그릴 때는 `ggplot()+geom_<graph>()` 형태를 취해야 한다.
- `ggplot2`가 제공하는 함수들은 공식 사이트 [Function Reference](https://ggplot2.tidyverse.org/reference/index.html) 에서 설명해준다.
- `ggplot()` 함수는 그래프를 초기화한다. 다른 그림(레이어)가 그려질 캔버스(Canvas)를 준비한다고 생각하면 된다. 함수 안에 `data` 매개변수를 통해 그래프를 그릴 데이터를 받는다.
- `geom` 함수에는 여러 종류가 있으며, 막대그래프를 그릴때는 `geom_bar()`를 사용한다 ([참고](https://ggplot2.tidyverse.org/reference/geom_bar.html)).
- `geom_bar()` 함수는 제공된 데이터에 대하여 기본적으로 `stat_count()`를 사용함으로 각 변수에 대한 빈도수를 계산한다.
- `forcats`는 범주형 데이터를 다루기 위한 함수들을 제공하는 패키지이다. 더 자세한 정보는 [패키지 공식 사이트](https://forcats.tidyverse.org/index.html) 또는 [[forcats_cheatsheet.pdf]] 에서 찾아볼 수 있다.
- `forcats` 패키지가 제공하는 `fct_infreq()` 함수는 범주형 데이터에서 빈도수가 높은 순서대로 변수들(Levels)을 정렬한다.
- `geom_bar()` 함수에 `mapping=aes()` 는 주어진 형식에 따라 데이터와 그래프를 매핑해준다. `aes(x=fct_infreq(transp_data))` 를 지정함으로서, 그래프의 X-Axis에 출력될 정보들이 매핑된다. `y` 매개변수는 직접 지정하지 않아도 기본적으로 `stat_count()`로 계산된 빈도수들에 따라 자동으로 그래프의 Y-Axis 출력될 정보들이 매핑된다.
- `xlab()` 함수를 사용하여 그래프 X-Axis 라벨링(타이틀)을 지정할 수 있다.

#### 소스코드
```R
# 패키지 로드
library(ggplot2)
library(forcats)

# 데이터 입력
transp_opts <- c('bicycle', 'bus', 'walking')
transp_data <- sample(transp_opts, size=30, replace=T)
transp_df <- data.frame(transp_data)

# 막대그래프 출력
ggplot(data=transp_df) + geom_bar(mapping=aes(x=fct_infreq(transp_data))) +
  xlab("Transportation")
```

#### 출력 결과
![[Pasted image 20230104115645.png]]


### ggplot 막대그래프 (2)
- 이 예시는 `geom_bar()`에 기본적으로 제공하는 빈도수 계산을 무시하고, 직접 각 변수에 대한 값을 지정하는 방식으로 막대그래프를 출력한다.
- `geom_bar()` 함수 안에 `stat='identity'` 를 지정함으로서 `mapping=aes(y=)` 에 지정된 값들로 막대그래프를 출력한다.

#### 소스코드
```R
# 패키지
library(ggplot2)

# 데이터
cats = c('underweight', 'normal', 'overweight', 'obese')
weight_level <- factor(cats,levels=cats)
weight_count <- c(6,69,27,13)
weight_perc <- weight_count/sum(weight_count)*100
df <- data.frame(weight_level, weight_count, weight_perc)

# 그래프 출력
ggplot(data=df) + 
  geom_bar(mapping=aes(x=weight_level, y=weight_perc), stat='identity') +
  xlab("Weight Levels") + ylab("Percentage (%)")
```

#### 출력 결과
![[Pasted image 20230104125719.png]]

### ggplot 파이차트

#### 소스코드
```R
# 패키지
library(ggplot2)

# 데이터
transp_opts <- c('bicycle', 'bus', 'walking')
transp_data <- sample(transp_opts, size=30, replace=T)
transp_table <- table(transp_data)
transp_names <- names(transp_table)
transp_counts <- as.numeric(transp_table)

transp_df <- data.frame(transportation=transp_names, count=transp_counts)

# 그래프 출력
ggplot(data=transp_df) +
  geom_bar(
    mapping=aes(x='',y=count, fill=transportation),
    stat='identity'
  ) +
  coord_polar('y', start=0) + xlab('') + ylab('')
```

#### 출력 결과
![[Pasted image 20230104134645.png]]

### hist 함수
- R에서 제공하는 built-in 함수 `hist()` 를 사용하여 막대그래프를 그릴 수 있다. 마찬가지로 빈도수는 자동으로 계산된다.
- `set.seed(int)` 함수로 랜덤 시드를 지정해준다. 랜덤 시드를 지정해줌으로서 복제(Replicate)가 가능한 난수를 생성할 수 있다.
- `runif(n, min, max)` 함수로 균등분포 난수를 생성할 수 있다. 또는, `rnorm(n, mean, sd)` 함수로 정규분포 난수를 생성할 수 있다.
- `floor()` 함수는 벡터 안에 있는 값들을 내림 해주어 `int` 형식으로 변환해준다.
- `hist()` 함수 안에 `breaks` 매개변수를 사용하여 x 값의 간격을 지정할 수 있다.

#### 소스코드
```R
# 난수 시드 지정
set.seed(420)

# 데이터
scores <- floor(runif(100, 1, 100))

# 막대그래프 출력
hist(scores)
```

#### 출력 결과
![[Pasted image 20230104140010.png]]

### boxlplot 함수

#### 소스코드
```R
age <- floor(runif(100, 20, 80))

boxplot(age, ylab='Age')
```

#### 출력 결과
![[Pasted image 20230104193513.png | 300]]

### 참고 자료
- [w3schools ai statistics](https://www.w3schools.com/ai/ai_statistics.asp)
- [w3schools descriptive statistics](https://www.w3schools.com/statistics/statistics_descriptive_statistics.php)
- [byjus mean median mode](https://byjus.com/maths/mean-median-mode/) : shows advanced methods of calculating the measures of central tendency.
- [dplyr 패키지](https://dplyr.tidyverse.org/) : 데이터 처리 전용 패키지

## Chapter 3
- **통계적 실험 (Statistical Experiment)** : 주어진 조건 하에 가능한 모든 사건 중 특정 사건의 발생 가능성을 추정 가능토록 무한히 반복될 수 있는 절차. 확률적 실험으로도 불린다.
- **표본공간 (Sample Space)** : 통계적 실험의 모든 가능한 결과의 집합. 수학에서 주로 $S$로 표시된다.
- **사건 (Event)** : 표본공간의 한 부분집합. 수학에서 주로 대문자 알파벳 ($A, B, C, ..$)으로 표시된다.
- **이산형 표본공간 (Discrete Sample Space)** : 표본공간의 원소 개수가 유한개(Finite)거나, 무한하나 셀 수 있는 경우(Countably Infinite)를 뜻한다.
    - 주사위 던지기 같은 경우, 나올 수 있는 결과는 $S=\set{1,2,3,4,5,6}$, 즉, 원소 개수가 6개로서 유한하다. 따라서, 주사위 던지기의 표본공간은 이산형이다.
    - 상공에 날아다니는 새(Bird)의 마리 수는 셀 수 있지만 무한하다 -> $S=\set{1,2,3,..}$. 따라서, 상공에 날아다니는 새 마리 수 세기 문제의 표본공간은 이산형이다.
- **연속형 표본공간 (Continuous Sample Space)** : 표본공간의 원소 개수가 셀 수 없는 무한(Uncountably Infinite)한 경우를 뜻한다.
    - 피자 배달에 걸리는 시간을 알아보는 실험의 표본공간은 $0$보다 큰 모든 실수, 즉, $S=\set{(0,\infty)}$ 이다. 이러한 배달 시간 문제는 모두 연속형 표본공간을 갖는다. 참고로, 배달 시간이 20분 이내 걸릴 사건을 $A=\set{(0,20)}$와 같이 표현한다.
- **확률 (Probability)** : 어떤 사건이 일어날 가능성을 0과 1 사이의 실수로 표시한 것..이라 간단하게 표현할 수 있지만, 실제로 확률의 "정의"라는 것은 [아주 심오한 토픽](https://en.wikipedia.org/wiki/Probability_interpretations)이다.
    - **객관적(Objective) 확률** : 고정된 조건 하에 규칙을 찾음으로서 발생 확률을 계산할 수 있다는 관점.
        - 객관적 확률은 주사위 게임, 카드 게임 등 완벽히 파악할 수 있는 조건/시스템/환경으로서 어떤 사건이 발생하는 규칙을 찾을 수 있는 경우에만 적용된다.
        - 주사위에는 6면이 있고, 각 면이 나올 가능성이 균등하다는 조건 하에 각 면이 나올 확률은 $1/6$ 이 된다. 이는 주사위를 여러번(무한번) 던졌을 때 특정 면이 나온 수와 총 던진 횟수의 비율이 $1/6$에 근접해진다는 것으로서 검증할 수 있다.
        - 다르게 정리하면, 확률은 반복 가능한 "객관적" 절차에 따라 찾을 수 있다는 가정 하에 확률을 여러 실험의 상대도수(Relative Frequency)의 극한(Limit)으로 정의하는 것이 객관적으로 바라보는 확률이다.
    - **주관적(Subjective) 확률** : 지식, 경험, 통찰력, 정보에 입각하여 어떤 사건이 발생할 확률을 계산할 수 있다는 관점.
        - 주관적 확률은 새로운 정보로서 기존의 "믿음"을 갱신하는 시스템으로 볼 수 있다.
        - 주사위 게임, 카드 게임 같은 경우 특정 사건이 발생하는 모든 조건을 완벽히 파악할 수 있다. 하지만 게임이 아닌 현실 세계에서는 어느 사건이 발생하기 위한 모든 조건을 완벽히 파악하기는 어렵다. 예를 들어, 어떤 사람이 감기 걸릴 확률은 감기 전파 경로, 건강 상태 등 수많은 변수가 있기 때문에 계산하기 어렵다. 이러한 경우, 객관적 확률로 계산할 수 없다. 이러한 경우는 주관적 확률로 계산 하는게 더 용이하다.
        - 학생 A가 감기 걸릴 확률을 구해본다. 작년 겨울에 교실 내 학생 100명 중 30명이 감기 걸렸다는 정보를 확보한다. 현재 학생 A가 감기 걸릴 확률은 30%이다. 작년 겨울에 감기 걸렸던 30명 중 12명이 남자였다는 정보를 새로 확보한다. 학생 A는 남자이다. 따라서, 학생 A가 감기 걸릴 확률이 
    - 주관적 확률, 객관적 확률 중 어느 하나가 더 좋다고 말할 수는 없다. 
    - 객관적 확률은 [빈도주의적 확률 (Frequentist Probability)](https://en.wikipedia.org/wiki/Frequentist_probability) 로 주로 불린다. 
- 확률의 고전적 정의 (Classical Definition of Probability) : 

### 참고자료
- [확률론(Probability Theory) Wiki](https://en.wikipedia.org/wiki/Probability_theory)
- [데이터 사이언스 스쿨 - 수학 편](https://datascienceschool.net/02%20mathematics/00.00%20%EC%86%8C%EA%B0%9C%EC%9D%98%20%EA%B8%80.html)