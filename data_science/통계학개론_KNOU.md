# 통계학개론

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
- **변동/변산도 (Variability)** : 데이터에 각 값들의 차이를 표현하는 값을 뜻한다. 영어로 Variation, Spread, Scatter, 또는 Dispersion으로 불리기도 한다. 변산도는 최소/최대값, 범위 (Range), 사분위수(Quantile), 분산 (Variance), 편차 (Deviation), 분포 (Distribution), 비대칭도/왜도 (Skewness), 그리고 첨도 (Kurtosis)로 표현된다.
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
- **모집단 평균 수식** : 모집단의 크기(관찰값의 개수)가 $n$인 데이터의 관찰값을 $x_1, x_2, \ldots, x_n$ 이라고 할 때, 모집단의 평균은 $\bar{x} = \frac{\sum_{i=1}^{n}x_i}{n}$ 이다.
- **표본 평균 수식** : 표본의 크기(관찰값의 개수)가 $n$인 데이터의 관찰값을 $x_1, x_2, \ldots, x_n$ 이라고 할 때, 표본의 평균은 $\mu = \frac{\sum_{i=1}^{n}x_i}{n}$ 이다.
- **편차 (Deviation)** : 관찰값에서 평균을 뺀 값. 관찰값과 평균 사이의 거리 (Distance)로 이해하면 된다.
- **분산 (Variance)** : 편차 제곱의 평균. 편차의 경향을 파악하기 위해 편차의 평균을 구할 수 있는데, 일반적인 방법으로 평균을 구하는 경우, 편차의 값이 양수 또는 음수이기 때문에 값은 언제나 0이 된다. 따라서, 편차의 제곱을 구함으로서 양수/음수 문제를 해결한다. 하지만 완변한 "편차 평균"이라 보기는 힘들다.
- **표준편차 (Standard Deviation)** : 데이터의 변산도(Variability/Spread), 즉, 데이터가 얼만큼 "퍼져있는지"를 측정하는데 일반적으로 사용되는 값이다. 진정한 편차의 평균이라 볼 수 있으며, 분산에 제곱근(Square Root)을 계산하면 구할 수 있다. 참고 : 어떠한 값의 제곱에 제곱근을 구하면 이 값의 절대값 (Absolute Value)이 구해진다 -> $|x| = \sqrt{x^2}$.
- 표준편차 수식 : 표

### 개인 노트
- 

### 참고 자료
- [w3schools ai statistics](https://www.w3schools.com/ai/ai_statistics.asp)
- [w3schools descriptive statistics](https://www.w3schools.com/statistics/statistics_descriptive_statistics.php)